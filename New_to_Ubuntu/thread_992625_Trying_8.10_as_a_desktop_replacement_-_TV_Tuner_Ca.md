---
title: "Trying 8.10 as a desktop replacement - TV Tuner Card FRUSTRATION"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by DirtyBirdNJ on 2008-11-24
Hello everybody. A week or so ago I decided to take the plunge and install 8.10 instead of my usual windows xp stolen edition. Aside from some very confusing stuff I had to get to get my video card to work, everything has performed excellently!

Well, everything except my Pinnacle HD PCI card. I'm no linux guru, but I'm a web developer so I know enough to sudo around and use vi to edit conf files. I've been googling this subject for a good 4 or 5 days now and I can't get ANY traction. This is the only thread I've found that gives any human readable suggestions:

[http://ubuntuforums.org/showthread.php?t=587474](http://ubuntuforums.org/showthread.php?t=587474)

And even that, it seems the guy has a different chipset on his card than I do. He mentioned running Kaffine to figure out what my card really was, and I found this bit of information while Kaffine tried (without success) to install & config itself:

Samsung S5H1409 QAM/8VSB Frontend

So I'm guessing I need the drivers for this right? So I downloaded tip.tar.gz off of the thread I linked to, and ran a ./ command like the thread suggested, from the dir that was created when I un-tared.
```
mat@mat-desktop:~/Desktop/v4l-dvb$ ./get_dvb_firmware S5H1409
bash: ./get_dvb_firmware: No such file or directory
```So not only can I not locate the drivers, this command dosn't work either.

This video card business is totally ridiculous. Is it really THIS hard? This tv-card thing has me at wit's end. I even downloaded a Mythbuntu .iso, and the card STILL wouldn't work... which leads me to believe it's a driver issue. 

HELP!

---

### Post by anewguy on 2008-11-24
Well, the first thing I can think of is to post a listing of your "mat@mat-desktop:~/Desktop/v4l-dvb" directory back here so we can see what you have or don't have, then we can try to go from there.

Dave :)

---

### Post by DirtyBirdNJ on 2008-11-25
Hello Dave, thanks for the quick reply!

the v4l-dvb directory on my desktop is an unarchived version of this file:

[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)

I just renamed it so I didn't have to type in the HUGE dir name that the tar gave itself when I did Right Click-> Extract Here

---

### Post by cariboo on 2008-11-25
What make and model is your TV tuner card, because if you try to make the drivers that you downloaded you will end up making all the v4l modules. You certainly don't need to do that. as they are already included with the kernel you are running.

Could you paste the output of:

```
sudo lshw -C multimedia
```

in your next post.

Jim

---

### Post by anewguy on 2008-11-25
I would follow the above advice first, then if no success, look at the directory v4l-dvb -> I downloaded and unpacked the file and there is no get_dvb_firmware file there to run - that would give you the not found message.  In addition, in searching the other sub directories I don't see a S5H1409 file either.  So, I don't know what the instructions where telling you to do, but they don't seem to apply to that tar file from what I have seen.  Also, I noticed other driver and firmware files in the sub directories are in lower case, so remember that Linux is case sensitive - S5H1409 is not the same as s5h1409.

Beyond that, I'll need to go back and follow your link for the forum post to see what it says.  If I find something I'll let you know!

dave :)

---

### Post by anewguy on 2008-11-25
Okay, I found the script, it is in the linux/Documentation/dvb sub directory.  To run it from your v4l-dvb directory I think you would do the following:

sudo sh linux/Documentation/dvb/get_firmware_dvb S5H1409
 
(or perhaps lower case s5h1409)

However, looking at that script, I don't believe it will work anyway, as it only has some firmware defined internally, and S5H1409 isn't one of those.  I just looked briefly at the script, but I believe it bombs out when the firmware you specify isn't one of those defined internally to the script.

If you can point me to the web site and the file on that site that is your firmware (assuming S5H1409), I could try to modify the script for you so it will retrieve that firmware as well.

Dave :)

---

