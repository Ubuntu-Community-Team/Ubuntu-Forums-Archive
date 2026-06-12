---
title: "Difficulties mounting USB drive."
date: 2015-02-16
forum: New to Ubuntu
---

### Post by konstantinos2 on 2015-02-16
Hello all! I'm glad I am here at last. I am new to Ubuntu 10.04 and I am facing some general difficulties with it, but I wanted to begin with asking you how I will be able to read a USB drive. My OS can see the device, but I cannot see the contents of it. It's NTFS formatted and I want to clear up that I've been trying to do that two days now. I have already typed many commands that I found on the web, but nothing of it helps.

So I was wondering if you could guide me into this..

Thank you in advance!! :D

---

### Post by Impavidus on 2015-02-16
10.04? That's end of life (desktop that is, but server nearly too). Best to use a supported release of Ubuntu. I suggest 14.04.

As for your usb drive, it may need a file system check, which you may have to run from Windows (as NTFS is a Windows file system). That may happen it you don't properly remove a usb drive, for example.

---

### Post by sammiev on 2015-02-16
Ubuntu 10.04 has reached End of Life (EOL) and many updates are not available. You really need to download 12.04LTS or 14.04LTS.

[Ubuntu Download site]("http://www.ubuntu.com/download").

---

### Post by konstantinos2 on 2015-02-16
I am sorry.. That was a mistake. I do use 14.04.

Now, can you tell me what are my options? My Windows XP can read the Flash Drive just fine.

---

### Post by SeijiSensei on 2015-02-16
I just mounted the Windows partition to the directory /windows like this:
```
sudo mkdir /windows
sudo blkid
[reports list of partitions on my drive; one entry reads:
/dev/sda3: LABEL="WIN7" UUID="1E1E81AF1E81808F" TYPE="ntfs" ]
sudo mount /dev/sda3 /windows

```
Now I can see the Windows partition from Linux in /windows.  Follow the same steps to identify the device name for your USB drive, then try mounting it with "sudo mount".

---

### Post by konstantinos2 on 2015-02-17
Hey, uuuuh.. I'm not too familiar with the terminal, so please be patient.

I copied and pasted what you have given to me, but it says "command not found".

I am sorry that you have to guide me step by step, but I am new to computer systems generally..

---

### Post by konstantinos2 on 2015-02-17
Oh, wait a minute! I only have Ubuntu installed in my system. I meant the other system which has Win XP can read the files. I have two PCs. I am sorry for the misunderstanding.

---

### Post by sotiris2 on 2015-02-17
Did you "safely remove" before unplugging the usb from the windows machine? 

Also do post output of ```
sudo blkid
sudo lsusb
```

Copy and paste don't type it out. In terminal if you press middle mouse button (usually the wheel) you will paste whatever you have selected (highlighted with mouse).

---

### Post by konstantinos2 on 2015-02-17
For your own convinience with codes and also mine, my Flash is called "Paradise Lost". Yes, it works fine on my other PC. I tried what you said. This is what appeared on terminal; 
/dev/sda1: UUID="5ee4b984-7e7c-4bdc-8bfa-2094a9aa120f" TYPE="ext4" 
/dev/sdb1: LABEL="Paradise Lost" UUID="24E2-DFA1" TYPE="exfat" 
/dev/sdb2: LABEL="Catholic Heaven" UUID="566406535BE31942" TYPE="ntfs"

Then I put my USB drive again and this is the error;

Unable to mount Paradise Lost
Error mounting /dev/sdb1 at /media/konstantinos/Paradise Lost: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/konstantinos/Paradise Lost"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

What do you think?

---

### Post by konstantinos2 on 2015-02-17
"Catholic Heaven" is an other device which I used to install Ubuntu but I didn't use it from then. I don't why it appears.

---

### Post by sotiris2 on 2015-02-17
Ok the problem is the filesystem, exFat, which is not supported out of the box in ubuntu. You have to options, try installing exFat support or reformatting to ntfs or fat (I reccomend ntfs). Are you certain "Catholic Heaven" is on an other device? It seems from the code that it's just another partition (volume) on the same usb drive. Can you mount this device? 

