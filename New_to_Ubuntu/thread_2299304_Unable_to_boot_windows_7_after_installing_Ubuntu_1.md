---
title: "Unable to boot windows 7 after installing Ubuntu 14"
date: 2015-10-17
forum: New to Ubuntu
---

### Post by korhan2 on 2015-10-17
Hi, I have installed Ubuntu 14.04 LSE from USB on the free partition of my ssdhd. When I power on the notebook it boots directly to Ubuntu instead of asking for dual boot option. I tried to run boot repair but I am not sure how to repair it without damaging my current w7 installation. 

The pastebin is here..
[http://paste.ubuntu.com/12816476/](http://paste.ubuntu.com/12816476/)

---

### Post by yancek on 2015-10-17
Your boot repair output shows the windows partitions which appear to have the necessary boot files.  For some reason, the windows system was not detected so you do not have an entry for windows in the Grub menu.  Boot Ubuntu and click on the Dash icon (the Ubuntu logo in the upper left on the Desktop) and enter the word terminal in the search bar.  When you see the terminal icon, click on it and then type the command below to update the grub menu:

```
sudo update-grub
```

You will be prompted for your primary user password, enter it and hit the enter key and watch the output.  You should see a message that windows was found.  If not, run the command below:

```
sudo os-prober
```

Then repeat the update-grub command.

---

### Post by oldfred on 2015-10-17
You have a newer UEFI system, but both Windows & Ubuntu are installed in BIOS/CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You booted Boot-Repair in UEFI boot mode, better to always boot in BIOS/CSM boot mode. Make sure UEFI & Secure boot are off in UEFI and CSM is on.

---

### Post by korhan2 on 2015-10-18
I updated grub and now I can select between w7 and Ubuntu from grub  menu. Seems like my problem is solved for now, thank you for your  assistance. But how can I fix BIOS,UEFI issue? Does it cause performance  related problems if I continue using current state?

---

### Post by oldfred on 2015-10-18
UEFI has some advantages, but there is no major issue using BIOS boot.
If you convert to UEFI you have to totally reinstall & reformat drive, so bigger issue converting.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