### Post by tomtom1982 on 2008-11-25
What kind of chip does it use?

Some pinnacle-cards come with Phillips SAA7030/7034 chipset, which isn´t supported by in ubuntu in many cases.

---

### Post by DirtyBirdNJ on 2008-11-25
Thanks for the replies everybody! First thing's first...

```
mat@mat-desktop:~$ sudo lshw -c multimedia
sudo password for mat: 
  *-multimedia            
       description: Multimedia audio controller
       product: nForce3 250Gb AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
  *-multimedia:0
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
  *-multimedia:1
       description: Multimedia controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
       vendor: Conexant Systems, Inc.
       physical id: a.1
       bus info: pci@0000:02:0a.1
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4 module=cx88_alsa
  *-multimedia:2
       description: Multimedia controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
       vendor: Conexant Systems, Inc.
       physical id: a.2
       bus info: pci@0000:02:0a.2
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6 module=cx8802

```

The card's retail packaging said it's a Pinnacle HD PCI Card. In one of the posts in the thread I linked to in my original post, a user who got the card to work said an app called Kaffiene showed him what the card *really* was and helped him find the appropriate drivers. This is what Kaffiene shows the device as when I open the DVB settings:

Samsung S5H1409 QAM/8VSB Frontend

here are some pics of the card itself:

[IMG]http://images.tigerdirect.com/SkuImages/gallery/large/Pinnacle-PCTV-HD-PCI-P121-8168-x.JPG[/IMG]

[IMG]http://images.tigerdirect.com/skuimages/large/Pinnacle-PCTV-HD-PCI-P121-9.jpg[/IMG]

---

### Post by Riffer on 2008-11-25
How do you know your tuner isn't working?  If you're using MythTV, that could be part of the problem, Myth can be a bear to setup.  Try tvtime (its in the repos), setup is easier and has the ability of being able to be placed in a window unlike Myth which takes over the whole desktop.

Also you need to setup either program for the correct decoding.  For instance here where I live I need to set things to NTPS and us-cable to get even a picture.  You would set things differently if you live in Europe or else where.

You need to know also if your card will support analog and digital signals.  I tried using a Hauppauge HVR 1800 that didn't fully support analog (no sound), since my cable company only supplies an analog signal there wasn't any way I could get the card working.

---

### Post by DirtyBirdNJ on 2008-11-25
Thanks for the reply Riffer.

I have tried three different programs:

1. tvtime - just gives me a blue screen and "no signal", channel scan goes to 99 and never finds anything

2. VLC - no idea what to connect to

3. Kaffiene - indicates a card/chipset I see nowhere else... and dosn't work either.

I need to:

1. Determine what drivers I need for the card
2. Find those drivers
3. Install the drivers to the proper location
4. Point whatever program I use to the correct path/location/whatever

I'm pretty confused as far as configuring these programs. At least Kaffiene gives me a configuration panel, using the command line to config these programs is very daunting for me.

---

### Post by DirtyBirdNJ on 2008-11-26
Alright, some further digging has produced some good info, but I'm still stuck in the mud. Before I get started, can someone explain the difference between V4L and DVB?

Ok, back to my tuner card... I'm so close I can almost see the episode of conan I could be watching right now.

[http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i](http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i))

I was right about the Samsung part- that's the demodulator, and the Xceive XC5000 is the tuner. This is definitely the same card, so at least I know I'm on the right track now. This page even shows you how to get the special firmware & drivers for the card.

[http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/)

The problem with this is... I can't run the extract.sh file! I opened it up with a text editor, and all I can tell is that it performs what I can only describe as voodoo magic on a file called hcw85bda.sys - and out pops dvb-fe-xc5000-1.1.fw and then it checksums the new file to make sure it's correct.

Cool and all that I can see what it's supposed to do... BUT IT'S NOT DOING WHAT IT'S SUPPOSED TO! Or maybe the problem is between the keyboard and the monitor :)

How can I get my system to run the extract.sh shell script? I've tried sudo sh, and ./ I really don't know anything else to try.

---

