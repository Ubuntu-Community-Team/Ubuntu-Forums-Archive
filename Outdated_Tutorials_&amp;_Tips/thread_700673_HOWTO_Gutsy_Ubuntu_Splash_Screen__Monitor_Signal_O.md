---
title: "HOWTO: Gutsy Ubuntu Splash Screen / Monitor Signal Out Of Range Problem"
date: 2008-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by erginemr on 2008-02-18
[COLOR="Red"]**_Preface:_**[/COLOR]

Although there are various sources on the net to solve this problem, as far as I know, there is no centralized place in the Ubuntu forums that Ubuntu users can easily find. This problem has emerged with Gutsy Gibbon (7.10), where a too high resolution has been predetermined for the Ubuntu splash screen by the installer. I have encountered many people complaining from the same incident and looking for an answer. So is the reason for this howto.

[COLOR="Red"]**_Symptoms:_**[/COLOR]

If during the boot up process your monitor goes off with or without an "signal out of range" error for a while until you reach the user login screen, and you cannot see the attached orange Ubuntu splash screen with a progress bar, then you are stricken with this problem.

[COLOR="Red"]**_Solution/Workaround:_**[/COLOR]

The resolution of the splash screen with the Ubuntu logo and orange bar is controlled by another config file "/etc/usplash.conf". What you need to do is to change the resolution to one that our monitor can handle, and run a configuration tool to reflect this change to the boot file "/boot/vmlinuz-<kernel_name>". But this is a critical file, and if writing to this file fails, you will not be able to boot again. That's why, we should backup as always.

You will input the following commands to a terminal (Main Menu -> Accessories -> Terminal). To avoid any sysntax errors, you can copy the commands from here and paste them to your terminal (by right-clicking on it) one by one.

