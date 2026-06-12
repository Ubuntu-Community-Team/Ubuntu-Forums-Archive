---
title: "How to get Epson 3490 Scanner working under Hardy H ?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by cloud3737 on 2008-09-11
Hi,

Has anybody had any luck getting an "Epson 3490 Photo" scanner working under Hardy Heron? 

When I try to run the XSANE utility, I get an abrupt error message of the form 

******************************************************************
Error
Failed to open device `snapscan:libusb:006:003': Invalid argument.
******************************************************************

My only option is to close the box and I'm done. I've searched these forums and seen a few posts on this particular scanner, but nothing I could decipher as a newbie. Any help would be appreciated!

---

### Post by wolfen69 on 2008-09-11
open a terminal and copy and paste the following:
```
gksudo gedit /etc/sane.d/epson.conf
```
then you will see the following:
```
# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
**# usb <product ID> <device ID>**
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0
```
the line that is in bold letters needs # to be removed from the beginning of the line and product ID and device ID inserted.
you will need to do ```
lsusb
```
to find out the product ID and device ID.

an example of what lsusb looks like, and what #'s you need are:```
ed@wolfenstein:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 077: ID **03f0:7e04** Hewlett-Packard 
Bus 001 Device 076: ID 0764:0501 Cyber Power System, Inc. 
Bus 001 Device 006: ID 1241:1203 Belkin 
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
```
the #'s in bold are what you need.

close and save.

---

### Post by phidia on 2008-09-11
The scanner appears to be supported see the SANE listing [for it]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson+&model=3490&bus=any&v=&p=").

Open a terminal and enter "sane-find-scanner" and/or "scanimage -L".
What is the output from those commands?

---

### Post by cloud3737 on 2008-09-11
Hi,

Responding to the last post, the command  sane-find-scanner gives

********
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:006:003
********

and the command scanimage -L gives
 
********
device `snapscan:libusb:006:003' is a EPSON EPSON Scanner flatbed scanner
********

---

### Post by cloud3737 on 2008-09-11
Wolfen69, I carried out your steps and I'm still getting the same error message. :(

---

### Post by kaibob on 2008-09-11
I have an Epson 3490 scanner that works fine. I have posted below my snapscan.conf file. The key to getting this scanner to work was the line near the top that begins with the word, firmware. You have to have the firmware file on your hard drive where indicated by the firmware line. You can get the firmware file from the Windows install of the Epson software or from the Epson scanner install cd.

```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/esfw52.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

#-------------------------- SCSI scanners ----------------------------------
# These SCSI devices will be probed automatically
scsi AGFA * Scanner
scsi COLOR * Scanner
scsi Color * Scanner
scsi ACERPERI * Scanner

#--------------------------- USB scanners -----------------------------------
# These USB devices will be probed automatically
# (This will currently work only on Linux)

# Benq/Acer/Vuego 310U
usb 0x04a5 0x1a20
usb 0x04a5 0x1a26

# Benq/Acer/Vuego 320U
usb 0x04a5 0x2022

# Benq/Acer/Vuego 620U / 620UT
usb 0x04a5 0x1a2a
usb 0x04a5 0x2040

# Benq/Acer/Vuego 640U
usb 0x04a5 0x2060

# Benq/Acer/Vuego 640BU
usb 0x04a5 0x207e

# Benq/Acer/Vuego 640BT
usb 0x04a5 0x20be

# Benq/Acer/Vuego 1240U
usb 0x04a5 0x20c0

# Benq/Acer/Vuego 3300 / 4300
usb 0x04a5 0x20b0

# Benq/Acer/Vuego 4300
usb 0x04a5 0x20de

# Benq 5000E / 5000U
usb 0x04a5 0x20f8

# Benq 5000
usb 0x04a5 0x20fc

# Benq/Acer 5300
usb 0x04a5 0x20fe

# Benq 5250C
usb 0x04a5 0x2137

# Agfa 1236U
usb 0x06bd 0x0002

# Agfa 1212U
usb 0x06bd 0x0001
usb 0x06bd 0x2061

# Agfa Snapscan e10
usb 0x06bd 0x2093

# Agfa Snapscan e20
usb 0x06bd 0x2091

# Agfa Snapscan e25
usb 0x06bd 0x2095

# Agfa Snapscan e26
usb 0x06bd 0x2097

# Agfa Snapscan e40
usb 0x06bd 0x208d

# Agfa Snapscan e42
usb 0x06bd 0x20ff

# Agfa Snapscan e50
usb 0x06bd 0x208f

# Agfa Snapscan e52
usb 0x06bd 0x20fd

# Epson Perfection 660
usb 0x04b8 0x0114

# Epson Perfection 1670
usb 0x04b8 0x011f

# Epson Perfection 2480
usb 0x04b8 0x0121

# Epson Perfection 3490
usb 0x04b8 0x0122

# Epson Stylus CX-1500
usb 0x04b8 0x080c
```

