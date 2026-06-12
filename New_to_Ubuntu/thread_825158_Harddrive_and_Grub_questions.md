---
title: "Harddrive and Grub questions"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by AmericasCup222 on 2008-06-10
Hi guys,
I am currently running my personalized Ubuntu Hardy system on a 30GB IDE Harddrive.  However, I recently purchased a larger 80GB SATA Drive and was wondering if there was any way that I could transfer my installation to that drive without having to re-install.  Also, I am soon to be getting another computer with a windows installation to make it easier for me to play games.  That computer has the installation of windows set up on a RAID 0 with duel 72GB harddrives.  Will windows still work if I take the drives directly out of that computer and put them into mine? also, will GRUB recognize that there is now a windows system running with it and allow me to select what system i wish to use? Thank you very much, AC222

System Specs:
AMD x2 4200+ 2.2 GHz processor
Biostar GeForce 7025 motherboard
2.5GB DDR2 memory
Compaq Floppy disc drive
Generic DVD drive
80GB ExcelStor SATA drive
30GB generic IDE drive
430 Watt power supply 
(also have many spare parts)

---

### Post by Duck2006 on 2008-06-10
You can use the dd commands.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

Or part image.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

To copy your system from one drive to the other.
You will have to edit your menu.lst file and your fstab after you have copyed  the files from one drive to the other.

---

### Post by gr4nf on 2008-06-10
Here is my awful but functional way to do it:

Boot into a live cd, like the ubuntu install disk. Open a terminal with the CD. use the commands:
```

sudo mkdir /mnt2
mke2fs -j /dev/(whatever the bigger HD is.) #WILL ERASE ALL DATA FROM BIGGER HD
sudo mount /dev/(whatever the smaller HD is. try sda.) /mnt
sudo mount /dev/(whatever the bigger HD is.) /mnt2
sudo cp /mnt/* /mnt2/
sudo umount /mnt /mnt2

```
this should work.

---

### Post by gr4nf on 2008-06-10
If you dont know what the /dev ids of your hard drives are, please post the output of 
```
ls /dev
```
to the forum, and we should be able to figure it out.

---

