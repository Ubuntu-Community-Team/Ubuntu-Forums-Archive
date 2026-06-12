---
title: "How To: If Your Nvidia Driver Won't Install (8.10)"
date: 2008-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by 67GTA on 2008-12-07
There are a large number of PC's with Nvidia graphics cards and certain TV tuner/radio card combos that are affected by this bug. If you can't get your Restricted Nvidia driver installed in Ubuntu 8.10, and are greeted with the bulletproofx "Low Graphics Mode" at boot, then this might be a solution. To see if you are affected, open a terminal and run: ```
lsmod | grep cx18
``` If you get no output from this command, this does not affect you. If you get something similar to this, then this how to is for you:

```
cx18                   96832  0 
dvb_core               86272  1 cx18
videodev               41344  2 tuner,cx18
compat_ioctl32          9344  1 cx18
i2c_algo_bit           14340  1 cx18
cx2341x                21124  1 cx18
v4l2_common            19840  4 cs5345,tuner,cx18,cx2341x
tveeprom               20228  1 cx18
i2c_core               31892  14 adm1021,mxl5005s,s5h1409,tuner_simple,tda9887,tda8290,cs5345,tuner,cx18,nvidia,i2c_algo_bit,v4l2_common,tveeprom,i2c_nforce2
```We are looking for the cx18 module. There is a known conflict between the cx18 module and the nvidia driver. The cx18 module was introduced into the 2.6.27 kernel (Ubuntu 8.10/Mint6) for certain Hauppauge/Conexant TV tuner/radio cards. If your PC has one of these cards, the cx18 module will be loaded at each boot, and stop the Nvidia card from initializing while using the nvidia driver. The nv driver is not affected. There are two options at the moment to work around this. 

1.) If you plan on using your tuner/radio card, then this is the solution: 

Reallocate the virtual memory so both the cx18 and nvidia modules will coexist. Open a terminal and run ```
sudo gedit /boot/grub/menu.lst
``` Then you need to find the "kernel" line for your current kernel and add ```
vmalloc=256M
``` at the end and save. An example would be like this: ```
title        Ubuntu 8.10, kernel 2.6.27-10-generic
uuid        84456e0a-8648-477a-96ef-0116151ecc8c
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=84456e0a-8648-477a-96ef-0116151ecc8c ro quiet splash rootflags=data=writeback vmalloc=256M
initrd        /boot/initrd.img-2.6.27-10-generic
quiet
``` Now you should be able to boot normally with the nvidia driver installed and still use your Tuner card.

2.) If you do not plan on using your tuner/radio, or if you don't have one and the module is being loaded by mistake, then you can just blacklist the cx18 module so it won't load at boot time. Open a terminal and run ```
sudo gedit /etc/modprobe.d/blacklist
``` Then add ```
blacklist cx18
``` to the end of the file and save.

---

### Post by forks on 2009-02-27
Thanks for this post 67GTA.  It finally fixed my Mythbuntu setup.  My Hauppauge HVR-1600 was not playing well with my p5n7a-vm (GeForce 9300) and I was having no luck at all until now.  

Cheers

---

### Post by pzba77 on 2009-03-15
I couldn't find a solution for this conflict so I opted for dual booting Ubuntu 8.04 (so I could use accelerated graphics) and Ubuntu 8.10 but this worked for me. Thanks.

---

### Post by binbash on 2009-03-16
Thanks for the tip

---

### Post by dragonfixed on 2009-03-17
How did you get your Hauppauge HVR-1600 to run and be found my mythtv in ubuntu 8.04 or 8.10. I have the same card and the computer wont find the card in ubuntu 8.04 with mythtv


Shawn

---

### Post by 67GTA on 2009-03-19
> **dragonfixed said:**
> How did you get your Hauppauge HVR-1600 to run and be found my mythtv in ubuntu 8.04 or 8.10. I have the same card and the computer wont find the card in ubuntu 8.04 with mythtv


Shawn

The cx18 module for the 1600 was not in the 8.04 kernel version. It first came with the 2.6.27 version in 8.10. For 8.04, you will have to install the module, and put some firmware files in the kernel directory to make it work. MythTV has an easy how to here with copy and paste commands: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

---

### Post by 67GTA on 2009-03-19
Just my 2 cents, mplayer has been the easiest so far to watch TV with. For FM radio, you can use gnomeradio. There is a bug in the last two versions. You have to open gnomeradio, change /dev/radio to /dev/radio0. Then open a terminal and run  ```
aplay -f dat < /dev/video24
``` to get sound from the tuner.