You may also want to review the following thread:

[http://ubuntuforums.org/showthread.php?t=108256](http://ubuntuforums.org/showthread.php?t=108256)

---

### Post by cloud3737 on 2008-09-12
Ok kaibob, I found the file esfw52.bin on my Window installation ... so I have that. What do I do next? 

1. How do I edit the file /etc/sane.d/snapscan.conf ?

I can open and "edit" it, but can't seem to save it.

2. How do I move esfw52.bin into /usr/share/sane/snapscan/esfw52.bin ?

The subdirectory "snapscan" does not exist on my computer.

Thanks for hanging in with me here ...

---

### Post by kaibob on 2008-09-12
To edit snapscan.conf, first create a backup and then enter the following in a terminal window:

```
gksudo gedit /etc/sane.d/snapscan.conf
```

You can put the firmware file in whatever directory you like. I believe the default is /usr/share/sane/snapscan/. If it's not there, just create it, but be sure that the path is correct in the snapscan.conf file.

---

### Post by cloud3737 on 2008-09-12
Hi kaibob,

Still not working, but I must be getting closer.

I did what you said above. The first few lines of my snapscan.conf file now look like this:

#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/esfw52.bin

I made the missing folder using

sudo mkdir /usr/share/sane/snapscan

and copied the file esfw52.bin into it using

sudo cp ~/Documents/t/esfw52.bin /usr/share/sane/snapscan/esfw52.bin


The bin file appears to be in the desired location. Then I followed some instructions in another thread, including turning things off/on and rebooting. The command

scanimage -T

yields the following response:

[snapscan] Cannot open firmware file /usr/share/sane/snapscan/esfw52.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:001:003 failed: Invalid argument

Uff. Any ideas?

---

### Post by kaibob on 2008-09-12
I don't know why that doesn't work, other than the obvious one that you haven't successfully copied the file to the correct location. To check this, enter the following in a terminal window:

```
find /usr/share/sane/snapscan/esfw52.bin
```

Also, check capitalization--a few posts show the firmware file name as Esfw52.bin. 

Some people were having trouble with the 3490 and permissions. Do a forum search on "3490 permissions" (no quotes) and you'll find a number of threads.

---

### Post by cloud3737 on 2008-09-12
Hi again kaibob,

The command

find /usr/share/sane/snapscan/esfw52.bin

spits back

/usr/share/sane/snapscan/esfw52.bin

I take this to mean that the bin file is in the right place.

Thanks so much for your help. Can I ask you something else? Suppose I want to dump this scanner (it's a bit old anyway) and get a new one. Can you offer any recommendations on makes/models/types of scanners that won't entail these sorts of problems? Are these problems resulting from the fact that the scanner is a few years old, or that it's an Epson product, or that it's a USB scanner, or maybe something else? Any idea? Do you think I should start a new "absolute beginner" thread with that question?

---

### Post by kaibob on 2008-09-12
Sorry to hear that nothing has helped. The 3490 is actually a good basic scanner.

I don't keep up on scanners and can't recommend anything directly. The following page shows supported scanners and is a good starting point:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=&bus=any&v=&p=)

HP is often good. When you find a scanner that you might be interested in, it's best to do a search of this forum too see what experience others have had with the scanner. Unless it's a newly introduced scanner, you'll almost always find something.

Sorry I couldn't be of more help.

---

### Post by Kellemora on 2008-09-12
Hi Cloud

Just copying the mail here since I have a scanner that's totally useless on XP-MCE.........

When you copied your file, where you physically in the Root Directory, NOT in your home directory with Root privileges.

I've found that can make a big difference sometimes.

I had several files that when I tried opening them, they were blank pages, until I physically moved into the root directory.

Ubuntu has a ROOT TERMINAL, makes it easy to be in ROOT!
But STILL you have to cd .. enter, cd .. enter again to insure you are physically in ROOT.  If you do that, your files WILL come out in the right place.  Hmmmm, better stick my tongue in cheek while saying that, hi hi.........

TTUL
Gary

---

### Post by webaake on 2009-07-20
Fixed it by setting permission 777 to the bin file:

sudo chmod 777 /usr/share/sane/snapscan/Esfw52.bin

Watch out for the capital "E", or not.

---

### Post by deedeesuzanne on 2009-08-04
Hello, where do I find this esfw52.bin file? I can't find it on my Epson CD that came with the scanner.

---

### Post by webaake on 2009-08-05
Here it is.

---

### Post by eko291 on 2009-11-01
Awesome instructions and thank you for attaching the bin file!

---

### Post by kaibob on 2009-11-02
I recently did a fresh install of Ubuntu 9.10 and had to get my Epson 3490 scanner working again. I copied the firmware file to the Ubuntu partition and edited the snapscan.conf file to show the path to the firmware file. That's all and the scanner works great.

---

### Post by somger on 2010-04-27
Following the instructions, downloading the fw file, I just managed to put to work my Epson perfection 3490 photo on ubuntu 9.10 64-bit version. Great post! thanx!

---

### Post by richrock on 2010-05-31
Permissions settings did it for me - thanks guys! :)