### Post by AmericasCup222 on 2008-06-10
```
alex@FlakPanzer5:~$ ls /dev
adsp       port   ptyca  ptyp9  ptys8  ptyv7  ptyy6   sdb1        tty36  ttyad  ttydc  ttyqb  ttyt6  ttyw5  ttyz4
audio      ppp    ptycb  ptypa  ptys9  ptyv8  ptyy7   sdb2        tty37  ttyae  ttydd  ttyqc  ttyt7  ttyw6  ttyz5
bus        psaux  ptycc  ptypb  ptysa  ptyv9  ptyy8   sdb5        tty38  ttyaf  ttyde  ttyqd  ttyt8  ttyw7  ttyz6
cdrom      ptmx   ptycd  ptypc  ptysb  ptyva  ptyy9   sequencer   tty39  ttyb0  ttydf  ttyqe  ttyt9  ttyw8  ttyz7
console    pts    ptyce  ptypd  ptysc  ptyvb  ptyya   sequencer2  tty4   ttyb1  ttye0  ttyqf  ttyta  ttyw9  ttyz8
core       ptya0  ptycf  ptype  ptysd  ptyvc  ptyyb   sg0         tty40  ttyb2  ttye1  ttyr0  ttytb  ttywa  ttyz9
disk       ptya1  ptyd0  ptypf  ptyse  ptyvd  ptyyc   sg1         tty41  ttyb3  ttye2  ttyr1  ttytc  ttywb  ttyza
dsp        ptya2  ptyd1  ptyq0  ptysf  ptyve  ptyyd   sg2         tty42  ttyb4  ttye3  ttyr2  ttytd  ttywc  ttyzb
dvd        ptya3  ptyd2  ptyq1  ptyt0  ptyvf  ptyye   shm         tty43  ttyb5  ttye4  ttyr3  ttyte  ttywd  ttyzc
fd         ptya4  ptyd3  ptyq2  ptyt1  ptyw0  ptyyf   snapshot    tty44  ttyb6  ttye5  ttyr4  ttytf  ttywe  ttyzd
fd0        ptya5  ptyd4  ptyq3  ptyt2  ptyw1  ptyz0   snd         tty45  ttyb7  ttye6  ttyr5  ttyu0  ttywf  ttyze
fd0u1040   ptya6  ptyd5  ptyq4  ptyt3  ptyw2  ptyz1   sndstat     tty46  ttyb8  ttye7  ttyr6  ttyu1  ttyx0  ttyzf
fd0u1120   ptya7  ptyd6  ptyq5  ptyt4  ptyw3  ptyz2   sr0         tty47  ttyb9  ttye8  ttyr7  ttyu2  ttyx1  urandom
fd0u1440   ptya8  ptyd7  ptyq6  ptyt5  ptyw4  ptyz3   stderr      tty48  ttyba  ttye9  ttyr8  ttyu3  ttyx2  usbdev1.1_ep00
fd0u1600   ptya9  ptyd8  ptyq7  ptyt6  ptyw5  ptyz4   stdin       tty49  ttybb  ttyea  ttyr9  ttyu4  ttyx3  usbdev1.1_ep81
fd0u1680   ptyaa  ptyd9  ptyq8  ptyt7  ptyw6  ptyz5   stdout      tty5   ttybc  ttyeb  ttyra  ttyu5  ttyx4  usbdev2.1_ep00
fd0u1722   ptyab  ptyda  ptyq9  ptyt8  ptyw7  ptyz6   tty         tty50  ttybd  ttyec  ttyrb  ttyu6  ttyx5  usbdev2.1_ep81
fd0u1743   ptyac  ptydb  ptyqa  ptyt9  ptyw8  ptyz7   tty0        tty51  ttybe  ttyed  ttyrc  ttyu7  ttyx6  usbdev2.2_ep00
fd0u1760   ptyad  ptydc  ptyqb  ptyta  ptyw9  ptyz8   tty1        tty52  ttybf  ttyee  ttyrd  ttyu8  ttyx7  usbdev2.2_ep81
fd0u1840   ptyae  ptydd  ptyqc  ptytb  ptywa  ptyz9   tty10       tty53  ttyc0  ttyef  ttyre  ttyu9  ttyx8  usbdev3.1_ep00
fd0u1920   ptyaf  ptyde  ptyqd  ptytc  ptywb  ptyza   tty11       tty54  ttyc1  ttyp0  ttyrf  ttyua  ttyx9  usbdev3.1_ep81
fd0u360    ptyb0  ptydf  ptyqe  ptytd  ptywc  ptyzb   tty12       tty55  ttyc2  ttyp1  ttys0  ttyub  ttyxa  usbdev4.1_ep00
fd0u720    ptyb1  ptye0  ptyqf  ptyte  ptywd  ptyzc   tty13       tty56  ttyc3  ttyp2  ttyS0  ttyuc  ttyxb  usbdev4.1_ep81
fd0u800    ptyb2  ptye1  ptyr0  ptytf  ptywe  ptyzd   tty14       tty57  ttyc4  ttyp3  ttys1  ttyud  ttyxc  vcs
fd0u820    ptyb3  ptye2  ptyr1  ptyu0  ptywf  ptyze   tty15       tty58  ttyc5  ttyp4  ttyS1  ttyue  ttyxd  vcs1
fd0u830    ptyb4  ptye3  ptyr2  ptyu1  ptyx0  ptyzf   tty16       tty59  ttyc6  ttyp5  ttys2  ttyuf  ttyxe  vcs2
full       ptyb5  ptye4  ptyr3  ptyu2  ptyx1  ram0    tty17       tty6   ttyc7  ttyp6  ttyS2  ttyv0  ttyxf  vcs3
fuse       ptyb6  ptye5  ptyr4  ptyu3  ptyx2  ram1    tty18       tty60  ttyc8  ttyp7  ttys3  ttyv1  ttyy0  vcs4
hidraw0    ptyb7  ptye6  ptyr5  ptyu4  ptyx3  ram10   tty19       tty61  ttyc9  ttyp8  ttyS3  ttyv2  ttyy1  vcs5
hpet       ptyb8  ptye7  ptyr6  ptyu5  ptyx4  ram11   tty2        tty62  ttyca  ttyp9  ttys4  ttyv3  ttyy2  vcs6
initctl    ptyb9  ptye8  ptyr7  ptyu6  ptyx5  ram12   tty20       tty63  ttycb  ttypa  ttys5  ttyv4  ttyy3  vcs7
input      ptyba  ptye9  ptyr8  ptyu7  ptyx6  ram13   tty21       tty7   ttycc  ttypb  ttys6  ttyv5  ttyy4  vcs8
kmem       ptybb  ptyea  ptyr9  ptyu8  ptyx7  ram14   tty22       tty8   ttycd  ttypc  ttys7  ttyv6  ttyy5  vcsa
kmsg       ptybc  ptyeb  ptyra  ptyu9  ptyx8  ram15   tty23       tty9   ttyce  ttypd  ttys8  ttyv7  ttyy6  vcsa1
log        ptybd  ptyec  ptyrb  ptyua  ptyx9  ram2    tty24       ttya0  ttycf  ttype  ttys9  ttyv8  ttyy7  vcsa2
loop0      ptybe  ptyed  ptyrc  ptyub  ptyxa  ram3    tty25       ttya1  ttyd0  ttypf  ttysa  ttyv9  ttyy8  vcsa3
lp0        ptybf  ptyee  ptyrd  ptyuc  ptyxb  ram4    tty26       ttya2  ttyd1  ttyq0  ttysb  ttyva  ttyy9  vcsa4
MAKEDEV    ptyc0  ptyef  ptyre  ptyud  ptyxc  ram5    tty27       ttya3  ttyd2  ttyq1  ttysc  ttyvb  ttyya  vcsa5
mcelog     ptyc1  ptyp0  ptyrf  ptyue  ptyxd  ram6    tty28       ttya4  ttyd3  ttyq2  ttysd  ttyvc  ttyyb  vcsa6
mem        ptyc2  ptyp1  ptys0  ptyuf  ptyxe  ram7    tty29       ttya5  ttyd4  ttyq3  ttyse  ttyvd  ttyyc  vcsa7
mixer      ptyc3  ptyp2  ptys1  ptyv0  ptyxf  ram8    tty3        ttya6  ttyd5  ttyq4  ttysf  ttyve  ttyyd  vcsa8
net        ptyc4  ptyp3  ptys2  ptyv1  ptyy0  ram9    tty30       ttya7  ttyd6  ttyq5  ttyt0  ttyvf  ttyye  xconsole
null       ptyc5  ptyp4  ptys3  ptyv2  ptyy1  random  tty31       ttya8  ttyd7  ttyq6  ttyt1  ttyw0  ttyyf  zero
nvidia0    ptyc6  ptyp5  ptys4  ptyv3  ptyy2  rtc     tty32       ttya9  ttyd8  ttyq7  ttyt2  ttyw1  ttyz0
nvidiactl  ptyc7  ptyp6  ptys5  ptyv4  ptyy3  scd0    tty33       ttyaa  ttyd9  ttyq8  ttyt3  ttyw2  ttyz1
oldmem     ptyc8  ptyp7  ptys6  ptyv5  ptyy4  sda     tty34       ttyab  ttyda  ttyq9  ttyt4  ttyw3  ttyz2
parport0   ptyc9  ptyp8  ptys7  ptyv6  ptyy5  sdb     tty35       ttyac  ttydb  ttyqa  ttyt5  ttyw4  ttyz3
```

