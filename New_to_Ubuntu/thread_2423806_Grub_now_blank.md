---
title: "Grub now blank"
date: 2019-07-29
forum: New to Ubuntu
---

### Post by cmcesq on 2019-07-29
Summary: When I boot, the Grub screen is dark grey. No text.  Eventually boots into Ubuntu.  

Background: this is an OLD laptop that I had originally set up with Win10 and Ubuntu 18.4 dual boot so i could learn/play with Ubuntu.  I decided to remove Win10.  I did so by using GParted to remove the Win10 partition and then expanding the Ubuntu partition to use the entire drive.  Then I used Grub Customizer to remove the Windows option from the list.  Since then, i've had this problem. Upon power-up, screen goes grey.  There's *nothing* listed.  

When I use Grub Customizer, it does still show various options (e.g. Ubuntu, Ubuntu with Linux 4.18, etc.)  I've tried using Customizer to change color and font options.  That did nothing.   I've also tried running Boot-Repair and also just reinstalling Grub2 completely.  Not fixed.  To be clear, this is NOT affecting boot.  I just let it sit, and eventually it does go into Ubuntu.   But it's slowing down the process.   Thank you.

---

### Post by oldfred on 2019-07-29
When you have only one install, grub is not normally shown. It just boots to default (only) entry.

       With 18.04 or later to always see menu, you can edit grub & then update grub.
sudo nano /etc/default/grub 
 sudo update grub.

Change this:
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu

---

### Post by Impavidus on 2019-07-30
There was no need to use grub customizer. Just running update-grub would have removed the Windows entry after you deleted the Windows partition. I've never used grub customizer, but I've seen many threads here about the problems it caused.

If you install Ubuntu as the only system on that computer, the installer gives you a /etc/default/grub that hides the grub menu. If you install it alongside Windows, the installer will give you a /etc/default/grub that shows the grub menu. /etc/default/grub isn't changed automatically when you delete Windows, so the menu should still be there. I think grub customizer hid your menu.

Can you show the contents of your /etc/default/grub?

---

### Post by oldfred on 2019-07-30
Grub customizer creates its own grub2 files in /etc/grub.d with proxy in the name.

If you do a total reinstall of grub2, it then restores the default grub files & settings. You may still have the customizer's backup of original grub2 files in a sub-folder which can then be deleted.

You can manually edit grub settings.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) 
    
       [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

