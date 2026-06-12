---
title: "UniChrome Driver Problems"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Lensflare on 2008-06-05
Okay, so I have a laptop with a UniChrome adapter.  I ran the entire commands as pertained to Ubuntu 8.04[here]("https://help.ubuntu.com/community/OpenChrome"), but when I went to the xorg.conf file to edit it as stated, it only says:

```
Section "Device"
             Identifier               "Configured Video Device"
```

What do I do?  I ran all the commands, and the test, but I got a messed up screen and had to force restart.  My screen works fine at a sharp quality, but the resolution is too large for the screen.  As you can see by my post count, I'm not too experienced with Ubuntu or other Linux-based operating systems.  I have internet access through ethernet at the time, but won't be able to configure my wireless as I'd like to until I fix the resolution.

EDIT:  Apparently my WiFi works--I changed the resolution to 800x600--there are lines running through it and I can't see the bottom, but I can see the right of the status bar and successfully connected to my router.

---

### Post by didac on 2008-06-06
Try in a terminal:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo displayconfig-gtk

```

Change the graphics card to via or unichrome, if you have the modules installed. If not, load vesa to start with. It's a 'safe mode' driver. Press Test to see if it works.

Then change the screen resolution to a higher one, ONE AT A TIME, and press test.

I hope you don't get hooked out of Xorg. If it happens --  cross fingers -- when rebooting, you'll be dropped to a terminal. There do:

```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

And reboot or enter

```
startx
```

Copy that in your notebook.

---

### Post by Lensflare on 2008-06-06
> **didac said:**
> Try in a terminal:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo displayconfig-gtk

```

Change the graphics card to via or unichrome, if you have the modules installed. If not, load vesa to start with. It's a 'safe mode' driver. Press Test to see if it works.

Then change the screen resolution to a higher one, ONE AT A TIME, and press test.

I hope you don't get hooked out of Xorg. If it happens --  cross fingers -- when rebooting, you'll be dropped to a terminal. There do:

```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

And reboot or enter

```
startx
```

Copy that in your notebook.

Thanks for the help.

Okay, I could get into the Screen and Graphics preferences, and my current "Graphics card (OpenChrome)" Driver was None.  So I went to choose driver by name, and it was on Openchrome.  So I went to via.  I clicked okay, and it still said I had no driver.  But I tested anyway.  All the resolutions had the same effect as before.

When entering the displayconfig-gtk command, I get this:

```
on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-g5Mj_11530/xauthority
Got pid 11546
(0,  0)
checkpoint 1
None
False
Sorry, this configuration video card driver and monitor doesn't appear to work:

Messages from the X server:
(EE) No devices detected.
Fatal server error:
```

By the way, how do I get superuser privileges?  When I try to install programs, it says

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

But when I enter the command in Terminal, it says I need superuser privileges.

Thanks in advance,
Lensflare

---

### Post by avtolle on 2008-06-06
For superuser privileges, type "sudo" before the command.

---

### Post by Lensflare on 2008-06-06
> **avtolle said:**
> For superuser privileges, type "sudo" before the command.

Oh thanks.  So that's why it appears in almost every command:lolflag:

---

### Post by didac on 2008-06-06
So, you don't have Unichrome drivers installed. Try 'vesa' and see whether it improves. The problem with vesa is that is a too generic driver and you will miss many functionalities. I have a Unichrome card, but I'm running Fedora in that computer. I solved the problem by installing a via package for Fedora. 
There is a package in Ubuntu. Install it by typing:

```
sudo apt-get install xserver-xorg-video-openchrome
```

But I don't know how it works. Search the forums and see whether somebody has managed. Maybe these can help:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome) (more complicated)

Also, you may post the results of the following commands:

```

cat /var/log/Xorg.0.log | egrep EE
cat /var/log/Xorg.0.log | egrep WW

```

It may help solving the problem

---

### Post by Lensflare on 2008-06-06
> **didac said:**
> So, you don't have Unichrome drivers installed. Try 'vesa' and see whether it improves. The problem with vesa is that is a too generic driver and you will miss many functionalities. I have a Unichrome card, but I'm running Fedora in that computer. I solved the problem by installing a via package for Fedora. 
There is a package in Ubuntu. Install it by typing:

```
sudo apt-get install xserver-xorg-video-openchrome
```

But I don't know how it works. Search the forums and see whether somebody has managed. Maybe these can help:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome) (more complicated)

Also, you may post the results of the following commands:

```

cat /var/log/Xorg.0.log | egrep EE
cat /var/log/Xorg.0.log | egrep WW

```

It may help solving the problem

