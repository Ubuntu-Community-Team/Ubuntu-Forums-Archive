---
title: "How To: Alps touchpad on 2.6.10 Hoary"
date: 2005-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by mendicant on 2005-04-18
At the request of somebody I helped earlier.

% sudo aptitude install linux-source-2.6.10 kernel-package xorg-driver-synaptics
% cd /usr/src
% sudo tar -x -j -f linux-source-2.6.10.tar.bz2
% cd linux-source-2.6.10
% gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1
% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config
% sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source
% cd ..
% sudo dpkg -i kernel*alps*deb

Then just use the template in /usr/share/doc/xorg-driver-synaptics/README.alps for your xorg.conf.  To disable tap-to-click while preserving the scrolling behavior on the right edge of the pad, try setting MaxTapTime to 0.

---

### Post by SteveGodfrey on 2005-04-20
Thanks for the guide but I'm failing at the aptitude command!

Can you tell me which repositries you're using?

Thanks

---

### Post by mendicant on 2005-04-20
[QUOTE=SteveGodfrey]Thanks for the guide but I'm failing at the aptitude command!
[/QUOTE]
 How are you failing?

xorg-driver-synaptics is in X11/main
kernel-package is in misc/main
linux-source-2.6.10 is in devel/main

I do have restricted, universe and multiverse, but those won't matter because everything is in main.

---

### Post by jasonmallison on 2005-04-20
You could just use apt-get instead of aptitude...

---

