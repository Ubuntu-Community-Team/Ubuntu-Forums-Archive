---
title: "Cannot use cd player"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by lexrexus on 2011-10-26
ls /dev  lists several cd-dvd players not in computer now.
Will removing their record allow present cd machine to work, or is that irrelevant?
If will help, how do it?

I put cd in player, it takes it and light on front lights up;
nothing on computer screen.
Cannot find player in places.


Am using uby 8.04, broken - apt won' t get;  with old kernel so dial-up modem will work - 19 something, I think.   Have kubuntu 10.04 cd to start over, but cd player in 'new' computer won't install it.  

How do I go further?

jk@jk-desktop:~$ sudo ls /dev
[sudo] password for jk: 
536ep0 ptyb7 ptyq6 ptyv5 ram12 tty48 ttyda ttys5 ttyx4
adsp ptyb8 ptyq7 ptyv6 ram13 tty49 ttydb ttys6 ttyx5
agpgart ptyb9 ptyq8 ptyv7 ram14 tty5 ttydc ttys7 ttyx6
audio ptyba ptyq9 ptyv8 ram15 tty50 ttydd ttys8 ttyx7
bus ptybb ptyqa ptyv9 ram2 tty51 ttyde ttys9 ttyx8
cdrom1 ptybc ptyqb ptyva ram3 tty52 ttydf ttysa ttyx9
cdrw1 ptybd ptyqc ptyvb ram4 tty53 ttye0 ttysb ttyxa
console ptybe ptyqd ptyvc ram5 tty54 ttye1 ttysc ttyxb
core ptybf ptyqe ptyvd ram6 tty55 ttye2 ttysd ttyxc
disk ptyc0 ptyqf ptyve ram7 tty56 ttye3 ttyse ttyxd
dsp ptyc1 ptyr0 ptyvf ram8 tty57 ttye4 ttysf ttyxe
dvd1 ptyc2 ptyr1 ptyw0 ram9 tty58 ttye5 ttyt0 ttyxf
dvdrw1 ptyc3 ptyr2 ptyw1 random tty59 ttye6 ttyt1 ttyy0
fd ptyc4 ptyr3 ptyw2 rtc tty6 ttye7 ttyt2 ttyy1
fd0 ptyc5 ptyr4 ptyw3 scd0 tty60 ttye8 ttyt3 ttyy2
fd0u1040 ptyc6 ptyr5 ptyw4 sda tty61 ttye9 ttyt4 ttyy3
fd0u1120 ptyc7 ptyr6 ptyw5 sda1 tty62 ttyea ttyt5 ttyy4
fd0u1440 ptyc8 ptyr7 ptyw6 sda2 tty63 ttyeb ttyt6 ttyy5
fd0u1600 ptyc9 ptyr8 ptyw7 sda3 tty7 ttyec ttyt7 ttyy6
fd0u1680 ptyca ptyr9 ptyw8 sda4 tty8 ttyed ttyt8 ttyy7
fd0u1722 ptycb ptyra ptyw9 sda5 tty9 ttyee ttyt9 ttyy8
fd0u1743 ptycc ptyrb ptywa sda6 ttya0 ttyef ttyta ttyy9
fd0u1760 ptycd ptyrc ptywb sda7 ttya1 ttyp0 ttytb ttyya
fd0u1840 ptyce ptyrd ptywc sequencer ttya2 ttyp1 ttytc ttyyb
fd0u1920 ptycf ptyre ptywd sequencer2 ttya3 ttyp2 ttytd ttyyc
fd0u360 ptyd0 ptyrf ptywe sg0 ttya4 ttyp3 ttyte ttyyd
fd0u720 ptyd1 ptys0 ptywf sg1 ttya5 ttyp4 ttytf ttyye
fd0u800 ptyd2 ptys1 ptyx0 shm ttya6 ttyp5 ttyu0 ttyyf
fd0u820 ptyd3 ptys2 ptyx1 snapshot ttya7 ttyp6 ttyu1 ttyz0
fd0u830 ptyd4 ptys3 ptyx2 snd ttya8 ttyp7 ttyu2 ttyz1
full ptyd5 ptys4 ptyx3 sndstat ttya9 ttyp8 ttyu3 ttyz2
fuse ptyd6 ptys5 ptyx4 sr0 ttyaa ttyp9 ttyu4 ttyz3
hpet ptyd7 ptys6 ptyx5 stderr ttyab ttypa ttyu5 ttyz4
hwrng ptyd8 ptys7 ptyx6 stdin ttyac ttypb ttyu6 ttyz5
initctl ptyd9 ptys8 ptyx7 stdout ttyad ttypc ttyu7 ttyz6
input ptyda ptys9 ptyx8 tty ttyae ttypd ttyu8 ttyz7
kmem ptydb ptysa ptyx9 tty0 ttyaf ttype ttyu9 ttyz8
kmsg ptydc ptysb ptyxa tty1 ttyb0 ttypf ttyua ttyz9
log ptydd ptysc ptyxb tty10 ttyb1 ttyq0 ttyub ttyza
loop0 ptyde ptysd ptyxc tty11 ttyb2 ttyq1 ttyuc ttyzb
lp0 ptydf ptyse ptyxd tty12 ttyb3 ttyq2 ttyud ttyzc
MAKEDEV ptye0 ptysf ptyxe tty13 ttyb4 ttyq3 ttyue ttyzd
mapper ptye1 ptyt0 ptyxf tty14 ttyb5 ttyq4 ttyuf ttyze
mem ptye2 ptyt1 ptyy0 tty15 ttyb6 ttyq5 ttyv0 ttyzf
mixer ptye3 ptyt2 ptyy1 tty16 ttyb7 ttyq6 ttyv1 urandom
net ptye4 ptyt3 ptyy2 tty17 ttyb8 ttyq7 ttyv2 usbdev1.1_ep00
null ptye5 ptyt4 ptyy3 tty18 ttyb9 ttyq8 ttyv3 usbdev1.1_ep81
nvidia0 ptye6 ptyt5 ptyy4 tty19 ttyba ttyq9 ttyv4 usbdev2.1_ep00
nvidiactl ptye7 ptyt6 ptyy5 tty2 ttybb ttyqa ttyv5 usbdev2.1_ep81
oldmem ptye8 ptyt7 ptyy6 tty20 ttybc ttyqb ttyv6 usbdev3.1_ep00
parport0 ptye9 ptyt8 ptyy7 tty21 ttybd ttyqc ttyv7 usbdev3.1_ep81
port ptyea ptyt9 ptyy8 tty22 ttybe ttyqd ttyv8 usbdev4.1_ep00
ppp ptyeb ptyta ptyy9 tty23 ttybf ttyqe ttyv9 usbdev4.1_ep81
psaux ptyec ptytb ptyya tty24 ttyc0 ttyqf ttyva usbdev5.1_ep00
ptmx ptyed ptytc ptyyb tty25 ttyc1 ttyr0 ttyvb usbdev5.1_ep81
pts ptyee ptytd ptyyc tty26 ttyc2 ttyr1 ttyvc vcs
ptya0 ptyef ptyte ptyyd tty27 ttyc3 ttyr2 ttyvd vcs1
ptya1 ptyp0 ptytf ptyye tty28 ttyc4 ttyr3 ttyve vcs2
ptya2 ptyp1 ptyu0 ptyyf tty29 ttyc5 ttyr4 ttyvf vcs3
ptya3 ptyp2 ptyu1 ptyz0 tty3 ttyc6 ttyr5 ttyw0 vcs4
ptya4 ptyp3 ptyu2 ptyz1 tty30 ttyc7 ttyr6 ttyw1 vcs5
ptya5 ptyp4 ptyu3 ptyz2 tty31 ttyc8 ttyr7 ttyw2 vcs6
ptya6 ptyp5 ptyu4 ptyz3 tty32 ttyc9 ttyr8 ttyw3 vcs7
ptya7 ptyp6 ptyu5 ptyz4 tty33 ttyca ttyr9 ttyw4 vcs8
ptya8 ptyp7 ptyu6 ptyz5 tty34 ttycb ttyra ttyw5 vcsa
ptya9 ptyp8 ptyu7 ptyz6 tty35 ttycc ttyrb ttyw6 vcsa1
ptyaa ptyp9 ptyu8 ptyz7 tty36 ttycd ttyrc ttyw7 vcsa2
ptyab ptypa ptyu9 ptyz8 tty37 ttyce ttyrd ttyw8 vcsa3
ptyac ptypb ptyua ptyz9 tty38 ttycf ttyre ttyw9 vcsa4
ptyad ptypc ptyub ptyza tty39 ttyd0 ttyrf ttywa vcsa5
ptyae ptypd ptyuc ptyzb tty4 ttyd1 ttys0 ttywb vcsa6
ptyaf ptype ptyud ptyzc tty40 ttyd2 ttyS0 ttywc vcsa7
ptyb0 ptypf ptyue ptyzd tty41 ttyd3 ttys1 ttywd vcsa8
ptyb1 ptyq0 ptyuf ptyze tty42 ttyd4 ttyS1 ttywe watchdog
ptyb2 ptyq1 ptyv0 ptyzf tty43 ttyd5 ttys2 ttywf xconsole
ptyb3 ptyq2 ptyv1 ram0 tty44 ttyd6 ttyS2 ttyx0 zero
ptyb4 ptyq3 ptyv2 ram1 tty45 ttyd7 ttys3 ttyx1
ptyb5 ptyq4 ptyv3 ram10 tty46 ttyd8 ttyS3 ttyx2
ptyb6 ptyq5 ptyv4 ram11 tty47 ttyd9 ttys4 ttyx3
jk@jk-desktop:~$

