<!--lint disable list-item-indent-->
<!--lint disable list-item-bullet-indent-->
# Research

## brainstorming

- base housing
    - multiple laser cut plywood layers
    - best practice: press-fit connection or screw
- led module
    - LED: [Rohm MSL0402RGB](https://www.rohm.com/datasheet/MSL0402RGBU) (1.8x1.6x0.5mm RGB)
    - Driver: [TI TLC5971](http://www.ti.com/product/TLC5971) (16bit dimming, constant current driver)
    - 8 or 12 leds in a circle with ~30mm diameter
    - center with large hole
        optional usage for rotation axis or similar
- control module
    - maybe partly combined with led module
    - connector for led module (SPI + power)
    - controller
        - easy: alternative socket for [Adafruit ItsyBitsy M4](https://learn.adafruit.com/introducing-adafruit-itsybitsy-m4)
        - advanced: onboard mcu
            - mcu: Microchip ATSAMD51
            - hw compatible to ItsyBitsy M4 so only minimal fw changes needed
            - CircuitPython support
    - power
        - v1 (luxury)
            - LiFePo charger 2S
            - step-down converter
            - cells
                - [ENERpower 18650 LiFePo4 3,2V 1800 mAh](https://enerprof.de/akkus/akkus-lifepo4/akkuzellen-lifepo4/akkuzellen-lifepo4-18650/32/enerpower-18650-lifepo4-3-2v-1800-mah?c=26)
        - v2 (advanced)
            - LiFePo charger 1S
            - step-up converter
        - v3 (easy)
            - USB connection
            - external power-bank
    - user input
        - rotary dial
        - one or two of the rings of the base housing are the dials
        - inner edge of ring has slots
        - small pcb with two optical sensors
            - [GP2S700HCP](https://cdn-reichelt.de/documents/datenblatt/A500/GP2S700HCP-SHA.pdf)
                - Optimal Sensing Distance : 3mm
                - ~1€@[reichelt](https://www.reichelt.de/reflexlichtschranke-3-0mm-compact-smd-gp-2s700hcp-p146683.html?&nbc=1)
            - [GP2S60](https://www.pololu.com/file/0J683/GP2S60_DS.pdf)
                - Optimal Sensing Distance : 0.7mm
                - used by [pololu motor encoder](https://www.pololu.com/product/2591)

## LED
- [SK6805-EC15 1,5mm]() [10x = 3,39€](https://www.exp-tech.de/zubehoer/led-leuchtmittel/9951/ec15-05-10-pack)
- [SK9822-EC20 2mm]() [10x = 3,89€](https://www.exp-tech.de/zubehoer/led-leuchtmittel/9952/ec20-9822-10-pack)
- [SparkFun LuMini LED Matrix - 8x8 (64 x APA102-2020)](https://www.exp-tech.de/zubehoer/led-leuchtmittel/9337/sparkfun-lumini-led-matrix-8x8-64-x-apa102-2020?c=1100) 2,54x2,54cm 30€
- [SparkFun LuMini LED Ring - 20 x APA102-2020](https://www.exp-tech.de/zubehoer/led-leuchtmittel/9274/sparkfun-lumini-led-ring-20-x-apa102-2020?c=1100) 2,54cm 10,35€
- [Adafruit NeoPixel Ring - 12 x 5050 RGBW ~3000K](https://www.exp-tech.de/module/led-controller/7066/adafruit-neopixel-ring-12-x-5050-rgbw-leds-w/mit-integrierten-treibern-warmweiss-3000k?c=1100) 36.8mm   10,17€
- [Rohm MSL0402RGB](https://www.rohm.com/datasheet/MSL0402RGBU) (1.8x1.6x0.5mm RGB)
- [TI TLC5971](http://www.ti.com/product/TLC5971) (16bit dimming, constant current driver)


### LiFePo4 cells
- [lipopower.de](https://shop.lipopower.de)
    - [LiNANO® LiFePO Rundzelle IFR 14430, 3,2V, 400mAh (Button-Top)](https://shop.lipopower.de/LiNANOZ-LiFePO-Rundzelle-IFR-14430-32V-400mAh-Button-Top) 4,3€
    - [LiNANO® IFR16340 400 mAh Zelle SL-FMC](https://shop.lipopower.de/LiNANOZ-IFR16340-400-mAh-Zelle-SL-FMC) 3,8€
    - [LiNANO® 2450 80mAh LiFePO4 Knopfzelle mit Lötfahnen](https://shop.lipopower.de/LiNANOZ-2450-80mAh-LiFePO4-Knopfzelle-mit-Loetfahnen)
- [18650batterystore.com](https://www.18650batterystore.com)
    - [Vapcell 16340 800mAh 7A Button Top Battery](https://www.18650batterystore.com/16340-battery-p/vapcell-16340-battery-800mah.htm) 4$
    - [Epoch 18350 1100mAh 9A Battery](https://www.18650batterystore.com/18350-battery-p/epoch-18350-battery-1100mah.htm) 5$
- [akkuteile.de](https://www.akkuteile.de)
    - [IFR 10440 - 200mAh 3,2V LiFePo4 Akku (Button Top) ungeschützt](https://www.akkuteile.de/lifepo-akkus/10440/ifr-10440-200mah-3-2v-lifepo4-akku-button-top-ungeschuetzt_101105_1335) 3,9€
    - [IFR 14430 - 400mAh 3,2V LiFePo4 Akku (Button Top) ungeschützt](https://www.akkuteile.de/lifepo-akkus/14430/ifr-14430-400mah-3-2v-lifepo4-akku-button-top-ungeschuetzt_100213_2269) 3,95€
        - Entladestrom (konstant): 3C 1500mA
        - 14x44mm
    - [IFR 16340 - 400mAh 3,2V LiFePo4 Akku (Button Top) ungeschützt](https://www.akkuteile.de/lifepo-akkus/16340/ifr-16340-400mah-3-2v-lifepo4-akku-button-top-ungeschuetzt_100317_1161) 4,5€
        - Entladestrom (konstant): 3C 1200mA
        - 17x35mm
        - [Opus BT-C100: Ladegerät mit Analysefunktionen](https://www.akkuteile.de/ladegeraete/opus_500517_1574) 18,40€ (use-able as power-bank)
        - [Nitecore UMS4 - intelligentes Ladegerät für Li-Ion, LiFePo4, Ni-MH, Ni-CD Akkus](https://www.akkuteile.de/ladegeraete/nitecoresysmax/nitecore-ums4-intelligentes-ladegeraet-fuer-li-ion-lifepo4-ni-mh-ni-cd-akkus_510102_2446) 35€
    - [Schutzelektronik BMS](https://www.akkuteile.de/zubehoer/schutzelektronik)
