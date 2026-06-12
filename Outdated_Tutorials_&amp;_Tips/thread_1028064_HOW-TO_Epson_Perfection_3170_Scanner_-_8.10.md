---
title: "HOW-TO Epson Perfection 3170 Scanner - 8.10"
date: 2009-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by reidi on 2009-01-02
This is what I did to enable the Epson Perfection 3170 Photo scanner in Ubuntu 8.10.

(1) Get the software from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) for the Perfection 3170 PHOTO.
As of 1/1/2009 there were two downloads for Ubuntu 8.10. 
Download both rpms to the Desktop:
iscan-2.10.0-1.c2.i386.rpm
iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm

(2) Open a terminal and enter the entire following string on one line, its okay if it wraps, just don't press enter until it is all entered correctly.  You may get one or two non-fatal warnings as the deb packages are built and intalled - don't worry.

sudo apt-get install alien && cd $HOME/Desktop && sudo alien -d iscan*.rpm && sudo dpkg -i iscan*.deb

(3) Now add these packages, using the terminal:

sudo apt-get install libstdc++5
sudo apt-get install xsane
sudo apt-get install sane-utils

In the terminal enter:
sudo gedit /etc/udev/rules.d/50-libsane-extras.rules
Search for the line for the Perfection 3170, and change 0664 to 0666.
Save and exit.

Reboot
Run sane-find-scanner, you should see a line for your scanner.
Run scanimage -L, you should see a line for your scanner.
Sometimes it takes a couple of power cycles on the scanner before scanimage finds the hardware.
Run xsane.

##########
Also note /etc/init.d/mountdevsubfs.sh had previously been edited to support USB in Virtualbox.  I have no idea if this is necessary for the hardware to be found in Ubuntu 8.10:

Note 5 lines added starting with "FOr Virtualbox..."
do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
	#
	#FOr VirtualBox per [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

}
###########

---

### Post by sdennie on 2009-01-02
Moved to Tutorials & Tips.  Thanks for the HOWTO.

---

### Post by contrarian_66 on 2009-01-03
Hi,

I am trying to get an Epsom Perfection 4490 photo going, so should be the same procedure.  I have followed the first steps i.e. convert the iscan packages to .deb using alien then install them, along with xsane.  However when I come to edit 50-libsane-extras-rules, this doesn't exist on my system.  I am on Ubuntu 8.10 with all latest updates.

Neither xsane or iscan recognises my scanner, although it is reported correctly when I run sane-find-scanner. Running imagescan -L also reports that it cannot find the scanner.  The results are the same if I run xsane or iscan as root.

I have not tried the additions that you mention to mountdevsubfs.sh as I don't understand them and am feeling very out of my depth there.  Any more advice anyone?  I'm guessing what I have here is more a USB issue than a scanner issue.

---

### Post by juliette on 2009-01-03
> **contrarian_66 said:**
> Hi,

I am trying to get an Epsom Perfection 4490 photo going, so should be the same procedure.  I have followed the first steps i.e. convert the iscan packages to .deb using alien then install them, along with xsane.  However when I come to edit 50-libsane-extras-rules, this doesn't exist on my system.  I am on Ubuntu 8.10 with all latest updates.

Neither xsane or iscan recognises my scanner, although it is reported correctly when I run sane-find-scanner. Running imagescan -L also reports that it cannot find the scanner.  The results are the same if I run xsane or iscan as root.


I have the same problem. 

> **contrarian_66 said:**
> 
I have not tried the additions that you mention to mountdevsubfs.sh as I don't understand them and am feeling very out of my depth there.  Any more advice anyone?  I'm guessing what I have here is more a USB issue than a scanner issue.

I have those lines in mountdevsubfs.sh, since I use virtualbox, but they do not help.

