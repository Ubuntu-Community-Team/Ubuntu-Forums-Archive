---
title: "Booting issue"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by kd55 on 2011-10-26
Hi there,
I recently tried to install ubuntu 10.04 onto my dell laptop which already has windows 7 on it. I think the instalation hasn't worked as when I turn the computer on, after the dell loading screen, all I get is a black screen with a flashing underscore. I want to reset the computer back to the factory settings by pressing f8 as I don't think I should have even attempted to install ubuntu myself, but how do I recover files before I reset the laptop?

Any help would be great as I am i my 4th year of mu mechanical engineering degree and seemed to have just killed my computer.

Kind regards,

Kit

---

### Post by drs305 on 2011-10-26
Here is what may be happening:

Your installation may have been sucessfull but the correct video driver is not installed. Especially if the blinking cursor doesn't appear for a minute or so. If Ubuntu installs but the bootloader (GRUB) doesn't see another OS (Windows), it will boot without displaying the menu.

As it boots, try holding down the SHIFT key to see if the Grub menu displays. If it does, since Grub is one of the final things in the installation, you may just have to make a change to the menu.

I won't go into the details unless you tell us you can get the Grub menu to display.

If you can't, please boot the LiveCD and download/run the boot info script from the following page. Then post the contents of RESULTS.txt, which the script will generate. It will show us the status of your boot files.

You can get the script's donwload and instruction page by clicking the "BIS" link in my signature line.

---

### Post by kd55 on 2011-10-26
Hi drs305,

thanks for your reply. The curser comes up immediately after the dell loading screen which only takes a few seconds. Tried holding shift down but nothing happens. I thought I might try and put the computer back to its original state and then possibly try to install again when someone who knows what they are doing, are near by.

Thanks again,

Kit

---

### Post by drs305 on 2011-10-26
Yes, that doesn't sound like the issue I was describing.

If you can boot the Ubuntu LiveCD you can install an app and, if you know the drive Windows is on and it's boot files are intact, you should be able to regain your Windows boot.

To do this, boot the LiveCD and open a terminal: ALT-F2, or Applications, Accessories, Terminal.
```

sudo apt-get install lilo
```
You will be asked for your password. Type it in and press ENTER. You won't see your password as you type.
```
sudo lilo -M /dev/sda mbr
```
This assumes you have only one drive. If Windows isn't on 'sda', you will need to change the command. As the command runs, it will warn you that lilo is not configured. Don't worry about it and don't run any other commands.

Reboot and see if the computer boots to Windows. If it doesn't, please run the boot info script.

---

### Post by kd55 on 2011-10-26
Hi again,
I literally can't gain any access to a terminal window. On the dell screen, it says in the bottom right hand coner, F2 set up, F12 Boot options and these appear to be the only things I can access, If I go into boot options, it gives me options for:
cd/dvd rom: PCI ROM Setup, B13
Hard Disc: ST9320423AS
Diagnostics
Enter Setup

all these options appear on a blue window in white writing with a black backgroung (if this helps to draw a picture/show how confused by the whole thing)

---

### Post by drs305 on 2011-10-26
I'm not sure I understand the situation, but you would want the computer set to boot the CD first, which would be obtained by pressing F12. 

Hopefully you can set it to boot from the CD, then run the Ubuntu CD and select "Try Ubuntu". That would take you to a Desktop, where you would then be able to open a terminal.

---

### Post by afrim on 2011-10-29
Try installing boot-repair from your liveCD
Open terminal and enter:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```
enter: boot-repair on terminal
Go to advanced options and select > mbr options
Find the label > Partition booted by MBR and select Windows 7. Enter Apply. If this doesn't help go to windows forums and find how to restore an overwriten MBR to boot windows.

---

### Post by rng on 2011-10-31
Are you able to run ubuntu livecd at all on your computer? Further steps depend on that.

---