---

### Post by spartan777 on 2009-05-06
67GTA, you are awesome. worked like a charm.

---

### Post by k4kelly on 2009-05-17
I'new to the command line interface is this correct place for the code  vmalloc=256M. Wher can i get a copy of the commands and some examples.

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e350bf4-1126-4330-9114-369714c919df ro quiet splash vmalloc=256M
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e350bf4-1126-4330-9114-369714c919df ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/memtest86+.bin
quiet

---

### Post by 67GTA on 2009-05-17
> I'new to the command line interface is this correct place for the code vmalloc=256M. Wher can i get a copy of the commands and some examples.

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e350bf4-1126-4330-9114-369714c919df ro quiet splash vmalloc=256M
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e350bf4-1126-4330-9114-369714c919df ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6e350bf4-1126-4330-9114-369714c919df
kernel        /boot/memtest86+.bin
quiet 	

Yes, that is correct. You can copy paste the commands from my howto plus see an example of mine in the first post of this thread.

---

### Post by skompier on 2009-05-21
Thank you.

---

### Post by Tim_Olaguna on 2009-05-22
WOW!  This worked great for me (the 2nd option).  I have an HP Media Center m8120n PC connected to a Samsung 226BW monitor and just could not get my nvidia 7350 LE card to work at all.  I have no desire to watch TV via cable or antenna on my system so disabling the TV tuner card is just fine.

Thank you so much.

---

### Post by Son of William on 2009-05-23
Thanks so much for this thread.

I just updated Ibex to the latest kernel and this bug popped up again when the installer wrote a generic entry on my menu.lst.  This is the second time I have had to fix this problem.  Does anyone know if this bug is fixed in Jackalope?

---

### Post by 67GTA on 2009-05-23
> **Son of William said:**
> Thanks so much for this thread.

I just updated Ibex to the latest kernel and this bug popped up again when the installer wrote a generic entry on my menu.lst.  This is the second time I have had to fix this problem.  Does anyone know if this bug is fixed in Jackalope?

No, it's still affected. I reported it against the kernel, but was marked "won't fix" because the cx18 module comes from Hauppauge. It is actually still in beta right now. It has been reported to them also, so maybe it will get fixed in the next couple of kernel releases.

---

### Post by MythAaron on 2009-06-19
Thank you, thank you, thank you!  Your trick solved my problem.

Let my throw in another wrinkle:  I didn't have this problem until I upgraded from 512MB to 1GB.  If my experience keeps someone from getting the big headache I have, then I'll be happy.

---

### Post by Lepy on 2009-09-07
Thank you!!!!!!!!

My mythbuntu box had been running flawlessly with a HVR-1600 and a 6800GT for a few months now, but yesterday the screen wouldn't wake, and upon reboot I was greeted with the evil low-graphics mode.

After pulling my hair out and trying literally every fix I could think of, this worked like a charm and has me up and running 185's. I completely agree with you, MythAaron.

---

### Post by Seakip18 on 2009-10-11
You sir, have made my day and the next 3 days of hair pulling a lot easier. 

No where have I read about this issue until I saw it here. I was instead just upgrading my box to use my new Hauppage card and kept hitting walls

I'll update the mythTV wiki with this info, but....Thank you. You made what was quickly becoming a harrowing experience into a 30s vi session. 

NOTE:
With both upgrades and fresh installs of 9.04, this issue is STILL PRESENT. If you install Mythbuntu and have an Hauppage card cx18, and also have a 7600Nvidia, you will get this issue.

---

### Post by 67GTA on 2009-10-11
I filed a bug report, but it was marked "WON'T FIX" because the cx18 module comes from Hauppauge. I have not found any way to give feedback about this to Hauppauge. At least they release drivers:)

---

### Post by Seakip18 on 2009-10-12
Just wanted to follow up with that this managed to save my upgraded Mythbuntu (from 7.10 to 9.04) and a lot of headaches. Step one solved my fresh install issues right away, but I had mucked up the upgraded with attempting to install newer drivers. 

If this solution doesn't immediately fix your install, uninstall any downloaded drivers and reinstall ONE nvidia driver. Check out the guide provided [here from help.ubuntu]("https://help.ubuntu.com/community/NvidiaManual")

