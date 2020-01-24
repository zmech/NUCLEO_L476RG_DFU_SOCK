# NUCLEO_L476RG_DFU_SOCK
MicroPython board definition NUCLEO_L476RG_DFU_SOCK

## Firmware
Clone the board definitions to your MicroPython ports/stm32/boards folder.
```
cd micropython/ports/stm32/boards
git clone https://github.com/zmech/NUCLEO_L476RG_DFU_SOCK
```
Open NUCLEO_L476RG_DFU_SOCK folder, open mpconfigboard.h and uncomment spi flash size line wich you are using.
For exsample 64 Mbit AT25SF641.
```
// SPI Flash(uncomment right size of flash chip)
//#define MICROPY_HW_SPIFLASH_SIZE_BITS (8 * 1024 * 1024)
//#define MICROPY_HW_SPIFLASH_SIZE_BITS (16 * 1024 * 1024)
//#define MICROPY_HW_SPIFLASH_SIZE_BITS (32 * 1024 * 1024)
#define MICROPY_HW_SPIFLASH_SIZE_BITS (64 * 1024 * 1024)
//#define MICROPY_HW_SPIFLASH_SIZE_BITS (128 * 1024 * 1024)
```
Save and build firmware
```
cd ..
make BOARD=NUCLEO_L476RG_DFU_SOCK
```
## Flashing via DFU 
To put the board in DFU mode,connect the BOOT0 (CN7 pin7) to the VDD (CN7 pin5) with jumper and connect USB.
![Jumper position](https://github.com/zmech/NUCLEO_F401RE_DFU_SOCK/blob/master/bootjumper.jpg)
Now you can flash the board using DFU with the command:

`make BOARD=NUCLEO_L476RG_DFU_SOCK deploy`

Once the upload is complete, connect BOOT0 to the GND (CN7 pin8) and press reset button.
