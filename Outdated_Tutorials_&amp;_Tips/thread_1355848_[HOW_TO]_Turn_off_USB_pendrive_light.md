---
title: "[HOW TO] Turn off USB pendrive light"
date: 2009-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by jbruni on 2009-12-15
On Windows, when we click to "safely remove" a USB pen drive, its light is turned off. We feel confident on removing it.

This didn't happen in my Kubuntu 9.10 Karmic Koala installation. After unmounting, the pen drive light still turned on.

I did some Google research, and now I am able to do turn it completely off, including the light! As I could not find this information in Ubuntu Forums, I want to share it here.

Basically, we need to **change the pendrive USB device power level to "suspend"**. How? It is as easy as changing a specific text file contents to "suspend", and save it. The whole problem lies in **finding** this file.

The complete solution for me is to run the script below, which I called "**pendrive_off.sh**"

```
#!/bin/bash
umount [COLOR=Red]**/dev/sdc**[/COLOR]
DEVICE=$(udevadm info --query=path --name=**[COLOR=Red]/dev/sdc[/COLOR]** --attribute-walk | grep '[COLOR=Red]**SanDisk**[/COLOR]' -B50 | grep 'looking at parent device' | tail -n 1 | cut -d"'" -f2)
echo 'suspend' > /sys/$DEVICE/power/level

```You need to change [COLOR=Red]**/dev/sdc**[/COLOR] to your specific pendrive location under **/dev**

And you need to change **[COLOR=Red]SanDisk[/COLOR]** to a string that identifies you pendrive.

How do you find this string? Use the following command (change /dev/sdc to your pendrive device specific location):

```

udevadm info --query=path --name=**[COLOR=Red]/dev/sdc[/COLOR]** --attribute-walk

```You will see a lot of info. You must find any text that identifies your pendrive hardware. In my case, I found and chose "**SanDisk**", the manufactor identification.

To "test" the string of your choice, try the following command. Substitute **/dev/sdc** for your pendrive location, and "**SanDisk**" for the pendrive identification string you will test.

```
udevadm info --query=path --name=[COLOR=Red]**/dev/sdc**[/COLOR] --attribute-walk | grep '**[COLOR=Red]SanDisk[/COLOR]**' -B50 | grep 'looking at parent device' | tail -n 1 | cut -d"'" -f2
```In my case, this command returns

```
/devices/pci0000:00/0000:00:1d.7/usb1/1-5
```This means that the "level" file to be changed is located at:

```
/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/power/level
```In fact, if I edit this text file and change it from "on" to "**suspend**", the pendrive turns off! This is exactly what the script does for me.

After saving the script file, it is necessary to make it executable (**chmod a+x pendrive_off.sh**). And to run it as root from the command-line, type "**sudo ./pendrive_off.sh**" being in the directory where the script is.

I am aware that this is a completely raw solution, and absolutlely raw explanation. But it just works for me. I hope that other users can improve this solution and its explanations, making them better.

---