To install exFat support ```
[FONT=Ubuntu Mono]sudo apt-get install exfat-utils exfat-fuse
``` and reboot, now it should mount it when you plug the drive.

You can format the usb drive either using your windows machine (since you 'll have to backup the data in it or LOSE them) or via gparted.[/FONT]

---

### Post by konstantinos2 on 2015-02-17
Sorry I didn't see this.

---

### Post by konstantinos2 on 2015-02-17
I'll try!!

---

### Post by konstantinos2 on 2015-02-17
:KS Thanks! It worked!! Does it happen for you to also know why when I play a video on Youtube on 1080p, I have so much tearing and excessive lag which totally ruin it?? I searched for some solutions but I couldn't get it worked properly.

I have an AMD FX-8350 and an XFX Radeon 270x DD 4GB, so I know that I can play HD videos with no problem if Ubuntu had not this problem.

---

### Post by konstantinos2 on 2015-02-17
It also happens with a video file. I say this because it is not my connection in any way. I have an excellent connection.

---

### Post by sotiris2 on 2015-02-17
Are you using the default open source driver (as in you didn't install anything related to amd your self) or catalyst? 

In catalyst there is a an option for Tearing which if I don't enable I always have tearing fullscreen. With the open source driver I never had any problem with a 7770 and an APU (A660K i think). But do try installing ccsm with ```
[COLOR=black][FONT=monospace]sudo apt-get install compizconfig-settings-manager[/FONT][/COLOR]
```[COLOR=black][FONT=monospace] and afterwards run it and enable [/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]Sync to Vblank in OpenGL settings.  You might also try changing unredirect Fullscreen Windows and/or setting the refresh rate yourself in Composite settings (in ccsm). 

If you want to install catalyst I suggest you do it by following [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx]this guide.]([/COLOR)[COLOR=#252525][FONT=sans-serif]



[/FONT][/COLOR]

---

### Post by konstantinos2 on 2015-02-17
Unfortunately, the link doesn't work. The code worked, but where am supposed to enable what you said? And I don't know what driver I am using. How can I find out?

---

### Post by sotiris2 on 2015-02-17
Search for compiz in the dash (win key). 
The correct link is [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

### Post by konstantinos2 on 2015-02-17
I found it, but how am I supposed to [COLOR=black][FONT=monospace]enable [/FONT][/COLOR][COLOR=#252525][FONT=sans-serif] ??
I also installed the drivers from the page you provided but nothing changed. I rebooted, though.

---

### Post by sotiris2 on 2015-02-17
If you installed the driver from the link, you installed catalyst. Run catalyst control center (Admin), go to screen settings, and it has an option to reduce tearing.

---

### Post by konstantinos2 on 2015-02-17
Are you from Greece? Because when I try to open Catalyst I get an error in Greek and I am not sure how I can change that. All other errors pop up in English. I don't even have installed Greek!!

 &#928;&#961;&#959;&#941;&#954;&#965;&#968;&#949; &#941;&#957;&#945; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945; &#956;&#949; &#964;&#951;&#957; &#960;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#964;&#951;&#962; &#941;&#954;&#948;&#959;&#963;&#951;&#962; Catalyst Control Center &#963;&#949; Linux.  &#924;&#960;&#959;&#961;&#949;&#943; &#957;&#945; &#960;&#961;&#959;&#954;&#955;&#942;&#952;&#951;&#954;&#949; &#945;&#960;&#972; &#964;&#945; &#949;&#958;&#942;&#962;.
  &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#959; &#960;&#961;&#972;&#947;&#961;&#945;&#956;&#956;&#945; &#959;&#948;&#942;&#947;&#951;&#963;&#951;&#962; &#947;&#961;&#945;&#966;&#953;&#954;&#974;&#957; AMD &#942; &#964;&#959; &#960;&#961;&#972;&#947;&#961;&#945;&#956;&#956;&#945; &#959;&#948;&#942;&#947;&#951;&#963;&#951;&#962; &#964;&#951;&#962; AMD &#948;&#949;&#957; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#949;&#943; &#963;&#969;&#963;&#964;&#940;.
 &#917;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#942;&#963;&#964;&#949; &#964;&#959; &#954;&#945;&#964;&#940;&#955;&#955;&#951;&#955;&#959; &#960;&#961;&#972;&#947;&#961;&#945;&#956;&#956;&#945; &#959;&#948;&#942;&#947;&#951;&#963;&#951;&#962; AMD &#947;&#953;&#945; &#964;&#959; &#965;&#955;&#953;&#954;&#972; AMD &#960;&#959;&#965; &#948;&#953;&#945;&#952;&#941;&#964;&#949;&#964;&#949; &#942; &#948;&#953;&#945;&#956;&#959;&#961;&#966;&#974;&#963;&#964;&#949; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; &#964;&#951;&#957; &#949;&#957;&#964;&#959;&#955;&#942; aticonfig.

---

### Post by sotiris2 on 2015-02-17
Do ```
[COLOR=black][FONT=monospace]sudo amdconfig --initial -f
``` and reboot.
Then please post the output of ```
[/FONT][/COLOR][COLOR=black][FONT=monospace]fglrxinfo
```[/FONT][/COLOR]
[COLOR=black][FONT=monospace]Yes I am greek, we also have a greek community forum @ [/FONT][/COLOR]https://forum.ubuntu-gr.org . I noticed now that my catalyst center is in greek too though I have the interface set to english, and it is so in any other application.

---

### Post by konstantinos2 on 2015-02-17
YES!! It worked!!!!

Thank you soooo much, friend! I really appreciate it. It works great!!

I'm not sure I know the reason of it, but here you are;

Output:

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R9 200 Series
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005



It's a little unimportant and I don't want to create a new thread about it, so do you know if I can add subtitles in MP4 player? If not, do you know how to set VLC as default video player??

---

### Post by konstantinos2 on 2015-02-17
I don't understand. The tearing stopped, but it's back now. Why is this happening again? :(

---

### Post by konstantinos2 on 2015-02-17
But only when I play a video file, not on youtube anymore..

---

### Post by konstantinos2 on 2015-02-17
It comes and goes I guess. I should know that ATI graphics and Ubuntu are not a good combination.

---

### Post by sotiris2 on 2015-02-18
Right click on a video file, go to properties and then on Open with Tab andyou should be able to choose vlc. You might have to repeat it for different video filetypes such as mpeg, mkv etc..

Now for tearing, a year ago I would tell you that completely being rid of tearing with an amd card is impossible, but nowadays I don't get tearing even with catalyst drivers. Let's recap:

You have enabled Sync to Vblank in CompizConfig under OpenGL section ?

Have you gone to catalyst control center (admin, where you get asked your password) and to &#916;&#953;&#945;&#967;&#949;&#943;&#961;&#953;&#963;&#951; &#927;&#952;&#959;&#957;&#974;&#957; -> &#935;&#969;&#961;&#943;&#962; &#960;&#949;&#961;&#953;&#954;&#959;&#960;&#941;&#962; and enabled it?

To cover all bases do ```
[COLOR=black][FONT=monospace]sudo amdconfig --sync-video=on
``` although I think that's the same as from catalyst control center. 

[/FONT][/COLOR]Try disabling unredirect fullscreen windows in compiz config in composite section. 

Does it happen with all video players? Vlc and Totem?

---

### Post by konstantinos2 on 2015-02-19
I don't have too much tearing, but when the camera moves horizontally I can see it and it's enough ugly. But not how it was before. It is much better. But this ain't the real problem, right now. I was trying to enable num-lock on boot with some codes on terminal and when I restarted my PC, it boots, but later (after the logo) it leads me to a black screen with a horizontal cursor at the up top. I cannot use my keyboard, everything freezes. Can you help me on that?

---