Thats the output
Thanks, AC222

---

### Post by gr4nf on 2008-06-10
nevermind. See below, that's faster.

---

### Post by Duck2006 on 2008-06-10
From the terminal,

sudo fdisk -l

and post the output.

---

### Post by AmericasCup222 on 2008-06-10
```
alex@FlakPanzer5:~$ sudo mke2fs -j /dev/sda
mke2fs 1.40.8 (13-Mar-2008)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5029888 inodes, 20104560 blocks
1005228 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
614 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```

So, sda appears to be the device I am currently using.  Also, I'm not trying to be a pain, but could someone give me a bit of a walkthough on exactly what Im suppose to do here? Im really kind of a Newbie here and have only been using Linux for a few months, and I really don't want to screw anything up as i have some information on here i don't wish to loose.  Thank you once again, AC222

---

### Post by gr4nf on 2008-06-10
are you running off your working system right now?

Ok, you should have an ext3 partition on your bigger drive now. Try:
```

sudo mount /dev/sda /mnt
or
sudo mount /dev/sda1 /mnt

```

so you can see of the creation was successful.

if it mounts successfully, you can then boot from a live cd, and install ubuntu on the bigger drive. Make sure that the device you install it on is /dev/sda, not /dev/sdb.

---

### Post by Duck2006 on 2008-06-10
There is a walk through on the partimage link i gave you.

---

### Post by AmericasCup222 on 2008-06-10
Yes, Im on my working system right now.  And im sorry guys, alot of this stuff is just flying right over my Uber n00bly head.

---

