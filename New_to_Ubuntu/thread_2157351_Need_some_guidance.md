---
title: "Need some guidance"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by thenorm on 2013-06-25
Hello,

I've recently installed ubuntu 12.04 alongside windows 7, and have made a mess of it experimenting and want to now delete the partitions and start from scratch. can someone look at the .jpg i've added and tell me which ones are safe to delete? I know my c:/ is my windows, and that the 25gb part is ubuntu but im not sure what the two are to the right of the ubuntu part. thanks for the help!

---

### Post by carl4926 on 2013-06-25
Can you boot Ubuntu and take a screen using gparted
Because that windows info is next to useless

---

### Post by thenorm on 2013-06-25
no I can't, see what had happen was. I was messing with the display drivers under additional drivers and installed some new display driver, i believe amd and ubuntu will start and show the ubuntu screen and spit some text on black screen just stay black and never boots to login screen. maybe theres another tool to show them in more detail?

[edit] and no i don't have time to read the text, it doesn't display but a brief second before going off.

---

### Post by MidnightGrey on 2013-06-25
Do you have access to GRUB menu? Can you enter linux recovery mode?

Do you want to fix your ubuntu (i believe it is a case of proprietary drivers failing, which may be a simple fix) or are you just interested in deleting all ubuntu partitions and starting from scratch?

---

### Post by carl4926 on 2013-06-25
Can you use the live cd to do said same?

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> Do you have access to GRUB menu? Can you enter linux recovery mode?

Do you want to fix your ubuntu (i believe it is a case of proprietary drivers failing, which may be a simple fix) or are you just interested in deleting all ubuntu partitions and starting from scratch?

You're right. It's a case of proprietary drivers failing, and i'm a complete ubuntu noob, so in lamen terms could you give me the fix? thank you for the reply! Thanks for your input as well carl, I downloaded another partition manager and saw 3 NSTF partitions and I assume the other two, the 25 gb partition for my ubuntu install, and the 2.74 gb partition is the swap space, i guess? once again thank you guys for your help!

---

### Post by MidnightGrey on 2013-06-25
what graphics card do you have? is it nvidea or amd?

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> what graphics card do you have? is it nvidea or amd?

amd, I believe - using toshiba satellite laptop, series L655D-S5050

[edit] also i can reach ubuntu recovery by holding shift during logo screen.

---

### Post by MidnightGrey on 2013-06-25
Did you try to install something like fglrx? and do you have access to Linux Recovery mode?

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> Did you try to install something like fglrx? and do you have access to Linux Recovery mode?

I can't remember the actual drive, but I remember running the command line to see what my video driver was and it was amd. 

I went into system settings and clicked additional drivers, and it was one of the display drivers I activated and updated. When I rebooted to complete the driver installation I was welcomed with a black screen. All this was the cause of me trying to fix a suspend issue

I can reach ubuntu recovery with shift

---

### Post by carl4926 on 2013-06-25
Ubuntu will have created a extended partition and inside that one for the system and a swap partition
Anything other than the the C partition can usually be deleted, but you understand it deletes the so called recovery partition. As little use as that is.
You do need some understanding of this though to proceed.
And I'd still like to see a view from gparted

---

### Post by MidnightGrey on 2013-06-25
Okay you can enter recovery mode, there should be an option to enter **root**, that will give you command line access.
You can use this command to figure out your graphics card:
```

lspci -v

```
scan the output and look for a section that says "VGA compatible controller" and read ahead to figure out what graphics card you have. 
If your graphics card says AMD, then type in this code and paste the output (so i can see if you did install fglrx).
```
 dpkg --get-selections | grep 'fglrx' 
```

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> Okay you can enter recovery mode, there should be an option to enter **root**, that will give you command line access.
You can use this command to figure out your graphics card:
```

lspci -v

```
scan the output and look for a section that says "VGA compatible controller" and read ahead to figure out what graphics card you have. 
If your graphics card says AMD, then type in this code and paste the output (so i can see if you did install fglrx).
```
 dpkg --get-selections | grep 'fglrx' 
```

Carl uploaded a more detailed photo, hope this helps.

At Grey, I'm about to try those commands now

---

### Post by MidnightGrey on 2013-06-25
Thenorm,

There is a 99% chance that those two 'other' partitions are your ubuntu partitions, but as long as you're viewing them from windows you'll never get any detailed info. If you do want to delete your partitions the best course of action is to follow carl's instructions and run gparted from a LiveCD environment.

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> Thenorm,

There is a 99% chance that those two 'other' partitions are your ubuntu partitions, but as long as you're viewing them from windows you'll never get any detailed info. If you do want to delete your partitions the best course of action is to follow carl's instructions and run gparted from a LiveCD environment.

I feel pretty positive they are as well. But I will boot up ubuntu from usb just to double check.

lol, I couldn't figure out how to scroll in that recovery, arrows wouldn't scroll up to view all the output, I just saw Atheros, but i think that has nothing to do with display.

I ran that check - dpkg --get-selection and it showed the two drives in red and 'install' next to them

