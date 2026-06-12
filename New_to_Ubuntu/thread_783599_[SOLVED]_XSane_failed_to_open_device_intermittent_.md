---
title: "[SOLVED] XSane failed to open device intermittent MFC-240c brother"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-05
My Brother MFC-240c printer/scanner/copier/fax has worked with XSane/Gimp until today without intermittent problems.

I'm not fiddling with USB devices during the scan process.

mark@Lexington-19:~$ lsusb
 
Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd 

The printer works, so what gives?

Full XSane error message attached as screenshot.

---

### Post by aouie on 2009-01-30
Changing the permissions as in [the linked post]("http://ubuntuforums.org/archive/index.php/t-166944.html") will help.
First of all you should find out which bus your usb scanner resides on, this is easily done with the lsusb command.


user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


as you can see the scanner resides on Bus 002 as the second (002) device in my case. The syntax for changing permissions of the scanner device is


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE


remember to change the $BUS and $DEVICE variables according to the lsusb output as described above. to change permissions to my scanner device i would enter:


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002

---

### Post by orange_roughy on 2009-09-09
awesome solution. thanks

---

### Post by rrazian on 2009-10-30
Worked for me as well!  Thanks!!!

---

### Post by xs2michele on 2010-06-12
U rock.....

Just 1 chmod command that made all the difference in the world. :)

Thanks.

---

### Post by Gunnar Hjalmarsson on 2010-08-08
> **aouie said:**
> ... to change permissions to my scanner device i would enter:

user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002

Your post solved the problem for mee too. Thanks, "aouie"!

However, one thing makes me fear that the solution is a workaround. In my case, while the scanner at this moment is represented by device 004 in bus 006:

```
$ lsusb | grep Brother
Bus 006 Device 004: ID 04f9:01ab Brother Industries, Ltd MFC-240C
```... XSane keeps displaying bus 003 and device 001:

[IMG]http://gunnar.cc/img/xsane_screenshot.png[/IMG]

That was true before I had fiddled with some USB connected devices. So even if it 'works', it would be even better if somebody could tell how to get rid of this inconsistency.

---

### Post by mikenh on 2010-08-20
Aouie, Thanks. your post solved the problem for me too. With great respect I add, sometimes y and w.

---

### Post by cainwong on 2010-09-28
I dunno how i got into this problem (perhaps upgrading ubuntu to Lucid release :confused:) Anyway, thanks for sharing the quick solution on 1st post. I've improved it with a **bash** script and attach it to the **udev** script. So that, i have no need to apply the **chmod** all the time when i wanna to use the MFC-240C USB scanner.

The followings are the simple steps i have applied to my Ubuntu **Lucid** server environment:

(1) Download [**brscan.sh**]("http://ubuntuforums.org/attachment.php?attachmentid=170686&stc=1&d=1285651569") to **/opt**

(2) **chmod 755 /opt/brscan.sh**

(3) **nano /etc/udev/rules.d/45-libsane.rules** (Create it if not existed)

(4) Add the following lines:
```
# Brother MFC-240C
ATTR{idVendor}=="04f9", ATTR{idProduct}=="[COLOR=Red]01ab[/COLOR]", RUN+="/opt/brscan.sh"

```Please change the [COLOR=Red]01ab[/COLOR] (*Product ID* - might be different from mine) to the one you owned. You can find it with **lsusb**.

(5) **nano /lib/udev/rules.d/40-libsane.rules** (Shall be existed)
(6) Add the following lines at the end, just before the "*# The following rule will disable USB autosuspend for the device*":
```
# Brother Scanners
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="[COLOR=Red]01ab[/COLOR]", ENV{libsane_matched}="yes"

```Again, please change the [COLOR=Red]01ab[/COLOR] (*Product ID* - might be different from mine) to the one you owned. You can find it with **lsusb**.

Hopefully will safe you some time to solve this problem\\:D/

---

### Post by Gunnar Hjalmarsson on 2010-10-11
> **cainwong said:**
> ... thanks for sharing the quick solution on 1st post. I've improved it with a **bash** script and attach it to the **udev** script. So that, i have no need to apply the **chmod** all the time when i wanna to use the MFC-240C USB scanner.

When fixing the permissions issue, I made "lp" the group, and added write access to the group:
```
~$ ls -l /dev/bus/usb/006
total 0
crw-rw-r--  1 root root 189, 640 2010-10-11 23:09 001
crw-rw-r--  1 root root 189, 641 2010-10-11 23:09 002
crw-rw-r--+ 1 root lp   189, 642 2010-10-12 00:14 003
```Scanning has worked fine since; no need to chmod again.

---

### Post by carpetmanleo on 2011-01-07
Thanks Man this worked great!:popcorn:

---

### Post by carpetmanleo on 2011-02-06
I wonder if it would be possible to scan with this device from another pc on network. I can print to it so how would one go about scanning to it. Any help is greatly appreciated.

---

### Post by Gunnar Hjalmarsson on 2011-02-06
> **carpetmanleo said:**
> I wonder if it would be possible to scan with this device from another pc on network.That question is off topic in this thread, I think. I suggest that you start a new thread, where your latest question is reflected in the title. To increase the chances to get help, you'd better describe the exact steps you took when trying, what error messages you got (if any), etc.

---

### Post by hariprasad on 2011-02-11
> **aouie said:**
> Changing the permissions as in [the linked post]("http://ubuntuforums.org/archive/index.php/t-166944.html") will help.
First of all you should find out which bus your usb scanner resides on, this is easily done with the lsusb command.


user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


as you can see the scanner resides on Bus 002 as the second (002) device in my case. The syntax for changing permissions of the scanner device is


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE


remember to change the $BUS and $DEVICE variables according to the lsusb output as described above. to change permissions to my scanner device i would enter:


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002

11.02.2011. It woks for Brother DCP-J125 as well on Ubuntu 10.04, AMD x86-64.:D

---

### Post by BobSongs on 2011-02-28
Perfect!! **aouie**, you've done it for me!

What I did:

```
lsusb | grep Brother
```which gave me
```
Bus 004 Device 002: ID 04f9:01ab [COLOR=Red]**Brother**[/COLOR] Industries, Ltd MFC-240C
```so, I entered, as instructed by **aouie**:
```
sudo chmod a+w /dev/bus/usb/004/002
```and the scanner software fired up perfectly!

---

### Post by blueturtl on 2011-06-19
A bit of bad advice floating around here.

There is a simple reason why the chmod method works: you are giving write access to the scanner for everyone. In my case I noticed the permissions for the printer/scanner were as follows:

owner root (read write), group lp (read write), others (read only)

You can come up with elaborate attempts to permanently change the permissions to allow access to all OR you could simply add yourself to the group 'lp' with a simple:

sudo usermod -a -G lp <username>

For network access you need to add the user you're running the sane daemon as (typically 'saned') to this group. So for network users getting the error 'can't open device: invalid argument', the solution would be

sudo usermod -a -G lp saned
(this on the system sharing the scanner)

---

