---
title: "Watch TV on Ubuntu Studio 8.04"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by F.R Mostert on 2008-09-01
Hi,

I have a Philips SAA7130 TV card I want to know what program to use and exactly how to configure it.  I have TV time installed but do not know how to scan for channels or to configureit.  Please be very specific in the instructions.

Regards:)

---

### Post by lovinglinux on 2008-09-01
Please read all the instructions below before using any commands.

First you need to make sure everything needed is "loaded" on startup (or something like that)

Open a terminal and use this command
```

sudo gedit /etc/modprobe.d/options
```

A text editor will be opened to edit the options file. Add the following line to the end of the file and save

```
options saa7134 card=xx tuner=yy alsa=1
```

You must replace "xx" with the number of your card and "yy" with the number of your tuner. You can find instructions how to get these numbers [HERE]("http://gentoo-wiki.com/HARDWARE_saa7134"). It is very important to get the correct values, otherwise it won't work.

 **DON'T** replace the "saa7134" with "saa7130", because this is the name of the v4l module and is the same for all saa713... cards.

Then open a terminal and use this command (You must replace "xx" and "yy" again)

```
sudo modprobe saa7134 card=xx tuner=yy
```

Reboot.

Open TVTime, click with the right mouse button on it to show the menu. Then select "Input configuration > Television Standard" and select the appropriate option for your card. Make sure the "Change video source" is showing "Television".

Now click "Back" to return to the main menu, then hit "Change frequency table" and select "cable". Then hit "Scan channels for signal" and your channels should be displayed one by one.

Exit the menu and watch your TV. For more info, including controls, use the following command:

```
man tvtime
```

I hope this help. Configuring my TV card was the most difficult part of my transition to Linux ](*,)

---

### Post by F.R Mostert on 2008-09-02
Thank You very much lovinglinux but I cannot access Gentoo wiki - any other place to get the information?  Maybe on the card itself or the box I bought it in?

Anybody with any ideas?

---

### Post by lovinglinux on 2008-09-02
> **F.R Mostert said:**
> Thank You very much lovinglinux but I cannot access Gentoo wiki - any other place to get the information?  Maybe on the card itself or the box I bought it in?

Anybody with any ideas?

I guess the site is off line, but I have a local image. I have attached a screenshot. Sorry about the compression, but I had to make it 976Kb to be allowed.

---

### Post by F.R Mostert on 2008-09-02
Thank You very much lovinglinux you are wonderfull. I will play with it tonight.

Regards

---

### Post by lovinglinux on 2008-09-02
You are welcome. I hope you make it work without too much hassle. Good luck.

---

### Post by deece on 2008-12-04
Hi there, 

I'm not new to ubuntu but when it comes to configuring and loading hardware i have no idea even where ot begin so i guess i'm a bit of a noob really, haha. ANYWAY i'm using your instructions to configure my tv tuner card which uses the same philips saa713x chipset. I'm going through the wiki page you added and it says to cd usr/src/linux. My usr/src directory has only linux-headers-*numbers* and have tried all with menuconfig command. All coming back with error. Am I in the right place/right track? 

Any help would be awesome :)

Jono

---

### Post by lovinglinux on 2008-12-04
> **deece said:**
> Hi there, 

I'm not new to ubuntu but when it comes to configuring and loading hardware i have no idea even where ot begin so i guess i'm a bit of a noob really, haha. ANYWAY i'm using your instructions to configure my tv tuner card which uses the same philips saa713x chipset. I'm going through the wiki page you added and it says to cd usr/src/linux. My usr/src directory has only linux-headers-*numbers* and have tried all with menuconfig command. All coming back with error. Am I in the right place/right track? 

Any help would be awesome :)

Jono

Forget about that tutorial. It deals with things like configuring the kernel to load the video modules, which is unnecessary in the default Ubuntu installation. I have included the tutorial screenshot just to allow the OP to find his card number. So, just follow my instructions on [[COLOR="Red"]**post #2**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5707560&postcount=2") and you should be fine. If you need to find the card numbers, then check those big lists in the complex tutorial screenshot.

---

### Post by F.R Mostert on 2009-01-19
Hi.
I have tried everything and gave up but I want to try again.  I did not get a "cable" option at all I have played around but cannot get a picture or sound.  I live in South Africa - will it make a difference or is it generic everywhere.

Regards

---