Thanks, but I've tried the vsea driver.  Same results; distorted screen.  I tried both commands, and the results are as follows:

```
cory@cory-laptop:~$ cat /var/log/Xorg.0.log | egrep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
cory@cory-laptop:~$ cat /var/log/Xorg.0.log | egrep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) CHROME(0): Panel on K8M800, PM800, VM800, P4M890, K8M890, CX700 or P4M900 is currently not supported.
(WW) CHROME(0): Using VBE to set modes to work around this.
(WW) CHROME(0): Bad V_BIOS checksum
(WW) CHROME(0): Unable to estimate virtual size
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) Configured Mouse: No Device specified, looking for one...
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
cory@cory-laptop:~$ 


```

I'll be sure to try those links as soon as possible.


EDIT:  Okay, I like the second link, since the first one didn't help me.  I know I have a Unichrome display card, but I don't know the exact model.  What's the command in Terminal to determine my video card?

---

### Post by Lensflare on 2008-06-06
Anyone know the command to find your specific graphics card?  I've searched all my documentation and online support online, but haven't been able to find the specific chipset/model number specs.

Also, I accidentally moved the status bar to the right side, making it to where I can't see it anymore.  This means I have no access to apps and such (or at least I don't know the terminal commands for them).  Does anyone know a command to fix/reset it?

If nothing else, I can fix the status bar with a fixed resolution.

Thanks,
Lensflare

P.S.:  Both Ubuntu help links are down.

---

### Post by ardvark71 on 2008-06-06
> **Lensflare said:**
> Anyone know the command to find your specific graphics card?  I've searched all my documentation and online support online, but haven't been able to find the specific chipset/model number specs.

Also, I accidentally moved the status bar to the right side, making it to where I can't see it anymore.  This means I have no access to apps and such (or at least I don't know the terminal commands for them).  Does anyone know a command to fix/reset it?

If nothing else, I can fix the status bar with a fixed resolution.


Hi...

This command might work...

```
lspci
```

Please post those results. :)

If not, the device manager should tell you and if nothing else, you can go to the web site of the manufacturer of your laptop to get the model specs there.

Best Regards...

---

### Post by Lensflare on 2008-06-06
```

```Thanks, but for some reason the command didn't work.  I have no statusbar, so I have no access to Terminal.  I'd love to get the bar back :D

I created a Launcher on the desktop, but it didn't work.  Does anyone know what I can do to get the status bar back?

Got it!  The chipset is Via VN800, so I downloaded it and ran it in Ubuntu.  But it came back with

```
This driver package is only support the default kernel
"2.6.22-14-generic" for Ubuntu 7.10
```

Does this mean I need to get a copy of 7.10?  Gah I hate this :(

---

### Post by ardvark71 on 2008-06-06
> **Lensflare said:**
> 
Oh yeah, I checked Device Manager on my other laptop, didn't give any specs besides the basic UniChrome stuff.  I did check the chipset, and it says Via VN800.  This was in a random place, but is it referring to the graphics card?

Looks like you got it....;)