1. First things first, take a back up of both files.
```
sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.mybackup
```
```
sudo cp /etc/usplash.conf /etc/usplash.conf.mybackup
```
Note that the ` sign is different from a single apostrophe '.

2. Now, edit the config file:
```
gksudo gedit /etc/usplash.conf
```
When asked, enter your user password.

The default resolution in a fresh Gutsy installation is:
```
# Usplash configuration file
xres=1280
yres=1024
```

However, this is too high or disproportional for quite a few monitors. It was 1024x768 in Feisty Fawn (7.04), the previous Ubuntu release. So, you should edit it to look like:
```
# Usplash configuration file
xres=1024
yres=768
```
for a standard CRT/LCD monitor with a 4/3 screen size. If this does not work, then try 800x600 instead.

For wide-screen desktop and laptop monitors, you can try the "natural resolution" of your monitor. 
```
# Usplash configuration file
xres=1280
yres=800
```
is a good starting point. Other possible candidates are 1680x1050 and 1440x900 (for 19" wide-screen monitors).

Save the file and close.

3. On to writing the new "initrd.img-<kernel_name>" file:
```
sudo dpkg-reconfigure -phigh usplash
```

When asked, enter your user password. It will take a while, approximately one minute, so be patient.

Make sure that the process has been completed successfully. Otherwise, re-apply the very same command.

4. Finally, reboot to welcome back the orange splash screen.

5. This should work, but for some reason if you still get an "out of range" error, try a lower resolution. You can refer to your monitor's user manual or the manufacturer's web site to get the natural resolution.

[COLOR="Red"]**_Other Sources:_**[/COLOR]

The following web sites also address this issue:
1. [http://www.livingubuntu.com/?p=72](http://www.livingubuntu.com/?p=72)
2. [http://blogs.howtogeek.com/jatecblog/posts/make-the-boot-screen-work-on-ubuntu/](http://blogs.howtogeek.com/jatecblog/posts/make-the-boot-screen-work-on-ubuntu/)
3. [http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html)
4. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by L_V on 2008-02-19
Do you call this a "solution", or a workaround ?

Hope this kind of problems will be solved for Hardy.

---

### Post by PinkFloyd102489 on 2008-02-19
Seems like a workaround. Im sure the devs know about it and are adding it into a GUI somehow. Ive been having this problem ever since I got a 15" LCD from my friend. Highest res it'll go is 1024x768, instead of the 1280x1024 that I want.


Thanks.

---

### Post by bhavi on 2008-02-19
yes.. I recieve a lot of qustions on this in the answer tracker.. Its a nice workaround..

---

### Post by erginemr on 2008-02-19
> **L_V said:**
> Do you call this a "solution", or a workaround ?

Hope this kind of problems will be solved for Hardy.

You are right. I will change the terminology accordingly...

---

### Post by Sargan on 2008-02-21
I am sorry but this does not explain how to fix the same problem if you have it when you are trying to install ubuntu. I have tried both 32-bit and 64-bit version.

I select to start live version or if I try to install my monitor go black and nothing more happen. I have an 19" CRT that can handle very high resolution so I do not understand why this does not work.

---

### Post by erginemr on 2008-02-22
> **Sargan said:**
> I am sorry but this does not explain how to fix the same problem if you have it when you are trying to install ubuntu. I have tried both 32-bit and 64-bit version.

I select to start live version or if I try to install my monitor go black and nothing more happen. I have an 19" CRT that can handle very high resolution so I do not understand why this does not work.

Hi,

I am working on a workaround for that too. I will post it very soon for you to try.

---

### Post by erginemr on 2008-02-22
If your monitor turns off **before** you install Ubuntu, that is, when you try to boot into the Live CD, then your monitor probably cannot handle the resolution imposed by the graphical installer. Please follow these steps for a workaround. 

You may want to write the commands down on a scrap of paper or print it out before the attempt, as it will be hard to remember on a black screen:

1. First, boot your system with the Ubuntu Live CD.

2. At the Ubuntu boot up screen, make sure that the first item (Start or Install Ubuntu) is active and press F6.

3. Replace the words "quite splash --" with "single" without the quotes and press Enter to continue.

4. Some text messages will flow. When the boot process is complete, you will find yourself logged as root in text mode.

5. When (or if) you reach the text prompt at the end of the boot up process, issue this command:
```
dpkg-reconfigure -phigh xserver-xorg
```
Select "vesa" as the driver and "1024x768" and “800x600” as the resolutions.

6. Exit the root session either with "exit" or "Ctrl+D".

7. The system will automatically load to the graphical Live CD environment. If not, you can force it manually by entering "startx".

8. If this does not work, then repeat the same steps and select a different low resolution proportional to your screen size.

9. Normally, this step is not necessary, but just for your information; you can also write "nano -w /etc/X11/xorg.conf" or if you are familiar with Vi Editor, "vim /etc/X11/xorg.conf" to edit the resolutions manually in the "xorg.conf" file.

10. Otherwise, the only option you have is to download Ubuntu Alternate CD from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

There should be checkbox down the page that will let you download the text-mode installer CD.

---

### Post by Chew55 on 2008-02-22
Thanks for the Howto.  It fixed my problem instantly.  I knew what was wrong I just didn't know how to fix it.

Cheers

---

### Post by Sargan on 2008-02-22
Hello again, I have tried what you wrote but it still does not work.

First it takes around 5 minutes before I come to the root to be able to type the command. This is because the program is having problem with my new harddrive for some odd reason, it tries to set an xfermode but it fails like 10 times and then gives up after 5 minutes.

Anyway, I went into the reconfigure-thingy and I could only see the resolutions, nothing about VESA... Anyway, onward I went and I press ok and it gives me some kind of warning about saving (I think it was because it was an important file, not sure).

Next thing I press CTRL-D and wait for like 5 minutes and nothing more happen. I type startx and it looks like something is going to happen but then I get another error that says that no monitor is found (or something like that).

I am sorry but I am really starting to loose faith in Ubuntu. It does not work with a 5 year old monitor that can handle resolutions from 1024x768@120Hz up to 2048x1536@60Hz... Do I have to have some kind of supermonitor to be able to run Ubuntu?

This feels like a critical thing to have working from the start and it just doesnt work... Not very good advertizing for Ubuntu. It is very hard to recommend Ubuntu for my friend and workmates and relatives when it just simply doesnt install at all without some kind of überknowledge in linux/debian...

:(

---

### Post by SilverWave on 2008-02-22
Thanks if I had seen this 4 months ago I would have been tempted ;)

8.04 is 2 months away - here is hoping :)

My workaround was Start-UP Manager and some painful messing around to get the startup messages showing.

[http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html)

[EDIT]oh and its available in the repositories as 'startupmanager'

---

### Post by erginemr on 2008-02-22
> **SilverWave said:**
> Thanks if I had seen this 4 months ago I would have been tempted ;)
8.04 is 2 months away - here is hoping :)
My workaround was Start-UP Manager and some painful messing around to get the startup messages showing.
[http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html)
[EDIT]oh and its available in the repositories as 'startupmanager'

Unfortunately startupmanager was not cut for me, so I decided to write this HOWTO nonetheless. If you want to learn why, please refer to our discussion below with a fellow Ubuntu forum member:
[http://ubuntuforums.org/showpost.php?p=4369012&postcount=15](http://ubuntuforums.org/showpost.php?p=4369012&postcount=15)
[http://ubuntuforums.org/showpost.php?p=4369154&postcount=17](http://ubuntuforums.org/showpost.php?p=4369154&postcount=17)

---

### Post by nrayever on 2008-02-22
i have to try it. some time i got this problem. :lolflag::lolflag:

---

### Post by naser on 2008-02-28
Thanks  a lot. That really worked out well. I have been searching thread after thread for a solution to my H-V Frequency OverRange problem, finally what spewed out was this. Thanks for showing us the light, I was having second thougts about Gutsy.

---

### Post by erginemr on 2008-02-28
> **naser said:**
> Thanks  a lot. That really worked out well. I have been searching thread after thread for a solution to my H-V Frequency OverRange problem, finally what spewed out was this. Thanks for showing us the light, I was having second thougts about Gutsy.

You are welcome. :) This is a temporary problem and I am sure will be solved with the release of Hardy. Take care and do not lose your confidence in Ubuntu! :popcorn:

---

### Post by Sargan on 2008-04-08
I made another try to install ubuntu without luck.

I bought a new monitor for around $500, a 22" Widescreen LCD and it still does not work to install Ubuntu. Again with the sync out of range...

How much do I have to spend on a monitor to be able to install a so called "free" operation system?

---

### Post by erginemr on 2008-04-08
> **Sargan said:**
> I made another try to install ubuntu without luck.

I bought a new monitor for around $500, a 22" Widescreen LCD and it still does not work to install Ubuntu. Again with the sync out of range...

How much do I have to spend on a monitor to be able to install a so called "free" operation system?

I suggest you try my post #8;
[http://ubuntuforums.org/showpost.php?p=4380153&postcount=8](http://ubuntuforums.org/showpost.php?p=4380153&postcount=8)

and if it doesn't work, to use the Ubuntu Alternate CD for text-mode installation. Don't worry, the resolution problem can be solved after the installation.

---