### Post by anewguy on 2008-11-26
I downloaded the zip file and the extract - the extract actually runs against the zip file, so I had both on my desktop and did the following in terminal:

sh extract.sh xc5000

This extracted the fw file to my desktop with instructions to copy it.  On my installation, the copy "to" directory does not exist, so perhaps there is another folder it goes to in Ubuntu (I believe one of the other threads mentioned this and gave the path).

At any rate, IF you were trying to extract the xc5000 firmware, I have attached it to this message.  I extracted as described above, then did zip driver.zip *.fw .  I also had to change the permissions on the extract.sh file to 777 to allow executing it (it was by default read only and I didn't know if it would execute it or not so I did the chmod 777 just to be safe).

Hope that helps!

Dave :)

---

### Post by DirtyBirdNJ on 2008-11-26
Dave to the rescue yet again!

So with your help, I was able to download the v4l-dvb sources via Mercurial and then do a make on the dir that I filled up with it's output.

Lo and behold, tvtime WORKS... but... there's no sound :(

I tried to configure VLC, but I still have no clue how to point the media players at the tv/audio stream. 

I'm 95% there... SO CLOSE TO GETTING IT TO WORK!

---

### Post by anewguy on 2008-11-27
I'll do some more digging and see what I can come up with.  It may be a little while, though.  Thanksgiving day I'm getting together with my "second" family, and the father there was just diagnosed today with stage 4 cancer.  I know he has a growth in his chest, tumors in his lymph nodes and a brain tumor, so tomorrow I'm afraid is going to be a rather somber day.

I'll post back as soon as I can find more info for you!

Dave :)

---

### Post by anewguy on 2008-11-27
I did a quick search and turned up this:

[http://ubuntuforums.org/showthread.php?t=930561&highlight=tvtime+sound]("http://ubuntuforums.org/showthread.php?t=930561&highlight=tvtime+sound")

I don't know if that will help you or not.

Dave :)

---

### Post by dadie11 on 2008-11-27
Hya, DirtyBirdNJ! For what it' worth ~ this issue of multi-media card compatibility is a bit of a nightmare. Like you, I too, have enjoyed the dubious pleasures of xp and windows' stranglehold on our everyday lives. But business is business, so they say; and 'Linux' (whilst gaining in support), is only catered for by a small number of manufacturers willing to accept that it is a worthy cause.                                          I digress. Try '[http://[COLOR="Red"]www.linuxtv.org[/COLOR]]("http://www.linuxtv.org")' which is a good starting point for mythtv, wiki, etc to help you on your way. My thoughts are that you'll have to bin the 'Pinnacle' (as I did) and go for a 'Hauppauge'. But a word of warning ~ I am putting together a 'Cubit' 'Mythtv' htpc and it ain't  easy. Good Luck.

---

### Post by sdennie on 2008-11-27
I have a Pinnacle USB card and to get sound working, I start tvtime with a script like this:

```

#!/bin/bash

sox -t ossdsp -r 48000 /dev/dsp1 -t ossdsp /dev/dsp &
/usr/bin/tvtime --mixer=/dev/mixer:vol &

sleep 2
amixer --card 1 sset PCM 0
amixer --card 1 sset PCM 16

while pgrep tvtime ; do
    amixer --card 1 sset PCM 15
    amixer --card 1 sset PCM 16
    sleep 1
done

pkill -9 sox

```

The reason for all the amixer stuff is because I found that every time I change the channel, the tuner card does something odd to the sound where it becomes hard to hear unless you then manually set the PCM to something other than max volume and then back to max volume.  For this script to work, you'll need sox installed.  Unfortunately, sox is an OSS program so, you won't be able to hear other sounds at the same time and if any app has the sound card opened (possibly including the default sound server, pulse audio), you won't hear sound.  I don't know if this solution will work for you but, hopefully it will get you moving in the right direction.

---

### Post by anewguy on 2008-11-29
As mentioned by vor, you'll need sox.  The link I pointed you to contains the instructions for installing and using it.

Dave :)

---

