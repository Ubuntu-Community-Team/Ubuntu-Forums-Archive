---
title: "[SOLVED] Wine C-drive location"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by TheDarkMaster on 2008-11-22
Hi all,
I've just installed Ubuntu on my pc dual-booting with Windows XP. I'm mainly using Ubuntu now but I've got many applycations on my Windows like Photoshop for which I don't want to boot windows again. I can run them i wine but then they are missing files installed on my Original c-drive. I got Ubuntu installed on a 500GB external HDD without making any partitions on that HDD. Does anyone have an idea on how to change the location wine c-drive is on?
When it's possible I don't want to install Photoshop again.

---

### Post by marshall.robert on 2008-11-22
Applications -> Wine -> Configure Wine -> Drives

may i ask where you want to change your drives too? because it may be an idea just to install from the disk without changing anything.

---

### Post by shifty_powers on 2008-11-22
go into your homr directory, press control + h and look for .wine folder.

---

### Post by marshall.robert on 2008-11-22
> **shifty_powers said:**
> go into your homr directory, press control + h and look for .wine folder.

even easier than that is Applications -> Wine -> Browse C:\ Drive

---

### Post by shifty_powers on 2008-11-22
really? didn't realise that.... (sarcasm :D)

i know, but it is also useful to know the physical location in the file system...

---

### Post by janraem2008 on 2008-11-22
It's in /home/Username/.wine/Drive_C

at least on my PC

Jan

---

### Post by walkerk on 2008-11-22
~/.wine/drive_c

---

### Post by c_o_c_a_s on 2008-11-22
Just type cd ~/.wine/drive_c/ to reach there
Regards

---

### Post by TheDarkMaster on 2008-11-22
Great ideas guys but it still doesn't work. Maybe i didn't explain right.
I've got a computer home on which I had installed Windows XP, then I got an external HDD on which I installed Photoshop. But this also installed some files on the windows c-drive. Now I've installed Ubuntu 8.10 also on that new external HDD. I used wine and tried to run the previously installed Photoshop, but it couldn't run because it couldn't find the right files on the c-drive. Now I want wine to be configured so that it points to my original Windows Xp c-drive so i don't have to boot in Windows for using photoshop. Using the options menu and changing the preferences so it points to the original windows HDD doesn't work I just can't change the location, not even as root.

---

### Post by shifty_powers on 2008-11-22
go into terminal

```
winecfg
```

and then go to drives tab.

thats the only thing i can think of.

unless the "options" menu is the above...

---

### Post by TheDarkMaster on 2008-11-22
again thx shift_powers but that's what I ment with the options menu, srry.

---

### Post by shifty_powers on 2008-11-22
ok. well the only suggestion i can make is to visit

