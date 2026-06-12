---
title: "Problems connecting HP Deskjet 3630 in Ubuntu 14.04"
date: 2017-10-27
forum: New to Ubuntu
---

### Post by tmichaelglass on 2017-10-27
Hi
First time posting. A bit overwhelmed with all the menu options here so I hope I'm posting appropriately.

My immediate problem is getting an HP Deskjet 3632 working with my computer (Dell Inspiron 530 w/3gig ram) running Ubuntu 14.04.
I have already managed get a Deskjet 3520 working. The Deskjet 3632 must be a later series and I suspect the 3632 is an Australian market version of the 3630 series.

I have added (and removed at times) both printers, downloaded hplip, run hp setup, hp check etc, but perhaps not correctly and maybe I'm not reading the output correctly.

When I try to print something on the 3632 printer, the job goes to the print queue and eventually reads as complete without any print coming from the printer. The Deskjet 3520 prints normally (although I haven't tried photocopy, wifi or other functions).

In the longer term, am trying to learn and troubleshoot the process to install the printer on my brother's Toshiba laptop with ZorinOS installed. I presume the process will be the same.

I can always upgrade or change the OS if that is needed.

---

### Post by ajgreeny on 2017-10-27
Are these both wifi connected or USB?

Have you tried installing using cups at [http://localhost:631/](http://localhost:631/) which may help, though if hplip does not work there may be some other problem, eg the version of hplip you have installed.
Check it out at [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

---

### Post by oldfred on 2017-10-27
If newer HP printer you have to download from HP, the HPLIP in Ubuntu is usually several versions older.

With my HP 3520, I find it stops printer regularly. Not sure if how I turn it on or what. So my wife then prints something several times, then later printer spits all the copies out. I found I need to use HP Device Manager and go to last tab to start printer, if not used for a while or not printing.
Also a lot easier to configure wifi from HP device manager and USB connection that from printer.

HPLIP issue on 14.04 - manual download of plugin to solve
[http://ubuntuforums.org/showthread.php?t=2230875](http://ubuntuforums.org/showthread.php?t=2230875)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by tmichaelglass on 2017-10-28
I think I have located the problem (or at least one of them) It appears the hplip file I had did not support the newer printer. I had downloaded the appropriate file hplip-3.16.11.run but I hadn't succeed in running/applying it and the computer was still using hplip-3.14.3. What's the actual command line I should use to execute the newer version?

============================================================================================================
I have both printers set up by USB. I only use one at a time (of course) and I unplug and plug the cables as needed (using the same cable and usb port.
I tried using CUPS at [http://localhost:631/](http://localhost:631/) following the instructions.
I have been to [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and downloaded the latest version.
I have tried deleting and reinstalling printers one at a time in case there is a conflict having two similar printers.

From the terminal if I run hp-setup for the 3632, I get this.
[i]HP Linux Imaging and Printing System (ver. 3.14.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

Done.[/i]

The GUI setup will say "no devices found" on the second window.

---

### Post by mörgæs on 2017-10-28
The general rule is: New hardware runs best in a fresh install of the latest Buntu. 

> **tmichaelglass said:**
> I had downloaded the appropriate file hplip-3.16.11.run...

3.16.11 was the default version in Buntu 17.04. I assume 17.10 is even higher. 

I am confident that the other posters can make the printer work in 14.04 and I am not going to interfere in their advice. Just saying that next time you encounter hardware compatibility problems you can probably save yourself time by installing the latest Buntu.

---

### Post by ajgreeny on 2017-10-28
As you have now downloaded the appropriate file hplip-3.16.11.run, you should first uninstall the repo version of hplip you already have, then simply run that file in a terminal as shown in the instructions at [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index).

Do not run it as root with sudo but wait for the script to ask for your password at the appropriate time. You will need to ensure that you have the universe repos enabled which is probably so already, but check in "Software and updates", and that you are online as some dependencies may be needed.

It can take a while to run the script and install hplip, depending on your computer hardware, but it is very good at showing what it's doing and where it's got to so let it finish and you should be good to go.

---

### Post by oldfred on 2017-10-28
In addition, make sure the printer is plugged in to a USB port and on. It wants to see a HP printer.
If you only want WiFi, you can configure it easily when plugged in, then unplug USB.

---

### Post by ajgreeny on 2017-10-28
> **oldfred said:**
> In addition, make sure the printer is plugged in to a USB port and on. It wants to see a HP printer.
If you only want WiFi, you can configure it easily when plugged in, then unplug USB.
I have never bothered with this but it does require that you know the IP address of the printer and enter it in the manual detection part of the installation, all of which may be unnecessary if you use a USB cable first.

---

### Post by tmichaelglass on 2017-10-31
I have solved my initial problem and can now print.
The problem was not knowing how to run a .run file.
Thanks all for nudging me in the right direction.

I'm still experimenting with wifi connection and scanning functions. No success there yet.

---