### Post by gr4nf on 2008-06-10
What we have done so far is formatted your bigger drive. Your smaller drive, with all your data on it, is basically impregnable while you are using it, so it wont be screwed up by all this. What you should do now is install ubuntu on the bigger drive. Make sure that you dont install it on the smaller one. Do you have an install cd? while booted into the cd, you can still run a browser and get on the forums. I can walk you through the install once you are booted into the cd.
Good Luck!

---

### Post by AmericasCup222 on 2008-06-10
Ok, so im running a fresh install onto my large harddrive and when im done with that i should come back here?

---

### Post by gr4nf on 2008-06-10
when you are done, boot into the new system, and call us from there, yes.

---

### Post by AmericasCup222 on 2008-06-10
Ok, will do. Be back in around 50 minutes.  Thanks a lot for your time!

---

### Post by AmericasCup222 on 2008-06-10
Thanks guys, but it looks like i wont be able to install untill tomorrow, but ill be back then. Thank you, AC222

---

### Post by gr4nf on 2008-06-10
see you then. (is always on, has no other life :))

---

### Post by AmericasCup222 on 2008-06-16
Sorry for the extreem delay, but Im now beginning my install. Thanks!

---

### Post by gr4nf on 2008-06-16
No problem. Good Luck, will advise.

---

### Post by AmericasCup222 on 2008-06-16
Ok, I am now on the new installation. What should I do now?

---

### Post by gr4nf on 2008-06-16
Skip through untill you reach the partitioner. It should give you the option to select a device at some point either in the partitioner or along the process.

---

### Post by AmericasCup222 on 2008-06-16
I already have installed a 2nd Hardy installation to my 80GIG HD, I am no longer on the live CD.

---

### Post by AmericasCup222 on 2008-06-16
One odd thing I am noticing is that some of my programs seem to have carried over their settings (such as my accounts in pidgin) however, other options I had such as my optionally installed games/programs are no longer in the menu.

---

### Post by gr4nf on 2008-06-16
Ok, now open a terminal and try:
```

sudo mount /dev/sdb /mnt

```
and if that's the wrong one (meaning it says "in use") then try:
```

sudo mount /dev/sda /mnt

```

---

### Post by AmericasCup222 on 2008-06-16
The first code comes up as "mount: /dev/sdb already mounted or /mnt busy" but when I enter the second set of code it comes up with "mount: you must specify the filesystem type"

---

### Post by gr4nf on 2008-06-16
try:
```

sudo mount -f ext3 /dev/sda /mnt

```

---

### Post by AmericasCup222 on 2008-06-16
Ok that seems to have worked. Whats next?

---

### Post by Duck2006 on 2008-06-16
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by AmericasCup222 on 2008-06-16
I all ready succeeded in mounting the drive, the question is how to transfer that installation to this one. Thanks though, Duck

---

### Post by gr4nf on 2008-06-16
Go into /mnt with a standard file browser, and retrieve what you need. The only essential materials are in:
/home
/etc
/root
and any other specific places you may have put them. Replace the ones the installer mad with the ones that you have in your old drive.

---

### Post by meierfra. on 2008-06-16
gr4nf:  Do you realize that you told the OP to mount the whole hard drive?  "/dev/sda" is a hard drive, not a partition. As far as I know, one cannot mount a hard drive

---

### Post by AmericasCup222 on 2008-06-16
It says I dont have the proper permissions, which I know means i must log in as ROOT but how do I find out the ROOT password in ubuntu?

---

### Post by meierfra. on 2008-06-16
>  sudo mke2fs -j /dev/sda

O.k   gr4nf. I see, you turned  the whole hard drive into a file system. I hope you know what you are doing.

---

### Post by AmericasCup222 on 2008-06-16
OK guys, I'm back to where I started- aka booting straight up onto my 30GB HDD which is still working perfectly. I think I've decided to stay here, as I'm getting quite wary of loosing my things...I guess ill just use the 80 gig as storage space for now, until I feel more comfortable with what Im doing.  I appreciate your help, but I guess ill just stay where I am as the transferring the files to the other drive didn't seem to work, it just booted me to my old drive  TYVM, AC222


Actually, can anyone answer my original question about GRUB while were at it still?

---

### Post by gr4nf on 2008-06-16
Sorry i couldn't be of more service. I suppose an easier way, if you wished to do so, would be to simply back up all your important stuff and install on your big drive, wiping the smaller one. To help with grub, run:
```

man grub

```
and once you know what you need to do, reconfigure it with those instructions.

Good Luck, and sorry to have put you through that fruitless process!

---