I was getting API mismatch errors when I ran sudo nvidia-xconfig -a. 

For me, I had downloaded and installed 815. Once I uninstalled it using the package used to install, I reinstalled the 800 via apt-get and was able to run Nvidia-settings. I replaced my new Nvidia xorg.conf with a backup I had made prior to upgrading and my TV was receiving 1920x1080 once again!


I've updated the HVR-1600 MythTV entry with a partial republish w/ attribution of the first post and links pointing to this thread:[Mythtv: Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600")


Lessons learned:
1. When performing an upgrade to support new hardware and the upgrade works only to start having new failures, assume the new hardware had a hand. This would have cut down on the amount of searching I did. 

2. Just when you get ready to swear off getting the hardware to work, you'll come across a thread like this. 

3. A backup today is worth a week in the future:

```

 mkdir confs
//I like to know WHERE it came from...so I keep a file of that around.
sudo find / -name *.conf >> confLocs.txt
while read line
do
sudo cp $line ~/confs/
echo $line copied.
done < confLocs.txt
```

---

### Post by TenGees on 2009-11-07
Anyone willing to update this vmalloc hack for fresh installs of 9.10 which don't use menu.lst (grub2)? I just reinstalled 9.04 to use this method. I think if I do a system upgrade, it'll keep grub1 and the hack will still work but I'm not sure that I want to try it. ;)

---

### Post by The Odometer on 2009-11-20
> **TenGees said:**
> Anyone willing to update this vmalloc hack for fresh installs of 9.10 which don't use menu.lst (grub2)? I just reinstalled 9.04 to use this method. I think if I do a system upgrade, it'll keep grub1 and the hack will still work but I'm not sure that I want to try it. ;)

Ditto here. Using the open source driver until someone comes out with instructions on how to do it. I'm not certain how to get started--and really don't want to mess up what I have going.

---

### Post by The Odometer on 2009-11-22
Here's the answer to my question. If I'd only read more closely before posting. I'm posting here for anyone else that has the same question. I tried this--and it worked perfectly!

