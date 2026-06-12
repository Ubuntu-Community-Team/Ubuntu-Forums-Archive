---
title: "Help! Internet issues when trying to install Ubuntu or Mint on windows 8 laptop"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by woodapple on 2013-03-17
Hey guys,

I am completely new to using linux and would appreciate any feedback.  I want to be able to duel boot windows 8 and Linux.  I have been attempting to install Linux Ubuntu or Mint on my new Toshiba Satellite laptop that came with windows 8, but have had several issues.  I have tried disabling securityboot, changing the boot up settings from UEFI to CFM, and using life-usbs and nothing seems to work.  I have been using the 64bit installations of Ubuntu or Mint.  I am having the following 2 issues whenever I try to install Ubuntu or Mint.

1) There is no internet detected (wired or wireless).  When using windows 8, I do not have trouble connecting to the internet.
-  I read one post that suggested that you can get internet issues if the "allow the computer to turn off this device to save power" option is checked for the wireless card under device manager -> properties -> power management.  I unchecked this box and it unfortunately did not fix my issue. 

2) When I start the installation process, it does not detect my windows 8 operating system and therefore I do not have the option of installing linux along side windows.

I have spent many hours trying figure this out and I am completely stuck.  I would greatly appreciate any help.  Since I was having so much installing linux ubuntu on my new computer, I decided to install it on my old laptop and I had no issues there.

Thanks,

Aaron

---

### Post by Impavidus on 2013-03-17
I understand you can run a live session (booting from the live dvd/usb)? You say you can't use wifi or wireless. Can you use a wired internet connection? You may need additional drivers to get the wireless working. Set up a wired connection and install the recommended driver. Search the dash for "additional drivers" or "additional hardware". I'm not sure, I don't use Unity myself. This way you can test your wifi. It's not persistent, but you'll know how to install the drivers later when you've installed ubuntu.

Concerning your second problem, could you open a terminal in a live session, execute the command **sudo blkid** and post the output here? Or run **gparted** and post a screenshot? It will show the layout of your partitions. This may help one of the specialists here find out why your ubuntu installer doesn't recognise your win8.

---

### Post by presence1960 on 2013-03-17
[QUOTE=Impavidus;12562059]I understand you can run a live session (booting from the live dvd/usb)? You say you can't use wifi or wireless. Can you use a wired internet connection? You may need additional drivers to get the wireless working. Set up a wired connection and install the recommended driver. Search the dash for "additional drivers" or "additional hardware". I'm not sure, I don't use Unity myself. This way you can test your wifi. It's not persistent, but you'll know how to install the drivers later when you've installed ubuntu.
 

+1

 I have a Toshiba Satellite and had to install with a wired connection. After the install was complete I went to additional drivers and the wireless driver was downloaded.

---

### Post by woodapple on 2013-03-17
Sorry, I meant to type that I do not have wired or wireless connection.  I will work on that terminal command and I will get back with you.

Aaron

---

### Post by woodapple on 2013-03-17
Impavidus and Presence1960, thank you for your input.  Using a live usb, security boot off, but UEFI mode on, I executed the sudo blkid and the sudo gparted commands.  I had to take pictures with my phone because it would not mount another usb to transfer the screenshots too.  Since my wired internet is also not working, I do not know how I can download the drivers for the wireless internet.

[ATTACH=CONFIG]240301[/ATTACH][ATTACH=CONFIG]240302[/ATTACH][ATTACH=CONFIG]240303[/ATTACH]

---