[http://www.via.com.tw/en/products/chipsets/v-series/vn800/](http://www.via.com.tw/en/products/chipsets/v-series/vn800/)

Also, the OpenChrome page comes up for me...

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Best Regards...

---

### Post by ardvark71 on 2008-06-06
> **Lensflare said:**
> 
Does this mean I need to get a copy of 7.10?  Gah I hate this :(

Hi...

Are you using 8.04? It might be worth a try if you can get better results, unless someone else can guide you...

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Best Regards...

---

### Post by Lensflare on 2008-06-07
Okay thanks, I'll burn a copy of that ISO.  For some reason I'm in a good mood today.  My jailbroken iPod touch with 211 apps just randomly reset itself and I've spent three days perfecting my laptop's Ubuntu, and now I'm going to start over with both of them.  Wow.

So should 7.10 be better for me?  That's weird; usually newer versions work better.  :lolflag:


Anyone have a VN800 chipset that has a working driver on 8.04?

---

### Post by ardvark71 on 2008-06-07
> **Lensflare said:**
> 
So should 7.10 be better for me?  That's weird; usually newer versions work better.  :lolflag:


It could. There have been a lot of folks I've seen on this forum who have had disasters upgrading to 8.04 from prior versions, all for different reasons. 

Newer isn't automatically better. ;)

Best Regards...

---

### Post by didac on 2008-06-07
> 
So should 7.10 be better for me? That's weird; usually newer versions work better.


This is a community effort. Newer versions work better because people try them, find problems and try to solve them with the collaboration of other people. If you persist trying to make your Unichrome work with 8.04, it'll help other people. Just by posting here you are already helping to solve that problem for you and for others.

As for your panel:

Alt-F1 should pop the Applications menu up. Open the terminal and type:

```
gconf-editor
```

Navigate to apps/panel/default_setup/top_panel/orientation and type the value 'top' without inverted commas.

Now that you have a terminal, try again lspci or sudo lspci and post the line for your graphic card. The last numbers will tell vendor and device number separated by colon and in between square brackets. Go to Openchrome website and file a report for your card.

---

### Post by Lensflare on 2008-06-07
Thanks, but that didn't work either.  I got to the configuration editor, and to orientation, but it was already set on top!  I put it on left, but it didn't appear either!  What am I doing wrong?  Could it be hidden or something?

---

### Post by didac on 2008-06-07
Sorry, my mistake. The correct key is apps/panel/top_levels/top_panel/orientation. Isn't apps/panel/default_setup/top_panel/orientation

---

### Post by Lensflare on 2008-06-07
> **didac said:**
> Sorry, my mistake. The correct key is apps/panel/top_levels/top_panel/orientation. Isn't apps/panel/default_setup/top_panel/orientation

Yes, I figured that out, seeing as though there is no key that matches the wrong one.  But I edited the correct one, and it didn't work.  Do I have to restart or something?

---

### Post by anewguy on 2008-06-08
I had a Gateway laptop that I sold late last year because of the OpenChrome problems.  I could eventually get the 2D driver working okay, but the 3D needed a patch for 7.04 (or/and maybe even 7.10) because the installation would abort part way through.  This is when you install the patch and continue.  It was not good.  That Unichrome GP didn't have any horsepower, was lacking (either via [excuse that] not being implemented on the chip or the driver not supporting it) many things, including those needed to run desktop effects like compiz cube, etc.. I fought resolution problems like crazy with that thing - I had to play with both vert and horz freqs in xorg.conf at the same time changing the resolution there as well.   A LOT of time taken, and for nothing.  I think I eventually settled on a GLX driver of some sort, or maybe just vesa, but still had to specify things in xorg.conf.  I eventually hated it enough I got rid of it.  I hope you find better luck.  :)

---

### Post by didac on 2008-06-08
> **Lensflare said:**
> Yes, I figured that out, seeing as though there is no key that matches the wrong one.  But I edited the correct one, and it didn't work.  Do I have to restart or something?

Beats me. The 'wrong' key exists in my computer but doesn't have any effect. The 'right' key has immediate effect, no need to restart. Maybe try Ctrl-Alt-Backspace, it restarts the xorg server. No need to restart all the way.

---

### Post by Lensflare on 2008-06-08
> **didac said:**
> Beats me. The 'wrong' key exists in my computer but doesn't have any effect. The 'right' key has immediate effect, no need to restart. Maybe try Ctrl-Alt-Backspace, it restarts the xorg server. No need to restart all the way.

Well, I played around and found .../panel/toplevels/top_panel_screen0.  There are a lot of top_panel_screen folders, but this one worked.  I edited the orientation to top and clicked expand, and it worked!  Only this time, all the stuff on the right is on the left, as well as all the stuff on the left is still on the left!  In other words, all the stuff I couldn't see before are now there.  Awesome!

> **anewguy said:**
> I had a Gateway laptop that I sold late last year because of the OpenChrome problems.  I could eventually get the 2D driver working okay, but the 3D needed a patch for 7.04 (or/and maybe even 7.10) because the installation would abort part way through.  This is when you install the patch and continue.  It was not good.  That Unichrome GP didn't have any horsepower, was lacking (either via [excuse that] not being implemented on the chip or the driver not supporting it) many things, including those needed to run desktop effects like compiz cube, etc.. I fought resolution problems like crazy with that thing - I had to play with both vert and horz freqs in xorg.conf at the same time changing the resolution there as well.   A LOT of time taken, and for nothing.  I think I eventually settled on a GLX driver of some sort, or maybe just vesa, but still had to specify things in xorg.conf.  I eventually hated it enough I got rid of it.  I hope you find better luck.  :)

Thanks, I've heard just how stubborn these UniChrome graphics cards can be.  My laptop is 2 years old, and I've been annoyed by Windows ever since.  After reading an article in PC World, I decided to give Ubuntu a shot.  But, my cheap investment in a base model Gateway has come back to haunt me, apparently.  I'm getting a MacBook in a few weeks, but I'm not sure if I want to dual boot with Ubuntu or what.  If it works well, I'll do it; but I'm not fully aware of the graphic capabilities.

I wouldn't care (at least not right now) about 3D graphics, I just want my full desktop :)  I'm really leaning towards 7.10 right now, just to see if I can get the UniChrome drivers working.  Thanks for all your help, guys, and I might be back with 7.10 problems.  But then again, I might do away with Ubuntu altogether.  I'm not very savvy with all the code and programming that goes into it.


I had an epiphany as to why it's not working:  I have no graphic drivers installed!  I went to the Display Configure thing, and picked the via and vsea drivers, but both said "No Drivers Installed" after I clicked okay! In my xorg.conf, there is no "Device   'via'" that I can change to openchrome!  Why is this?  Can I install any off the CD, or is there some thing I've failed to update?  I also went to the Hardware Drivers window, but the only one that was there was the Wireless card, which came with the CD, apparently!

---

### Post by didac on 2008-06-08
Drivers are usually installed in /usr/lib/xorg/modules/drivers There you can check what you have.

If you want to entertain yourself, I attach my xorg.conf from my Fedora box, the one with Unichrome. This is what it works for me. In case the whole thing gets messed up, do you knoiw how to recover the xserver from a command prompt? Do a backup of your original xorg.conf before make manual changes.

---

### Post by Lensflare on 2008-06-08
> **didac said:**
> Drivers are usually installed in /usr/lib/xorg/modules/drivers There you can check what you have.

If you want to entertain yourself, I attach my xorg.conf from my Fedora box, the one with Unichrome. This is what it works for me. In case the whole thing gets messed up, do you know how to recover the xserver from a command prompt? Do a backup of your original xorg.conf before make manual changes.

Thanks.  I tried editing the xorg.conf file on my laptop, but it said I don't have the necessary permissions.  I do have a backup, but I don't know how to recover the xserver from a command prompt.  If anything goes wrong, I can report back from my other Windows-based laptop.

---

### Post by didac on 2008-06-08
As for permissions:

sudo gedit /etx/X11/xorg.conf

Change a line at a time -- or two. Don't copy the whole stuff

---

### Post by Lensflare on 2008-06-08
> **didac said:**
> As for permissions:

sudo gedit /etx/X11/xorg.conf

Change a line at a time -- or two. Don't copy the whole stuff

Sorry I figured out the sudo as soon as I typed it.  But forgot to update :D

I changed the device (added it and entered openchrome) but it didn't work.  For some reason, it doesn't want me to have a display driver installed.  It won't even let me try via or vsea.

---

### Post by starcannon on 2008-06-08
VIA has some official drivers now as well, might be worth a look see:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

They work great, my only issue is getting the monitor on a cloudbook happy with them, the direct rendering is excellent though.

---

### Post by Lensflare on 2008-06-08
> **starcannon said:**
> VIA has some official drivers now as well, might be worth a look see:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

They work great, my only issue is getting the monitor on a cloudbook happy with them, the direct rendering is excellent though.

Thanks!  Unfortunately, it appears there is no VN800. :(


EDIT:  Found this link:  [https://issues.foresightlinux.org/browse/FL-21]("https://issues.foresightlinux.org/browse/FL-21") while googling--could it offer any help?  I would try it, but I have no clue what it's asking.

I also saw on the OpenChrome installation that someone used the files from here: [http://www.gtlib.gatech.edu/pub/ubuntu/pool/main/x/xserver-xorg-video-openchrome/]("http://www.gtlib.gatech.edu/pub/ubuntu/pool/main/x/xserver-xorg-video-openchrome/") and they worked.  However, I have no clue which ones I would need.

---

### Post by didac on 2008-06-09
Found this one:

[http://ubuntuforums.org/showthread.php?t=746932](http://ubuntuforums.org/showthread.php?t=746932)

---

### Post by Lensflare on 2008-06-09
> **didac said:**
> Found this one:

[http://ubuntuforums.org/showthread.php?t=746932](http://ubuntuforums.org/showthread.php?t=746932)

Thanks, but whenever I enter the command to update the xorg.conf, it takes out the Driver   "openchrome"   section!  Why doesn't Ubuntu let me have a display driver?  According to it, I'm not running Vsea, via, openchrome--nothing!

I also entered this code as found on that page, and here are my results:

```
cory@cory-laptop:~$ grep openchrome /var/log/Xorg.0.log
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
(!!) For support, please refer to http://openchrome.org/.
cory@cory-laptop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
```


Okay I'm pretty sure it's a monitor problem now.  I tried all the drivers (vsea, via, and openchrome) in the Display configuration, with all different monitors/LCD screens, and none of them produced wanted results.  I think the UniChrome drivers are installed correctly, but for some reason my LCD Screen doesn't want to play nice with the graphics card. It detects the screen as a Plug and Play monitor, which is what it was listed as in Windows.  Anything I should be doing?

---

