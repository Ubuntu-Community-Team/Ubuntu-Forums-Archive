---
title: "[SOLVED] Hardy - libsane.rules OK - not!"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-21
Dear kind experts...

I am trying to reinstall my Epson V200 scanner in Hardy (it was OK in Gutsy...).
I am blindly following (again) the instructions I found for Dapper, which worked fine in Gutsy:[http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example)

When I get to the bit about checking in 45-libsane.rules for my scanner, I find 45-libsane.rules no longer exists.
Nor anything obviously like it in etc/udev/rules.d

A lot of Googling did not produce anything I could use.

Can some kind expert please tell me how to proceed from there?

Thanks!

---

### Post by forger on 2008-08-21
could you try installing the following, execute the commands in Applications > Accessories > Terminal:
```
sudo apt-get install libsane sane sane-utils libsane-extras xsane
```
reboot the machine and try again.

If it doesn't work, try reinstalling:
```
sudo apt-get install --reinstall libsane sane sane-utils libsane-extras xsane
```
reboot and then try once more

---

### Post by 2CV67 on 2008-08-21
Thanks for your rapid response!

Trying GUI methods, I looked in Synaptic & found I already had:
libsane
xsane
sane-utils

I added by Synaptic
sane
libsane-extras

After reboot, I now have a file 025_libsane-extras.rules but still no libsane.rules

(Note that several sources have said I need to REMOVE libsane-extras before installing my deb packages for this scanner...)

I then ran your command for re-installing, using Terminal & copy/pasting> sudo apt-get install --reinstall libsane sane sane-utils libsane-extras xsane

After reboot - no change...

I tried searching file system for "libsane.rules" but found nothing.

:confused:

---

### Post by forger on 2008-08-21
I think you have to add yourself to the group scanner and add the driver for it.

Let's see, do this command:
```
cat /etc/group | grep scanner
```

1)
- If you see your username continue go to (2)
- If you don't see your username in that line, try this:
```
sudo adduser $USER scanner
```
log out and log in again
- Once you're done go to (2)

2) Go root:
```
sudo -s
```
Add the printer driver for epson v200:
```
echo 'epkowa' >> /etc/sane.d/dll.conf
```
Exit root:
```
exit
```

Then do:
```

sudo /etc/init.d/udev restart

```
log out and log in again

```

lsusb
sane-find-scanner
scanimage -L

```

Now try scan something, reply with the output of the commands if it doesn't work :)

---

### Post by 2CV67 on 2008-08-22
Thanks, Forger, for that reply, and sorry for the delay in responding.

I used GUI to add myself to scanners group & logged out/in.
I hope that corresponds to your item 1.

I then went exactly (copy/paste) through your remaining instructions & after another log out/in, ran
> lsusb
sane-find-scanner
scanimage -L

After that, I went to XSane Image Scanner, but only got "no devices available".

Here is the output from the last commands:
> chris@DESKTOP:~$ lsusb
Bus 004 Device 005: ID 04b8:012e Seiko Epson Corp. 
Bus 004 Device 004: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1019:0c55 Elitegroup Computer Systems (ECS) USB Flash Reader, Desknote UCR-61S2B
Bus 001 Device 001: ID 0000:0000  
chris@DESKTOP:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:004:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
chris@DESKTOP:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
chris@DESKTOP:~$ 

The lsusb & sane-find-scanner commands found the scanner OK > Bus 004 Device 005: ID 04b8:012e Seiko Epson Corp. 

But after that...

So far, I have not installed the drivers I downloaded from Epson Japan (should I ??) & I still don't have a libsane.rules file (should I ??).

Pretty obviously, I don't at all understand what I am doing here - just following instructions.

Thanks for any further instructions!

---

### Post by 2CV67 on 2008-08-23
Nobody?

---

### Post by 2CV67 on 2008-08-28
I gave up on that & followed guidelines from robc02 which worked just fine.

see: [http://ubuntuforums.org/showthread.php?t=892351](http://ubuntuforums.org/showthread.php?t=892351)

---

### Post by badfish69 on 2008-09-18
Still tells me

Failed to open device 'Brother2:bus2;dev1':
Error device I/O

---

