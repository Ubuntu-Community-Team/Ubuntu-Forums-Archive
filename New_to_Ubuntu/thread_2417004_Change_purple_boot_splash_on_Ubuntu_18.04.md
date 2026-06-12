---
title: "Change purple boot splash on Ubuntu 18.04"
date: 2019-04-19
forum: New to Ubuntu
---

### Post by klie97 on 2019-04-19
Hi to everyone I'm new to Ubuntu.

I need to change the purple boot flash to black one.

I have tried different options but nothing works for me.

I changed:

ubuntu-logo.script 
[COLOR=#242729][FONT=Consolas]Window.SetBackgroundTopColor (0.0, 0.00, 0.0);     # Nice colour on top of the screen fading to
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]Window.SetBackgroundBottomColor (0.0, 0.00, 0.0);  # an equally nice colour on the bottom
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]ubuntu-logo.grub
[COLOR=#101094][FONT=inherit]if[/FONT][/COLOR][COLOR=#303336][FONT=inherit] background_color [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#101094][FONT=inherit]then[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
   clear
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]fi[/FONT][/COLOR] 
By terminal and directly on file.

Removed "quiet splash", replaced with "", and "nomodeset" but nothing.


Any suggestion?


Thank you!

---

### Post by jeremy31 on 2019-04-19
Moved to New to Ubuntu

---

### Post by Cheltspy on 2019-04-19
After you have changed that file(ubuntu-logo.script) you must update the theme with

sudo update-initramfs -u

---

### Post by johnsonmartincox on 2019-04-19
Correct one. Thank you.

---

### Post by klie97 on 2019-04-19
I have updated but... nothing... I don't understand what I'm wrong...

---

### Post by klie97 on 2019-04-19
> **Cheltspy said:**
> After you have changed that file(ubuntu-logo.script) you must update the theme with

sudo update-initramfs -u


[COLOR=#000000][INDENT]I have updated but... nothing... I don't understand what I'm wrong...[/INDENT]


[/COLOR]

---

### Post by Cheltspy on 2019-04-19
Looks like you aren't set to plymouth-theme-ubuntu-logo

Try
sudo apt-get install --reinstall plymouth-theme-ubuntu-logo

reboot and then edit the file in
/usr/share/plymouth/themes/ubuntu-logo

---

### Post by klie97 on 2019-04-19
> **Cheltspy said:**
> Looks like you aren't set to plymouth-theme-ubuntu-logo

Try
sudo apt-get install --reinstall plymouth-theme-ubuntu-logo

reboot and then edit the file in
/usr/share/plymouth/themes/ubuntu-logo

A message on terminal tells me that it isn't possible to download plymouth-theme-ubuntu-logo....

---

### Post by oldos2er on 2019-04-19
Can you copy/paste the terminal output here please?

---

### Post by klie97 on 2019-04-19
> **oldos2er said:**
> Can you copy/paste the terminal output here please?

sudo apt-get install --reinstall plymouth-theme-ubuntu-logo
[sudo] password for dodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of plymouth-theme-ubuntu-logo is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Cheltspy on 2019-04-19
You're not installed along side/in side windows?

---

### Post by richard378 on 2019-04-21
Does this help? [http://www.ashwinraon.in/changing-boot-splash-screen-in-ubuntu-18-04/](http://www.ashwinraon.in/changing-boot-splash-screen-in-ubuntu-18-04/)

---

### Post by klie97 on 2019-04-23
> **Cheltspy said:**
> You're not installed along side/in side windows?

No...

---

### Post by klie97 on 2019-04-23
> **richard378 said:**
> Does this help? [http://www.ashwinraon.in/changing-boot-splash-screen-in-ubuntu-18-04/](http://www.ashwinraon.in/changing-boot-splash-screen-in-ubuntu-18-04/)

The terminal show me this, after run the first command sudo apt update

Hit:1 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic InRelease
Ign:2 [http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu](http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu) bionic InRelease
Err:3 [http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu](http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu) bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