Post Script:   I don't understand any of this, but fstab contains:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0



Help?

---

### Post by lexrexus on 2011-10-26
jk@jk-desktop:~$ sudo mount /dev/cdrom /mnt/mountpoint
[sudo] password for jk: 
mount: special device /dev/cdrom does not exist

jk@jk-desktop:~$ sudo mount /dev/cdrom0 /mnt/mountpoint
mount: special device /dev/cdrom0 does not exist
jk@jk-desktop:~$ 

jk@jk-desktop:~$ sudo mount /dev/scd0 /mnt/mountpoint
[sudo] password for jk: [..... long time ....] 
mount: No medium found
jk@jk-desktop:~$ 


??? 


None of this makes any sense to me.  If you learned anything from the above please explain so an idiot might be able to retain some of your info for future 'events.'   


Thank you!

---

### Post by wolfen69 on 2011-10-26
If all you want to do is reinstall, put the cd in the drive and reboot. Usually hitting F12 at startup or maybe another key will bring up a list of bootable devices. See if cd rom shows up. You could also check your BIOS to see if it is listed.

---

### Post by lexrexus on 2011-10-27
> **wolfen69 said:**
> If all you want to do is reinstall, put the cd in the drive and reboot. Usually hitting F12 at startup or maybe another key will bring up a list of bootable devices. See if cd rom shows up. You could also check your BIOS to see if it is listed.

Checked boot order earlier - cd drive is listed.

Will reboot again & try f12.

Thank you for your reply!

---

### Post by lexrexus on 2011-10-27
> **lexrexus said:**
> Checked boot order earlier - cd drive is listed.

Will reboot again & try f12.

Thank you for your reply!

Didn't see cd.  Will keep reboots to minimum so won't try more keys, but f12 did nothing.

OS barely loads - takes ages, now, used to be much much quicker.
Hope to get 10.04 installed ...  


Thank you!

---

### Post by lexrexus on 2011-10-28
Thank you for your x and expertise.
I will assume that 1. CdDrive is shot; or
2. Same is incompatible w/uby, or
3. OS is broken there, too.

Input?

---

