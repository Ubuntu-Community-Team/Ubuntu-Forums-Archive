---
title: "Help to install HP SCANJET 6200C"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-10-02
I am trying to install (get the computer to recognize) a HP Scanjet 6200C. I've read some threads here about scanners, e.g., 
[http://ubuntuforums.org/showthread.php?t=870746&highlight=scanjet](http://ubuntuforums.org/showthread.php?t=870746&highlight=scanjet)

[http://ubuntuforums.org/showthread.php?t=829244&highlight=scanjet](http://ubuntuforums.org/showthread.php?t=829244&highlight=scanjet)

[http://ubuntuforums.org/archive/index.php/t-454355.html](http://ubuntuforums.org/archive/index.php/t-454355.html)

and have tried to follow the advice in this one: [http://ubuntuforums.org/showthread.php?t=810143&highlight=scanjet](http://ubuntuforums.org/showthread.php?t=810143&highlight=scanjet) 

since the 6200c is included on the list of scanners at 
[http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html)

I ran the command: sudo aptitude install sane

And it seemed that sane was installed successfully, but then the computer crashed. So I have lost what the screen said about it. In any case the computer still does not recognize my scanner. I'm in Hardy Ubuntu. Any advice about what to do next would be much appreciated.

---

### Post by fr.theo on 2008-10-02
try this tread, it one of mine but the guys helped me out see if it will work for you.

[http://ubuntuforums.org/showthread.php?t=810143](http://ubuntuforums.org/showthread.php?t=810143)

---

### Post by Ludwig9 on 2008-10-02
> **fr.theo said:**
> try this tread, it one of mine but the guys helped me out see if it will work for you.

[http://ubuntuforums.org/showthread.php?t=810143](http://ubuntuforums.org/showthread.php?t=810143)

fr.theo, I do not understand what you mean when you say: 
"I have checked the with "cat scsi" and the scanner is listed"

or: 
I also ran the "lsscsi" and the same result apeared

"[0:0:1:0] process HP C1130A 3540 - " 

Please explain. I am very much a noobie.

I re-ran in Terminal the command: sudo aptitude install sane

These are the results:

george@george-desktop:~$ sudo aptitude install sane
[sudo] password for george: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
george@george-desktop:

---

### Post by clive littlewood on 2008-10-02
Hi

The output would suggest that Xsane is installed.

Have you checked under applications > Graphics > Xsane image scanner ?

I have an HP scanner and this worked for me out of the box !!!

cl

---

### Post by kansasnoob on 2008-10-02
Have you tried the "sane-find-scanner" search:

[http://www.sane-project.org/man/sane-find-scanner.1.html](http://www.sane-project.org/man/sane-find-scanner.1.html)

---

### Post by Ludwig9 on 2008-10-02
I have gotten the following message:
> george@george-desktop:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.




[B]
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0201 [HP ScanJet 6200C]) at libusb:001:005

  # Your USB scanner was (probably) detected. It may or may not be supported by

  # SANE. Try scanimage -L and read the backend's manpage.
[/B]


  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.


What does this mean?   # SANE. Try scanimage -L and read the backend's manpage.

---

### Post by Ludwig9 on 2008-10-02
In Terminal I got the following: 
george@george-desktop:~$ scanimage -L
device `hp:libusb:001:005' is a Hewlett-Packard ScanJet 62x0C flatbed scanner
george@george-desktop:~$ 

What next anyone? It still does not recognize the scanner. I don't understand the bit about: read backend's manpage

---

### Post by Ludwig9 on 2008-10-02
> **clive littlewood said:**
> Hi

The output would suggest that Xsane is installed.

Have you checked under applications > Graphics > Xsane image scanner ?

I have an HP scanner and this worked for me out of the box !!!

cl Yes, I checked there and received this message.

What is the next step? I think I'm getting warm.

---

### Post by Ludwig9 on 2008-10-02
Well it seems to recognize it now, although I haven't had a chance to see if it works yet. At least it is there!!!! Thanks to all. I'll be back for more help very soon undoubtedly.:popcorn:

---

### Post by kansasnoob on 2008-10-02
Generally I'd go to Xsane. Applications > Graphics ...........

But I've always preferred Kooka which you can install from synaptic.

Just DO NOT try to install the documentation or you'll end up with a KDE desktop - in fact Kooka is not available in 8.10 at this point.

---

### Post by fr.theo on 2008-10-02
you must go to the /proc/scsi directory in terminal and then type cat scsi

this will bring up a list of you devices attached to scsi.

e.g theodore@theodore-desktop:/proc/scsi$ [COLOR="Red"]cat scsi[/COLOR]

sorry it took some time to get back to you.


here this process worked for me give it a go

[COLOR="Red"]input in terminal[/COLOR] "sudo apt-get install sane-utils"

[COLOR="Red"]input in terminal[/COLOR] "scanimage -L"

[COLOR="Red"]output in terminal[/COLOR] "device `hp:[COLOR="RoyalBlue"]/dev/sg1[/COLOR]' is a Hewlett-Packard C1130A flatbed scanner"


[COLOR="Red"]input in terminal[/COLOR] "ln -s [COLOR="RoyalBlue"]/dev/sg1[/COLOR] /dev/scanner 

[COLOR="Red"]input in terminal[/COLOR] "chmod 666 [COLOR="RoyalBlue"]/dev/sg1[/COLOR]"

then run xsane it should see the scanner.


see if that works and good luck.

---

### Post by Ludwig9 on 2008-10-03
Right now Xsane image scanner does nothing for me other than to tell me it is looking for a scanner, and then it disappears and never comes back.

fr.theo, you have suggested that I do 2 things, first: 
> 
 you must go to the /proc/scsi directory in terminal and then type cat scsi
this will bring up a list of you devices attached to scsi.
e.g theodore@theodore-desktop:/proc/scsi$ cat scsi
sorry it took some time to get back to you.

And second: 

> here this process worked for me give it a go
input in terminal "sudo apt-get install sane-utils"
input in terminal "scanimage -L"
output in terminal "device `hp:/dev/sg1' is a Hewlett-Packard C1130A flatbed scanner"
input in terminal "ln -s /dev/sg1 /dev/scanner 
input in terminal "chmod 666 /dev/sg1"
then run xsane it should see the scanner.  

I don't understand whether I should do one or the other or both together. And with regard to the first, should not the command be:
george@george-desktop:~$/proc/scsi 

and then george@george-desktop:~$ cat scsi

???

I am confused since in Terminal I cannot type before the $. 

I will wait for your response before proceeding.

---

### Post by Ludwig9 on 2008-10-04
Bump. Can anyone advise me about how to proceed with this installation? In particular, how to correct (if need be) the Terminal commands suggested by fr.theo.

---

### Post by Ludwig9 on 2008-10-08
I have tried to follow fr.theo advice but got nowhere. Any ideas? Xsane Image Scanner finds the scanner but then says that it can't find one  whenever I try to scan something. Here is what I got from Terminal:

> george@george-desktop:~$ /proc/scsi

bash: /proc/scsi: is a directory



george@george-desktop:~$ /proc/scsi$ cat scsi

bash: /proc/scsi$: No such file or directory

george@george-desktop:~$ sudo apt-get install sane-utils

[sudo] password for george: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

sane-utils is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

george@george-desktop:~$ scanimage -L



No scanners were identified. If you were expecting something different,

check that the scanner is plugged in, turned on and detected by the

sane-find-scanner tool (if appropriate). Please read the documentation

which came with this software (README, FAQ, manpages).

george@george-desktop:~$ 

The scanner was plugged in and was on.

---

### Post by Ludwig9 on 2008-10-08
I found this at [http://linux.derkeiler.com/Mailing-Lists/Fedora/2004-05/5564.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2004-05/5564.html)

> Date: Fri, 21 May 2004 20:16:38 -0400
To: [email]fedora-list@redhat.com[/email]


Folks, a tale of woe...

My HP ScanJet 6200C was working fine with FC1, using USB. Under FC2,
it's really weird. sane-find-scanner gives "found USB scanner
(vendor=0x03f0, product=0x0201) at libusb:002:002" . So far, so good.
But note that sane-find-scanner does NOT report the product/manufacturer
ASCII info.

Now scanimage -L (run as root) gives one of 3 responses:
1. Segmentation fault
2. device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed
scanner (good!), or
3. No scanners were identified....

I get all 3 responses randomly as I retry 'scanimage -L'. I have tried
reorganizing my USB ports, power cycling, etc. - same kind of thing.

/var/log/messages (after my su to root):
May 21 10:43:57 localhost kernel: ppdev: user-space parallel port driver
May 21 10:44:05 localhost kernel: usb 1-1: control timeout on ep0out
May 21 10:45:22 localhost last message repeated 4 times
May 21 10:45:44 localhost last message repeated 4 times
(here I power cycled my scanner)
May 21 10:45:54 localhost kernel: usb 1-1: USB disconnect, address 3
May 21 10:45:58 localhost kernel: usb 2-1: new full speed USB device
using address 2
May 21 10:46:43 localhost kernel: usb 2-1: control timeout on ep0in
May 21 10:46:44 localhost kernel: usb 2-1: control timeout on ep0in
May 21 10:46:59 localhost kernel: usb 2-1: control timeout on ep0out
May 21 10:47:18 localhost last message repeated 2 times

All this is on an ASUS A7V8X-MX, Athlon 2000+, 1 GB RAM, etc., etc.

p.s. Here is my 'lsmod'

Module Size Used by
ppdev 5888 0
sd_mod 16384 0
snd_ens1371 17120 1
snd_mixer_oss 13824 2
snd_via82xx 19104 4
snd_pcm 68872 2 snd_ens1371,snd_via82xx
snd_timer 17156 1 snd_pcm
snd_ac97_codec 50436 2 snd_ens1371,snd_via82xx
snd_page_alloc 7940 2 snd_via82xx,snd_pcm
gameport 3328 2 snd_ens1371,snd_via82xx
snd_mpu401_uart 4864 1 snd_via82xx
snd_rawmidi 17184 2 snd_ens1371,snd_mpu401_uart
snd_seq_device 6152 1 snd_rawmidi
snd 38372 15 snd_ens1371,snd_mixer_oss,snd_via82xx,snd_pcm,snd_
timer,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,s
nd_seq_device
soundcore 6112 3 snd
w83781d 26240 0
eeprom 6024 0
i2c_sensor 2176 2 w83781d,eeprom
i2c_isa 1792 0
i2c_viapro 5388 0
i2c_core 16388 5 w83781d,eeprom,i2c_sensor,i2c_isa,i2c_viapro
vmnet 25360 4
vmmon 41912 0
parport_pc 19392 1
lp 8236 0
parport 29640 3 ppdev,parport_pc,lp
nfsd 158496 9
exportfs 4224 1 nfsd
lockd 47944 2 nfsd
ipv6 184288 10
autofs4 10624 1
sunrpc 101064 19 nfsd,lockd
via_rhine 15624 0
mii 3584 1 via_rhine
floppy 47440 0
sg 27552 0
scsi_mod 91344 2 sd_mod,sg
dm_mod 33184 0
ehci_hcd 21896 0
uhci_hcd 23708 0
button 4504 0
battery 6924 0
asus_acpi 8472 0
ac 3340 0
ext3 102376 4
jbd 40216 1 ext3
-----------
There was a hint that the latest sane/xsane packages might have fixed
some HP problems, so I compiled them and replaced the FC2 RPMs. No
luck, same behavior. Other people report that the current sane works OK
with this scanner and USB -- so it's either a hardware problem or a
Fedora/USB problem, I guess.

I have dropped back and connected the Scanjet via its SCSI port. Works
fine that way.

-mse

-- 
fedora-list mailing list
[email]fedora-list@redhat.com[/email]


My 6200C is connected by its USB port.

---

### Post by Ludwig9 on 2008-10-08
I found this at the Fedora forum: [http://forums.fedoraforum.org/showthread.php?t=174468&highlight=6200C](http://forums.fedoraforum.org/showthread.php?t=174468&highlight=6200C)
Suggestions would be much appreciated.

> Well since you said fedora 7 worked with the scanner (i.e. Scanjet 6200C), I tried compiling fedora 7 packages and using them. well I found the problem after not looking that long... your correct Fedora 7 packages do work.. atleast the orignal packages do, updated ones have a usb_reset patch and apparently our scanner doesn't like it very much. so I got the source for the newest Fedora 8 package and removed the usb_reset patch and all works fine now...

sane-backends-1.0.18-18.mc.fc8.i386.rpm :
[http://www.mediafire.com/?5ecxrlqajme](http://www.mediafire.com/?5ecxrlqajme)

sane-backends-libs-1.0.18-18.mc.fc8.i386.rpm
[http://www.mediafire.com/?3je9zjyzpp9](http://www.mediafire.com/?3je9zjyzpp9)

- Mike C 

---