[http://forum.winehq.org/viewforum.php?f=2&topicdays=0&start=0](http://forum.winehq.org/viewforum.php?f=2&topicdays=0&start=0)

and ask on the wine forums...

---

### Post by walkerk on 2008-11-22
post the output of 
```
ls /dev
```

your windows partition should show up under /dev/disk or /dev/media. as far as pointing wine at that location... dunno.

---

### Post by Kellemora on 2008-11-22
Hi TDM

I can probably save you a lot of reading and trial and error here!

Wine cannot normally SEE outside of it's imaginary Drive_C in the hidden .wine folder.  There are exceptions, but not many.

I HATE having .wine in my /home directory because that means when I backup the /home directory, I'm backing up programs instead of Data.

I've tried moving DATA folders outside of .wine onto a DataFiles Partition, and nothing I have tried has worked.  So, within .wine on the Drive_C I have a DataFiles folder there, unfortunately Wine does not let you install files from programs where you really would like them to be for some reason.
So it makes backing up DataFiles from programs run in Wine a horrendous task.

I'm a noob too and have not figured any way to ELIMINATE folders from being backed up, or in my case mirrored.
The only option I've found so far is to write a separate program for each file you want to back up or mirror.  Which pretty much says, you can't back up /home without the redundant garbage.
There may be a way and I just haven't learned it yet.

From a program in Wine with a link that uses a web browser, I've never had a problem.  But attachments for documents, images, etc.  I have to go to the Attachments folder from outside of Wine to open them.  Even though I've loaded all the necessary programs for them right in Wine on the Drive_C, it just can't seem to find them.  I think it was designed primarily for stand alone programs and not much else.  And they cannot have any API calls or they won't function!

TTUL
Gary

---

### Post by TheDarkMaster on 2008-11-22
Here is the output of ls/dev:

```

audio               ptyd7  ptytd  ram11       tty62  ttyq1  ttyw3
block               ptyd8  ptyte  ram12       tty63  ttyq2  ttyw4
bus                 ptyd9  ptytf  ram13       tty7   ttyq3  ttyw5
cdrom               ptyda  ptyu0  ram14       tty8   ttyq4  ttyw6
cdrw                ptydb  ptyu1  ram15       tty9   ttyq5  ttyw7
char                ptydc  ptyu2  ram2        ttya0  ttyq6  ttyw8
console             ptydd  ptyu3  ram3        ttya1  ttyq7  ttyw9
core                ptyde  ptyu4  ram4        ttya2  ttyq8  ttywa
cpu_dma_latency     ptydf  ptyu5  ram5        ttya3  ttyq9  ttywb
disk                ptye0  ptyu6  ram6        ttya4  ttyqa  ttywc
dri                 ptye1  ptyu7  ram7        ttya5  ttyqb  ttywd
dsp                 ptye2  ptyu8  ram8        ttya6  ttyqc  ttywe
dvd                 ptye3  ptyu9  ram9        ttya7  ttyqd  ttywf
dvdrw               ptye4  ptyua  random      ttya8  ttyqe  ttyx0
fd                  ptye5  ptyub  rtc         ttya9  ttyqf  ttyx1
full                ptye6  ptyuc  rtc0        ttyaa  ttyr0  ttyx2
fuse                ptye7  ptyud  scd0        ttyab  ttyr1  ttyx3
hidraw0             ptye8  ptyue  sda         ttyac  ttyr2  ttyx4
hpet                ptye9  ptyuf  sda1        ttyad  ttyr3  ttyx5
initctl             ptyea  ptyv0  sdb         ttyae  ttyr4  ttyx6
input               ptyeb  ptyv1  sdb1        ttyaf  ttyr5  ttyx7
kmem                ptyec  ptyv2  sdc         ttyb0  ttyr6  ttyx8
kmsg                ptyed  ptyv3  sdd         ttyb1  ttyr7  ttyx9
log                 ptyee  ptyv4  sde         ttyb2  ttyr8  ttyxa
loop0               ptyef  ptyv5  sdf         ttyb3  ttyr9  ttyxb
loop1               ptyp0  ptyv6  sequencer   ttyb4  ttyra  ttyxc
loop2               ptyp1  ptyv7  sequencer2  ttyb5  ttyrb  ttyxd
loop3               ptyp2  ptyv8  sg0         ttyb6  ttyrc  ttyxe
loop4               ptyp3  ptyv9  sg1         ttyb7  ttyrd  ttyxf
loop5               ptyp4  ptyva  sg2         ttyb8  ttyre  ttyy0
loop6               ptyp5  ptyvb  sg3         ttyb9  ttyrf  ttyy1
loop7               ptyp6  ptyvc  sg4         ttyba  ttys0  ttyy2
lp0                 ptyp7  ptyvd  sg5         ttybb  ttyS0  ttyy3
MAKEDEV             ptyp8  ptyve  sg6         ttybc  ttys1  ttyy4
mem                 ptyp9  ptyvf  shm         ttybd  ttyS1  ttyy5
mixer               ptypa  ptyw0  snapshot    ttybe  ttys2  ttyy6
net                 ptypb  ptyw1  snd         ttybf  ttyS2  ttyy7
network_latency     ptypc  ptyw2  sndstat     ttyc0  ttys3  ttyy8
network_throughput  ptypd  ptyw3  sr0         ttyc1  ttyS3  ttyy9
null                ptype  ptyw4  stderr      ttyc2  ttys4  ttyya
oldmem              ptypf  ptyw5  stdin       ttyc3  ttys5  ttyyb
parport0            ptyq0  ptyw6  stdout      ttyc4  ttys6  ttyyc
port                ptyq1  ptyw7  tty         ttyc5  ttys7  ttyyd
ppp                 ptyq2  ptyw8  tty0        ttyc6  ttys8  ttyye
psaux               ptyq3  ptyw9  tty1        ttyc7  ttys9  ttyyf
ptmx                ptyq4  ptywa  tty10       ttyc8  ttysa  ttyz0
pts                 ptyq5  ptywb  tty11       ttyc9  ttysb  ttyz1
ptya0               ptyq6  ptywc  tty12       ttyca  ttysc  ttyz2
ptya1               ptyq7  ptywd  tty13       ttycb  ttysd  ttyz3
ptya2               ptyq8  ptywe  tty14       ttycc  ttyse  ttyz4
ptya3               ptyq9  ptywf  tty15       ttycd  ttysf  ttyz5
ptya4               ptyqa  ptyx0  tty16       ttyce  ttyt0  ttyz6
ptya5               ptyqb  ptyx1  tty17       ttycf  ttyt1  ttyz7
ptya6               ptyqc  ptyx2  tty18       ttyd0  ttyt2  ttyz8
ptya7               ptyqd  ptyx3  tty19       ttyd1  ttyt3  ttyz9
ptya8               ptyqe  ptyx4  tty2        ttyd2  ttyt4  ttyza
ptya9               ptyqf  ptyx5  tty20       ttyd3  ttyt5  ttyzb
ptyaa               ptyr0  ptyx6  tty21       ttyd4  ttyt6  ttyzc
ptyab               ptyr1  ptyx7  tty22       ttyd5  ttyt7  ttyzd
ptyac               ptyr2  ptyx8  tty23       ttyd6  ttyt8  ttyze
ptyad               ptyr3  ptyx9  tty24       ttyd7  ttyt9  ttyzf
ptyae               ptyr4  ptyxa  tty25       ttyd8  ttyta  urandom
ptyaf               ptyr5  ptyxb  tty26       ttyd9  ttytb  usbdev1.1_ep00
ptyb0               ptyr6  ptyxc  tty27       ttyda  ttytc  usbdev1.1_ep81
ptyb1               ptyr7  ptyxd  tty28       ttydb  ttytd  usbdev1.4_ep00
ptyb2               ptyr8  ptyxe  tty29       ttydc  ttyte  usbdev1.4_ep02
ptyb3               ptyr9  ptyxf  tty3        ttydd  ttytf  usbdev1.4_ep81
ptyb4               ptyra  ptyy0  tty30       ttyde  ttyu0  usbdev2.1_ep00
ptyb5               ptyrb  ptyy1  tty31       ttydf  ttyu1  usbdev2.1_ep81
ptyb6               ptyrc  ptyy2  tty32       ttye0  ttyu2  usbdev2.2_ep00
ptyb7               ptyrd  ptyy3  tty33       ttye1  ttyu3  usbdev2.2_ep01
ptyb8               ptyre  ptyy4  tty34       ttye2  ttyu4  usbdev2.2_ep82
ptyb9               ptyrf  ptyy5  tty35       ttye3  ttyu5  usbdev3.1_ep00
ptyba               ptys0  ptyy6  tty36       ttye4  ttyu6  usbdev3.1_ep81
ptybb               ptys1  ptyy7  tty37       ttye5  ttyu7  usbdev4.1_ep00
ptybc               ptys2  ptyy8  tty38       ttye6  ttyu8  usbdev4.1_ep81
ptybd               ptys3  ptyy9  tty39       ttye7  ttyu9  usbdev4.2_ep00
ptybe               ptys4  ptyya  tty4        ttye8  ttyua  usbdev4.2_ep81
ptybf               ptys5  ptyyb  tty40       ttye9  ttyub  usbdev5.1_ep00
ptyc0               ptys6  ptyyc  tty41       ttyea  ttyuc  usbdev5.1_ep81
ptyc1               ptys7  ptyyd  tty42       ttyeb  ttyud  vcs
ptyc2               ptys8  ptyye  tty43       ttyec  ttyue  vcs1
ptyc3               ptys9  ptyyf  tty44       ttyed  ttyuf  vcs2
ptyc4               ptysa  ptyz0  tty45       ttyee  ttyv0  vcs3
ptyc5               ptysb  ptyz1  tty46       ttyef  ttyv1  vcs4
ptyc6               ptysc  ptyz2  tty47       ttyp0  ttyv2  vcs5
ptyc7               ptysd  ptyz3  tty48       ttyp1  ttyv3  vcs6
ptyc8               ptyse  ptyz4  tty49       ttyp2  ttyv4  vcs7
ptyc9               ptysf  ptyz5  tty5        ttyp3  ttyv5  vcs8
ptyca               ptyt0  ptyz6  tty50       ttyp4  ttyv6  vcsa
ptycb               ptyt1  ptyz7  tty51       ttyp5  ttyv7  vcsa1
ptycc               ptyt2  ptyz8  tty52       ttyp6  ttyv8  vcsa2
ptycd               ptyt3  ptyz9  tty53       ttyp7  ttyv9  vcsa3
ptyce               ptyt4  ptyza  tty54       ttyp8  ttyva  vcsa4
ptycf               ptyt5  ptyzb  tty55       ttyp9  ttyvb  vcsa5
ptyd0               ptyt6  ptyzc  tty56       ttypa  ttyvc  vcsa6
ptyd1               ptyt7  ptyzd  tty57       ttypb  ttyvd  vcsa7
ptyd2               ptyt8  ptyze  tty58       ttypc  ttyve  vcsa8
ptyd3               ptyt9  ptyzf  tty59       ttypd  ttyvf  watchdog
ptyd4               ptyta  ram0   tty6        ttype  ttyw0  xconsole
ptyd5               ptytb  ram1   tty60       ttypf  ttyw1  zero
ptyd6               ptytc  ram10  tty61       ttyq0  ttyw2

```

---

