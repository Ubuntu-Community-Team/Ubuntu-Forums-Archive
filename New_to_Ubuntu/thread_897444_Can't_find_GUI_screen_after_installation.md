---
title: "Can't find GUI screen after installation"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Xavi_R on 2008-08-22
I have just installed Ubuntu several times over trying both the PC version, Server version and alternative versions. The all start up with text based input.

I have searched to find how I can install a graphical interface like Gnome of KDE and I cannot find clear instructions as to what actually needs installing and how I get to initialise the program.

I am a complete newbie to Linux and just cannot find the information I need. Can anyone point me to a step by step guide to getting my PC up and running using the graphical interface?

---

### Post by mcduck on 2008-08-22
To get the graphical desktop, use the Desktop-CD to install.

Alternate-CD also gives the graphical desktop, unless you choose some other install option.

Server version doesn't install any graphical environment.

I don't know what the "PC version" you mentioned would be.. 

Anway, simply starting the Desktop-CD should bring you into the graphical desktop, and then offer you the option to install Ubuntu. It will install the GUI desktop by default, Ubuntu installs Gnome, Kubuntu installls KDE and Xubuntu installs XFCE4.

If you did a normal install with the Desktop-CD, and it still boots into command line, your install ddn't work as it should,a nd you most likely get soem eror message while booting. If that is the case please post that error here, with more information about your computer, so people can try to figure out what went wrong.

---

### Post by skrållarn on 2008-08-22
Do you get to the login screen?
you can try login in textmode with ctrl+alt+f1 and type "startx"
Try also "sudo apt-get [COLOR="DarkRed"]upgrade[/COLOR]"(thanx Dougie187) to get the latest updates and then restart.

---

### Post by Dougie187 on 2008-08-22
> **skrållarn said:**
> Do you get to the login screen?
you can try login in textmode with ctrl+alt+f1 and type "startx"
Try also "sudo apt-get update" to get the latest updates and then restart.

If you are really looking to get the latest updates, you have to follow this command with
```
sudo apt-get upgrade
```
Update only searches the repositories for packages.
Whereas upgrade actually installs the updates.

However, this shouldn't fix your issue, just because if you can't get to a gui I don't think patches are going to help you. Did the live cd work?

---

### Post by Xavi_R on 2008-08-22
Thanks for the response folks, I am performing the upgrade but I can see where the issue may be located. I have tried the following ISO files:

[LIST]
**ubuntu-8.04.1-desktop-i386.iso**
[/LIST]
[LIST]
**ubuntu-8.04.1-server-i386.iso**
[/LIST]
[LIST]
**ubuntu-8.04.1-alternate-i386.iso**
[/LIST]

The first two work just fine but of course they only use the text input commandline. However the alternate ISO produces the problem.

I download the file and perform an MD5sum on the file and it says it is fine but when I perform a validation on the CD on bootup I get the following message around the 90% mark:

[COLOR="Red"]The .pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.2.4-1_i386.deb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.[/COLOR]

I thouhgt I might by-pass this issue by installing the text-based versions and be able to run some sort of apt-get to build the GUI as required.

P.S. Can the Live CD be downloaded somewhere?

---

### Post by Xavi_R on 2008-08-22
Once again, thankyou for your ideas. I reloaded the Destop version from a mirror and it appears to be working

---