[edit] I'm scared to run gparted in live ubuntu and mess with the partitions, and not be able to get back into windows, my initial plan was to delete the ubuntu partitions and repair MBR with easy bcd. Then just reinstall ubuntu from there and start 'fresh'.

---

### Post by carl4926 on 2013-06-25
Opening gparted in live mode will be fine

---

### Post by MidnightGrey on 2013-06-25
> **thenorm said:**
> 
I ran that check - dpkg --get-selection and it showed the two drives in red and 'install' next to them


Okay since you basically confirmed fglrx (fglrx is the for AMD's proprietary drivers) in your system you can remove them and reset to the open gfx drivers which **may** fix your black screen issue.

enter root and type in these commands to remove fglrx.
```

apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
rm -rf /etc/ati 

```

edit: fixed formatting

---

### Post by thenorm on 2013-06-25
Thank you two for your help! I will try this solution tomorrow. Thanks again guys! This gives me the confidence to keep fiddling with it knowing theres support here like this.

---

### Post by thenorm on 2013-06-25
> **MidnightGrey said:**
> Okay since you basically confirmed fglrx (fglrx is the for AMD's proprietary drivers) in your system you can remove them and reset to the open gfx drivers which **may** fix your black screen issue.

enter root and type in these commands to remove fglrx.
```

apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
rm -rf /etc/ati 

```

edit: fixed formatting

Thank you so much! This cleared the black screen issue and now ubuntu will launch to the desktop. Thanks again MidnightGrey!

@Carl or anyone, I uploaded a screenshot of GPART, could one of you confirm the linux partitions? I still may delete, and start from scratch with 13.04 and see if my suspend issue persists.

---

### Post by carl4926 on 2013-06-25
The linux partitions are all inside the extended space sda4

You need to tell us what you would best like to achieve

---

### Post by thenorm on 2013-06-25
> **carl4926 said:**
> The linux partitions are all inside the extended space sda4

You need to tell us what you would best like to achieve

Thank you, Carl. My plan; 

- delete linux partitions from windows 7. (decided to start 'fresh' since ubuntu 12.04 is acting weird now)
- Fix MBR with easy bcd. 
- Put ubuntu 13.04 iso on bootable usb
- install 13.04 alongside win 7

will this work?

---

### Post by carl4926 on 2013-06-25
> **thenorm said:**
> Thank you, Carl. My plan; 

- delete linux partitions from windows 7. (decided to start 'fresh' since ubuntu 12.04 is acting weird now)
- Fix MBR with easy bcd. 
- Put ubuntu 13.04 iso on bootable usb
- install 13.04 alongside win 7

will this work?
Why delete Ubuntu, are you wanting to make it occupy more space? Then yes, you would probably be best doing that, otherwise you can just re-install Ubuntu in to the existing partitions.

So:

1. Do you want me to tell you how to delete Ubuntu and give it more space or

2. How to re-install Ubuntu over your existing install?

---

### Post by thenorm on 2013-06-25
First option please, thanks!

---

### Post by carl4926 on 2013-06-25
> **thenorm said:**
> First option please, thanks!

First make sure you can restore the MBR, I have only ever used the Windows DVD.

One you have windows booting normally, make a backup of anything important.
Delete sda6, sda5 and sda4 using the windows disk management tool.
Now make sure you have de-fragmented windows.
Now with the windows disk manager, shrink sda2 to gain 100GB of free space, that should make sda2 about 158GB or adjust the shrink to suit your needs.
Once that is done, you need a use a Linux live CD that has Gparted and partition the free space, I use Parted Magic.

Step 1: Create an extended primary partition to take up all the free space

Step 2: Create Linux logical partitions inside the extended space
[LIST=1]
[*]swap 4GB
[*]ext4 20GB will be for (root) /
[*]ext4 to use all the remaining free space ~75GB will be for /home
[/LIST]

Apply the operation

Now install Ubuntu
See this Eg: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

---

### Post by thenorm on 2013-06-25
Hmm, I'm not quite comfortable with the first steps, is there a way to reinstall ubuntu over itself and allocate the size then? Maybe option 2 now. Thank you for your patience.

---

### Post by carl4926 on 2013-06-25
> **thenorm said:**
> Hmm, I'm not quite comfortable with the first steps, is there a way to reinstall ubuntu over itself and allocate the size then? Maybe option 2 now. Thank you for your patience.

No
You can't easily resize Ubuntu that way.

The instructions I gave are a piece of cake. It's really not as scary as it seems.



If you prefer to keep Ubuntu small as in option 2. Just follow the guide I posted. But you lack a /home
Creating a partition for /home makes upgrades easier
In your case you would only need to point to sda5 and set the mount point to /

---

### Post by oldfred on 2013-06-26
My standard suggestion is to use Windows tools for Windows and Linux tools for Linux.

Or use Windows to shrink Windows and reboot, so it can run its required repairs/chkdsk after any resize. If you resize Windows from gparted or the installer it usually works but some have issues and blame Linux.
Make sure you do not hibernate Windows.

Then use gparted or Linux installer to install. If you have not deleted partitions, you have to use Something else or manual install and choose to use the same partition. It will find swap. If you resized Windows then you have room for the added /home.


Just in case you need to have a Windows repairCD or flash drive.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