### Post by mendicant on 2005-04-20
aptitude vs apt-get isn't likely to be the issue.  In any case, you should use aptitude in preference to apt-get or other console based front ends:

  [http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

---

### Post by SteveGodfrey on 2005-04-20
Right then I've eventually managed to get all that done! It's taken me around 15 hours.....

I re-boot the PC and my new kernel was there (ends in -alps) booted into that and X wouldn't start. So I restored the original xorg.conf and it started up ok :-)

The tap to click has now been disabled (phew) but I still get the mouse occasionally scrolling down the screen and getting stuck at the top or bottom menu bar :-(

Any ideas?

Thanks

---

### Post by mendicant on 2005-04-20
That's a weird one.  I've never seen it before.  Does this happen when you're intentionally moving the mouse, or does it seem random?

---

### Post by SteveGodfrey on 2005-04-21
Both! I might be using the mouse then the pointer will scroll up (or down) the screen and just sit there. I can move it left and right withing the menu bar but not out of the menubar.

I'm going to trying installing the 2.6.11 kernel as from what I've read that has the synoptics (Alps in my case) support built in.

Anyone know any Ubuntu howto's on installing new kernels?

---

### Post by mendicant on 2005-04-21
How old is the touchpad?  It could very well be a hardware issue, as well.  It could be dirty, or something much more difficult.  Do you dual boot?  Does it happen in other OS's?  Is it a recent thing?

---

### Post by SteveGodfrey on 2005-04-21
It's an 18 month old Toshiba Tecra S1, the touchpad works fine in XP.

It is a dual touchpad/nipple thing!

As I'm typing this the mouse is moving around the top of the screen! It's a nightmare tabbing around to find the buttons!!

It would seem as if there is a problem with the dual-pointer. I always have the nipple one disabled in windows so know I need to find out how to do that in Linux.....

Oh well.

---

### Post by laggerzero on 2005-04-21
just a quick tip:


when applying the kenel patch you might want to actually become root by doing the following:

```
sudo su
``` 

that will keep you logged in as root. when trying to apply the patches just using sudo, it gave me permission denied. using sudo su will fix this.

---

### Post by mendicant on 2005-04-21
Maybe decrease the sensitivity in Linux?  This would be the FingerLow/FingerHigh numbers.  LockedDrags aren't on, are they?

---

### Post by mendicant on 2005-04-21
[QUOTE=SteveGodfrey]
It would seem as if there is a problem with the dual-pointer. I always have the nipple one disabled in windows so know I need to find out how to do that in Linux.....
[/QUOTE]

Some BIOSes have an option to disable one or the other.

---

### Post by SteveGodfrey on 2005-04-21
Not this BIOS, I can only disable the mouse completely.

---

### Post by aburda on 2005-04-26
gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz - | sudo patch -p1

I'm not an expert and don't completely understand what all of the commands are doing, but from my basic knowledge of the command line I assume that the dash (-) after .....alps.patch.gz is a typo.  

Just so I don't lead any poor suckers astray, somebody want to confirm this?

Aaron

---

### Post by mendicant on 2005-04-26
Right.  It actually won't hurt anything, which is why I didn't notice it before.  The warning just goes to stderr, not stdout, which is what gets piped to patch.  I'll edit the post.

---

### Post by pardasaniman on 2005-04-26
For the record, it **almost** works on my Toshiba Satellite 2400.

I get a pointer, but it just jumps randomly on the screen.

---

### Post by aburda on 2005-04-27
[QUOTE=pardasaniman]For the record, it **almost** works on my Toshiba Satellite 2400.

I get a pointer, but it just jumps randomly on the screen.[/QUOTE]
 To add a bit to the list of things that are necessary to get the ALPS touchpad going on a (Toshiba) laptop.  In addition to all of the above, including the editing of xorg.conf according to what is listed in the ALPS patch I had to add "Corepointer" after my "Touchpad" (or whatever you named your device) as follows in xorg.conf. 

	InputDevice	"Touchpad" "CorePointer"   

        I found this in some other forum a couple of weeks ago and it didn't work (as I didn't have the patch at that time) so I commented it out of my xorg.conf.  When I booted up after doing the patch and changing my xorg.conf my mouse didn't work so I used the hotkeys to get to xorg.conf and decided what the hell and tried uncommenting the "Corepointer" and voila, CTRL-ALT-Backspace and my ALPS has finally been found!!! I can use Photoshop and Gimp!

         I do have another problem though in that after grub my screen goes completely blank until X starts up.  I checked my menu.lst file and the alps kernel startup options are the same as what I had before for my 686 kernel.  Any guesses as to what I did to make my kernel not be able to display in text mode?  I have the vga=771 option set.

           Aaron

---

### Post by aburda on 2005-04-27
In addition, it appears that the tapping only partially functions with this alps driver.  Double tapping does not seem to work.  According to this newsgroup [here](http://www.ussg.iu.edu/hypermail/linux/kernel/0501.3/1918.html)  that I found through google apparently the hardware support for tapping is disabled meaning that the ALPS pad can't distinguish between two quick taps, i.e. double clicking doesn't work by tapping.  Some kind of patch is included on the forum, but it appears that it is for the 2.6.11 kernel.  Has anybody gotten the ALPS touchpad to work and as well have the ability to double click using tapping?
        I'm thinking (hoping) maybe I'm wrong on this and just have to work out the values better in xorg.conf.


            Aaron

---

### Post by Jimbo Jones on 2005-05-20
Hello,
I've tried to apply your tip to get my alps touchpad working but it doesn't work more  ](*,) . As I say in another thread ([http://ubuntuforums.org/showthread.php?t=25110](http://ubuntuforums.org/showthread.php?t=25110)), I only managed to get that touchpad working by going back to kernel 2.6.8 . By trying your method, I have the same results as before (my keyboard doesn't work until I press many times the PrtScr or Shift key, and only the usb mouse works). 
If you think there is despite all another new method to get that touchpad working, tell me and i'll try it. 
Thank you very much for the tip,
Jimbo

---

### Post by JALenon on 2005-06-02
Hi, thanks for this thread.

I'm new to Linux and this line is unclear to me.

*% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config*


What goes in place of ## in the line above?

---

### Post by mendicant on 2005-06-02
[QUOTE=JALenon]
*% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config*


What goes in place of ## in the line above?[/QUOTE]

Nothing.  It's a comment, so you could just print out the whole line and it would work.  The comment itself refers to the fact that config-2.6.10-5-386 might have to change.  For example, if you use a 686 kernel, it would be config-2.6.10-5-686.

---

### Post by dejitarob on 2005-06-13
Using basically the same method posted by mendicant, I got the alps/synaptic driver loaded according to my Xorg.0.log. However the sensitivity is very low and immediately after I log into and KDE loads, the touchpad stops working completely. I'm using mlord's [xorg.conf](http://rtr.ca/dell_i9300/xorg.conf), who got it working in this [thread](http://ubuntuforums.org/showthread.php?p=210972).

Update: Ok via the README, adding the "AlwaysCore" and "CorePointer" in the ServerLayout section of my xorg.conf while commenting out the CorePointer options in the InputDevice section fixed it.

---

### Post by jc3835 on 2005-07-01
[QUOTE=mendicant]At the request of somebody I helped earlier.

% sudo aptitude install linux-source-2.6.10 kernel-package xorg-driver-synaptics
% cd /usr/src
% sudo tar -x -j -f linux-source-2.6.10.tar.bz2
% cd linux-source-2.6.10
% gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1
% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config
% sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source
% cd ..
% sudo dpkg -i kernel*alps*deb

Then just use the template in /usr/share/doc/xorg-driver-synaptics/README.alps for your xorg.conf.  To disable tap-to-click while preserving the scrolling behavior on the right edge of the pad, try setting MaxTapTime to 0.[/QUOTE]


Got to the gunzip line and I'm having an issue... 
```
patching file drivers/input/mouse/Makefile
patching file drivers/input/mouse/alps.c
patching file drivers/input/mouse/alps.h
can't find file to patch at input line 486
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -puN drivers/input/mouse/psmouse-base.c~alps drivers/input/mouse/psmouse-base.c
|--- linux/drivers/input/mouse/psmouse-base.c~alps      2004-10-20 20:04:38.190737928 +0200
|+++ linux-petero/drivers/input/mouse/psmouse-base.c    2004-10-20 20:04:38.196737016 +0200
--------------------------
File to patch:

```

So what exactly is the file I'm patching? Am I missing something really obvious?
Sorry if so...
Help!

Thanks.

---

### Post by jc3835 on 2005-07-01
[QUOTE=jc3835]Got to the gunzip line and I'm having an issue... 
```
patching file drivers/input/mouse/Makefile
patching file drivers/input/mouse/alps.c
patching file drivers/input/mouse/alps.h
can't find file to patch at input line 486
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -puN drivers/input/mouse/psmouse-base.c~alps drivers/input/mouse/psmouse-base.c
|--- linux/drivers/input/mouse/psmouse-base.c~alps      2004-10-20 20:04:38.190737928 +0200
|+++ linux-petero/drivers/input/mouse/psmouse-base.c    2004-10-20 20:04:38.196737016 +0200
--------------------------
File to patch:

```

So what exactly is the file I'm patching? Am I missing something really obvious?
Sorry if so...
Help!

Thanks.[/QUOTE]
 OK, so I'm not really supposed to be asking questions here... SORRY.
It's just you're reading the HOWTO, you have QUESTIONS about the HOWTO, and you ask.
:shame:

---

### Post by mendicant on 2005-07-04
It's trying to patch the file called psmouse-base.c, which is in the linux source tree, under drivers/input/mouse/.  Do you have that file?

---

### Post by TmP on 2005-09-15
Hey!
It's my first post here.
The problem with the mouse moving by itselfes...
Its normal for touchpoint laptops (in both toshiba and ibm laptops)
its because of a hardware algorythm which centers the touchpoint ( it actually looks like a small joystick in the middle of your keabord).
So when you apply some force to it and keep your hand very steady, it'll think the touchpoint's center got shifted. So it'll stop moving. when you lift your finger, the cursor runs away, but after 3 seconds or so, recognises the new center of weight.

I think it could be resolved by making the time-it-takes-to-center longer. I guess it would be possible only if its in the alps, not the software.
It's mostly annoying , when your using precision tools in gimp.

---

### Post by TwiceOver on 2005-09-18
I have a Toshiba A15 laptop with an Alps touchpad.  I followed this instruction and everything seemed to go well.  However the right-edge scrolling doesn't work.  I think I may have done something wrong in the xorg.conf portion.  I did change the "MaxTapTime" to 0 but that didn't help.

What I am wondering is was I supposed to REPLACE the device section in the xorg.conf with the information from the README.alps or just ADD the information?  I tried to replace the synaptics device information in xorg.conf with the new input device information in the README.alps file and on reboot x-term failed and dumped me into the prompt.  When I just add the information to the xorg.conf everything boots fine.

I can live without the scrolling, at this point it is just force of habit from using it in Windows for the last year.  Any help greatly appreciated.

---

### Post by dontodd on 2005-10-02
The alps patch fails on the 2.6.12 kernel source (Breezy). Any ideas?

Thanks!

---

### Post by ptepper on 2005-10-28
For anyone using 5.10 Breezy and searching for answers on this, you should stop reading this thread, I've gone through all these steps, they don't work, but they will take you a long time to get through. Instead, proceed here immediately:

[http://ubuntuforums.org/showthread.php?t=76585]("http://ubuntuforums.org/showthread.php?t=76585")

This worked for me and it's real quick. Make sure you actually reboot when it says to, just restarting X didn't work for me. 

-paul

(thanks to Chad Glendenin for pointing me to it)

---

