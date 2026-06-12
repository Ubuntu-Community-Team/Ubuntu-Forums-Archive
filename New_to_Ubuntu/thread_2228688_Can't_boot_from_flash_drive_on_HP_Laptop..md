---
title: "Can't boot from flash drive on HP Laptop."
date: 2014-06-08
forum: New to Ubuntu
---

### Post by matthew31 on 2014-06-08
I have an HP laptop model #17-e116dx.

My BIOS is InsydeH2O Setup Utility Rev. 3.7.

I cannot seem to boot from a flash drive on this computer. I have tried disabling SecureBoot, I've tried setting both the UEFI and Legacy boot orders and the computer continues to boot into Windows 8.

What can I do?

---

### Post by oldfred on 2014-06-09
Some other HP threads. Are you sure flash drive is bootable. Only correctly configured bootable flash drives will show as bootable device.

 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

### Post by JeQhdMD on 2014-06-09
Pls describe flash drive . . is it a standard usb flash-stick with a dos file system (fat32?)?

How did you create it? (what software , what iso image)?

Am assuming you're not referring to a "flash-card" (like SD)

---

### Post by matthew31 on 2014-06-13
It's an ordinary sandisk flash drive 8 GB.

I used YUMI to create the boot image from the ISO.

---

### Post by rahul4557 on 2014-06-13
Since you have windows you can use an utility called [B]
RUFUS[/B] 
"Rufus support UEFI as well as GPT for installation media, meaning that  it will allow you to install Windows 7, Windows 8 or Linux in full EFI  mode."
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

make a Bootable USB from ISO using RUFUS and then try booting from pendrive.
Even i booted Ubuntu on my InsydeH2O BIOS on my HP Laptop..

---

### Post by /ADM on 2014-06-13
My Acer Aspire One 725 has the exact same BIOS also.  My USB's are prepared using unetbootin and I have never had a problem booting from USB.  Currently I even have SecureBoot enabled.

Try using unetbootin and see if it boots for you.  Of course it does not work with everything, but it does work great for Ubuntu.  It is how I installed it on this computer as it has no CD/DVD drive.

---

