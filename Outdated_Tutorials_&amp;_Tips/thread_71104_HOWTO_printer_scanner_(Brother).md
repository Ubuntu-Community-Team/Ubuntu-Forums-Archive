---
title: "HOWTO: printer scanner (Brother)"
date: 2005-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by marcw on 2005-10-02
As [http://linuxprinting.org](http://linuxprinting.org) points out, the state of multifunction devices that work well for Linux isn't very good.  One that I've discovered works quite nicely however is Brother.  While their LPR drivers are proprietary, at least they are offered and they work well.  I have recently installed two such devices on Hoary - MFC-420CN and MFC-210C.  I chose Brother both times for these reasons:
- good reviews
- inexpensive to purchase  (both were under $100.00 after rebates)
- I could get inexpensive generic ink cartridge replacements (~$5.00/ea)
- there were Linux drivers available

The only prerequites I've found is that the drivers need these installed:
- cups
- xsane and sane
- csh
The first two are installed in a default Hoary install, I believe.  The last one, csh, needs to be installed separately with either apt-get or Synaptic.
The Brother Linux site is located here:  [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) .

What follows is pretty much the same instructions that are posted on the Brother site, with one major modification.  Also, these instructions assume a USB connection to the device, not a network connection.  I believe there is a different thread covering a Brother network printer.

1) From the above Brother site, find and download the Debian LPR driver for your MFC, the Debian CUPS wrapper (if available), and the Debian scanner driver.  Pay close attention to getting the correct ones for your device - their web site could definitely be clearer.

2) After fulfilling the prerequisites metioned earlier, install the LPR drivers first e.g.:
```
sudo dpkg -i mfc210clpr-1.0.2-1.i386.deb
```

3) Then install the CUPS wrapper (if available) similarly e.g.:
```
sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb
```

4) Then install the scanner driver.  These instructions are where one major modification take place.
a) install the scanner package e.g.:
```
sudo dpkg -i brscan2-0.0.1-0.i386.deb
```
b) edit the /etc/fstab file e.g.:
```
sudo gedit /etc/fstab
```
add the following line to the end of the file:
```
none /proc/bus/usb usbfs auto,devmode=0666 0 0
```
save
(Note the Brother instruction say to use 'usbdevfs'.  This won't work.  It must be 'usbfs'.)
c) modify the USB access control e.g.:
```
sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
sudo mknod -m 666 /dev/usbscanner c 180 48
```

That's it.  Your printer should have magically appeared in System -> Administration -> Printing and your scanner should now be recognized by xSane when you navigate to Applications -> Graphics -> XSane.

---

### Post by irwand on 2005-12-14
I went about this a bit differently.. 

Instead of putting devmode=0666 in the usbfs line in fstab, I go about this a different route. I think putting devmode=0666 as suggested opens the permission of all nodes under /proc/bus/usb so that they're readable and writable to anyone, which may open security risk.

Potentially, a better way is to add brother USB device ID into /etc/hotplug/usb/libsane.usermap.
So edit that file with your favorite editor, and add the following lines:

```
# Brother|MFC 210c
libusbscanner             0x0003      0x04f9   0x0161    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000

```

That line will make the scanner device of the multifunction USB device to be owned by root.scanner by the hotplug subsystem. So with this, only users that are a part of the scanner group can access the printer. Security-wise, this is better, and this is how Ubuntu scanner system was designed to work, AFAIK.

---

### Post by jdautz on 2006-03-27
I try MFC9880 with Ubuntu Dapper,  and scaneimage said:

$ scanimage >toto.pnm
$ scanimage: open of device brother:bus5;dev1 failed: Error during device I/O

but scanimage work with sudo 

Why? ](*,)

---

### Post by frio on 2006-10-31
I have the same problem after upgrading to Dapper (over this past weekend). The thread below shows a solution but I have yet to implement it. I will add that running xsane as sudo did work in my case so I believe it is safe to say it is a permissions problem. Also, this problem was not an issue for me on Breezy.
 