UPDATE:
Problem solved by reinstalling scanner according to the howto in this thread [http://ubuntuforums.org/archive/index.php/t-587371.html](http://ubuntuforums.org/archive/index.php/t-587371.html)

---

### Post by Indyviews on 2009-01-11
What to do if you can't get the sane extras -rules? I get a blank screen and nothing changed after nearly an hour. When I click it off, it asks if I want to lose fifty some minutes.

Does it take hours...should I wait longer?

---

### Post by Indyviews on 2009-01-14
In case there is anyone out there..I have downloaded backends and seem to get farther along with this....now when I hope to get the 50-libsane-extras-rules, it says:

E: Couldn't fine package sane - utilssudo

Can anyone tell me what to do as of course I don't understand this but feel I am close to getting my scanner working.

---

### Post by beech_13465 on 2009-01-20
Thanks for tge HOWTO! It worked fine for me, but 2 remarks:

> **reidi said:**
> 

sudo apt-get install alien && cd $HOME/Desktop && sudo alien -d iscan*.rpm && sudo dpkg -i iscan*.deb 

Make sure to store the downloads in your desktop folder, otherwise you have to change the path ($HOME/Desktop).

> In the terminal enter:
sudo gedit /etc/udev/rules.d/50-libsane-extras-rules
Search for the line for the Perfection 3170, and change 0664 to 0666.
Save and exit.

The name of the file is "50-libsane-extras.rules". If it doesn't exist, create it and paste the following line:

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="666", GROUP="scanner"

Hope it helps.

---

### Post by interknighterrant on 2009-03-06
There might be a much simplified solution on how to install the Epson Perfection 3170 Scanner in Intrepid.  I did the howto, got stuck with the blank udev file, and worked backwords a bit.  I don't want to re-install Intrepid to test this, so if someone could confirm this working for them it might speed things up for people in the future:


1.  Install **libsane-extras** and the other packages in the original howto ([COLOR="DarkRed"]original packages necessary???[/COLOR]):
```
sudo apt-get install libstdc++5 sane-utils libsane-extras xsane
```

2.  Edit the udevs file, according to the original howto
```
sudo gedit /etc/udev/rules.d/50-libsane-extras.rules
```
Search for the line for the Perfection 3170, and change 0664 to 0666.
Save and exit.

3.  Rebooting may or may not be necessary.  libsane-extras restarts the hardware.

4.  Test to see if it is installed ok

Type in "sane-find-scanner, see if the output is similar to what I put down.
```
user@computer:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bb4, product=0x0c02) at libusb:007:004
found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Type "scanimage -L" and see if the output is similar
```
user@computer:~$ scanimage -L
device `epson:libusb:003:002' is a Epson  flatbed scanner
```


If that all works ok, start up xsane or any other scanner software and it should see the scanner.


If anyone uses this quick howto and it works ok, please give a comment.  I'd love to squirrel this away for the future.  Although in just another few weeks I guess Jaunty should be out anyway.

---

### Post by kurisha on 2009-05-01
Hello all,
I fallowed the instructions to the letter and I had the problem lacking that rules file but i created it with that line also mentioned in this thread and saved it.
When I opened the XSane and clicked the scan button it returned an error: Failed to start scanner: invalid argument.

I'm using the Ubuntu 8.04 but I didn't think since the instructions were for 8.10, that it would be so different.  Is it? or did I not fallow complete instructions? or did I not set some access rules for the device?
Everything i did fallowing the instructions was done completely and i got now issues.  All packages were downloaded and installed although i had XSane app already but it installed still without mention that it existed already.  The driver files were on desktop and so all instructions worked for me and it was even detected when i used the command to detect the scanner.  But as i said, in the XSane scan application, when i push scan, it returns the error.
I don't know how to set device or file rules but I'm sure i can find the command line parameters for it.
If anyone has any idea what I can do now, please let me know.

thank you in advance!

Kurisha

---

### Post by gazer22 on 2009-05-05
In Jaunty (9.04), I was able to get the scanner working with a slightly modified process:

[LIST=1]
[*]Download iscan-plugin-gt-9400 rpm from: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) **to your desktop**
[*]From the terminal:
```

sudo apt-get install alien
cd ~/Desktop
sudo alien -d iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
sudo dpkg -i iscan-plugin-gt-9400_1.0.0-2_i386.deb
sudo apt-get install sane-utils libsane-extras xsane

```
[*]Add yourself to the scanner group (adding the scanner group if needed) System->Administration->Users and Groups - unlock, then hit manage groups.
[*]Reboot
[*]sane-find-scanner should yield something like:
```
found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:001:010
```
[*]scanimage -L should give something like:
```
device `epson:libusb:001:010' is a Epson  flatbed scanner
device `epkowa:libusb:001:010' is a Epson Perfection 3170 flatbed scanner

```

[/LIST]

When running xsane, use the epkowa driver.

---