[http://ubuntuforums.org/showthread.php?t=1308935&highlight=vmalloc+grub2](http://ubuntuforums.org/showthread.php?t=1308935&highlight=vmalloc+grub2)

(see post #6)

---

### Post by LarryJ2 on 2009-12-21
Like Christmas Scrooge, the nvidia binary driver VS. conexant cx18 conflict is still with us. (written 21 Dec 09) So after installing the nvidia drivers and  doing  nvidia-xconfig and you are still stuck at a max screen resolution of 800x600,  this might help:

My mythbuntu  is now 9.10 with myth .22. 
> lj@mythtv:~$ mythbackend --version
Please include all output in bug reports.
MythTV Version   : 22594
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.2
lj@mythtv:~$ uname -a
Linux mythtv 2.6.31-16-generic-pae #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 i686 GNU/Linux

Mythbuntu installs the xfce desktop manager by default, and again by default,  the grub2 boot manager is installed.  This means that the applicable grub file is located at /boot/grub/grub.cfg.  However, you can't write to it because the file is read only!  The reason this is read only is because Mythbuntu 9.10 and Karmic Koala 9.10 all use the newer grub2 boot manager.  So, if my understanding is correct, the proper place to put the "vmalloc=256M" imperative suggested by 76GTA is in the file  /etc/default/grub.  Specifically the line  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash
```

can be changed to 

```
GRUB_CMDLINE_LINUX_DEFAULT="vmalloc=256M
```.

As far as I understand,  this should serve the same purpose as the original grub entry in the menu.lst suggested by 76GTA.
Larry

---

### Post by ravalox on 2010-04-02
Editing Ubuntu 10.04's /etc/default/grub in the above way seems to do nothing for me, any ideas?

---

### Post by ravalox on 2010-04-02
sorry, running sudo update-grub clears up the situation.  Thanks for all the advice in this thread.

---

### Post by LarryJ2 on 2010-04-03
If you are missing the familiar menu.lst file,  your installation probably uses the newer grub2 program.  Here's how my grub2 reports itself (April 3, 2010):

```
lj@dell:~$ grub-setup --version
grub-setup (GRUB) 1.97~beta4
```

More info here:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by alex_o on 2010-04-16
i couldnt wait for ubuntu 10.04 and the 195 driver so i installed beta 2

at first i couldnt even get Xorg to work so i had to use a tty(which WAS working) to apt-get update;apt-get upgrade which fixed the issue.

then i had the problem of low graphics which was an eye sore and since i use dual head i only have 1 working screen atm.

at one stage i have had working 18x drivers and 195 drivers working but on package updates this broke :(

help anyone?

---

### Post by tcchris on 2010-04-25
Just for general info , I ran into this problem about a year ago , but I did not find this thread at the time .

I tried to install 32 bit Ibex , and always ended up in low graphics . So I went back to 64 bit which I never had a problem with . Again with Lucid I tried and failed 32 bit . Then I tried this thread , which worked but my tv card "cx18" was choppy , so I went back to 64 bit .

So , if you don't have a problem with 64 bit , it might work better for you , if you have hvr1600 tv card and want to use nvidia drivers . 
Boxee was my need for 32 bit but I don't run it on this computer anymore , so I use 64 bit on this computer with no problem

---

### Post by Quadari on 2010-09-25
Big thank you to this thread!  =D>
Especially the first poster, 67GTA, and to ravalox for showing how to do it in grub2.

Just to detail out what I did, so that if someone else comes along with this problem they can fix it also:

I'm running 10.04, have a Sparkle 8400GS graphics card and a Hauppauge HVR-1600 tuner card.

What I did was:
```
sudo vim /etc/default/grub
```
(I use vim, you can use the editor of your choice.  If you're totally new, pico might be a good choice.)
And commented out the line that says:
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And added the line right after that:
```
GRUB_CMDLINE_LINUX_DEFAULT="vmalloc=512M"
```

Then save the file.  Then back at the command line you have to run
```
sudo update-grub
```
Then reboot and things should work.

Yay!  You can't believe how long it took to isolate this problem for me.  ](*,)8)
 
One question, for those of you who are better at this than me:
Note that I put "vmalloc=512M" rather than the originally suggested "256M".  I did this because my graphics card has 512MB of RAM built in to it.  Is that the right way to think of it?  It seems to be working, so I wanted to get people's thoughts on that.

---

### Post by 67GTA on 2010-09-25
I can't believe this still hasn't been fixed. I've moved to 64bit, and this bug is not present because of how the 64bit kernel addresses virtual memory. Your virtual memory is your swap partition in Linux. Windows uses a page file. Since your graphics card has it's own memory, the vmalloc size isn't as important. The only thing vmalloc is doing in your case is allocating some VM early in the boot process for your GFX card (even though it doesn't need it) because the cx18 and nvidia modules fight over VM and causes a kernel panic and keeps both modules from loading. Generally vmalloc does it's own thing after boot according to I/O and hardware needs, so the vmalloc=? command doesn't matter at that point.

---

### Post by teet on 2011-06-17
> **Quadari said:**
> Big thank you to this thread!  =D>
Especially the first poster, 67GTA, and to ravalox for showing how to do it in grub2.

Just to detail out what I did, so that if someone else comes along with this problem they can fix it also:

I'm running 10.04, have a Sparkle 8400GS graphics card and a Hauppauge HVR-1600 tuner card.

What I did was:
```
sudo vim /etc/default/grub
```
(I use vim, you can use the editor of your choice.  If you're totally new, pico might be a good choice.)
And commented out the line that says:
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And added the line right after that:
```
GRUB_CMDLINE_LINUX_DEFAULT="vmalloc=512M"
```

Then save the file.  Then back at the command line you have to run
```
sudo update-grub
```
Then reboot and things should work.

Yay!  You can't believe how long it took to isolate this problem for me.  ](*,)8)
 
One question, for those of you who are better at this than me:
Note that I put "vmalloc=512M" rather than the originally suggested "256M".  I did this because my graphics card has 512MB of RAM built in to it.  Is that the right way to think of it?  It seems to be working, so I wanted to get people's thoughts on that.

I just picked up a Hauppauge HVR 1600 off of ebay and found that it would not allow my nvidia drivers to load properly.  I am running Ubuntu 11.04 (natty narwhal) and an Nvidia 9500 GT graphics card utilizing the "nvidia-current" drivers from the ubuntu repositories. I did the following to fix the problem.=:

```
sudo nano /etc/default/grub
```

I found the follwing line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and changed it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```

Then 'Control + x'.  Then 'y'.  Then enter to save the file.

Then enter:
```
sudo update-grub
```

Then reboot and everything worked for me.

-teet

---