---

### Post by jorgebit on 2011-11-26
> **kaibob said:**
> I have an Epson 3490 scanner that works fine. I have posted below my snapscan.conf file. The key to getting this scanner to work was the line near the top that begins with the word, firmware. You have to have the firmware file on your hard drive where indicated by the firmware line. You can get the firmware file from the Windows install of the Epson software or from the Epson scanner install cd.

```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/esfw52.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

#-------------------------- SCSI scanners ----------------------------------
# These SCSI devices will be probed automatically
scsi AGFA * Scanner
scsi COLOR * Scanner
scsi Color * Scanner
scsi ACERPERI * Scanner

#--------------------------- USB scanners -----------------------------------
# These USB devices will be probed automatically
# (This will currently work only on Linux)

# Benq/Acer/Vuego 310U
usb 0x04a5 0x1a20
usb 0x04a5 0x1a26

# Benq/Acer/Vuego 320U
usb 0x04a5 0x2022

# Benq/Acer/Vuego 620U / 620UT
usb 0x04a5 0x1a2a
usb 0x04a5 0x2040

# Benq/Acer/Vuego 640U
usb 0x04a5 0x2060

# Benq/Acer/Vuego 640BU
usb 0x04a5 0x207e

# Benq/Acer/Vuego 640BT
usb 0x04a5 0x20be

# Benq/Acer/Vuego 1240U
usb 0x04a5 0x20c0

# Benq/Acer/Vuego 3300 / 4300
usb 0x04a5 0x20b0

# Benq/Acer/Vuego 4300
usb 0x04a5 0x20de

# Benq 5000E / 5000U
usb 0x04a5 0x20f8

# Benq 5000
usb 0x04a5 0x20fc

# Benq/Acer 5300
usb 0x04a5 0x20fe

# Benq 5250C
usb 0x04a5 0x2137

# Agfa 1236U
usb 0x06bd 0x0002

# Agfa 1212U
usb 0x06bd 0x0001
usb 0x06bd 0x2061

# Agfa Snapscan e10
usb 0x06bd 0x2093

# Agfa Snapscan e20
usb 0x06bd 0x2091

# Agfa Snapscan e25
usb 0x06bd 0x2095

# Agfa Snapscan e26
usb 0x06bd 0x2097

# Agfa Snapscan e40
usb 0x06bd 0x208d

# Agfa Snapscan e42
usb 0x06bd 0x20ff

# Agfa Snapscan e50
usb 0x06bd 0x208f

# Agfa Snapscan e52
usb 0x06bd 0x20fd

# Epson Perfection 660
usb 0x04b8 0x0114

# Epson Perfection 1670
usb 0x04b8 0x011f

# Epson Perfection 2480
usb 0x04b8 0x0121

# Epson Perfection 3490
usb 0x04b8 0x0122

# Epson Stylus CX-1500
usb 0x04b8 0x080c
```You may also want to review the following thread:

[http://ubuntuforums.org/showthread.php?t=108256](http://ubuntuforums.org/showthread.php?t=108256)

Thank you :KS. It works fine for me in Ubuntu 11.10 x64. 
I Just added the firmware statement and copied esfw52.bin to the /usr/share/sane/snapscan directory and it worked.

---

### Post by chingchong on 2012-11-08
None of the solutions worked for me, so I simply commented out the "firmware" line in /etc/sane.d/snapscan.conf
```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
#firmware /usr/share/sane/snapscan/Esfw52.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

```

After that there were no errors. Using Ubuntu 12.04 Epson 3490.

---

