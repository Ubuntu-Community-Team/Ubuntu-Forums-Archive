---
title: "Display Resolutions Issue in Ubuntu"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by mike110 on 2013-09-27
As you will be able to see in the following, I am a new Linux user.

I have recently installed ubuntu on a clean partition on my hdd.

I can not get it to do ANYTHING!!! Yes, literally.

all stock resolutions do not work properly on my screen, for some reason my 32' is showing up in ubuntu as a 40' so in all resolutions available the desktop is way to big to fit the screen. 1920 x 1080 is the best at the moment as I can see the center of the screen and a full window when opened.

I have tried to install drivers from nvidia's website that I burnt on to a dvd... fatal error, part or all of the coding is wrong...

I have tried to add a new resolution, but do not have the xorg.conf file.

I have tried to generate this file in every way I have found on the internet so far. 

alt ctrl f1 takes me to a black screen, after a few min coding shows up but I cant see the far sides of my screen so I have no idea what it is, but it keeps repeating every few min.

I have qualicomm e2200 on my mobo, which I can not load drivers for (from dvd) it gets almost all the way finished then... fatal error, part or all of the coding is wrong according to ubuntu...

I have tried to run Xorg - configure (and every variation)... it lists something about a display error after running the command...

I forget the name of the file, but its in the grub folder... supposedly changing vga "xxxx" to vga "" ...  Xorg -configure is supposed to work... I dont have that file...

oh... and 75% of the time I cant get my mouse to work as I can not change the non existent xorg.conf file...

Am I just slow?
Please help!

does the xorg.conf file even exist on the newer versions of ubuntu? Am I going about this all wrong?

As mentioned my mouse doesnt work most of the time, and I cant see half of the screen, so if anyone does have a detailed step by step of how to dig myself out of this hole... It would be greatly appreciated.

Is there any reading I can do to learn more (after changing my screen resolution hopefully)?

---

### Post by QIII on 2013-09-27
Hello!

That sounds like a bit of a problem!  ;)

Could you tell us which version of Ubuntu you installed and how?

Could you give us the hardware specifications of your machine?

That will give us a bit of a reference for where to start.

Best wishes!

---

### Post by mike110 on 2013-09-27
I have tried both Ubuntu v12.04 LTS 64bit and Ubuntu 13.04 64bit.
Both have the exact same issues.

Installs were both done through boot to dvd drive.
dvd's were (I made 3, 2 with v12.04 1 with 13.04) by sending ubuntu image file to dvd.

my machine is;
i5 4670k @ 4.6ghz
Msi Z87-GD65 Gaming mobo
Gigabyte GTX 760 4gb
32gb 1600 ram
rat 3 mouse (i have tried another generic usb mouse with less results, would not even move the curser, no im not using it in the usb 3.0 slots)

I have formatted my 2.5' drive and It now only has Ubutu 13.04 on it.

I am also running a 5.25" hdd dock, I have a 3.5" (my main hdd) that runs win7 and has all of my everyday apps on it, the 2.5" only has Ubutu on it.  Only one is on at a time (the dock has power switches for each hdd).  I have no issues booting into Ubutu.

Since formatting and reinstalling 13.04 the mouse issue has gotten worse and I can no longer use the mouse.
The Terminal is extremely difficult to use now, as 95% of the time I can not drag it to the center of the screen to read what im typing.

I have found drivers for both my mobo and gpu but, as stated I can not do anything with them.
Also with this install I am able to open the mobo driver set with software Center but the install button is greyed out.

Any help would be greatly appreciated.

*fresh install still does not have xorg.conf, I couldnt get a look at the x11 folder as it opens on the far right of my screen but when running sudo gedit /etc/x11/xorg.conf it just shows up as a blank file and will not save.

---

### Post by mike110 on 2013-09-27
oh, I also cant switch between open windows.

when my mouse is working if i click on a window for some reason it selects what ever is behind that window (if I have 2 windows open, when clicking on a file in the front most window Ubuntu registers it as if im clicking a file in the rear most window)

I am also having the known alt tab issue, where I cant switch between windows.

So its open a window, hope it opens in the center of the screen and hope that it is set as an active window so i can tab to the files or alt f4 until it happens.

---

### Post by grahammechanical on 2013-09-27
> [COLOR=#000000]does the xorg.conf file even exist on the newer versions of ubuntu? Am I going about this all wrong?[/COLOR]

The answers are: No and Yes.

First off, deal with one issue at a time.

Second Ubuntu reads the monitor resolution from the monitor each time it boots. It does not read a configuration file. This is why we do not need to set  monitor resolutions during the install process. Search wikipedia for EDID or Extended Display Identification Data.

Third, when we install Ubuntu if we check to install third party software during the install process then the installer will download and activate a proprietary video driver as part of the installation process. It will install a Nvidia driver for you. Once we are at a desktop we can experiment with available video drivers through the Addtional Drivers utility in 12.04 or through Software and Updates>Additional Drivers tab in 13.04.

Fourth, with a Nvidia driver installed we get an Nvidia Xserver configuration utility. It is in the Dash. Just search for Nvidia. There is a Displays utility in System Settings but that is not activated when we use a Nvidia driver. That is there for when we use the Nouveau open source driver.

May I suggest that you activate one of the drivers in Additional Drivers and see where you go from there. It is always best to use the optimum video settings chosen by the monitor manufacturer. These are in the EDID code into the monitor. And are read at each boot time by Ubuntu.

You are not, by any chance trying to install Windows drivers (exe) for that Qualcomm are you?

Regards.

---

### Post by mike110 on 2013-09-27
No Im not trying to install windows drivers in Linux... contrary to my post I actually know about computers.

I switched to 13.04 because it is supposed to have drivers for the qualicomm killer e2200 included with the 13.04 os.

I will try searching through the drivers already in ubuntu, but as stated I can not access the internet to dl them.

As for my monitor, yes I agree that using manufacturer settings is best, but ubuntu thinks my screen is 8' larger than it actually is.  Hence why I want a 17xx x 992 resolution, so I can actually see the entire desktop.

As stated, what ever driver ubuntu installed for the qulicomm e2200 is not working with the e2200, so i cant 'check the box to download drivers'

---

### Post by mike110 on 2013-09-29
The additional drivers tab is empty.

I have managed to create another resolution with the terminal but it shows up as DP-1 disconnected.
Is there a way to put this resolution in the HDMI-1 section?
*edit*
I added the 1768x996 resolution to hdmi, it didnt change the desktop size at all. I logged out then back in, got a window on the left side with 1768x996 @60 display size repeated a bunch of times with some 1's and 0's thrown in.
open display 1768x996 is no longer there.
run xrandr, 1768x996 is gone all together.

---