### Post by Ronok on 2011-03-01
Hollo All
2 years ago started Trying to get the Epson to Scan 
with Ubuntu 8.04 and up through and Now Currently:
Linux Kernel: 2.6.35-27-generic (i686)
Distribution: Ubuntu 10.10
Gnome: 2.32.0
[URL="http://ubuntuforums.org/showthread.php?p=10510907"]Here is The Link to the Thread that I also started in January 2009
http://ubuntuforums.org/showthread.php?p=10510907[/URL]
I had not found this thread tell much later
and here is where things stand after looking at many Threads 
including this one.

**[SIZE="3"]My Trouble shooting sequence of Epson "Perfection 3170 Photo"[/SIZE]** and
Some generic Trouble shooting tips for Scanners in general
I tried the following: (with CODE = user@computer:~$ enter it here)

**1)** 
first see where things stand Is the Scanner USB properly connected to the computer ?
```
lsusb
```
> Bus 001 Device 007: ID 04b8:0116 Seiko Epson Corp. Perfection 3170 (GT-9400)

**2)** 
Check that SANE & XSANE are Present:
```
sudo apt-get install sane &&
sudo apt-get install libsane &&
sudo apt-get install libsane-extras &&
sudo apt-get install sane-utils &&
sudo apt-get install xsane &&
sudo apt-get install xsane-common &&
sudo apt-get install libstdc++5
```
**3)** Check That the system is upto date:
System > Administration > Update Manager (or)
```
sudo apt-get update && sudo apt-get upgrade
```

**4)** 
Then lets see where things stand:
```
xsane
```
Get a Pop up Window:
> No Devices available

**5)**
To get a list of devices
```
scanimage -L
```
> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
**6)**
See if SANE can see the Scanner ?
```
sane-find-scanner
```
> found USB scanner (vendor=0x04b8, product=0x0116) at libusb:001:007
**7)**
open and maybe edit this file Check to see that "epson" & epson2" are uncommented (that is with out"#")
```
sudo gedit /etc/sane.d/dll.conf
``` 
**8)**
(with Epson issues all roads seem to lead here) so Go to:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do")
Fill in the form and download: 
---> iscan-2.10.0-1.c2.i386.rpm
---> iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
to the Desktop
thats your:
```
cd ~/Desktop && pwd
```
**9)**
Get Alien
Alien allows you to convert [".rpm"]("http://en.wikipedia.org/wiki/RPM_Package_Manager") files into Debian [".deb"]("http://en.wikipedia.org/wiki/Deb_%28file_format%29") packages, which can be installed with dpkg.
```
sudo apt-get install alien
```
**10)**
Make the ".deb" file from the ".rpm" file (Note in the code-example the "*" takes the place of
e.g: "-plugin-gt-9400-1.0.0-1.c2.i386"
```
cd ~/Desktop
sudo alien -d iscan*.rpm
sudo dpkg -i iscan*.deb
```
**11)**
Edit the libsane-extras.rules
```
sudo gedit /etc/udev/rules.d/50-libsane-extras.rules
```
**12)** 
if it is empty add this line:
> SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="0666", GROUP="scanner"

**13)**
Edit the epson.conf
```
sudo gedit /etc/sane.d/epson.conf
```
**14)** 
add this line (the USB device ID from step #1 above) at the end:
> usb 0x04b8 0x0116
**15)**
Add yourself to the scanner group (adding the scanner group if needed) 
System > Administration > Users and Groups > manage groups > unlock > add > check self
**16)**
Do a complete Shutdown & restart the machine
**17)**
Try To get a list of devices again
```
scanimage -L
```
first got:
> Segmentation fault
Now get:
> device `epson:libusb:001:006' is a Epson  flatbed scanner
**18)**
```
iscan
```
get a Pop up Window: 
> Could not send command to scanner. Check the scanner's status

**19)**
anyway I Like and Just Want to use XSANE 
```
xsane
```
I get the "Xsane 0.997 window"  & "Preview window"
Both "Preview botton" & "Scan Botton"
Get pop up window:
> Failed to start scanner: invalid argument

[CENTER][B]- - - > at a Dead End < - - -
- - - > Still Will Not Scann < - - -[/B][/CENTER]

Has anyone had any recent Success under **Ubuntu 10.10**
see any errors in what I did ? any Help or ideas ?
**Thanks** Ronok
[My < Linux > Command Line Interface Page]("http://www.gongkuo.com/linuxcli.htm")

---

