# Holybro - Kakute F7
## Uploading PX4 on Kakute F7

Kakute F7 comes with pre-loaded Betaflight. To load PX4 firmware, do the following:

### Flashing the bootloader.
- Download the [kakutef7_bl.hex](https://github.com/PX4/px4_user_guide/raw/master/assets/flight_controller/kakutef7/kakutef7_bl_0b3fbe2da0.hex) bootloader binary and read [this page](https://docs.px4.io/master/en/advanced_config/bootloader_update_from_betaflight.html) for flashing instructions.

#### [Flashing using Betaflight bootloader](https://docs.px4.io/master/en/flight_controller/kakutef7.html)

There are two options for flashing the bootloader: via Betaflight Configurator (easier), or building from source.


##### Bootloader Update using [Betaflight Configurator] (https://docs.px4.io/master/en/advanced_config/bootloader_update_from_betaflight.html)

1. You should have downloaded already the pre-built bootloader binary (this depends on the board you want to flash).
2. Download the [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases)for your platform.
Download betaflight-configurator_10.7.2_amd64.deb for ubuntu or betaflight-configurator-installer_10.7.2_win32.exe for windows






### Building Firmware

To [build PX4](https://docs.px4.io/master/en/dev_setup/building_px4.html) for this target

```make holybro_kakutef7_default```

### Installing PX4 Firmware

The firmware can be installed in any of the normal ways:

Build and upload the source
```make holybro_kakutef7_default upload```

[Load the firmware](https://docs.px4.io/master/en/config/firmware.html) using QGroundControl. You can use either pre-built firmware or your own custom firmware.

Follow this link for more detail

https://docs.px4.io/master/en/flight_controller/kakutef7.html




# Matek 743 - Mini

Steps:
1. Flash the bootloader
2. Build PX4 firmware
3. Install PX4 Firmware



## Step-1: Flash the bootloaded

1. Download pre-built bootloader binary (matek_h743-mini_bootloader.bin) from [here](https://github.com/PX4/PX4-Autopilot/tree/master/boards/matek/h743-mini/extras)
2. Download the [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases) for your platform.
TIP: If using the Chrome web browser, a simple cross-platform alternative is to install the configurator as an extension from here
3. Connect the board to your PC and start the Configurator.
4. Press the Load Firmware [Local] button
 ![image](https://user-images.githubusercontent.com/16509873/169690052-cb60e91f-5f0f-4c46-b150-223a8fde62b3.png)

5. Select the bootloader binary from the file system and then flash the board.

You should now be able to install PX4 firmware on the board.

## Step-2: Building PX4 Firmware
  - Setting up a Developer Environment [Toolchain](https://docs.px4.io/master/en/dev_setup/dev_env.html)
  ``` 
  sudo apt-get install git
  git clone https://github.com/PX4/Firmware.git --recursive
  
  cd Firmware
  bash ./Tools/setup/ubuntu.sh
  
  # reboot
  sudo reboot now
  
  make px4_sitl jmavsim
  
  ```
  Now build the Firmware for specific board insidd
  ```
  cd Firmware
  
#For Holybro Kakute 
make holybro_kakutef7_default

# Creating /home/ros2/Firmware/build/holybro_kakutef7_default/holybro_kakutef7_default.px4

# For Matek
make matek_h743-mini_bootloader

# Creating /home/ros2/Firmware/build/matek_h743-mini_bootloader/matek_h743-mini_bootloader.px4
```

## Step-3: Installing the PX4 Firmware
The firmware can be installed in any of the normal ways:
- Build and upload the source
```
# For Holybro Kakute
make holybro_kakutef7_default upload

# For Matek
make matek_h743-mini_bootloader upload

```

OR

[Load the firmware](https://docs.px4.io/master/en/config/firmware.html) using QGroundControl. You can use either pre-built firmware or your own custom firmware.



  



## Building Firmware


# Reinstall Betaflight
In order to switch back to Betaflight:

Backup the PX4 parameters, e.g. by exporting them to an SD card
Keep the bootloader button pressed while attaching the USB cable
Then flash Betaflight as usual with the Betaflight-configurator