[http://www.ubuntuforums.org/showthread.php?t=280901&highlight=Brother+scanner](http://www.ubuntuforums.org/showthread.php?t=280901&highlight=Brother+scanner)

---

### Post by frio on 2006-10-31
Well I gave the fix I mentioned in my earlier post a go but to no avail. Xsane simply re-created the hidden folder under my home folder. However, what did work is adding the following line to /etc/udev/rules.d/45-libsane.rules:

```
# Brother|DCP 7020
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0183", MODE="664", GROUP="scanner"
```Then I turned the device off and then on and it worked, no errors.

The Vendor and Product ID's can be obtained by using sane-find-scanner which is part of the sane-utils (installable from the Synaptic Package Manager)

Hope this helps someone.

---

### Post by Athanasius on 2006-11-25
Frio, thank you !!! I have that same model and I really needed to get the scanner working.  Thanks!!

---

### Post by ßodincµs on 2006-12-26
Yup, confirmed, that works with the DCP110C either.
Here's a quick howto... 
In addition to the usual Brother installation procedure, straight after the "mknod ..." command, do this procedure. All the steps must be done in a root terminal (enter the command "sudo -i").

1.Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor, e.g vi.
2.Add the following description to the file, just after the other two Brother models (MFC 7300 and MFC 9600C) as below:
================= 
# Brother DCP 110C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0169", MODE="664", GROUP="scanner"
================= 
3.Restart the user devices with the following command:
$ /etc/init.d/udev restart

There is no need to restart the OS.
Happy scanning!

---

### Post by pseudo_nz on 2007-02-05
Thanks guys, this had my DCP 130C up and scanning in about ten minutes (after staring incomprehensibly at the instructions on the Brother page for far too long!)

---

### Post by turtlepaul on 2007-02-19
I have a 420CN and have been having problems with it. I got up to 4c where it said to enter

> sudo umount /proc/bus/usb

It came up with

> /proc/bus/usb: device is busy

I tried turning the printer off and I checked to see if I had any applications running that would cause it to be busy, but it still did not work. 

At this point, I also decided to check the System-->Administration-->Printing to see if my printer was there and it wasn't. Can someone help me?

---

### Post by phpmonkey on 2007-03-04
Just a note - I have a DCP-130C running without too much trouble.

I had an issue printing PDFs from Document Viewer - the top few cm were always cut off. I solved that by installing the acroread package, and printing from there. :KS

Oh, and turtlepaul - I had the same issue re "device is busy" message. I can't remember exactly how I fixed it, but it involved rebooting the printer, possibly with the machine plugged in but turned off and skiiping the "umount" bit and maybe even the "mount" bit.

---

### Post by Galban on 2007-03-22
:) Thanks! yes, adding that line to "/etc/udev/rules.d/45-libsane.rules" fix the permissions problem with Xsane. You know, Xsane showing up a error window saying:

```
Failed to open device ' brother2:bus2:dev1':
Error during device I/O
``` 

And the "sudo" way wasn't practical because others users were needing the root password to use Xsane. So You are right guys, it was a question of permissions. The Model that I have it's the MFC 210c. So, the line for this model is as fallow:

# Brother MFC 210C.
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="[COLOR="Red"]0161[/COLOR]", MODE="664", GROUP="scanner" 

Important to note that the "SYSFS{idProduct}" parameter (number in red) changes as the model changes, it took me to googleling to find the right number for my model in order to get it working.Thanks again!

---

### Post by pawiel on 2007-04-05
Hi,
I use ubuntu (my first distribution) since two months so I am not very experienced with it. I have DPC-130. The printer works OK but the scanner does not. I have the 'i/o error' when I open xsane. It works if I use sudo xsane. I have modified 
/etc/udev/rules.d/45-libsane.rules 
by adding 

# Brother DCP-130C 
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0x01a8", MODE="664", 
GROUP="scanner"

I took the idProduct from sane-find-scanner. Anyway, it stil does not work and it still works if i use sudo xsane. I have made myself member of the "scanner" group. 

What else should I do?

---

### Post by Alchera on 2007-04-19
/etc/udev/rules.d/45-libsane.rules:
```
# Brother DCP 130C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01a8", MODE="664", GROUP="scanner"
```
Next 
```
1.Create the file "10-local.rules" under the directory:
"/etc/udev/rules.d/"
which includes the following content:

===========
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="_end"
# For brother
SYSFS{idVendor}=="04f9", MODE="666", GROUP="scanner"
LABEL="_end"
===========
```
Followed by:
```
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start
```
Also make absolutely certain that System~Administration~Printing (Properties/Driver) is actually using DCP-130C.

Up until I had done the "extras" (above) I had printing working perfectly; not scanning! Now I have it all! :)

---

### Post by Richhard on 2007-05-04
Hi marcw,

I tried to follow your advice, but I have an AMD64 system, and therefore it did not work :-(
Do you (or somebody else9 have any good idea?

---

### Post by tradesman on 2007-08-19
Been reading this thread with interest as I have a brother DCP-310CN  printer/scanner got the printer working ok but getting the IO error with XSane anyone know the SYSFS{idProduct no for this model.

Now upgraded to Feisty Fawn 7.04

---

### Post by tradesman on 2007-08-20
Ok I solved the XSAne i0 error heres how,
first I had to install sane-utils then  I did sane-find-scanner in terminal this gave me 3 USB scanning  devices I located the one I wanted.
Then  did > "/etc/udev/rules.d/45-libsane.rules"  as root and added this line for my brother DCP-310CN
> GROUP="scanner"
# Brother DCP-310CN
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="016b", MODE="664",

then in terminal
> sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start

started XSAne from  applications /graphics
and bingo up came a working scanner.
Hope this may help others with the same model.

---

### Post by Alchera on 2008-05-25
For those who have upgraded to 8.04 the above instructions no longer apply.
Use this link: [http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9)

---

