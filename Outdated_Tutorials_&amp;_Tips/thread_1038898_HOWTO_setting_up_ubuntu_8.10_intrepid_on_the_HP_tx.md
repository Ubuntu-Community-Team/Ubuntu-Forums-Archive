---
title: "HOWTO setting up ubuntu 8.10 intrepid on the HP tx2z tablet pc"
date: 2009-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by glurgle on 2009-01-14
[B]Important!
Though I will endeavour to keep this post updated with any changes to this guide, the absolute up-to-the-minute version can be found here on my blog: [http://goatonabicycle.com/rambles/?p=74](http://goatonabicycle.com/rambles/?p=74)[/B]

Installation was pretty straightforward, but the touchscreen/digitizer and sound took some tweaking to get working properly. There was also a bit of a glitch with suspend/resume.

I chose to enable the closed source ‘fglrx’ driver for the ATI chipset using the “jockey” tool that comes with Ubuntu. Just click the icon in the notification area and choose to enable the driver, and the rest of the install is handled automatically.

At the time of this writing, Stylus input works excellently via the linuxwacom driver after installing Rene Mayrhofer’s pre-compiled packages (available at his Latitude XT page).

However, his packages contain an fdi file that will cause the digitizer to be auto-configured by HAL, thus preventing the use of xsetwacom to rotate the orientation of tablet input and n > 1 device mapping the linuxwacom driver uses to enable touch and stylus input from the same device. So either move or delete /usr/share/hal/fdi/policy/2Othirdparty/1O-wacom.fdi after you install the package.

Then (before you restart X) edit your xorg.conf to enable the input devices. Mine looks like this:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen "Default Screen"
        InputDevice    "Trackpad"
        InputDevice    "stylus"
# I've commented out the eraser because it either doesn't exist or doesn't work
#        InputDevice    "eraser"  # "SendCoreEvents"
        InputDevice    "touch"
EndSection                                 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Load	"dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "InputDevice"
	Identifier  "Trackpad"
	Driver      "synaptics"
	Option	"Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
EndSection

Section "InputDevice"
	Driver "wacom"
        Option "Mode" "Absolute"
        Identifier "touch"
	Option "Touch" "on"
        Option "Type" "touch"
 	Option "ForceDevice" "ISDV4"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#        Option "USB" "on"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "9600"
	Option "BottomY" "7200"
	Option "DebugLevel" "8"
 	Option "Button1" "1"
 	Option "Button10" "1"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Mode" "Absolute"
        Option "Type" "stylus"
 	Option "ForceDevice" "ISDV4"
 	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
 	Option "TPCButton" "on"
        Option "USB" "on"
        Option "Button2" "3"
        Option "Button3" "core key alt F2"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Mode" "Absolute"
	Option "Type" "eraser"
	Option "ForceDevice" "ISDV4"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
 	Option "TPCButton" "on"
	Option "USB" "on"
	Option "Button1" "2"
EndSection
```

The sound device is recognized and seems to work just fine at startup, but often when playing sound the card goes mute after less than a second, and won’t come back on without rebooting. Adding the correct option for modprobe seems to have fixed it though:

```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base

```
Also on the subject of sound, the built-in beep speaker is absolutely horrid. So make sure you get rid of that by editing another modprobe.d file to blacklist that little bugger into oblivion (I really hate the pc speaker):

```
sudo modprobe -r pcspkr
sudo echo "blacklist pcspkr" >> /etc/modprobe.d/alsa-base
```

These settings won’t take effect before you reboot, but there’s one other thing to take care of first. You may have stumbled upon this already, but if you suspend the machine, the keyboard and touchpad no longer work on resume. To fix this, we need an additional kernel option to reset the i8042 controller that manages the keyboard and touchpad. So you will want to edit /boot/menu/grub.lst and add i8042.reset to the default kernel options like so:
```

# kopt=root=UUID=42519078-9aec-4171-a2bd-5ba1667357b7 ro i8042.reset

```
After this, go ahead and reboot, and everything should be smooth as silk.

---

### Post by Vincent_Lin on 2009-02-03
Hi,

I just want to chime in.  Got this piece of machinery for my birthday!!

I followed this HOWTO and setup 8.10 on my tx2z and got all those mentioned working.  THANKS..   I also installed broadcom (download from broadcom.com) proprietary 64bit driver and wireless works without ndiswrapper.  Don't have any BT device, so I did not test it.

Absolute not working:
Resume after suspend - that i8042.reset appending kopt line in menu.lst is not working.  I have not found a solution yet.  No resume by opening the closed lid.  Pitty!  HELP???

Haven't tweaked much yet - 
        - X rotations, 
        - disable finger touch at will (when drawing using pen only)
        - While we are at this, what is the way to enable middle-button mouse action on the pen?  I have an application that uses all three buttons but I don't know how/where the middle button is.  Through pen control, that it.
        - handwriting recognition stuff (read somewhere that it is compared to the mechanism that MS offers).

BTW, this machine came with Vista.  Out of curiosity, I ran it for about 12 hours, buy can not stand how sluggish it ran.  I have another T42 with centrino 1.7GHz (ATI9600M) and 8.10 flies on it already - compiz, etc...  Really can't stand the Vista running on a machine/hardware that is several generations advanced.  How bad Vista could be??

Does anyone know if I can still request a MS tax refund?  And where can I proceed?  

Thanks.

Vincent

---

### Post by Favux on 2009-02-04
Hi,

Fat chance you'll get a refund out of MS.  The letter writing recognition app I think you are talking about is Cell Writer.  Search cellwriter in Synaptic.

Eraser only works if it's enabled in a specific program like gimp.  In Xournal the eraser is your stylus side-switch (if it's set up as right-click).

I don't understand some stuff in the xorg.  "Option "ForceDevice" "ISDV4"" is only for a serial tablet, I think.  I don't think you want "Option "Mode" "Absolute"" either.  Since it's a N-trig digitzer, I'm not totally sure.  Also HAL should run your synaptics touchpad.  Was there a problem?  Is the touchpad new enough that there isn't a .fdi file to run it or something?

Finally the pci usb input path is the same for stylus/eraser and touch.  In the TX2000/TX2500 stylus/eraser are suppose to be the same but touch is different.  Do you want to find out if there is a separate "touch" pci input path?

So anyway I messed with your xorg.conf.  If you're interested in messing around with it, give it a shot.  Otherwise.

---

### Post by Vincent_Lin on 2009-02-04
Thanks.
Favux,

Thanks for the prompt response.


OK, got cellwriter to work now.  Well, actually a couple click only.  I am still training it.

Having installed fglrx downloaded from ATI website, xrandr works as advertised.  There is an entry at (unofficial) ATI wiki site that documents the extra command to run before xrandr works.  

[http://wiki.cchtml.com/index.php/Features](http://wiki.cchtml.com/index.php/Features)

So I ran your scripts in Method 2 in another thread about rotating tablet on tx2000-ish.  After X refreshes and the screen, 
 - stylus/cursor movement are synched, no miss-alighed issues, 
 - stylus moves cursor

except, a BIG EXCEPT, that 
 - stylus click does not trigger anything, 
 - keyboard does not accept any input.
 - touchpad (below keyboard) does not rotate at all - acceptable since it is assumed that keyboard/keyboard are both covered by screen anyway  

Other behaviour
 - Gnome panel scales well, 
 - but the desktop did not get resized - meaning that any application/window stays where they were before rotating.  But I am not sure since the screen/keyboard do not accept any input except cursor movement by stylus.
 - BUT, there are some reactions on the screen if I stick/click style at lower-right corner.  Some rubber-bands appear, as if some windows are coming alive but could not finish it.

Strange stuff
 - caps-lock is not dead, as the LED toggles as you press it

 - Num-lock is also alive, same as above

 - Ctrl-Alt-Backspace DOES kill X and gdm restarts afterward without issues

- Ctrl-Alt-(left or right) for rotating virtual desktop causes the cursor to disappear and appear again later with repeated pressing of such combo.


OK, I suspect that Compiz is the problem.
 
Or, could this be also related to that no resume after sleep/suspend issues?

So I 
 - added i8042.reset back to kernel option line and reboot the machine.  Well, this time gdm unlock window pops but still does not accept any input.  Caps-lock is not accepted neither num-lock.  Still no go on this.


- disabled Compiz by disabling Desktop effects.  Success.  Rotation is perfect and all input are intact.

WOW!!!

Compiz does not live well with fglrx or something!!??

Now I remember that you had mentioned somewhere else you do not run compiz at all.  Am I correct on this?  I should have read all the posts more carefully.

Thanks a lot for giving the directions for playing around this wonderful machine, and eventually getting somewhere with 8.10.

Sorry about this long verbose post.  I still have my final two questions:

1. How to setup stylus to emulate middle button of a mouse
2. i8042.reset never fixed frozen(no-input-accepted)-on-resume-after-suspend issue.  Does anyone have more ideas that I can messing around?

Thanks again.

Vincent

---

### Post by Favux on 2009-02-04
Hey Vincent,

Good about cellwriter.

Wow!  Quite the post.  Can't blame you, excited by your new toy.  If you look at the top of the rotation HOW TO mememe says although the new "fglrx" do offer rotation, they don't work with Compiz.  He meant that rotation doesn't work right, not that it won't rotate.

You might want to slow down before you get yourself in a mess.  Although getting out of a mess can be kind of fun!  lol

On the middle mouse button thing.  Not sure, I'd have to go back and reread that stuff.  I'll make a guess you can try, but no guarantees.  Instead of:
```
Option		"Button2"	"3"  # make side-switch a right button
```
try:
```
Option		"Button2"	"2"  # make side-switch a middle button
```

I'm going to have to come back and reread your post.  Too much to digest.

---

### Post by Vincent_Lin on 2009-02-05
Hi Favux,

Thanks for all the help you have there.

I created a couple scripts just like the HOW TO says and put them on Gnome Panel so that it is easy for me to rotate the screen in tablet mode.  It is really wonderful to have rotation work at will.  Unfortunately without compiz of course.  But, for me anyway, compiz is for show off purpose most of the time, though I think it please my eye sights at a great deal so that my productivity is improved, a bit!!

The change in xorg.conf to assign "push"  on styles to work as middle button works.  Thanks.

I have not explored much in pressure sensitive setting yet, but I think it is just the matter of time to accomplish it. GIMP and Inkscape are the two applications I want to have this to work, and I already saw some instructions to set it.  So, another matter in time to finish it.

I actually installed ubuntu studio 64 bit version on this machine.  This distribution has focus on media (video, music, graphics) creation and is running on generic kernel.  Obviously all the setup that works for regular 64 bit kernel works on this machine.  I also need to spend some time to setup jack and midi stuff before it becomes my main workstation.

The only bummer is freeze-after-resume-from-suspend.  I am still reluctant to install linux-rt package to bring all the goodies of realtime kernel.

Thanks a bunch.

later,

Vincent Lin

---

### Post by Favux on 2009-02-05
Hi Vincent_Lin,

> It is really wonderful to have rotation work at will. Unfortunately without compiz of course.
Great!  And don't give up on Compiz.  ATI has released a bunch of stuff to open source so "radeon" should be making progress along with "fglrx".  And the Compiz developers finally got organized, so look for progress there.

> The change in xorg.conf to assign "push" on styles to work as middle button works.
Outstanding!  Now I won't have to reread the stuff.  I can pretend I still remember it!

---

### Post by Vincent_Lin on 2009-02-06
Favux,

Do you have any other ideas about fixing freeze-after-resume-from-suspend issue?  i8042.reset really is not working for my tx2z.  I also tried i8042.reset=1 and it does not fix it either.  From reading other threads, I know tx2500 has some issues as well, so that it is required to disable acpi or something.  Do you think they could be related?

Thanks.

Vincent

---

### Post by Favux on 2009-02-06
Hi Vincent,

Did you try the xorg.conf I posted?  Did it work for you?

Does touch work for you?  What I would like is for you to remove any attached usb devices and dock etc. and reboot.  Then immediately get the output of:
```
dmesg | grep Wacom
```
or sometimes it's "wacom", with the small "w".  And the output of:
```
ls -l /dev/input/by-path
```
And post the output of both as attachments.

I'm not sure I can help you with the suspension thing.  Remember gurgle is using Feisty (7.04).  I think Feisty used at most kernel 2.6.24.  Maybe earlier.  So it wouldn't surprise me if the i8042.reset line he used doesn't work right anymore with 2.6.27.  That said you used your own UUID # not his, right?  How much RAM do you have.  How big is your /swap ?

---

### Post by Vincent_Lin on 2009-02-06
Hi Favox,

Thanks for the reply.  the output of dmesg and the contents in /dev/input/by-path is attached.

To answer your questions and in turn hopefully, solve my problem :), 

I did add i8042.reset on the tail of my kopt line, with my own UUID.

I bought this tx2z with 4Gb installed, and I set swap to be exactly 4Gb as well.

Cheers,

Vincent

---

### Post by Favux on 2009-02-06
Hi Vincent,

It's recommended, if you are going to do suspend, that /swap be 1.5x (up to as much as 2x) your RAM.  So I think you would want your /swap to be about 6 GB.  It's possible that having it a 4 GB (/swap=RAM) may be part of your problem.

Good, thanks for the output.  I'll take a look.  Does touch (finger or fingernail) on your screen work for you?

---

### Post by Vincent_Lin on 2009-02-06
Hi Favux,

I did hear that swap should be set to around 1.5 times of actual physical memory, but I don't know that it is related to suspend.  I guess it is worth a try.

Regarding the tablet functions, I can say - YEAH!!

I have those scripts and some are even one-liners to be packed to icons in a drawer of gnome panel, so that not only I can use the functionality but my little girls (4 and 6 years olds) can boot the machine and use it by themselves.  They are taking up too much time using my T42 playing simply tuxpaint.  But now I can show them to draw stuff on inkscape and the likes, but not gimp, just not yet.

These icons will do rotation-right(toggle), rotation-up-side-down(toggle), no-touch, and both-touch-and-pen.  When touch is not that much used as stylus, I simply disable it, by issuing xsetwacom commands, to prevent the interfering when my palm is touching the screen.

Pressure sensitive works in both gimp and inkscape.  I went though documentation of linuxwacom and it is all there.  

This machine is actually very sweet.  I was eye-ing on Lenovo X200, but it is expensive enough to put off my purchase decision, until I saw this tx2z.

Thanks.  Will let you know if increasing swap will help solving resume issues.

Cheers,

Vincent

---

### Post by Favux on 2009-02-06
Hi Vincent,

That is cool.  Your tablet has turned into sort of a family activity!

If everything is working well, we should probably leave well enough alone.  The reason I wanted the output (thanks again) is because gurgle's xorg.conf confused me.  Everything was on the same input path.  As far as I know touch should have a different input path.  But since the TX2z uses a N-trig digitizer I could easily be wrong.  I was surprised that dmesg did not return some pci paths with the wacom stuff.  Would you mind terribly attaching your xorg.conf?

I agree, HP tablets are a great bargain.  Good luck on suspension.  Don't take my word on the 1.5x thing, check around first.

---

### Post by Vincent_Lin on 2009-02-07
Favux,

gparted is resizing my data partition to yield some more hd space for swap.  It is taking very very long time now.  I guess I will see what comes out tomorrow morning.

Please find my attached xorg.conf.  It is a mixed copy of here and there, etc.., mostly based on what glurgle posted here.

Cheers,

Vincent

---

### Post by Vincent_Lin on 2009-02-07
Hi Favux,

OK.  Here is the thing.  Resume after suspend now is working, after I added i8042.reset to the end of the actual kernel line, instead of #kopt line.  I suppose adding options on the #kopt line is to add "generic" options that would be applied to and and all kernels you would boot from, resulting in the options to survive and upgrade/change of kernels.

Yet, I did remember I once tried that but it did not work at that time.  And this time it works.  Strange isn't it?

BUT, there is always a big but, wired networking stopped working, and yet wireless networking IS working.

How bizarre is that!!

catting /var/log/pm-suspend.log (suspend and resume log) would show exactly the same before and after this change, both are success.

Initial commandline parameters: 
Sat Feb  7 13:07:01 CST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: Welcome to PulseAudio! Use "help" for usage information.
>>> success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Sat Feb  7 13:07:04 CST 2009: performing suspend
Sat Feb  7 13:07:20 CST 2009: Awake.
Sat Feb  7 13:07:20 CST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume: success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume: Welcome to PulseAudio! Use "help" for usage information.
>>> success.
/usr/lib/pm-utils/sleep.d/00clear resume: success.
Sat Feb  7 13:07:21 CST 2009: Finished.


So I gain some and lose some.  Afterall, I can live with no-wire-networking as long as wireless networking is working, in addition to suspend works.

Cheers,

Vincent Lin

---

### Post by Favux on 2009-02-07
Hi Vincent,

Great!  So maybe giving swap a little more room did the trick.

All the kernel mods I had to do before the 2.6.27 kernel, were always at the end of the actual kernel line.  Why that would break wired networking is beyond me.  I agree, bizarre!

Oh well glad it is working.  One more favor.  Could you attach the output of:
```
more /proc/bus/input/devices
```
I have found some more stuff about N-trig.  There should be at least two sections in the output that start with something looking like:
```
I: Bus=0003 Vendor=056a Product=0093 Version=0330
N: Name="Wacom ISDv4 93"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input10

```
Also could you repeat the:
```
dmesg | grep [Ww]acom
```
command and see if you get pci/usb paths in it.  Even try changing wacom to n-trig (or N-trig or N-Trig, etc.).  Basically I'm trying to do appendix 1 of:
[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")
of the kernel driver HOW TO for N-trig.  Thank you.

---

### Post by Vincent_Lin on 2009-02-07
Favux,

So stupid me.  

1. After a reboot, wired and wireless networking both work.  

2. I forgot I resized/increased swap partition.  That might be it.  gparted works pretty well, except that the time it took was so long that it actually worried me a bit.

Now I have attached the output of the those commands you requested.  
Glad to help and showoff the status of a working 8.10 on tx2z.

Thanks again.

Cheers,


Vincent Lin

---

### Post by Favux on 2009-02-07
Hi Vincent,

Outstanding!

So still no output from Wacom.  Darn.  Say you misspelled trig.  Could you please try again using:
```
dmesg | grep [Nn]-[Tt]rig
```
instead of:
```
dmesg | grep [Nn]-[Tt]ring
```
Oh and please try it without the hypen.  "[Nn][Tt]rig".  Thank you so much.

---

### Post by Vincent_Lin on 2009-02-07
Favux,

No sign of [Nn]-[Tt]rig nor [Nn][Tt]rig when I ran dmesg.

vincent@tx2z:~$ dmesg | grep [Nn]-[Tt]rig
vincent@tx2z:~$ dmesg | grep [Nn][Tt]rig
vincent@tx2z:~$ dmesg | grep N-Trig
vincent@tx2z:~$ dmesg | grep N-trig
vincent@tx2z:~$ dmesg | grep n-Trig
vincent@tx2z:~$ dmesg | grep n-trig
vincent@tx2z:~$ dmesg | grep NTrig
vincent@tx2z:~$ dmesg | grep Ntrig
vincent@tx2z:~$ dmesg | grep nTrig
vincent@tx2z:~$ dmesg | grep ntrig
vincent@tx2z:~$ 


Yet, the wired networking is rather unstable.  I suspended this machine and open it after a few hours, wired networking was not working again.

After a fresh reboot, and closed the lid then open it, wired networking is still working.

On either case above, i checked /var/log/pm-suspend.log and both had 
10Networkmanager resume: success.

I certainly hope that my network card is not mal-functioning.  I will play more with it over the weekend.

Cheers,

Vincent

---

### Post by Favux on 2009-02-07
Hi Vincent,

Well, something strange is going on.  But the current version of Network Manager (0.70) seems to have a fair number of problems.  Maybe it will improve with Jaunty.  And so should your N-trig support.  Kernel 2.6.28 is suppose to have more support for it.  And Rafi already has a patch out for it.

Thank you very much for checking on the N-trig stuff!  I can't figure out why there isn't any input paths.  I come back to maybe there is a problem with the N-trig patch.  I think the Dell latitude user was using event 3 as his touch input path.  It has me confused.  Oh well.

---

### Post by Vincent_Lin on 2009-02-12
Hi Favux and Glurgle,

After much tweaking and messing around, I decided to install ubuntu studio 8.10 64bit edition once more.

1. ubuntu studio DVD
2. all updates/upgrades
3. enable restricted drivers - fglrx + broadcom wireless
3. fglrx upgrade download directly from ati/amd site
4. wacom driver download from Rene Mayrhofer’s pre-compiled packages
5. menu.lst tweak i8042.reset on actual kernel line
6. then installed whole bunch of applications

Result?  A fully working ubuntu on tx2z - wireless, resume, pen, touch, rotation (no compiz), touch-sensitive on GIMP and Inkscape, etc...

I also ordered an ExpressCard 1394 card that works wonderfully with kino for video footage capture.

Oh!  There is a firefox plugin called "Grab and Drag" that enables Firefox to take pen/touch input - so that you can scroll web pages using your finger(s), just like how iPhone does it.  Fun stuff!!

THANK YOU ALL, wonder guys!!

I guess my initial swap partition was really too small for resume purpose.  And I have never heard that it is related.  I also hope that more applications can explore and take advantage of touch and stylus input.  Also, multi-touch capability is also unheard on linux, just yet, I think.

Cheers,

Vincent

---

### Post by tempo500 on 2009-02-13
hey,
im new in this forum...just upgraded from an tx2000 to the tx2z. i am having problems getting my audio capture right. i need it for skype. i get a very static feedback using alsa, if i turn the front mic boost up too high its just static, too low and no recording... i dont get any feedback trough pulse audio, but playback works fine.

i tried all three lines and currently using the first one(it seems all work...)
options snd-hda-intel model=toshiba
#options snd-hda-intel index=0 model=toshiba position_fix=1
#options snd-hda-intel index=0 model=acer

besides... is there any hope we can tune the fans? its a bit too loud for my taste... i am using the frequency applet with the fan all the time on (set in bios) i dont like the bios turning the fans all the time off/on with full blast every 5 minutes

greets, phil

---

### Post by Vincent_Lin on 2009-02-13
Hi tempo500,

My tx2z has a problem now.  The sound suddenly stopped working, no sound coming from any application.  I had not tweaked sound settings after my second installation and the sound suddenly died, two days after a perfectly working tx2z.  Sorry I can´t help you on this one.

The fan is *almost* driving me crazy.  I have not done anything on it either.  Just yet.  

So, good luck in finding the solutions you want, and please come back and post your solutions when they are resolved.

Vincent

---

### Post by eccuser on 2009-02-15
hi Vincent,
i would like to know how to make the screen automatically rotate after i switch to tablet mode ?
i got my everything working, also to notify everyone that the finger on screen is working too, but i just would like to know how to make the screen automatically rotate when i switch to tablet mode?
Thanks you and best regards

---

### Post by Vincent_Lin on 2009-02-15
Hi eccuser,

The gnome desktop of my tx2z would not automatically rotation when you rotate the screen into tablet mode.  I created a couple of scripts, according to the HOWTO by Favux, talking about rotation, that you must have read already, and put them into buttons of gnome panel.  They are rotate-right, rotate-upsidedown, no-touch, enable-touch, which are basically all accomplished by issuing xsetwacom command.  Facux mentioned that he has not found the trigger from the hardware screen rotation.  Therefore, no automatic rotation of X yet.

Hope this helps.

Do you have sound working?  Can you post your /etc/modprobe.d/alsa-base, and /etc/modules.  I have this annoying problem that no sound coming out to speakers nor headphones.

Thanks.

Vincent

---

### Post by Vincent_Lin on 2009-02-16
OK,

Looks like I am talking to myself these days.

I re-installed ubuntustudio on tx2z again, and again.

The result is 50-50.  The working sequence I have is like this

1. Install DVD
2. enable proprietary drivers - ATI + Broadcom
3. Install network-manager (reboot)
4. run update
5. reboot
6. Insall linuxwacom driver
7. replace xorg.conf (all the stylus and touch goodies, see first post)
8. tweak /etc/modprobe.d/alsa-base, /boot/grub/menu.lst
9. Now reboot and make sure everything is working
10. Install fglrx (remember to run aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"  to enable xrandr)
11. Reboot - success - sound, wireless, rotation all worked.

The sequence is working for about 15 minutes as when gdm starts the chime and the sound after login were both there.

Until I ran totem to watch my movie files, mp4 by HandBrake.  Totem asked to install extra codec so I went ahead.  Afterwards, the movie plays but the sound came out for around 10 seconds and now sound is dead.  

I can't believe it was caused by Totem gstream codecs.  What's going on here?

I am really frustrated.  Does anyone remember what those two codecs Totem asks to play mp4 files?  When can I remove them?

Help!

Vincent
P/S. tablet rotation and wireless are working fine, but no sound.

---

### Post by Favux on 2009-02-16
Hi Vincent_Lin,

This thread may help.  mememe starts it off in post #512, and especially in post #514.

[http://ubuntuforums.org/showthread.php?t=845911&page=52]("http://ubuntuforums.org/showthread.php?t=845911&page=52")

I don't know if this will work with a TX2z or just mess you up further.  It's a thought anyway.

---

### Post by Vincent_Lin on 2009-02-16
Thanks.

I was looking at pulseaudio setup/configuration for the last hour or so.  This is new stuff to me.  So I will look it up and study further.

Thanks again.  It feels great someone is taking of me :).

Vincent

---

### Post by eccuser on 2009-02-17
Hi Vincent and everyone,
I hope this post helps, regarding ubuntu 8.10 interpid on the HP tx2z touchsmart tablet pc.
thanks god, i got everything working now and fully functional.
regarding the speakers and sound muting issue, find below my /etc/modprobe.d/alsa-base and my /etc/modules 

nixnub@nixport:~# cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=toshiba


nixnub@nixport:~# cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp



hope this helps :)

---

### Post by eccuser on 2009-02-17
Vincent,
Could you please post the scripts you made for the tablet rotation ?
i can create gnome new buttons for executing these scripts.
just please post these scripts :)
thanks and best regards,
:)

---

### Post by eccuser on 2009-02-17
Hi Vincent,
Also one more issue harrasing me, it's related to mplayer
when i try to run any movie in mplayer, the player keeps flashing and the screen flashes, i think it's related to the vo (Video output) part in mplayer configuration, or there might be some ATI config i must do
Any hints ?
p.s: nixnub [ at ) gmail d0t com is my m4il if someonen needed help :)

Thanks and best regards,
nixnub

---

### Post by Vincent_Lin on 2009-02-17
Hi nixnub,

These scripts are in Favux's HOWTO, first post

[http://ubuntuforums.org/showthread.php?t=996830&highlight=Howto+HP+tablet](http://ubuntuforums.org/showthread.php?t=996830&highlight=Howto+HP+tablet)

The other two are one liners to enable and disable touch, like this

xsetwacom set touch touch off
xsetwacom set touch touch on

Hope this works.

Vincent

---

### Post by eccuser on 2009-02-17
Vincent,
Sadly these scripts did not work , i am getting this error when i run the command xrandr -o left

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

any hints ?

btw, did your sound work ?
nixnub

---

### Post by Vincent_Lin on 2009-02-17
Right.  I happen to know this one.

After your fglrx is installed, you have to run, at command line like this, found at ati unofficial wiki site.

sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

This enables xrandr for your fglrx driver.  Restart gdm or reboot then these scripts shall work.  

I have not found the solution to my sound problem just yet.  I suspect it is caused by new fglrx from ATI(not the one enabled from Hardware Driver), because as I stated in prior posts, I tried to install the whole thing for a couple times, and sound stopped working every time after I installed fglrx driver.  Yet, without the new driver, all the stylus and touch goodies would not work properly.

Cheers,

Vincent

---

### Post by tempo500 on 2009-02-18
hi, i cant confirm the fgrlx sound issue. cause the ati was the first thing i did. sound worked fine a few days until i started to change settings for the skype capture problem. i am still working the next few days untill i can look into this sound issue... but i am a graphics guy not an administrator.... besides ubuntu login chimes and stuff work. after login, nothing. i have pulse installed(it worked fine with it) ubuntu 64bit 8.04.

---

### Post by Vincent_Lin on 2009-02-18
Dear all,

I have to say that I am really frustrated about this audio situation.  OK, here it is what I have:

1. It is definitely related to the line put in /etc/modprobe.d/alsa-base documented in the first post of this HOWTO:
options snd-intel-hda model=toshiba.

2. Any adjustment of sound setting at alsa-mixer, say I change Front Speaker volume setting, sound output stopped following some loud static sound.  Then it is all dead.

3. When I installed gstream codec pack, say bad or ugly, sound output stopped.
4. now the bizzard part - if the sound stopped when the file alsa-base has this line mentioned above, all I have to do is to comment it out and reboot, and sound will come back after boot.

5. If sound stopped when the line is commented out, all I have to do is to edit the file and un-comment that line, and the sound output comes back after reboot.

How bizzard is that?  At least I can have sound working at will now.  And after some of the applications are all installed, I will make sure that sound is there and DO NOT TOUCH alsa-mixer in any way.

Other than this, I pretty much have all I want - wireless, screen rotation, and stylus/touch on and off at will.  I might be encouraged to play with finger-print scanner for a while.  Nyhh, maybe not for a while.

Cheers,

Vincent

---

### Post by the-root on 2009-02-24
Hello, I am about to purchase this laptop but I had two questions that I couldn't easily answer.

First, what is the wireless chipset for the N w/ Bluetooth? (If someone could post their whole lspci -v that'd be nice for everything). Also if someone could please verify that this wireless chipset works with Ad-Hoc networks, I would be so obliged. It is a main requirment of a laptop/wireless chipset for me, because I need to wifi tether to my cellphone when I'm on the road for work.

Secondly, Does the fingerprint recognition work at all? Not necessarily a deal breaker but i couldn't find it mentioned anywhere..


Thanks everyone, I really appreciate it!

---

### Post by tempo500 on 2009-02-25
hi, i got my sound working again. pulseaudio was messing something up. i removed some pulse packages, but probably not all of them. i deleted everything inside /etc/asound.conf. changed the  /etc/modprobe.d/alsa-base back to the intel thosiba, like the first page of this thread. i even removed all entrys in the /etc/modules file except fuse and lp. so sound is back ill try the skype capture again.... phil

---

### Post by the-root on 2009-02-25
Can you post the output of lspci -v ? It would help me a lot, thanks.

---

### Post by tempo500 on 2009-02-26
here you are... besides the audio capture does not work! i tested it with the gnome sound recorder, checked all volume controls, the sound preferences all use the alsa - advanced audio system.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d2200000-d23fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d1200000-d21fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3045
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3045
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0000000-b00fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3045
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 6038 [size=8]
	I/O ports at 604c [size=4]
	I/O ports at 6030 [size=8]
	I/O ports at 6048 [size=4]
	I/O ports at 6010 [size=16]
	Memory at d2409000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2408000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2407000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2409500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2406000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2405000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2409400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6000 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_acpi, ata_generic, pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2404000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=256]
	Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2200000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 1380
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-73-ff-ff-00-49-c5
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

### Post by Vincent_Lin on 2009-02-26
tempo500,

My installation of 8.10 64bit on this tx2z always loses sound after I installed tuxpaint.  So, if you don't mind, could apt-get install tuxpaint and see how it goes?  A reboot is required.

Before that, can you give me the setup of your working computer?

1. These files /etc/modprobe.d/alsa-base, /etc/asound.conf, 

2. markbuntu mentioned that there is a way to stop pulseaudio and start it up in verbose mode.  These commands all run in a terminal.  After a reboot the pulseaudio server should start as usual.
  killall pulseaudio 
  pulseaudio -vvv

Then you run some applications with sound output, such as vlc, rhythmbox, then close them.  Could you post the verbose log generated on your terminal?

3. Can you check your Synaptic and search the following terms and see what packages are installed?
   1). pulseaudio - I have pulseaudio, pulseaudio-esound-compat, pulseaudio-module-hal, pulseaudio-module-x11, libpulse0, libpulsecore5, gstreamer0.10-pulseaudio, and other utility like ackages installed.
   2). libsdl - I hae libsdl1.2debian, libsdl1.2debian-all.libsdl1.2debian-alsa, installed.  
   3). alsa - I havee alsa-base, gstreamer0.10-alsa, libasound2, libesd-alsa0, linux-sound-base installed.

I would appreciate that very much.

Thanks.

Vincent

---

### Post by ubuwan on 2009-02-26
Was hoping to follow on the coat tails of this thread, but the initial installation of ubuntu 8.10 intrepid on my new HP tx2z failed to complete.  Started a new thread for that problem here:  [http://ubuntuforums.org/showthread.php?t=1081529]("http://ubuntuforums.org/showthread.php?t=1081529")

Any pointers would be appreciated!

ubuwan

---

### Post by tempo500 on 2009-02-26
ok. for step two, im sorry im finished with pulse audio. the only reason i messed around with it was because of flash, which works now just fine without pulse. ill install tux paint and report back, but just because i really dont think i will mess up my sound with a graphic program... but what do i know... sound capture is not working at all, no matter what device i use in the sound preference. oss at least gives me some cracking sound... by the way, a fresh ubuntu install and changing the alsa-base file to intel thosiba works just fine! i somehow think sound even worked out of the box after installing, but i am not sure any more. greets, phil

---

### Post by Keeper of the Keys on 2009-02-26
On my tx2z I used modconf instead to set the "model=toshiba" parameter for snd-intel-hda, I also added myself to the "audio" group and ever since then it seems to work fine, I did have the static once or twice though but now it's fine.
I do have to point out that I am running jaunty amd64.

Other than that, what I have working:
Video - only "radeon" driver, there is some problem with fglrx at the moment, I tried the latest version from AMDs website but that also seems not to work.
Networking - wireless/wired/bluetooth all work beautifully (with the propriatary firmware), also the switch to toggle wireless works.
Pen input - work fine
Touch - not yet, I just patched the wacom driver with the patch mentioned above and will be trying that shortly.
Touchpad - works fine, only complaint is that the "scrollbar" only works if you touch the 1 line of knobs most to the right, if you touch more it doesn't but I guess I could change that somewhere will have to look into it.
Fingerprint - the scanner works and the program to scan/enroll (pam_fprint_enroll/fprint-demo) works, but I had some problems with actually using it for authentication, will have to look at that later, I did have to change the group of the fingerprint scanner device to plugdev.
Special keys - mute/vol up/down work, haven't played with the rest.

Edit:
Well I just tried the - I hope - patched wacom drivers but it still does not seem to work... every time I touch the screen with my fingers the pointer 'jumps' to the upper left corner....

Oh and by me waking up from hibernate I did not need to do the reset thing mentioned above....

---

### Post by Favux on 2009-02-26
Hi Keeper of the Keys,

> every time I touch the screen with my fingers the pointer 'jumps' to the upper left corner....
That kind of behavior generally means that Xserver isn't getting any input.

---

### Post by tempo500 on 2009-02-27
hi all,

capture is working again! sound preferences-> everything to alsa sound.
volume control -> options tab -> input source is fornt mic
recording tab -> 
capture: levels to 0%. mute icon should not be enabled.
digital: 90%
playback tab -> front mic boost to 100%
line in and mic boost to 0%.
it works, but is not ideal, i dont think the levels in the volume control where meant that way. there a great deal of static if the levels are not set right. 

i wanted to install tux paint but got chickenshit. this laptop is my office/communication computer... so i cant really play with it until it breaks. but ill try to give you as much info as i can. greets, phil

---

### Post by Vincent_Lin on 2009-02-27
Dear all,

I have a very interesting find.

Though I don't have sound at all, regardless of the 
options snd-intel-hda model=toshiba or 3stack or 3stack-dig, etc...., as I used to disable pc speaker as depicted in the first post of this thread, I did not touch that for this installation.  So I still have pc speaker sound.

Here is the thing: 

I have vlc running playing my Cars ripped from handbrake.  I switched to console 1 by Control-Alt-F1 and started to see some of my configuration files.  By accident, I pressed Down-arrow to bring up prior commands, when there no command in the queue.  So the machine BEEPed, listen to this, and the sound of the playing VLC CAME UP ALIVE!!

So I switched back to Control-Alt-F7, and watched my beautiful Cars video, and messed around with mixer, pulse-device-chooser, gedit, etc...  

Sometimes sound died again when I touched volume or something, I switch back to the first console and pressed down-arrow to beep, as to wake the sound up.

What is going on here?  

1. a volume change in mixer should not affect any configuration of ALSA, PULSE, Llibsdl, esound, etc..., but it could kill the sound.
2. a wake-up beep by pressing down-arrow brings back all the sound.

Is my machine defected in some way or what?  Has any one  heard or seen such "phenomenon"??

Thanks again.

Vincent

---

### Post by Vincent_Lin on 2009-02-28
While setting up the rest of configuration of this tx2z, I found that ATI release yet another version Catalyst, version 9.2, on 2/19/2009, with the fglrx driver version 8.58.2.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English&rev=9.2&ostype=](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English&rev=9.2&ostype=)

With the high expectation, I tried this fglrx, compiz, and wacom driver together.  But, unfortunately this combination still does not work.

When compiz is activated, the keyboard, mouse, screen, stylus all rotated fine, using Favux's script in his howto in this thread

[http://ubuntuforums.org/showthread.php?t=996830&highlight=howto+HP+tablet](http://ubuntuforums.org/showthread.php?t=996830&highlight=howto+HP+tablet)

except that X11 would not accept mouse and stylus click.  

To test it further down, xrandr rotates the screen, but clicks from stylus, touch, and touchpad fail, as if X11 would not accept mouse and stylus clicks, when xrandr is run.  

So that's it.  fglrx even the newest released version from ATI, would still not work well with compiz in terms of xrandr.

Please note that, when compiz is disabled (without desktop effects, that is), rotation and xsetwacom commands to set rotation properties for stylus, touch and eraser all work as advertised.

Cheers, 

Vincent
PS. It really feels to me that, on this tx2z of mine, the circuit to Altec Lansing speakers is broken or something (would mute itself when the max volume is requested.  When I ask it to beep at console and it will bring the muted speakers back alive, where, no configuration, etc... is changed.)

---

### Post by abramdemski on 2009-03-01
> **Keeper of the Keys said:**
> On my tx2z I used modconf instead to set the "model=toshiba" parameter for snd-intel-hda, I also added myself to the "audio" group and ever since then it seems to work fine, I did have the static once or twice though but now it's fine.
I do have to point out that I am running jaunty amd64.


Keeper, could you possibly post a more explicit version of these instructions?

[Currently a few system sounds like the loud beep and the startup ubuntu noises work for me, but no sound on applications (I've tested on youtube and zsnes, to be specific). Is that the situation for other people that are having sound troubles?]

Oh, and thanks to everyone! This thread has been very helpful!

---

### Post by abramdemski on 2009-03-03
Well, I got my sound working now (by starting over, and skipping the sound fix mentioned in the instructions... sound appears to work better w/o that fix for me). However, suspend/hibernate does not work correctly: the *graphics* settings appear to be bad when ubuntu comes back up. Is there anything I can add to reset the graphics, similar to the 8042.reset that was recommended for the keyboard & touchpad issue?

Thanks,

Abram

---

### Post by abramdemski on 2009-03-03
Sound stopped working today... what would cause it to suddenly stop after having been working? The modprobe option from the initial post hasn't fixed it.

---

### Post by abramdemski on 2009-03-03
Interesting note-- I found that if, directly after starting up, I say:

```
 sudo /etc/init.d/gdm stop

```

I get a screen of messages from startup, including a message that tells me that the line I added to alsa-base (which I copied directly from the first post) is a bad line. Good to know! But why?

---

### Post by abramdemski on 2009-03-04
I got it working by adding "options " to the beginning of the line, making it match the other lines in the file. So it seems that rather than

```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base
```

one should use

```
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base
```

(or just edit the file directly like I did).

---

### Post by Keeper of the Keys on 2009-03-05
Sorry for my longish absence busy busy....

I now switched back to intrepid because jaunty was just not stable enough, though I am using the kernel from jaunty.

Concerning my remark earlier: instead of echo'ing (ie. adding) the "options model=toshiba" line to the end of /etc/modprobe.d/alsa-base I basically created a file /etc/modprobe.d/snd-intel-hda

I did not do this "by hand" but instead used a tool called modconf, I first unloaded the snd-intel-hda module using either rmmod or modconf (you need to stop the sound sub-system to be able to do this) and then when I reloaded it through modconf I passed it the "model=toshiba" argument, like this I make sure that the configuration is saved in the place where the system prefers/expects it.

---

### Post by tsao on 2009-03-09
I chose to enable the closed source &#8216;fglrx&#8217; driver for the ATI chipset using the &#8220;jockey&#8221; tool that comes with Ubuntu. Just click the icon in the notification area and choose to enable the driver, and the rest of the install is handled automatically.

How do I do this? I'm new to Linux and don't know how to do that or enter the codes and such, any guide that'll show me those basics? Or can someone dumb down installation for me? I know how to install ubuntu but not to get the touchscreen working. Also I ran the test or whatever ubuntu in it and I can't get the wireless to work. The wireless on off appears to be off, it's orange, and it won't turn on.

---

### Post by Vincent_Lin on 2009-03-09
Tsao,

I am not sure what you want to do by reading what you wrote.

If what you want to enable are:

1. compiz - then you would simply right click on desktop and choose the bottom one "change desktop background" and select Visual effect tab, and select normal or extra effects.  This would do it.  Finer control of compiz effect would need extra package such as compizconfig-settings-manager.  You can go to synaptic package manager (mainmenu->system->management is where to go).  It will be installed at mainmenu->system->configuration.

2. wireless - my wireless is enabled by stock installation.  But, you need to install network-manager for easier management of netowrking.  Same place to install network-manager and it will show up at notification area.  Right-click that network-manager icon to enable wireless networking, and left-click it to choose the wireless router to use.

3. If tablet functions with touch is what you want, you would have to go to the first post and follow the instructions(every step) to install watcom driver.  Since ubuntu stock fglrx driver would not support rotation and tablet functions properly, you would have to go to ati website and download fglrx drivers (9.1 or 9.2)and follow the instructions to install it.  fglrx driver also requires you to run this line at commandline (open a terminal and run it): "sudo aticonfig --set-pcs-str="DDX, EnableRandr12,TRUE" before you restart your computer or restart your X server.  Then you can copy the scripts described in this thread 
[http://ubuntuforums.org/showthread.php?t=996830&highlight=tablet](http://ubuntuforums.org/showthread.php?t=996830&highlight=tablet)
and run them at will.

There are still limitations what this combination of drivers/packages/etc can do - such as rotation while compiz is enabled would not run properly, but we can wait a while when ati drivers are better in next release :).

You can post questions for details of what I just wrote and I will try to help.

Vincent

---

### Post by Vincent_Lin on 2009-03-09
Dear all,

Before I send my tx2z in to HP for repair or replacement(?) for my speakers, I want to make sure that I am the only one that has this problem.

1). I am using options snd-intel-hda model=toshiba
2). I did not blacklist my pcspkr (so pc speaker beeps, obviously I need it to bring back my sound)
3). My speakers will mute itself when in loud volume scenes while watching movies.  A PC speaker beep will bring back the sound.  Or a reboot.
4). headphone is not working (no sound at all).  Speakers would not stop the sound when I plug in the headphone (no auto-sensing either).

Please confirm that I am the only one that has the tx2z faulty in this way.

Thanks.

Vincent

---

### Post by Favux on 2009-03-10
Hi Vincent_Lin,

Some more sound "fixes".  Don't know if they apply except maybe to volume.  Some are interesting though, especially:
```
alsamixer -D hw:0
```
The thread is in the Jaunty testing:
[http://ubuntuforums.org/showthread.php?t=1090643]("http://ubuntuforums.org/showthread.php?t=1090643")

I hope you can get something useful out of it.

---

### Post by Sashin on 2009-03-10
Does anyone know how Jaunty works on this machine?

Could someone please try booting the alpha 5 cd on this?

Is there a list on exactly what can and cannot work with this.
How compatible is the multi-touch with compiz's effects? What exactly can be done, cube rotation, scaling etc? Also does anyone know any applications that utilize the multi-touch (not single touch) as well as the pressure sense). And is the accelerometer compatible? Is there a way to have the screen auto-orientate? Also what about lightscribe and the fingerprint reader that could come with this, do they work?

---

### Post by Keeper of the Keys on 2009-03-11
@Jaunty on tx2z:
In my experience it was fairly ubstable and you will have to patch the wacom driver yourself.
I now run intrepid with the jaunty kernel and that seems to work fine though I sometimes have crashes/lockups which I think are related to pulseaudio.

@Vincent_Lin
If it doesn't even switch to your headphones that does look suspicious...
I have some nasty background noise when trying to record (a high beep in the background), but other than that my sound works fine.

General questions:
Does anyone know what keyevents are sent by the buttons on othe side of the screen (the tablet screen buttons) and how to bind them to something? I have been trying to find their keycode/event by catting various devices but to no avail....

Has anyone noticed the following: it seems that when I touch my screen in more than two places at once it goes of calibration and stays off until X is restarted... (ie. the mouse will show up several inches from my finger)?

---

### Post by Keeper of the Keys on 2009-03-11
BTW, does anyone know if the tx2z features tilt sensors or accelerometers?
/me is thinking about neverball and slapbook....

---

### Post by Sashin on 2009-03-12
It does.

---

### Post by Vincent_Lin on 2009-03-12
Dear all,

Just want to report the status of my tx2z.

Well, HP support did not help much, as they insisted on re-installing Vista (full restore) first to make sure that there is no software/driver issues, before they would admit that it might be a hardware issue.

Meanwhile, I was searching for a way to setup a button on gnome panel, which will beep when I press it (instead of opening a terminal and press down arrow).  I have to do this bacause this computer will be a family PC, and my 4 and 6 years old daughters will be using this computer all the time, mostly for drawing in tuxpaint, and maybe gimp later, who knows.  

Well, this part is fun.  

At first, I thought, humm..., "beep" might be the command/program to run.  It is, except that it is not installed by default.  So I apt-get install beep.  Now I have a beep program with options to control the pitch (frequency), duration(length of playing), plus some other options.  But unfortunately it would not work as a button.  It works in a console, eg, VC-1 (Ctrl-Alt-F1), and in a terminal, but it does not work as part of a gui program, such as the action of a button.    

Stuck!!  

So I searched google using the term "beep in linux gui" and the likes, and whola!  This thread came up.  

[http://ubuntuforums.org/showthread.php?t=671274](http://ubuntuforums.org/showthread.php?t=671274)

After a couple tries, the solution is to create an executable/text/script file, such file being the command line of gnome panel button.  The contents of this file is like this:

echo -e "\a" >/dev/console

So now when my speakers mute themselves, I simply click on this button for the beep sound, and the sound comes back, after I also reduce the volume of course.

If anyone knows how to set up command line of "beep" so that it can be used as a gnome panel button, please let me know.  I would like to setup this wake-up beep into bells like sound such as third interval "ding-dong", or forth or fifth.  According to man page of beep, it is do-able.


Vincent
Maybe I will play with Vista tomorrow night (I have restore DVDs, extracted from HD before I installed ubuntu on it) to make sure if the speakers/Mic are working properly under that "dark side".

---

### Post by markkupaakkonen on 2009-03-13
Hi guys,
I've got a keyboard problem. Lost it!

I installed Jaunty on my new new tx2 (the scandinavian model).
All went fine until I installed cellwriter. I lost my keyboard. 

A usb keyboard works so it is not a driver problem.

And this happened twice. First time I called HP customer service and they agreed it was a hardware problem, after I installed Vista back and the keyboard still didn't work. So they replaced the machine.

And I did all again, installed Jaunty (Ubuntu Studio), installed cellwriter, trained it, used it and lost my keyboard :o :(

Anyone have any ideas? I really don't think anymore it was a hardware problem first time either. It must be something to do with cellwriter...

What do you think?

Edit: okey, from hp forums found out that this seems to be a bios problem, need to update that, I guess
Yes, updating bios solved this, it has nothing to do with cellwriter...
Cheers

Markku

---

### Post by abramdemski on 2009-03-13
markkupaakkonen,

Really!

I lost my keyboard too, and likewise got a replacement machine! (I did not post to this thread about it, because I concluded it was not associated with Ubuntu.)

Could you link to the HP forum thread? My keyboard is working fine with the replacement, but just in case...

---

### Post by markkupaakkonen on 2009-03-14
@ abramdemski,

sorry haven't got the link on this machine. Found the thread from google with "hp tx2 lost keyboard" or something like that. My model is the scandianavian variant of tx2z, namely tx2-1050eo. According to HP support it is the same machine.

The funny thing was that according to these threads I found, the easiest solution to get the lost keyboard back is to shut down computer, take the battery out, wait for couple of seconds, put the battery back and restart. And you get your keyboard back. I tried that with this replaced machine, and it worked. The latest bios update howevwr fixes this problem alltogether. I also told the HP finnish support this, and they actually were not aware of it.

But now I'm running Jaunty on this and everything I need works beutifully.
There are some issues though, but I'm happy.

Cheers Markku

---

### Post by Favux on 2009-03-14
Hi everybody,

I thought you'd like to know that they are working on multi-touch.  Well at least considering how to start working on it.  Now that MPX is available.  Read this thread on the xorg mailing list:

[http://thread.gmane.org/gmane.comp.freedesktop.xorg/37777]("http://thread.gmane.org/gmane.comp.freedesktop.xorg/37777")

The link is from Tom Jaeger on his EasyStroke thread.

Hi Vincent_Lin,

Maybe this is why we couldn't find a separate input path for touch.  From the thread above:
> That's odd; perhaps they didn't get the right HAL properties added.
The N-Trig (multi) touchscreen on the Dell Latitude XT and HP Touchsmart
TX2 works out of the box for touch with evdev GIT HEAD.  (Clicking via 
screen taps requires a patch to map BTN_TOUCH to BTN_LEFT, though.)

- Chris.
-- 
Chris Ball   <cjb <at> laptop.org>

Which brings up the possibility of an experiment.  What happens if you comment out the touch "InputDevice" section and touch in "ServerLayout"?  Do you still have touch?  My 10-wacom.fdi only mentions stylus for N-trig.  So I'd think touch shouldn't work and maybe the stylus and eraser would be disabled.

---

### Post by Vincent_Lin on 2009-03-15
Favux,

I will try it later tonight.  According to the first post of this thread, I always delete 10-wacom.fdi after installation of wacom driver.  Does that matter at all?

It is good to know that multi-touch is being worked on though.

Thanks for your help.

Vincent
BTW, do you know a way to make /dev/console to be read/write for regular user automatically after log on?  My little trick to "beep" would not survive a reboot as it is created freshly after reboot as rw-x---x--- owned by root.

I have been playing with model=xxxxxxx option in /etc/modprobe.d/alsa-base, and some models allow higher volume than others.  A very strange behavior.  Headphone jack never works, no auto-sensing of course.

---

### Post by Favux on 2009-03-15
Hi Vincent_Lin,

I don't see why you would have to delete 10-wacom.fdi.  The xorg.conf should take precedence.  Early on it was thought there would be a conflict, but there isn't.  That's kind of what I was wondering, would touch be handled by HAL without the xorg.conf entry?  And is that what's happening somehow anyway?

Normally to make user writable I think it would be something like:
```
sudo chown yourusername /dev/console
```
and then maybe:
```
sudo chmod u+rwx /dev/console
```
But I don't know if that will work.  I'd be careful.

---

### Post by Vincent_Lin on 2009-03-16
Favux,

If I comment out touch in ServerLayout and the Device section of touch altogether, touch no longer works.

Hope this works.

Vincent

---

### Post by exophobe on 2009-03-25
Thought I'd chime in, just got a tx2z and vista 64 sent me running to ubuntu.  Anyway, the stuff in this thread has been remarkably helpful, I've got the thing probably 99% of the way I want it, however, there are a couple things I'm trying to figure out.

First, I'm using the rotate stuff, works great.  Due to the lack of n-trig palm ignorance, I have set it to turn off touch when it rotates to tablet mode keeping that from being a problem, then turning it back on when swapping back to laptop mode.  *thumbs up*  Crazy thing is that it's almost smoother than doing it in Vista -- and certainly a lot faster.

The updated sound line seems to resolve the sound issue (where "option" is added at the front of the line).  I wasn't able to get anything more than a few minutes of sound out of it before using the option command.

Someone asked a couple posts ago about the buttons on the side of the screen.  It'd be cool to bind the rotate button to the rotate script, but if I press the button (any of the three) with xev running it doesn't give me any output.  I found Favux's post on setting the Q button up on a tx2500 or 2000, but I'm not sure if I'll cause problems with the other keys if I go digging where I don't know, any pointers?

The other issue I've run into is that the touch-screen/stylus input doesn't seem to "wake up" when the machine comes out of hibernate. I have a fully operational machine, just no tablet input.

The last thing, though there shouldn't be much use for it, anyone know if it's possible to rotate the mouse input with the screen?  It seems to be a function of the wacom driver, so I don't know if the convenience is even worth what it might take to get that going.

Again, I can't thank you guys enough, I'd still be trying to get the tablet to work if I hadn't found this.  ubuntu studio 64bit is ridiculously more stable than vista 64, at least so far as this little machine is concerned.

BTW, it doesn't seem to be necessary to mess with the .fdi file, I actually had more trouble when I did.

---

### Post by exophobe on 2009-03-25
The following is what I've got going on this machine, with the sequence of getting there.  Whenever it asks for a reboot, it seems to be a good idea to give it one.

[LIST=1]
[*]Hit esc during boot, in the BIOS change the fan so it's not required to run always.
[*]Partition drive, assign at least 1.5x your RAM. I have 3GB, I set swap to 5GB.
[*]It's best if you plug the machine into ethernet where it can obtain a DHCP license at this point, makes the rest of this go a lot smoother.
[*]Install UbuntuStudio, AMD64.
[*]Install Proprietary Drivers (ATI and Broadcom STA) through "jockey".
[*]Perform System Updates (as of this writing it was something like 270 updates).
[*]Install network-configuration package -- available in the synaptics package manager list after updates.
[*]Install Mayrhofer Wacom driver (used his version pre-compiled with the patch) -- [available here if you trust his package]("http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_amd64.deb").
[*]Download and install latest ATI Radeon HD 3200 driver from the ATI site ([http://ati.com](http://ati.com)).
[*]Issue command to enable randr with ATI driver "[COLOR="Lime"]sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"[/COLOR]".
[*]Modify xorg.conf (see attached).
[*]Turn off internal speaker beep (not required, but - [COLOR="Lime"]sudo echo "blacklist pcspkr" >> /etc/modprobe.d/alsa-bas[/COLOR]e.
[*]Update modprobe.d/alsa-base to make sound work (in my experience has to be done as root -- probably not in the audio group?) "[COLOR="Lime"]sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base[/COLOR]".
[*]Create scripts (see attached). 
[*]Add line to kernel to allow hibernate/wakeup -- I use vi, feel free to use whatever editor you like.
[**][COLOR="Lime"]sudo vi /boot/grub/menu.lst[/COLOR]
[**]*scroll down in the file until you get to the kernel list, it'll be after the "[COLOR="Lime"]## ## End Default Options ##[/COLOR]" line*
[**]Add "[COLOR="Lime"]i8042.reset[/COLOR]" to the end of your active kernel,the default line likely ends with "[COLOR="Lime"]ro quiet splash[/COLOR]" 
[/LIST]

I think that was it.  Will attach all the appropriate links and stuff in a little bit (tomorrow).  Can one of you guys give this a sanity check?

I haven't tested the webcam or mics, and I'm trusting that the bluetooth works, even though I haven't proven it.  Card reader is perfect, wireless is mostly perfect, the touch stuff works very well.  As far as the audio goes, works fine, even auto-switches when I plug in headphones.

It took me a few installs to get it right.  Don't try wi-fi until the network-configuration package is installed, it's just gonna make you mad -- especially when you see how easy it is with the network config package installed.

Thanks again for all the work that's gone into this topic to date.

---

### Post by Attila_fdd on 2009-03-25
Could i use intrepid amd64 instead of ubuntustudio?

---

### Post by exophobe on 2009-03-25
I got through the install okay, studio went a little bit smoother for some reason.  Presumably it would work just as well so long as you go through the install right.  As I understand, studio is just intrepid ibex packaged with audio/video production apps.

At least you wouldn't have to install the network configuration package manually.

---

### Post by Keeper of the Keys on 2009-03-25
I have intrepid running without too many problems.
I never tried studio so I can't tell you if there is something substantially different...

On my install I am now not using the STA (wireless) drivers anymore, I am just using whatever is in the kernel because I got the impression that I was having nasty system freezes when using said driver and whatever is built-in to the kernel (wl) is anyhow working fine....

(Description of said freezes: caps-lock and num-lock lights flash and the system ceases to respond to any input even the 4-finger salute).

Now I have been unsuccesful at finding what kernel module to use for the motion sensor, does anyone have pointers for me?

Also disabling pcspkr is of course not mandatory... some people like it.

---

### Post by Attila_fdd on 2009-03-25
exophobe, I hope you will post soon a complete guide to solve most of the problems, like you did in your installation

---

### Post by Favux on 2009-03-25
Hi exophobe,

The old hotplug commands were ctrl-alt-F1 and then ctrl-alt-F7.  Sometimes my wacom doesn't come up after suspend and that's what I use.  ctrl-alt-F1 by itself sometimes works for me.  It just hops in and out of the terminal.

---

### Post by exophobe on 2009-03-25
I'll be damned, that worked. Weird that it requires you to jump around like that.

Keeper - I think there might be something different between the two as far as the wireless driver or implementation goes (don't know too much about the back-end of it).  If I remember right, "regular" 8.10 came through fine without the STA driver, but wireless just sort of disappears when you're running studio without that driver.

I'm not having any luck finding anything on adjusting that internal beep, starting to think maybe it's not possible, unless anyone else knows of anything.

---

### Post by exophobe on 2009-03-26
This should be it as far as the xorg.conf and rotate script go.  I've updated the tutorial to include the information as I used it.

Again, none of this stuff I've written down would even exist if it weren't for the guys already here working on it a couple months ago, I just dug through it a few times.

Though I am curious if Vincent's sound ever came back.

By the way, if anyone has any pointers on the wireless divergence between ubuntu and studio, I'd be interested in a fix. :)

---

### Post by Keeper of the Keys on 2009-03-26
The internal beep *should* be the pcspkr module, so if you blacklisted it and rebooted (or did "rmmod pcspkr" as root or sudo) you should be fine....

[offtopic]
Always set a root password (sudo passwd) eventhough Ubuntu doesn't have you do it, otherwise you can get a rootconsole in recovery mode without being promted for a password...
[/offtopic]

---

### Post by Attila_fdd on 2009-03-26
all works fine except for the rotate script... when i launch it the desktop rotate but the input (mouse touch...) does not work well (plus the screen size is cut to half of the monitor)

PS: how can i handle right click with touchscreen (not pen)? could we setup like windows (hold touch on the screen)?

PPS: sometimes keyboard and mouse/touch stop working, the system is not freezed but i cant click (just move mouse pointer) or use keyboard to reboot, same with usb keyboard/mouse

---

### Post by exophobe on 2009-03-26
The mouse thing is what I'm wondering.  Wacom driver doesn't control the mouse, so I don't know if you can rotate it with some other driver.  

I don't know much at all about the touch functions, there's probably something in that driver to manipulate that, I haven't had time to read into it too deep.

I'm not sure what you mean by sometimes it stops working.  Is that after hibernate, or just randomly, like you'll be using it and it stops mid-action?  If it's after waking up from sleep/hibernate/etc, do the CTRL-ALT-F1/CTRL-ALT-F7 thing that favux described.

What I'd like to is get into doing multi-touch stuff, since the screen can recognize it, but there are much smarter people than me already working on that. I hope. :)

---

### Post by Attila_fdd on 2009-03-28
about multitouch functionality i hope we could get it soon! I think we cannot do it before xserver 1.7 on ubuntu 9.10 where MPX will be enabled.

About my notebook stops receiving input it is completely random i think.
I start using ubuntu, write documents, surf the web, listen music... after a little while (randomly) it stops to receive inputs like click and keyboards input (i can move the mouse pointer with touchpad or fingers or pen). Could it be compiz fusion i have enabled by default? i'm trying to disable it and works without that functionality...

PS: the new fglrx open drivers which supports 3d for hd3200 (i found in some online news) are available for intrepid 8.10?

---

### Post by tarjxvf on 2009-03-31
It's great to have touch screen working. But it seems that it's still not pressure sensitive. I've tried in Jarnal, Gimp etc., none of them  detects the level of pressure. However, there was pressure sensitivity in the "Windows Journal" of Windows 7 (my machine is dual boot). 

Hopefully I'm not too greedy...

---

### Post by Vincent_Lin on 2009-04-02
Guys,

I have not checked this thread for a while.  Here is the development on my end.

1. exophobe's post of setting up this tx2z with ubuntustudio64 is exactly what I have done to make this machine work.  

2. touch-sensitive is there.  You simply have to enable it in applications such as gimp and/or inkscape.  Search this forum and the instruction is there.

3. I have not tried finger-print scanner, nor I have the intention to do so.

4. Webcam works fine.

5. The only problem, for me anyway, is the sound issue I am experiencing.  Briefly, I set the options line with model=toshiba, and with or without disabling pc speaker.  My speakers would go mute when the volume is set to high.  For example, a fast action scene while playing DVD will simply mute it, after it has been playing fine with normal volume.  I would have to lower the volume, and issue a pc speaker beep to bring the sound back.  Headphone jack would not give me sound to headphone at all, nor auto-sensing.

What I did?  I bought another SATA 2.5" disk and restored Vista (HP sent me a set of recovery DVDs) onto that disk (with issues, but that's another story that no one in this forum should care).  And Vista plays my DVDs through speakers loud and clear.  Headphone works and auto-sensing works.  NO ISSUES!!  I am shocked.

In this regard, I have to rule out hardware defect, though I wanted it to be so much.  I would put back my ubuntustudio64 disk this weekend, but I don't really have much to say or to try at this moment.

Hope this information interests someone.

Cheers,

Vincent

---

### Post by Favux on 2009-04-02
Hi Vincent,

I ran across this at the Jaunty forum.  It was about Ubuntu Studio on Jaunty.  Apparently for the last several versions of Catalyst ATI hasn't been enabling "fglrx" to handle the rt kernel.
> **markbuntu**
The rt kernel is very useful and stable in 8.04. The only issue I have with it is that the newer fglrx drivers from ati are missing the rt patch and so do not work with it. But this is a very minor problem.
The link is here:
[http://ubuntuforums.org/showthread.php?t=1107537&highlight=studio+rt]("http://ubuntuforums.org/showthread.php?t=1107537&highlight=studio+rt")
Could this be the problem?  Or part of it?

---

### Post by Vincent_Lin on 2009-04-02
Favux,

Thanks for the prompt reply.  I went to that thread but it does not seem to be related.  Besides, expophobe reports that his tx2z is running fine with speakers and headphones, etc..., with the exact same steps to setup ubuntustudio64 on this tx2z. 

I am still puzzled a huge bunch of it.

Vincent

---

### Post by tarjxvf on 2009-04-03
> **Vincent_Lin said:**
> 
Haven't tweaked much yet - 
        - X rotations, 
        - disable finger touch at will (when drawing using pen only)
        - While we are at this, what is the way to enable middle-button mouse action on the pen?  I have an application that uses all three buttons but I don't know how/where the middle button is.  Through pen control, that it.
        - handwriting recognition stuff (read somewhere that it is compared to the mechanism that MS offers).
Vincent

Have you had any success with any of these? I think "disabling finger touch at will (when drawing using pen only)" is important, otherwise, jarnal/xournal is unusable, and keeps rolling down when I try to write something in it. Also, it would be very nice if we could get those quick launch buttons to work. Handwriting recognition will  absolutely be a big plus, but I don't expect it's there, especially for Chinese characters which I'm interested in.

---

### Post by tarjxvf on 2009-04-03
> **Vincent_Lin said:**
> Guys,

I have not checked this thread for a while.  Here is the development on my end.

2. touch-sensitive is there.  You simply have to enable it in applications such as gimp and/or inkscape.  Search this forum and the instruction is there.

Hope this information interests someone.

Cheers,

Vincent

Yes, indeed! Both gimp and xournal can detect pressure sensitivity (after enabling corresponding options). Thank you for your help!

---

### Post by Vincent_Lin on 2009-04-03
Good to know pressure-sensitive is working for you.

I just signed up to ALSA user mailing list hoping that someone would have solutions to my sound problem.

Vincent

---

### Post by tarjxvf on 2009-04-03
I haven't found any problem with my sound yet, though I haven't tested multimedia very much in Ubuntu.

There is this one very annoying problem, which I don't know if you guys also have: when you move the stylus close to the touchscreen, and put some of your fingers on the touchscreen, then when your finger moves, the screen also moves, as if the fingers are dragging the screen.  This is a common problem in firefox, xournal, jarnal etc. And it becomes VERY annoying if you try to write something in jarnal/xournal. 

Isn't the touchscreen supposed to be turned off if the stylus is close to the touchscreen (the so called proximity detection)?

---

### Post by Vincent_Lin on 2009-04-04
I am trying not to open another thread for my problem.

In ALSA project site, there is a small program written in python called HDA Analyzer - 
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

that,according the page, in an interface to access raw HD-audio controls.

But, when I downloaded this thing and tried to run it, it failed - it complained that either no HDA codecs were found, or no privilege for some files/devices.  Yet, I ran it with sudo.

Can someone help to explain what I am dealing with?  Thanks.

With my machine, /dev/snd/control* is there, but /dev/snd/hwdepC*D* is NOT there.

And what is HWDEP option for compiling alsa?  Should I download source codes and try to compile it?

Thanks again.

Vincent
Here is the output of the program:
-------------------------------------------------
girls@girls:~$ sudo python run.py
[sudo] password for girls: 
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
girls@girls:~$ sudo python run.py
Creating temporary directory: /dev/shm/hda-analyzer
Downloading file hda_analyzer.py
Downloading file hda_codec.py
Downloaded all files, executing hda_analyzer.py
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.
-----------------------------------------------

---

### Post by Keeper of the Keys on 2009-04-12
Here's a small update where I am standing...

I just dist-upgraded to jaunty because I wanted to try something, sadly the better n-trig support that supposedly should be present is not.

I tried if the dev version of the wacom drivers (0.8.3 from debian) would do better but they also just produce a totally not calibrated Stylus and no response to touch (when allowing the drivers to autoconfigure, when setting them through xorg.conf it seems to segfault causing X not to be able to start), I guess I will have to manually run the patch provided by Rene Mayrhofer...

Other than that I discovered that the "mediasmart"-button (the button on the side of the screen with a swirl on it) seems to cause a (keyboard) event, when doing cat /dev/input/event5.
It seems that normal keypresses, the volume/mute buttons and also the screen being closed/opened cause events on this evdev, the rotate button and the 'sun' button don't seems to get any response on any of the events.
Though pressing the swirl is registered by system no keypress seems to be associated with it...

I haven't had any major trouble with my sound (after setting model=toshiba) so Vincent_Lin maybe your model is defective?
Things I did notice about the sound:
- When you have headphones plugged in and you unmute the system sound in sent to both headphones and speakers, so apparently headphone detection and speaker disabling is done in software...
- When using mplayer instead of totem the system would sometimes get stuck completly, this I think has to do with pulseaudio...

[edit]
I noticed that there is a bit of response to touch, it gets treated as a double click, ie. if I place the cursor over an item and then touch the screen anywhere that item is opened.
[/edit]

---

### Post by Keeper of the Keys on 2009-04-13
A few updates:
* Using the default wacom-tools from jaunty and with the Stylus defined in xorg.conf (as in the xorg.conf files posted above) provides a working stylus input, touch whether defined or not does not work.
* Using the debian wacom-tools crashes Xorg
* I tried patching wacom-tools (0.8.2) on my own (based on the patch file provided for wacom-tools 0.8.1 by Rafi Rubin [here]("http://ofb.net/~rafi/latitude_xt.html")) touch it compiled and installed OK touch is still not working (stylus input is working fine though).
* In my current situation a touch event sends the cursor back to the left-top corner of the screen.

---

### Post by Favux on 2009-04-13
Hi Keeper of the Keys and Everyone,

I think the default wacom in Jaunty is now Timo's patched 0.8.2-2.  If so when you look at his 10-wacom.fdi you'll see he only set up N-trig for stylus:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
```
So you would need to modify it to something like:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <append key="wacom.types" type="strlist">touch</append>
       <merge key="input.x11_options.Button2" type="string">3</merge>
       <merge key="input.x11_options.TopX" type="string">0</merge>
       <merge key="input.x11_options.TopY" type="string">0</merge>
       <merge key="input.x11_options.BottomX" type="string">9600</merge>
       <merge key="input.x11_options.BottomY" type="string">7200</merge>
      </match>
    </match>
```
Notice I added touch back in.  I also gave you a stylus button with R mouse click function.  And I put in the  calibration you have been using.  Since your coordinates for stylus and touch are the same, this should work.

I'm not saying this will work, although it might, but it's close to what you need.  For example since touch isn't the "input.x11_options.Type" it may not work.  With our Wacom tablets it doesn't because you can't calibrate it.  But our digitizer and touchscreen are on seperate input paths.  With N-trig the digitizer and touchscreen are the same thing with one input path so who knows?

Timo Aaltonen's patch for 0.8.2-2 to get it to work with HAL/.fdi files and the dBUS callout program has only been available for about a week.  We've found some problems and maybe even a solution yesterday.  So hang on.

Even with a fix you still might end up needing to modify 10-wacom.fdi for your N-trig's functions.

Edit:  Removed eraser since the Touchsmart TX2z does not have one.

---

### Post by Keeper of the Keys on 2009-04-13
Hi Favux,

I changed the fdi with the file you provided but this did not help.

I also contacted Rafi Rubin, he sent me his version of wcmUSB.c that he uses in wacom-tools 0.8.3.2 on Debian unstable, I tried building the debian package from source with that but it failed.

I then took the ubuntu package (which is version 0.8.2) and replaced wcmUSB.c with Rafi's version, I had to remove patch 104 for the build to succeed, but also with these packages it didn't work.

To summarize:
Stylus still works, touch still doesn't - it sends the cursor to the top-left corner of the screen.

[edit]
A totally offtopic question since you seem to know Ubuntu intimately, I have noticed that processes (at least ones involving sound playback) seem to be halted paused when the tty they are running in is not in 'focus' (ie. mplayer on tty1 and try to work on tty2 no sound unless mplayer is running as root, or totem in gnome [tty7] and try to work on tty1 again all playback paused), which is not behavior I would expect...
I am now trying to play around with the fdi file, is there any documentation about this?
[/edit]

---

### Post by Favux on 2009-04-13
Hi Keeper of the Keys.

OK, so many things going on that it's hard to separate them out.  First thing you need to know is that the 0.8.2-2 in the repositories isn't the standard linuxwacom package.  It's been patched by Timo Aaltonen to work with Xserver 1.6 and have HAL support and the callout program in the .fdi file that queries dBUS.  So that may be why your patch failed against it.  0.8.3-2 is apparently first linuxwacom driver package to support all of this and work in Jaunty.

I was worried about touch.  If you remove it from the .fdi file while running the new now default patched 0.8.2-2 do you get everything else?  Not just stylus, but eraser, the stylus button, and the coordinates?

We've found some problems with Timo's patched 0.8.2-2.  But rec may have solved it.  See:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952) and the link to the launchpad site.  Gali98's going to try rec's fix so I'm waiting on that.

So right now playing with the .fdi file too much may not be worth it.  There is some .fdi stuff in the Ubuntu wiki.  If you find a good manual let me know.

So it may not just be that you need Rafi's patch to be specific to the version of linuxwacom you use.  There could be multiple other problems.  And it may be that the HAL method still isn't going to work.  It sounds like (given all the caveats) that appending touch like eraser doesn't work.  The N-trig logic circuits on the screen edge aren't able to parse the usb input based on what the .fdi file is feeding them?

As for the sound thing I don't know.  It may relate to the runlevels mplayer and it's associated processes is setup for.  But that's a wild guess.

---

### Post by Keeper of the Keys on 2009-04-13
> **Favux said:**
> Hi Keeper of the Keys.
I was worried about touch.  If you remove it from the .fdi file while running the new now default patched 0.8.2-2 do you get everything else?  Not just stylus, but eraser, the stylus button, and the coordinates?

- The tx2z does not have an eraser (though I guess you could set the button on the pen to change functionality to eraser if you want to).
- The stylus button works (gets me the context menu).
- What do you mean by coordinates? That the cursor tracks the stylus like it should? If you do then the answer is yes.
All of this is just set in xorg.conf at the moment though...

> **Favux said:**
> 
So it may not just be that you need Rafi's patch to be specific to the version of linuxwacom you use.  There could be multiple other problems.  And it may be that the HAL method still isn't going to work.  It sounds like (given all the caveats) that appending touch like eraser doesn't work.  The N-trig logic circuits on the screen edge aren't able to parse the usb input based on what the .fdi file is feeding them?

You've lost me here....

> **Favux said:**
> 
As for the sound thing I don't know.  It may relate to the runlevels mplayer and it's associated processes is setup for.  But that's a wild guess.
To the best of my knowledge everything would be running on the same runlevel and nice levels, it is definitely not expected behavior and debian doesn't do it. I can't say if intrepid had the same problem as I wasn't playing around much in the text consoles at the time, now with jaunty and needing to fix stuff from time to time I am visting the dear old text consoles more often. But this is quite offtopic I guess I will look around elsewhere on the forum and possibly start a topic on the subject....

---

### Post by Favux on 2009-04-13
Hi Keeper of the Keys,

By coordinates I mean the stylus maps accurately to the entire screen.  I just used the coordinates glurgle used and I guess got from Rafi.

I didn't realize you don't have an eraser because the TX2000 and TX2500's do.  I was wondering about the functionality of the .fdi file not xorg.conf.  So I guess the eraser entry needs to be removed from the .fdi file.

---

### Post by Keeper of the Keys on 2009-04-13
Hi Favux,
So yes it maps properly.

I just now downloaded 0.8.3 from the linuxwacom project and compiled and installed it (I removed the ubuntu versions of the debs and replaced wcmUSB.c with Rafi's version).
After installing at first it totally did not map properly, after I replaced the .fdi with the one you provided it again did, touch is still not functioning so I guess further playing with fdi is what is needed I am also going to ask Rafi if he has a modified fdi by any chance.

I could be wrong about the eraser, maybe that just means using the stylus with the stylus button pressed or something, I don't know but I always thought that it just didn't have one...

---

### Post by Favux on 2009-04-13
Hi Keeper of the Keys,

The eraser is like a special button on the back of your stylus.  When you depress it it sinks into the barrel of the stylus.  This can give you pressure like the stylus tip in Gimp etc.  At least for Wacom it's another inputdevice section in the xorg.conf.

Good that you've got things working again.  Rafi sounds like the best bet to find out what's going on for N-trig.  Remember the LWP does not support N-trig.  It's 10-wacom.fdi does not have N-trig entries.  It is Ubuntu that's putting the N-trig entries into it's version of the 10-wacom.fdi.  I'm pretty sure anyway.  It may be coming upstream from Debian.

---

### Post by Keeper of the Keys on 2009-04-14
Rafi replied that in Debian/unstable either no fdi is used, or at least he is capable of working without having touched any fdi file...

I have been trying to play around a bit with the fdi file but so far have had no success, now I have to admit that I am just shooting in the dark when editing the fdi file, so I will try to first read some docs...

Edit:
I just removed the n-trig section from the fdi, this just results in the following:
- Stylus coordinates totally off
- Touch acts as (double) click where-ever the cursor is pointing at that time (not where touching)

---

### Post by Keeper of the Keys on 2009-04-14
Here is the output of hal-device, it seems that there are 2 or more n-trig devices so maybe that is something to go by, I have tried duplicating the provided n-trig section and chaning it to contains if1, but it seemed not to work. This could either be because the second device is the one that's just called "mouse" (in the by-path) and not the "event-mouse" that seems to do both...
 
```

11: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_hiddev'
  linux.device_file = '/dev/usb/hiddev1'  (string)
  info.category = 'hiddev'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/usb/hiddev1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.subsystem = 'usb'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_hiddev'  (string)
  hiddev.device = '/dev/usb/hiddev1'  (string)
  hiddev.product = 'HID 1b96:0001'  (string)
  hiddev.application_pages = { 'Unknown page 0xd0002', 'Unknown page 0xd0004' } (string list)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  info.capabilities = { 'hiddev' } (string list)

12: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_hiddev'
  input.x11_options.BottomX = '9600'  (string)
  input.x11_options.BottomY = '7200'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  info.category = 'hiddev'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/usb/hiddev0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.subsystem = 'usb'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_hiddev'  (string)
  input.x11_options.TopX = '0'  (string)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'HID 1b96:0001'  (string)
  hiddev.application_pages = { 'Unknown page 0xd0002', 'Unknown page 0xd0004' } (string list)
  input.x11_driver = 'wacom'  (string)
  wacom.types = { 'eraser', 'touch' } (string list)
  input.x11_options.Button2 = '3'  (string)
  input.x11_options.TopY = '0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  info.capabilities = { 'hiddev' } (string list)

(...)

33: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  linux.device_file = '/dev/input/event7'  (string)
  info.category = 'input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.product = 'HID 1b96:0001'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input7/event7'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.x11_driver = 'evdev'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.tablet' } (string list)

34: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  input.x11_options.BottomX = '9600'  (string)
  wacom.types = { 'eraser', 'touch' } (string list)
  linux.device_file = '/dev/input/event6'  (string)
  info.category = 'input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input6/event6'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.x11_options.TopX = '0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Button2 = '3'  (string)
  input.x11_options.BottomY = '7200'  (string)
  input.x11_options.TopY = '0'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.tablet' } (string list)

(...)

77: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if2'
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  info.subsystem = 'usb'  (string)
  info.product = 'USB Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if2'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.2'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.vendor_id = 7062  (0x1b96)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor = 'N-Trig'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.speed = 12  (double)
  usb.version = 1.1  (double)
  usb.is_self_powered = true  (bool)
  usb.can_wake_up = true  (bool)
  usb.bus_number = 7  (0x7)  (int)
  usb.product_id = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Interface'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  usb.interface.number = 2  (0x2)  (int)
  usb.interface.class = 0  (0x0)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)

78: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  info.linux.driver = 'usbhid'  (string)
  info.subsystem = 'usb'  (string)
  info.product = 'USB HID Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.vendor_id = 7062  (0x1b96)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor = 'N-Trig'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.speed = 12  (double)
  usb.version = 1.1  (double)
  usb.is_self_powered = true  (bool)
  usb.can_wake_up = true  (bool)
  usb.bus_number = 7  (0x7)  (int)
  usb.product_id = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)

79: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  info.linux.driver = 'usbhid'  (string)
  info.subsystem = 'usb'  (string)
  info.product = 'USB HID Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.vendor_id = 7062  (0x1b96)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor = 'N-Trig'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.speed = 12  (double)
  usb.version = 1.1  (double)
  usb.is_self_powered = true  (bool)
  usb.can_wake_up = true  (bool)
  usb.bus_number = 7  (0x7)  (int)
  usb.product_id = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)

80: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'
  usb_device.speed = 12  (double)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  info.linux.driver = 'usb'  (string)
  usb_device.version = 1.1  (double)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.is_self_powered = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'  (string)
  linux.device_file = '/dev/bus/usb/007/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'  (string)
  info.subsystem = 'usb_device'  (string)
  usb_device.num_interfaces = 3  (0x3)  (int)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2'  (string)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.vendor_id = 7062  (0x1b96)  (int)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.vendor = 'N-Trig'  (string)
  usb_device.product = 'Duosense Transparent Electromagnetic Digitizer'  (string)
  info.vendor = 'N-Trig'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  info.product = 'Duosense Transparent Electromagnetic Digitizer'  (string)

```

---

### Post by Favux on 2009-04-14
Hi Keeper of the Keys,

Now that's interesting.  On the TX2000 and TX2500 the by-path that ends in "event-mouse-" is the stylus/eraser.  And "event-" is touch.  And they are seperate events like "/dev/input/event9" and "/dev/input/event10" each with different pci paths.

A slightly more convienent way to look at your stuff may be to use Device Manager which should be in Applications>System Tools.  It's the gui front end for HAL.  Just be sure to check properties in View.

I have speculated that since on the TX2*00's we have two usb paths for two devices maybe we should try to use two .fdi files.  One for stylus and the other for touch.  Earlier in this thread Vincent and I tried to find a seperate usb path for your touch but couldn't.  I had concluded that N-trig was doing everything on one usb channel.

---

### Post by Keeper of the Keys on 2009-04-16
There seem to be 2 devices, though I have not yet found the event they are associated with...
Would you like me to post a screenshot of the device manager?

Edit:
It seems that the two devices are tied to /dev/input/event6 and /dev/input/event7 as well as /dev/usb/hiddev0 and /dev/usb/hiddev1
I am now going to play around with wacdump on said devices...

Edit2:
Well it seems that only event6 responds to touch and stylus as was also found earlier, the hiddev's don't work with wacdump but a cat again shows that only one of the two devices seems to be registering input...

---

### Post by Favux on 2009-04-16
Hi Keeper of the Keys,

See what:
```
hal-find-by-property --key input.x11_driver --string wacom
```
shows you.  Then try:
```
hal-find-by-property --key usb_device.vendor --string N-trig
```
and then change the key to "info.vendor".

---

### Post by Keeper of the Keys on 2009-04-16
hal-find-by-property --key input.x11_driver --string wacom
```

/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_hiddev
/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input

```

hal-find-by-property --key usb_device.vendor --string N-Trig
```

/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial

```

hal-find-by-property --key info.vendor --string N-Trig
```

/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial

```

---

### Post by Favux on 2009-04-16
Hi Keeper of the Keys,

So if I'm understanding this HAL stuff (questionable) the parent is:
```
80: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'
```
And it's generating two daughters.
```
12: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_hiddev'
```
which has the Wacom stuff, presumably from the .fdi file, and:
```
11: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_hiddev'
```
which doesn't.  Why not?

And also:
```
77: udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if2'
```
which I don't understand.

So how come there are 2 daughters (actually 3)?  I don't know.  Could the N-trig logic be simulating 2 usb paths that HAL is picking up?  If so then maybe we're back to wondering if another .fdi file for touch would work.  We're in the middle of testing that for a TX2000.  Sort of groping around.  What we've come up with is that "linux.sysfs_path" seems to offer a differentiator.
```
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0
```
```
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1
```
that we may be able to use to segregate the two .fdi files with.

HAL spec.s:  [http://people.freedesktop.org/~david/hal-spec/hal-spec.html#spec-device-info](http://people.freedesktop.org/~david/hal-spec/hal-spec.html#spec-device-info)

---

### Post by Keeper of the Keys on 2009-04-16
Based on the output of the GUI it does indeed look like three daughters, 2 that actually are identified as N-Trig devices and a third (if2) "USB Interface" with Class/Subclass/Protocol of 00/00/00....

Regarding the other two daughters it seems that if0 creates an event device (event6) that responds to both stylus and touch while if1 creates an event device (event7) that does not respond to either....

---

### Post by Favux on 2009-04-16
Well, as I've said the N-trig is a mystery to me.  I haven't really looked at how the patches work.

As an aside yurtboy, a Dell Latitude XT user, had a unique set up:
```
Section "InputDevice"
	Driver "wacom"
	Option "Mode" "Absolute"
	Identifier "touch"
	Option "Type" "touch"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
	Option "Device" "/dev/input/event3"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "9600"
	Option "BottomY" "7200"
	Option "USB" "on"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Mode" "Absolute"
	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option "Type" "stylus"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "9600"
	Option "BottomY" "7200"
	Option "USB" "on"
	Option "Button1" "1"
	Option "Button2" "3"
	Option "Button3" "2"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Type" "eraser"
	Option "Mode" "Absolute"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "9600"
	Option "BottomY" "7200"
	Option "USB" "on"
	Option "Button1" "2"
	Option "Button9" "0"
EndSection
```
which he said worked for him.

---

### Post by dado_eyad on 2009-04-16
hi every one
i`ll get my tablet at the first of the month and i`ll try all of what you mentioned.

but don't you think that all of this can made into an ubuntu tablet edition, just a thought that if ubuntu put all this together they will make a tablet edition.!?

---

### Post by Keeper of the Keys on 2009-04-16
Ok, so here's a strange one, I just changed the device for the touch to the event, and instead of X loading I had it crash on me, this due to the wacom driver crashing.
Now due to logrotte I don't currently have the backtrace of the crash, but I will regenerate another one soon and post it.

The impression I get from this is that for whatever reason in it's current form two different drivers (or driver settings) can't or won't be loaded for the same device, therefor you need to specify one of the two as the eventX path and one as the by-path, unlike the way it's done in the original tutorial where both device sections use the same device path.

Before recreating this crash again I am going to switch back to the Ubuntu version of the wacom driver and see if maybe everything works with that.

---

### Post by Favux on 2009-04-16
Hi dado_eyad,

They tried a while ago.  It's called Tabuntu.  I think it still has a site.

Hi Keeper of the Keys,

On this thread rec discovered the problem with 0.8.2-2 as patched by Timo.  The callout in the .fdi file to D-BUS was returning names that weren't the Wacom names wacomcpl etc. expected.  He created a script to fix it:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)

The script, renamed wacom-names, is also on post #93 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=10](http://ubuntuforums.org/showthread.php?t=1038949&page=10)

If you compiled 0.8.3-2 without first removing "libhal1-dev" then you may have gotten HAL features that may be giving you similar problems.

---

### Post by Keeper of the Keys on 2009-04-16
Hi Favux,
Well I just tried with the Ubuntu driver nd the result was the same as with the self compiled driver (I am pretty sure it was the same error, I'd have to switch drivers for 100%, but I'm sure enough, maybe tomorrow I'll switch again).

The interesting thing is the crash only occurs when a different device is used for the touch and the stylus (ie. one is eventX and one is by-path/X) and the error always occurs on the touch device/driver.

Reading back through the Xorg log of my current session it would seem that both devices were initialized properly and that on top of that the events also get initialized as HIDs, so maybe there is a problem there.

I now noticed that the following error message is generated every time I touch the screen:
```

sendAButton: Invalid button index 9 (number of defined buttons = 5)

```

The error is the following wacom crash:
```

WACOM: touch max value(s) was wrong MaxTouchY = 7200 MaxTouchY = 0.
Failed to open device (fd=-1)
xf86WcmProc INIT FAILED
xf86WcmUninit
(II) UnloadModule: "wacom"

Backtrace:
0: X(xorg_backtrace+0x26) [0x4f1b66]
1: X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7f750f191040]
3: /usr/lib/xorg/modules/input//wacom_drv.so [0x7f750ce56035]
4: X(ActivateDevice+0x3e) [0x447a8e]
5: X(InitAndStartDevices+0x3a) [0x447baa]
6: X(main+0x37f) [0x433d4f]
7: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f750f17c5a6]
8: X [0x433219]
Saw signal 11.  Server aborting.

```

Current Xorg log (all non wacom related bits removed) seems to suggest an error:
```

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $

(**) Stylus: always reports core events
(**) Stylus device is /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse
(**) Stylus (Stylus) is not a pad 
(**) Stylus is in absolute mode
(**) Stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) Stylus: reading USB link
(**) Option "TPCButton" "on"
(**) /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse: Tablet PC buttons are on 
(**) Option "Button2" "3"
(**) Stylus: button2 assigned to 3
(**) Option "Button3" "core key alt F2"
(WW) Option "Button3" requires an integer value
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "Stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=9600 maxY=7200 maxZ=256 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "Stylus" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016
(**) Touch: always reports core events
(**) Touch device is /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse
(**) Option "DebugLevel" "8"
(**) WACOM: Touch debug level set to 8
(**) Touch (Touch) is not a pad 
(**) Touch is in absolute mode
(**) Touch: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "9600"
(**) Touch: bottom x = 9600
(**) Option "BottomY" "7200"
(**) Touch: bottom y = 7200
(**) Touch: threshold = 15
(**) Touch: max x = 9600
(**) Touch: max y = 7200
(**) Touch: max z = 256
(**) /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse: Tablet PC buttons are on 
(**) Option "Touch" "on"
(**) /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse: Touch is enabled 
(**) Option "Button1" "1"
(**) Option "Button10" "1"
(**) Touch: button10 assigned to 1
(**) Option "BaudRate" "9600"
(**) Touch: serial speed 9600
(II) XINPUT: Adding extended input device "Touch" (type: Wacom Touch)
BEGIN xf86WcmProc dev=0x1b66300 priv=0x1b5bf20 type=eraser(Touch) flags=16642 fd=-1 what=INIT
xf86WcmInitialScreens for "Touch" number of screen=1 
X factor = 0.133, Y factor = 0.111
(==) Wacom device "Touch" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=0 resol Y=0
xf86WcmInitialScreens for "Touch" number of screen=1 
X factor = 0.133, Y factor = 0.111
END xf86WcmProc Success 
BEGIN xf86WcmProc dev=0x1b66300 priv=0x1b5bf20 type=eraser(Touch) flags=16642 fd=16 what=ON
END xf86WcmProc Success 

(II) config/hal: Adding input device HID 1b96:0001
(**) HID 1b96:0001: always reports core events
(**) HID 1b96:0001: Device: "/dev/input/event7"
(II) HID 1b96:0001: Found 2 mouse buttons
(II) HID 1b96:0001: Found x and y absolute axes
(II) HID 1b96:0001: Found absolute touchpad
(II) HID 1b96:0001: Configuring as mouse
(**) HID 1b96:0001: YAxisMapping: buttons 4 and 5
(**) HID 1b96:0001: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1b96:0001" (type: MOUSE)
(**) HID 1b96:0001: (accel) keeping acceleration scheme 1
(**) HID 1b96:0001: (accel) filter chain progression: 2.00
(**) HID 1b96:0001: (accel) filter stage 0: 20.00 ms
(**) HID 1b96:0001: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID 1b96:0001
(**) HID 1b96:0001: always reports core events
(**) HID 1b96:0001 device is /dev/input/event6
(**) HID 1b96:0001 (HID 1b96:0001) is not a pad 
(**) HID 1b96:0001 is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) HID 1b96:0001: serial speed 9600
(II) XINPUT: Adding extended input device "HID 1b96:0001" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event6"
HID 1b96:0001 Wacom X driver can't grab event device, errno=16
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=9600 maxY=7200 maxZ=256 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "HID 1b96:0001" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016

BEGIN xf86WcmProc dev=0x1b66300 priv=0x1b5bf20 type=eraser(Touch) flags=16642 fd=16 what=OFF
Wacom number of open devices = 2
END xf86WcmProc Success 
Error reading wacom device : Invalid argument
sendAButton: Invalid button index 9 (number of defined buttons = 5)
sendAButton: Invalid button index 9 (number of defined buttons = 5)
sendAButton: Invalid button index 9 (number of defined buttons = 5)
sendAButton: Invalid button index 9 (number of defined buttons = 5)
sendAButton: Invalid button index 9 (number of defined buttons = 5)
sendAButton: Invalid button index 9 (number of defined buttons = 5)

```

---

### Post by Favux on 2009-04-16
Hi Keeper of the Keys,

Not good.  I'll look at it.

Maybe you can explain N-trig to me a little.  Basically the N-trig has driver support in the HID module of the kernel, correct?  And Rafi's patch latches into the linuxwacom stuff so it sees the usb input from the HID device as Wacom input.  Am I close?  And then the idea with switching to HAL is use the added N-trig part of the 10-wacom.fdi to replace the wacom entries in xorg.conf.

---

### Post by Keeper of the Keys on 2009-04-16
Hi Favux, 

I don't fully know what's flying with n-trig, as far as I understand it rafi wrote a patch both to the kernel and to the linux wacom driver to make n-trig work to whatever level possible.
It seems politics are harming the support of the N-Trig digitizer as the linuxwacom project seems to have recently taken the stance that they will only support wacom products and not N-Trig or others that happen to be close to supported by their driver...
If they are paid for by wacom I can understnd this though it still is a bit sad that such politics should hurt the rest.

Anyhow I just made another small discovery, it would seem tatht the problem with X crashing also exists when using event7 for both devices....
So I don't know why or how it different to the system if you use eventX or by-path but it seems that eventX leads to a crash.

The following is the editted Xorg log with the crash, it seems that even though the device has alreay been initialised with the eventX pth it then gets initialised like that again causing a crash (which is a bit different from the other crash):
```

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $

(**) Stylus: always reports core events
(**) Stylus device is /dev/input/event6
(**) Stylus (Stylus) is not a pad 
(**) Stylus is in absolute mode
(**) Stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) Stylus: reading USB link
(**) Option "TPCButton" "on"
(**) /dev/input/event6: Tablet PC buttons are on 
(**) Option "Button2" "3"
(**) Stylus: button2 assigned to 3
(**) Option "Button3" "core key alt F2"
(WW) Option "Button3" requires an integer value
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "Stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event6"
Stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=9600 maxY=7200 maxZ=256 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "Stylus" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016
(**) Touch: always reports core events
(**) Touch device is /dev/input/event6
(**) Option "DebugLevel" "8"
(**) WACOM: Touch debug level set to 8
(**) Touch (Touch) is not a pad 
(**) Touch is in absolute mode
(**) Touch: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "9600"
(**) Touch: bottom x = 9600
(**) Option "BottomY" "7200"
(**) Touch: bottom y = 7200
(**) Touch: threshold = 15
(**) Touch: max x = 9600
(**) Touch: max y = 7200
(**) Touch: max z = 256
(**) /dev/input/event6: Tablet PC buttons are on 
(**) Option "Touch" "on"
(**) /dev/input/event6: Touch is enabled 
(**) Option "Button1" "1"
(**) Option "Button10" "1"
(**) Touch: button10 assigned to 1
(**) Option "BaudRate" "9600"
(**) Touch: serial speed 9600
(II) XINPUT: Adding extended input device "Touch" (type: Wacom Touch)
BEGIN xf86WcmProc dev=0x2300180 priv=0x22f5da0 type=eraser(Touch) flags=16642 fd=-1 what=INIT
xf86WcmInitialScreens for "Touch" number of screen=1 
X factor = 0.133, Y factor = 0.111
(==) Wacom device "Touch" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=0 resol Y=0
xf86WcmInitialScreens for "Touch" number of screen=1 
X factor = 0.133, Y factor = 0.111
END xf86WcmProc Success 
BEGIN xf86WcmProc dev=0x2300180 priv=0x22f5da0 type=eraser(Touch) flags=16642 fd=16 what=ON
END xf86WcmProc Success 

(II) config/hal: Adding input device HID 1b96:0001
(**) HID 1b96:0001: always reports core events
(**) HID 1b96:0001: Device: "/dev/input/event7"
(II) HID 1b96:0001: Found 2 mouse buttons
(II) HID 1b96:0001: Found x and y absolute axes
(II) HID 1b96:0001: Found absolute touchpad
(II) HID 1b96:0001: Configuring as mouse
(**) HID 1b96:0001: YAxisMapping: buttons 4 and 5
(**) HID 1b96:0001: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1b96:0001" (type: MOUSE)
(**) HID 1b96:0001: (accel) keeping acceleration scheme 1
(**) HID 1b96:0001: (accel) filter chain progression: 2.00
(**) HID 1b96:0001: (accel) filter stage 0: 20.00 ms
(**) HID 1b96:0001: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID 1b96:0001
(**) HID 1b96:0001: always reports core events
(**) HID 1b96:0001 device is /dev/input/event6
(**) HID 1b96:0001 (HID 1b96:0001) is not a pad 
(**) HID 1b96:0001 is in absolute mode
(**) WACOM: suppress value is 2
(**) HID 1b96:0001: threshold = 15
(**) HID 1b96:0001: max x = 9600
(**) HID 1b96:0001: max y = 7200
(**) HID 1b96:0001: max z = 256
(**) /dev/input/event6: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) HID 1b96:0001: serial speed 9600
(II) XINPUT: Adding extended input device "HID 1b96:0001" (type: Wacom Stylus)
(EE) HID 1b96:0001: Top/Bottom area overlaps with another devices.
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7f0a80344040]
3: /usr/lib/xorg/modules/input//wacom_drv.so [0x7f0a7e009035]
4: /usr/bin/X(ActivateDevice+0x3e) [0x447a8e]
5: /usr/bin/X(OpenInputDevice+0x10) [0x4968e0]
6: /usr/bin/X(ProcXOpenDevice+0xa3) [0x545823]
7: /usr/bin/X(Dispatch+0x364) [0x44e304]
8: /usr/bin/X(main+0x3bd) [0x433d8d]
9: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f0a8032f5a6]
10: /usr/bin/X [0x433219]
Saw signal 11.  Server aborting.
(II) UnloadModule: "synaptics"
(II) UnloadModule: "wacom"
BEGIN xf86WcmProc dev=0x2300180 priv=0x22f5da0 type=eraser(Touch) flags=16642 fd=16 what=OFF
Wacom number of open devices = 2
END xf86WcmProc Success 
BEGIN xf86WcmProc dev=0x2300180 priv=0x22f5da0 type=eraser(Touch) flags=16642 fd=-1 what=CLOSE
END xf86WcmProc Success 
xf86WcmUninit
(II) UnloadModule: "wacom"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) HID 1b96:0001: Close
(II) UnloadModule: "evdev"

```

---

### Post by Favux on 2009-04-16
I don't know why the LWP decided that.  I do know they have been getting some support from Wacom.  Whether it is more than a few donated tablets and some spec.s and maybe some code I don't know.  It is a shame though.

Earlier it seems it was complaining about wacom_drv.so:
```
3: /usr/lib/xorg/modules/input//wacom_drv.so [0x7f750ce56035]

```
I still don't get why you need "(**) Stylus: forcing TabletPC ISD V4 protocol".  That's for serial tablets, not usb tablets.

It may be that it's not accepting Rafi's patch an hence the HID input:
```
(**) HID 1b96:0001: serial speed 9600
(II) XINPUT: Adding extended input device "HID 1b96:0001" (type: Wacom Stylus)
(EE) HID 1b96:0001: Top/Bottom area overlaps with another devices.
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

```

You're in Jaunty, are you configuring with xorg.conf or the 10-wacom.fdi.  Are you using the modified one?  Where is it getting the two sets of coordinates from?  Do you have a .xinitrc in the /home/username directory?

---

### Post by Keeper of the Keys on 2009-04-16
I'm in jaunty, I use Xorg to configure, at this point I am using the default fdi, I defined ISDV4 because that is what the earlier tutorials said to define....

The coordinates I think are the Top and Bottom X/Y as provided in xorg.conf.
My understanding of the error of overlapping was that because it is trying to init the same device on the same rea twice it was getting this error...

I am going to try and see what happens when I disable ISDV4....

Edit:
I was about to write that I had no xinitrc because I cannot remember ever mking one, but there is one doing some xsetwacom for the Stylus, under normal circumstances with the crashes it doesn't get to the stage of my xinitrc though as the crsh will happen while gdm is loading, when eventX and by-path are used mixed the screen will merely go blank, when only eventX is used a cursor will actually appear before the server hangs.

---

### Post by Favux on 2009-04-16
Hi Keeper of the Keys,

OK, which version of linuxwacom?  Timo's patched 0.8.2-2 or did you compile 0.8.3-2?  If you compiled 0.8.3-2 did you remember to remove libhal1-dev before you compiled it?  If you removed it xorg.conf should work with 0.8.3-2.

If your using xorg.conf why don't your rename 10-wacom.fdi to 10-wacom.bak so we're sure it's not being used.  Also are you using the modified N-trig.fdi I posted?

---

### Post by Keeper of the Keys on 2009-04-17
All the above crashes etc. were with the stock version of the wacom driver from the ubuntu repositories, with the fdi as provided with the package.
So 0.8.2...

When I used the self compiled 0.8.3 I had not disabled HAL...

Turning the ISDV4 option off in xorg.conf does not seem to affect the function of the tablet...

---

### Post by Favux on 2009-04-17
Hi Keeper of the Keys,

> All the above crashes etc. were with the stock version of the wacom driver from the ubuntu repositories, with the fdi as provided with the package.
OK, we're back on the same page.  And you didn't replace the stock 0.8.2-2's wcmUSB.c with Rafi's?  So you could try rec's script and see if that makes a difference.

A way forward for you might be compiling 0.8.3-2 without libhal1-dev.  Then use Rafi's wcmUSB.c?  This should let you go back to using xorg.conf (which doesn't seem to need the ISDV4 line).  Using xorg.conf means you'd lose usb hotplugging, but that isn't as important to us tablet pc users.  This has the virtue of letting you ignore the HAL/.fdi stuff, at least until Kharmic Kaola.

---

### Post by Favux on 2009-04-18
Hi Keeper of the Keys,

Breaking news.  Take a look at post #102 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Why don't you see if something similar works for you?  You've done most of the work already!

---

### Post by Keeper of the Keys on 2009-04-19
Hi Favux,
I have briefly tried this but so far to no avail, I might try more later...

The problem/difference is that unlike with the wacom where touch and stylus are detected on a different device with the n-trig everything is detected on the same device, so the impression I am getting is that the second time the same device is specified it overrides the first time.

Today I spoke to someone at n-trig and they said they are working on a Linux driver, I hope this is true and we'll see with time...
He also said that the datastream is according to microsoft specifications, maybe this will help someone with more knowledge of these things in reverse engineering the driver.
I am probably going to bug them again later, let them know we're out there.

---

### Post by Vincent_Lin on 2009-04-23
Hi guys,

I have not participated in the discussion for a while.  How are guys doing?

I have not figured out anything further about my audio mess yet.  As I said, I even purchased a second HD and restored Vista on my tx2z to make sure that if my hardware has defects in it.  Unfortunately, speakers and headphone run as spec-ed(maybe I should say fortunately??)

I have another question. 
 
Is there a way to run/setup this pretty tx2z so that when I am typing, the touchpad is disabled, at the exact moment a key on the keyboard is pressed?  I thought this is a desired feature and is already implemented, though I am not sure.

It is rather annoying when I am typing and a finger or two touching the touchpad will move my cursor to somewhere I have to hunt for it.  Sometimes, I lost the whole email I was typing in a webmail interface when the pages suddenly move forward or backward.

Does anyone know?

Thanks.

Vincent

---

### Post by Favux on 2009-04-23
Hi Vincent,

Good to hear from you again.  At the top of my touch pad is a narrow little button with a little blue touchpad icon next to it.  It took me a while to realize what it is for.  When I press it it turns off the touchpad and turns orange.  Does the TX2z have a similar button?

---

### Post by Vincent_Lin on 2009-04-23
Favux,

Yes it does have one such turn-off button.  It works as intended purpose, but most of the time, I forgot to turn it off when typing.

Does touchpad driver has the feature I mentioned above?

Thanks for the reply.  Horrray for the release of 9.04!!

Vincent

---

### Post by Favux on 2009-04-24
Hi Vincent,

Maybe this is what you are looking for?

[http://ubuntuforums.org/showthread.php?t=271052&highlight=tablet](http://ubuntuforums.org/showthread.php?t=271052&highlight=tablet)

If you try it and it works please let me know.

---

### Post by Vincent_Lin on 2009-04-26
Hi Guys,

Can you believe it?  I installed 9.04, and remove pulseaudio, and all my audio goodies are back - no sudden mute when loud, and headphone works as supposed to.  Call my a happy tx2z user!!

This idea was picked up at alsa-user email list.  Most of the solutions to those hdmi/spdif/internal mic problems suggested by those alsa gurus are like this - remove pulseaudio.  But I really could not remember if I had tried that before.  Anyhow, it works.

It will take me a while to setup all those interesting features ever mentioned in this thread and others, but really, I am very happy now.

Cheers,

Vincent Lin

---

### Post by tempo500 on 2009-04-27
hey, i did not follow the audio duscussion here, (beside my audio capture probs...:-/) anyway, i am using 9.04, and all audio problems were solved with the default pulse setup. changed everything to pulse in skype...

---

### Post by Vincent_Lin on 2009-04-27
Hi Tempo500,

I know what you meant.

My tx2z is the only one that were mentioned in this forum/these threads that has this problem - all went through the identical setup as depicted in this thread and others.  

At least, I am happy now for it is working as expected :).

Vincent

---

### Post by Keeper of the Keys on 2009-04-27
Vincent do you have touch working or are you like me deprived of touch?

I currently just have a dual boot with 8.10 for those applications where I have to have touch...

---

### Post by Vincent_Lin on 2009-04-27
I don't have touch working properly using the pre-installed wacom driver in 9.04.  The driver mentioned in the howto of this thread could not be installed.  I am stuck as you are.

However, even touch is not working "properly", the screen actually detects my finger when I touch it.  When I touch the screen and "scroll" using my finger, X goes into another virtual screen(desktop cube rotates when I scroll my finger on screen.)  That's the only action it would do.

Then I tried to remove the /usr/share/hal/fdi/policy/10-wacom.fdi and reboot, my finger touch is doing differently - the screen sort of ignores the movement of scroll, but detects the touch only.

I would think a good/well-defined fdi should resolve this.

Any one?

Vincent

---

### Post by glurgle on 2009-05-06
the thing is that the wacom driver had to be patched to support the n-trig device, it normally only initializes and works with wacom devices (using hard-coded device ids)

I attempted to patch a more recent version of linuxwacom on archlinux, but didn't get very far with it. Furthermore, the support in the kernel has been greatly improved since those packages were made, so that the device can be used with the evdev driver, no linuxwacom required. Unfortunately for me, I can't seem to convince evdev to use absolute mode instead of relative (still on archlinux, so it might be worth trying to use evdev and absolute mode on ubuntu)

---

### Post by Vincent_Lin on 2009-05-06
Hi Glurgle,

I am really not familiar with evdev stuff.  Sorry I can't help at all.  However, when I search evdev stuff on synaptic, it shows another packages called xserver-xorg-input-evtouch, xserver-xorg-input-mutouch, and xserver-xorg-input-tslib.  Are these the evdev driver you were talking about?  

Vincent

---

### Post by glurgle on 2009-05-06
as far as I'm aware those are all different drivers, you will already have evdev installed, as it's the default driver for keyboard and mice in recent X servers, it's meant to be a generic driver for event devices. The bigger change is that the kernel HID drivers have had the necessary quirks added for the n-trig digitizer to act as a standard event device rather than requiring a specialized driver to support it. I'm not really up to the minute on most of this stuff though, been meaning to look into it, as I'd like to get my tablet working better under arch as well as ubuntu

---

### Post by Favux on 2009-05-09
5-8-09 excerpted quote from Rafi Rubin
> Attached is a patch which simply adds the digitizer in my laptop to the list of recognized devices. As of 0.8.2 (or something near that version), the driver stopped working with unlisted devices which just so happen to follow the common interface and worked well with the driver.

So on behalf of myself and other users, I ask that you consider accepting this patch.  And for me, this is still the best way to get the touch screen working.

The patch was off the cvs of the dev branch. And I've also tested application to 0.8.3-4.

5-8-09 Ping Cheng
> Hi Rafi,

Thank you for supporting linuxwacom project. Your patch will be considered.
Hope you can provide more support to the project in general once the driver
works for you.
From here, patch posted also:  [http://sourceforge.net/mailarchive/forum.php?thread_name=4A03EE63.3010403%40seas.upenn.edu&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=4A03EE63.3010403%40seas.upenn.edu&forum_name=linuxwacom-discuss)

---

### Post by techphets on 2009-05-09
I'm thinking about picking up a tx2 but do not want to use Vista on it.  I wouldn't have a problem with XP but I'm not buying a special tablet edition.  

I've only read through a few pages of this thread and it looks like there are quite a few issues with using Ubuntu on the machine.  Would someone mind summarizing all the issues?  Also, is there a version of Linux which works better than Ubuntu? 

Seeing that the last few posts are discussing problems with touch I doubt I will pick it up any time soon.  Shame since the machine looks like a decent value.

---

### Post by Keeper of the Keys on 2009-05-10
First of, don't even think of running XP on this machine, drivers for the touchscreen only exist for Windows Vista and beta drivers for Windows 7.

Second as far as issues are concerned:
- Touch does not work on 9.04, the evdev usage mentioned above does not work properly yet, 9.10 will hopefully be better. Xorg will support multitouch starting 9.10 so if drivers supporting it by then are out you will have a multitouch device if not then with 8.10 you have a regular touch device.

- Buttons next to the screen don't seem to work (which I don't think matters so much but opinion may differ) the important buttons [keyboard, volume, wireless toggle, touchpad toggle and power] work.

- There seem to sometimes be some issues with the sound device, though I have had none since I set the correct parameter for the kernel module.

- The keyboard/mouse controller seems to sometimes lock, this is solved with the right boot parameters, I have a boot password and it froze on me locking me out, but it was reset by removing the battery from the device. (this was after running without the recommended reset parameter)

---

### Post by glurgle on 2009-05-11
I was just going to post about that patch, I've tested it with linuxwacom 0.8.3 on my arch install and it works well. I may upgrade my ubuntu to 9.04 and try to make a .deb that has this patch, but I doubt I'd be able to maintain it or create a 32-bit package. Perhaps a how-to on how to make your own patched package would be better?

---

### Post by Favux on 2009-05-11
Hi glurgle,

I think a HOW TO on making your own patched package sounds like an excellent idea!


Edit:  I forgot to mention that MisteR2 found out where the swivel hinge signal is hiding.  It turns out to be in the HP-WMI kernel module.  He contacted Matthew Garrett the module maintainer.  Matthew figured out the swivel hinge was sharing the signal with the docking function.  He separated it out with a patch for hp-wmi.c.  MisteR2 posted the patch and instructions and a .fdi on post #106 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11)  So this should give you auto-magic rotation in Jaunty.  I don't know about Intrepid.  I think it should work for the TX2z swivel hinge.  Wouldn't hurt to try anyway.  And maybe the bezel buttons are hiding somewhere in HP-WMI too?

---

### Post by Vincent_Lin on 2009-05-11
Hi,

I second that idea of making our own package.

Thanks for the great work.

Vincent

---

### Post by Frozen208 on 2009-05-14
Hi all,

I am fairly new to Linux(tried Mandrake back in 2000ish), I am planning on buying the Tx2z for college for note taking in class. I plan on dual booting with Ubuntu and Vista, for those who have installed 9.04 will the How To posted still work? And have you experienced any problems when in tablet mode?

Thanks in advance

---

### Post by Keeper of the Keys on 2009-05-21
Frozen208,
Unless someone has so far succeeded in building the modified wacom drivers for 9.04 touch does not work, stylus input does and either way multitouch is not supported yet (though supposedly 9.10 will be able to support multitouch).

Other than that the only relevant things in the howto are setting module=toshiba for the soundcard and adding the i8042.reset to the boot parameters so the keyboard doesn't lock.

---

### Post by Sativo on 2009-05-28
I just tried downloading Rene Mayrhofer’s pre-compiled packages, but his site seems to be down.  Can someone post them somewhere else, or is there another place I can download them?

Thanks,
Sativo

---

### Post by Favux on 2009-05-29
Hi glurgle, Keeper of the Keys, and Everyone,

Going by Rafi Rubin's site here:  [http://ofb.net/~rafi/latitude_xt.html](http://ofb.net/~rafi/latitude_xt.html)  the problem with getting N-trig working in Jaunty is two parts.

Part one is patching the linuxwacom driver so that it recognizes the N-trig digitizer.  Apparently that was a change that started with linuxwacom 0.8.2-x.  That part I can do.  I applied his "n-trig.patch" to 0.8.3-5 and it looks like it took it cleanly.  Now if you're running on kernel 2.6.29 that apparently is all you need to do.  The digitizer will work.

The second part is that the 2.6.28 kernel doesn't yet have the n-trig support 2.6.29 has.  So you need to patch the USB HID drivers with his "0001-Added-quirks-for-the-N-Trig-digitizer.patch".  Since it's nicely numbered and everything it looks like all you are suppose to do is add it to a "/debian/patches" folder and then when you tell the package to make the deb the "debian/rules" will apply the patch.  OK, but what package?  Does anyone have any idea which package source code you need?
Edit:  Looks like I may have answered my own question.  Looking here:  [https://www.linuxhq.com/kernel/v2.6/28-rc2/drivers/hid/Kconfig](https://www.linuxhq.com/kernel/v2.6/28-rc2/drivers/hid/Kconfig)  I was afraid that's what this was talking about.:
```
 drivers/hid/Kconfig     |    7 ++++
 drivers/hid/Makefile    |    1 +
 drivers/hid/hid-core.c  |    1 +
 drivers/hid/hid-ids.h   |    3 ++
 drivers/hid/hid-ntrig.c |   84 +++++++++++++++++++++++++++++++++++++++++++++++
 5 files changed, 96 insertions(+), 0 deletions(-)
 create mode 100644 drivers/hid/hid-ntrig.c
```
So you're modifying "drivers/hid/".  And "Kconfig" presumably means kernel configuration.  So you have to roll your own kernel?  Ouch.

If you're in Jaunty with a non-functioning digitizer maybe you'd be interested in at least patching the linuxwacom driver and then compiling it to see if that gets you anywhere?  See where it gets you with kernel 2.6.28?  Maybe they've added or backported some n-trig support?

Also for those of you who want to run Compiz with "fglrx" I have a rotation script called ".Compiz_off_Rotation.sh" that turns Compiz off when you rotate to portrait.  It then turns it back on when you go back to landscape.  So you could have Compiz part of the time, when you're in laptop mode.  It's worked for one person so far.  If it works and you're interested I could put it in the Rotation HOW TO.  It's located at post #151 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=16](http://ubuntuforums.org/showthread.php?t=996830&page=16)

---

### Post by Favux on 2009-05-31
Hi Everyone,

Actually it may not be that bad.  The linux kernel team has versions of kernel 2.6.29 posted here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  So you don't have to use the hid patch.  And the instructions I've found to package and install the kernel don't look very difficult.  I know a bunch of folks on the Jaunty develpment forum were doing that after the kerfluffle about Jaunty not coming with 2.6.29 so it must be doable.

---

### Post by Attila_fdd on 2009-06-08
I installed ubuntu 9.04 and i'm following your suggestion, Favux,  to install the kernel 2.6.29.
i've installed the kernel 2.6.29 from ppa but there are some issues:

wifi doesnt work anymore with this kernel
stylus works perfectly (how to setup right button on the pen?)
finger touchscreen doesnt work (probably not setted, how to do it?)
video drivers, which should i have to install to make it works?
thanks!

---

### Post by Keeper of the Keys on 2009-06-08
The ppa packages don't provide restricted mudules which you need for wifi to work, I don't know if there is a seperate project that does that, Favux?

Concerning videodrivers I would strongly suggest that if you want the best performance just get the propriatary closed source AMD/ATi drivers of their website and have the installer build debs to install it with as it's than still managed by the packagemanager.
If you want rocksolid stability and don't care about the penalty to batterylife and performance use the open source drivers.
If you choose to use the closed source I strongly suggest not to use the one Ubuntu provide as it has bugs the real drivers don't....

It should also be noted that the stylus has always worked, if you get touch working that is worthy of note the stylus we know works.

You can set the rightmousebutton either thourgh yout xorg.conf file or though the wacomcpl program.

Other than that I am sorry I have not had the time and probably won't have it for a while to play around with this, my temporary ugly solution is dualbooting to 8.10.

---

### Post by Favux on 2009-06-08
Hi Attila_fdd and Keeper of the Keys,

Absolutely outstanding!  Rafi Rubin didn't steer us wrong about 2.6.29's HID now supporting N-trig.  Great work!  Which version of 2.6.29 are you using?  And did you patch linuxwacom with his "n-trig.patch"?  And if so which version of linuxwacom did you patch?

So the "linux-image" for the kernel at the Ubuntu kernel team's site doesn't have the proprietary modules.  I thought that's what they were saying.  I wonder why?

The TX2z also uses Broadcom wireless, correct?  Broadcom just released a new WiFi driver for Linux.  The tarball is here:  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  There is detailed installation instrucions in the "README.txt" located with the tarballs.  I sure hope it works for you.

I guess I agree with Keeper of the Keys regarding ATI video.  Since I have Nvidia I would go along with the suggestions of a fellow ATI user.  Here is a link to the Jaunty Install section from the Unofficial ATI wiki:  [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

OK, now about the stylus button right click.  We could add it to the .fdi but let's see if we can configure it through "wacomcpl".  What's your output from?:
```
xsetwacom list
```
And from:
```
xinput --list
```
Now onto touch.  It would be nice not to have to comb through the lshal output.  But we probably won't be that lucky.  So before we do anything let's get lshal output into text format.
```
lshal>before_lshal.txt
```
And let's see what output we get with:
```
lshal | grep input.originating_device
```
Then let's add two lines to the current "10-wacom.fdi" at "/usr/share/hal/fdi/policy/20thirdparty/".  This is the simplest change I can think of that might do something.
```
         <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
         <append key="wacom.types" type="strlist">touch</append>
```
This would make the N-trig subsection look like:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
         <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
         <append key="wacom.types" type="strlist">touch</append>
      </match>
    </match>
```
Reboot.  Hopefully it won't break anything and you're stylus will still work.  It would be nice if touch worked also.  We can't be sure if linuxwacom has included all the HAL patches that the Jaunty 0.8.2-2 linuxwacom has.  Then let's see what the following commands look like:
```
xsetwacom list
```
and
```
xinput --list
```
and
```
lshal>after_lshal.txt
```
You do not need to post any of the lshal outputs yet (except the "input.originating_device" one).

---

### Post by Attila_fdd on 2009-06-09
from page:

> update 2009-05
linuxwacom 0.8.2 and above refuse to work with unidentified tablets. This will id the n-trig. linuxwacom_0.8.3.patch Aside from that, I no longer use any special patches. The 2.6.29 kernel should suffice. 

what does he mean?
i have installed 2.6.29-4 (the latest stable one)
which are the steps i have to do to make the touch works correctly because there are too many things all together (different kernel, different patches, ecc)

For the other configurations thanks very much, I know how to make wifi and ati works now thanks also for the right button issue (stylus).

---

### Post by Favux on 2009-06-09
Hi Attila_fdd,

What he is saying is that starting with 0.8.2-x the LWP added a "table" to wcmUSB.c that identifies supported Wacom digitizers.  This had the effect of locking out non-Wacom digitizers like the N-trig.  His n-trig.patch adds the N-trig digitizer to the "table" in wcmUSB.c so that it again works with the rest of the linuxwacom drivers.

I just downloaded 0.8.3.5 onto my Desktop along with the n-trig.patch and changed directory to the Desktop unpacked the 0.8.3-5 tar and patched it using:
```
patch linuxwacom-0.8.3-5/src/xdrv/wcmUSB.c < n-trig.patch
```
As I mentioned I used the second "more properly formatted" patch he posted at LWP.  Actually there's so few changes you could just manually edit the wcmUSB.c.

I don't think you can get touch without the patch.  You'd just be using the 2.6.29-4 N-trig HID support.  I think you need to use the linuxwacom drivers.  If I understand him right that's what he's doing.

Of course he doesn't tell how he got the stylus and touch working that I see.  Does he use a .fdi or xorg.conf?  Whichever, what's in it?  So I guess we have to figure that out.

---

### Post by Keeper of the Keys on 2009-06-13
I know from my communications with Rafi that he does not use an .fdi file. (He didn't change the one provided by LWM)

---

### Post by Ayuthia on 2009-06-13
Rafi Rubin has a [website]("http://ofb.net/~rafi/latitude_xt.html") where he posts his xorg.conf file.  I was able to get my TouchSmart tx2 laptop to work based on Rafi Rubin's info.  However, I am using it with Gentoo instead of Ubuntu.

The other piece of info is that the 2.6.30 kernel now has newer multitouch support.  It appears that there are a group of people that are working on getting the multitouch to work.  Here is a [link]("http://www.lii-enac.fr/en/projects/shareit/linux.html") to their demo.  I have not been able to use their demo on my laptop because I am unable to get compiz to work with the radeonhd open source driver (I have not found the right patch for the fglrx driver in the 2.6.30 kernel).

As I mentioned, I am using Gentoo with a 2.6.30 kernel and I am using Rafi Rubin's patch for the linux wacom driver to use the touch screen capabilities.  It works pretty well for the touch and the stylus works just fine (even with pressure sensitivity in GIMP).

---

### Post by Favux on 2009-06-13
Hi Keeper of the Keys and Ayuthia,

Thanks.  And of course I found his xorg.conf yesterday.  That has to be the longest, most complicated one I have ever seen!  Simply amazing.  But pulling out the N-trig stuff looks simple.  I'm reassured that I'm not missing a .fdi somewhere.

I took a look at his link to the multi-touch stuff.  I think we need to get touch working before we work on that.

Right now I'm pretty confident I can get the stylus and stylus button working for the TX2z in the default Jaunty setup with just a few simple things.  But not touch.

---

### Post by Favux on 2009-06-14
Hi Attila_fdd,

Keeper of the Keys and Ayuthia just did us a big favor.  Ayuthia just told us we are on the right track and it works for him in Gentoo.  Both of them told us we use the xorg.conf and not a .fdi.  So you are basically about an hour away from getting it to work.

You've successfully installed kernel 2.6.29-4.  So download Rafi's second n-trig.patch from the link in post #136 onto your desktop.  Then use the linuxwacom compile HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Be sure to use 0.8.3-5 instead of 0.8.2-2 on the three lines where it applies.  Then after you unpack the tar in step 4), but before you change directory into the unpacked source code, apply the patch using the command in post #152.  Then just resume following the HOW TO.  That should give you a linuxwacom install that supports the N-trig digitizer.

Now you need to modify your xorg.conf with the entries Rafi uses.  I've cleaned them up and reorganized them a little.  At least as much as I dared.  There are some syntax errors, but messing too much with them might remove the fuctionality.  So if you want to  you could post your xorg.conf I can add the entries.

---

### Post by Ayuthia on 2009-06-19
As of a an hour ago or so, I was finally able to get the touch portion working with the 2.6.28-13-generic kernel.  I did have to patch the kernel source to make it work though.  I ended up taking the ntrig portions from the 2.6.30 kernel and added it to this kernel.  After several hours of compiling and adding the missing pieces, I was able to get a working kernel.  The only major issue that I have right now is that the fglrx module does not want to play well with X but I forgot to check and see if it worked with the untouched 2.6.28-13-generic kernel.

I plan on posting the patches that I used to get the touch portion to work.  I can also write up a guide on how to build it also.  I used this [guide]("https://help.ubuntu.com/community/Kernel/Compile") to help build the kernel.  Because of this, I now have linux-image and linux-header files in a .deb format.  It is only for the i386 kernel at this time.  Is that worth posting somewhere for people to try?

I chose this route to go mainly because of all the precompiled kernel-dependent packages (fglrx, wireless drivers, virtualbox, etc.) that are already built.  It is nice not having to rebuild them or find all the patches to make them work in the 2.6.29+ kernels.

I did find that in order to get the touch and stylus to work, I had to use /etc/X11/xorg.conf instead of the /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi file.  I ended up removing (you could comment it out also) the ntrig entries there and added them to the xorg.conf file.  For some reason, I have not gotten the button to work as a right click yet (it works in my Gentoo partition).

I also found out that if the touch/stylus portion is not defined, hal will use it as a mouse.  It is a little odd using your touchscreen as a large mousepad.

---

### Post by Ayuthia on 2009-06-19
Attached is the list of patches and code that I took from 2.6.30 and applied to 2.6.28-13-generic.  To extract the file:
```
tar -xvjf ntrig.tar.bz2
```
It will extract the files into a folder called ntrig.  You will need to download the source by using this [guide]("https://help.ubuntu.com/community/Kernel/Compile").

Once you have downloaded the source, you can then go into the source directory:
```
cd linux-2.6.28
```
You will then need to copy the patches into this directory:
```
sudo cp ../ntrig/*.patch .
```
You will then need to copy the hid-ntrig.c in the proper place:
```
sudo cp ../ntrig/drivers/hid/hid-ntrig.c drivers/hid/hid-ntrig.c
```

Now the patches need to be applied:
```
sudo patch -p1 < hid-core.c-2.6.28-13-generic.patch
sudo patch -p1 < hid.h-2.6.28-13-generic.patch
sudo patch -p1 < hid-ids.h-2.6.28-13-generic.patch
sudo patch -p1 < input.c-2.6.28-13-generic.patch
sudo patch -p1 < input.h-2.6.28-13-generic.patch
sudo patch -p1 < Kconfig-2.6.28-13-generic.patch
sudo patch -p1 < Makefile-2.6.28-13-generic.patch
sudo patch -p1 < 0001-ntrig-tool-separation-and-pen-usages.patch
```

You can then update the config files (from the kernel compile guide) and then compile the kernel.

This is not the neatest guide, but I just wanted to get the information out there before I forget.  I will write a better how-to when I have a little more time.

I have also attached my xorg.conf file (it will be in the ntrig.tar.bz2 file).  You will need to use the xorg.conf file instead of the /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi file.  You will need to comment out the entries for the ntrig stylus in the .fdi file also.

EDIT:  I just switched over to my 2.6.30 kernel in Gentoo and have found that the button on the stylus no longer functions as a right click anymore.  There must have been a change somewhere during the rc phase of the kernel because it was working.

NEW UPDATE:  Rafi Rubin has created another patch that fixes the pen button issue.  I have updated the attachment and the guide above to reflect the changes.

---

### Post by Ayuthia on 2009-06-19
Here are the .deb files for the 32-bit 2.6.28-13-generic kernel:
[linux-image-2.6.28-13-generic_2.6.28-13.44_i386.deb]("http://linuxfans.betaserver.org/linux-image-2.6.28-13-generic_2.6.28-13.44_i386.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.44_i386.deb]("http://linuxfans.betaserver.org/linux-headers-2.6.28-13-generic_2.6.28-13.44_i386.deb")

To install the 32-bit:
```
sudo dpkg -i linux-image-2.6.28-13-generic_2.6.28-13.44_i386.deb
sudo dpkg -i linux-headers-2.6.28-13-generic_2.6.28-13.44_i386.deb
```

Here are the .deb files for the 64-bit 2.6.28-13-generic kernel:
[linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb]("http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb]("http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb")

To install the 64-bit:
```
sudo dpkg -i linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb
sudo dpkg -i linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb
```

CAUTION:  These packages have the same name as the currently released kernel (They are not official packages but something I just created to try out).  I kept it that way right now because it allows us to be able to use the Ubuntu supplied kernel-dependent packages.  If anything should go wrong with this kernel, you will need to drop down to the 2.6.28-11-generic kernel to recover.

Like the previous post, you will need to use the xorg.conf file instead of the .fdi.  I had a problem with the fglrx module when I initially installed it though Hardware Drivers, but it seems to work fine after I reinstalled it.  It seems to work fine with the Broadcom STA module.

---

### Post by Favux on 2009-06-20
Outstanding Ayuthia!

I thought I'd add Rafi Rubin's xorg.conf wacom sections to the conversation.  I commented out his 13.1 by-paths (for Dell Latitude XT?) and substituted the 14.5 by-paths for the TX2z.  As I mentioned above I cleaned them up and reorganized them a little.
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
 	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
	Option		"Touch"		"on"
	Option		"Mode"		"Absolute"
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#	Option 		"Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option     	"Type"		"touch"
	#Option		"USB"           "on"                  # USB ONLY
        Option		"Touch"		"on"
	Option		"Supress"	"0"
	#Option		"DebugLevel"	"8"
	Option		"Mode"		"Absolute"
	Option 		"TopX"		"0"
	Option 		"TopY"		"0"
	Option 		"BottomX"	"9600"
	Option 		"BottomY"	"7200"
EndSection
```
This may be the tricky part.  "ServerLayout" entries seem to cause Jaunty problems.  At least for some folks.  I thought that was just the result of going to HAL, but actually it appears there was a bug in the original Jaunty xorg-xserver.  Hopefully they've added the fix that was on launchpad by now.  But back up your xorg.conf anyway and be ready for breakage.  Here's his whole "ServerLayout".
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "TouchPad"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "stylus" 
	InputDevice    "touch" 	
	#InputDevice    "stylus" "SendCoreEvents"
	#InputDevice    "touch" "SendCoreEvents"
EndSection
```
Obviously these are the necessary wacom entries:
```
	InputDevice    "stylus" 
	InputDevice    "touch" 	
	#InputDevice    "stylus" "SendCoreEvents"
	#InputDevice    "touch" "SendCoreEvents"
```
Notice he's commented out the two lines with the correct syntax, the ones with "SendCoreEvents".  Midnight_Sun and I were able to get (or rather keep) stylus working (but not touch) with the correct xorg wacom syntax.  I don't know what would happen to touch if we tried it.  I suspect once you get the kernel (whichever one) and linuxwacom setup for N-trig you could actually clean these entries up to standard wacom xorg.conf entries.

---

### Post by Ayuthia on 2009-06-20
> **Favux said:**
> 
This may be the tricky part.  "ServerLayout" entries seem to cause Jaunty problems.  At least for some folks.  I thought that was just the result of going to HAL, but actually it appears there was a bug in the original Jaunty xorg-xserver.  Hopefully they've added the fix that was on launchpad by now.  But back up your xorg.conf anyway and be ready for breakage.  Here's his whole "ServerLayout".
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "TouchPad"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "stylus" 
	InputDevice    "touch" 	
	#InputDevice    "stylus" "SendCoreEvents"
	#InputDevice    "touch" "SendCoreEvents"
EndSection
```

I only kept the stylus and touch entries and left the rest for HAL to handle.  However, if you are using fglrx, you should keep that in xorg.conf--at least that is how Hardware Drivers set it up when I enabled it.

> Obviously these are the necessary wacom entries:
```
	InputDevice    "stylus" 
	InputDevice    "touch" 	
	#InputDevice    "stylus" "SendCoreEvents"
	#InputDevice    "touch" "SendCoreEvents"
```
Notice he's commented out the two lines with the correct syntax, the ones with "SendCoreEvents".  Midnight_Sun and I were able to get (or rather keep) stylus working (but not touch) with the correct xorg wacom syntax.  I don't know what would happen to touch if we tried it.  I suspect once you get the kernel (whichever one) and linuxwacom setup for N-trig you could actually clean these entries up to standard wacom xorg.conf entries.

I switched it over to using the "SendCoreEvent" for the touch and stylus and it seems fine.  I am still having issues with the button click on my stylus.  It still registers as a left click instead of a right click.

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

So "SendCoreEvents" works and doesn't break anything.  To get the stylus button as a right mouse click you could add to the stylus section;
```
        Option		"Button2"	"3"  # make stylus button R mouse click
```
Since touch is working with "SendCoreEvents" I wonder what happens with "standard" wacom entries?  They should look something like this:
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
 	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
        Option		"USB"		"on"                  # USB ONLY
        Option		"Button2"	"3"  # make stylus button R mouse click
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option     	"Type"		"touch"
	Option		"USB"           "on"                  # USB ONLY
        Option		"Touch"		"on"
	Option 		"TopX"		"0"
	Option 		"TopY"		"0"
	Option 		"BottomX"	"9600"
	Option 		"BottomY"	"7200"
EndSection
```
The rest should be either unnecessary or default.  And then "ServerLayout":
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection
```
Where the lines:
```
        Identifier      "Default Layout"
        Screen		"Default Screen"
```
Stand for whatever entries other than the wacom ones you need in it.

Have you tried "wacomcpl" yet?  That should let you calibrate your tablet and configure it.  For instance if you want the stylus button a middle mouse click.  Using "wacomcpl" is described in Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Ayuthia on 2009-06-20
One minor change:
```
Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#	Option 		"Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option     	"Type"		"touch"
	Option		"USB"           "on"                  # USB ONLY
        Option          "Touch"         "on"
	Option 		"TopX"		"0"
	Option 		"TopY"		"0"
	Option 		"BottomX"	"9600"
	Option 		"BottomY"	"7200"
EndSection
```

It was missing the option "Touch" "on".  If that is not enabled, the touch portion is not activated.

I have tried the wacomcpl setup and I also have the Button 2 option set to 3 and it still is not changing.  I know that the button still registers a response from /dev/hiddraw0.  I am thinking that the changes in 2.6.30 has defined the button differently so the wacom driver is not finding it.  I might check the older kernels to see if I can find the difference.

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

Great!  Standard syntax works!  The "Touch" "on" option is interesting.  It should be default, so it seems there is some difference with touch on the same usb input path.
```
        Option		"Touch"		"on"
```
I'll look at the linuxwacom-discuss and dev-discuss boards and see if there is anything regarding the button.  I seem to remember something about a patch by Tom Jaeger for linuxwacom called something like "don't mess with my map".  I don't remember the details (what few there were) but it may be Xserver 1.6 and not the kernel that is the problem.

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

I've been thinking about the problem you said you had with the wacom.fdi and how you recommend commenting out the N-trig section.  It isn't suppose to work that way.  My understanding is they should execute in this order:

10-wacom.fdi
custom_wacom.fdi
xorg.conf
wacomcpl's .xinitrc

And they should be able to coexist like they do in Intrepid.  Whatever executes last controls.  But something in an earlier one that isn't changed in a later one should still carry the setting applied.

So is something grabbing the settings from the .fdi and not letting go like it should?  Or is this a consequence of continued deprecation of the xorg.conf?  Or maybe a bug? 

If this wasn't happening I'd wonder about adding:
```
       <merge key="input.x11_options.Button2" type="string">3</merge>
```
to the N-trig section of the wacom.fdi.  Because RageAge said it gave him a working stylus button in post #6 here:  [http://ubuntuforums.org/showthread.php?t=1186428](http://ubuntuforums.org/showthread.php?t=1186428)

---

### Post by Ayuthia on 2009-06-20
I tried it out and had the touch stay in xorg.conf and defined the stylus in .fdi.  It ended up crashing X.  So I decided to comment out the touch in xorg.conf and just use the stylus in .fdi and the stylus works but the button still does not switch to the right-click.

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

Darn.  So we're probably back to a bug somewhere.  The kernel, Xserver 1.6, or linuxwacom.  If linuxwacom probably in wacom-tools?  And maybe from one of the N-trig patches?  Shoot.  Too many variables.

So right now we're looking at stylus with button or stylus with touch.  There has to be a way forward to get the whole panoply of stylus with button and touch.

---

### Post by Ayuthia on 2009-06-20
What I am finding out is that hal will assign wacom to the touch and stylus, but wacomcpl does not recognize them.  The only way that it will recognize both is if I add them to xorg.conf.

I am going to take a look at the two kernels now to see where the differences are.

EDIT:  If I have time, I might also try recompiling the kernel with the 2.6.29.4 ntrig changes.  That has a chance to get the button click to work again.  I say this only because I know that it was working once before.

---

### Post by Ayuthia on 2009-06-20
I just found out that there was no need for me to check the differences between the two kernels because Rafi Rubin has created another patch recently.  I checked out his website and found that he submitted another patch recently.  This patch fixes the button issue!

I have updated my previous [post]("http://ubuntuforums.org/showpost.php?p=7486554&postcount=157") to reflect the changes.  I also have updated the two .deb files  that was supplied in post [158]("http://ubuntuforums.org/showpost.php?p=7486766&postcount=158").

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

Excellent!  You've done it!  N-trig with full function in Jaunty.  Thank you Rafi Rubin.

By the way from what you were saying about HAL before you applied the new patch, it is possible we could construct a working .fdi now.  We would need to look at the output of:
```
xinput --list
```
and
```
lshal>Ayuthia_N-trig_lshal.txt
```
with the current N-trig.fdi active and go from there.

---

### Post by Ayuthia on 2009-06-20
Here is xinput --list:
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"HID 1b96:0001"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1122
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 935
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"HID 1b96:0001"	id=6	[XExtensionDevice]

```

Attached is the other requested file.  It had to be gzipped due to the .txt filesize requirement was exceeded.

Here is what I have tried out for the ntrig entry for my .fdi file:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if1">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">touch</merge>
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Touch" type="string">on</merge>
       <merge key="input.x11_options.TopX" type="string">0</merge>
       <merge key="input.x11_options.TopY" type="string">0</merge>
       <merge key="input.x11_options.BottomX" type="string">9600</merge>
       <merge key="input.x11_options.BottomY" type="string">7200</merge>
      </match>
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
      </match>
    </match>

```
It currently has the stylus working, but the touch is not happy.  It does not move unless you use more than one finger.  wacomcpl does not recognize the stylus or the touch.

EDIT: For those of you who want to look at the attached file but do not know how to extract it:
```
gunzip Ayuthia_N-trig_lshal.txt.gz
```

---

### Post by Favux on 2009-06-20
Hi Ayuthia,

Thank you.  This will take a while.  As you noted combing through lshal is quite the pain because it's so big.

Rather than:

stylus = "HID 1b96:0001" in the "HID 1b96:0001"	id=7	[XExtensionKeyboard] line and

touch = "HID 1b96:0001" in the "HID 1b96:0001"	id=6	[XExtensionDevice] line, or vice versa

I suspect it may be more complicated.  And the reason wacomcpl isn't working is because those aren't linuxwacom device names so:
```
xsetwacom list
```
would be blank.  But I wonder if rec's script would translate things correctly with stylus and touch being on the same path.

If the way forward requires an info callout to append touch to stylus or the reverse we'll most likely be stuck since you probably didn't compile linuxwacom with the libhal1-dev present (it isn't by default).  We found that prevented use of xorg.conf.  But maybe that is a bug, not by design.  Possibly the same bug I referenced earlier.  So this is a long shot and using xorg.conf is likely the only way that will work.

---

### Post by Ayuthia on 2009-06-21
> **Favux said:**
> 
If the way forward requires an info callout to append touch to stylus or the reverse we'll most likely be stuck since you probably didn't compile linuxwacom with the libhal1-dev present (it isn't by default).  We found that prevented use of xorg.conf.  But maybe that is a bug, not by design.  Possibly the same bug I referenced earlier.  So this is a long shot and using xorg.conf is likely the only way that will work.

Is it just a matter of installing libhal1-dev and recompiling?  If so, I can try it out.  If there is an additional option that needs to be added to the configuration, just let me know and I can make the updates.

---

### Post by Ayuthia on 2009-06-21
I just remembered to look at Xorg.0.log and found the following:
```
WACOM: touch max value(s) was wrong MaxTouchY = 0 MaxTouchY = 0.
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

```
So that is why the touch portion is not working when using the .fdi.

---

### Post by Ayuthia on 2009-06-21
> **Favux said:**
> 
Rather than:

stylus = "HID 1b96:0001" in the "HID 1b96:0001"	id=7	[XExtensionKeyboard] line and

touch = "HID 1b96:0001" in the "HID 1b96:0001"	id=6	[XExtensionDevice] line, or vice versa

I suspect it may be more complicated.  And the reason wacomcpl isn't working is because those aren't linuxwacom device names so:
```
xsetwacom list
```
would be blank. 

I was able to get the wacomcpl portion to recognize the stylus by adding the following to the ntrig stylus section of the fdi:
```
<merge key="info.product" type="string">stylus</merge>
```

I just know need to figure out how to fix the MaxTouchY value.

---

### Post by Favux on 2009-06-21
Hi Ayuthia,

I'm doing something similar.  I should look at this for another couple of hours but I've had it.  My eyes are glazed over and I'm cooked so I'll just throw out what I have.

Just replace the current 10-wacom.fdi with this after backing it up somewhere safe.  And then cross your fingers and toes.

If you get the Xorg.O.log problem with the MaxTouchY value thing try putting the coordinates in the stylus section.

---

### Post by Ayuthia on 2009-06-21
The info that you just posted is what I currently have.  I have tried changing the MaxTouchY values and it does not change.  I am going to have to look at it later.  Somehow the xorg.conf info is passing the values to the system better.

---

### Post by Ayuthia on 2009-06-21
I decided to try out one more thing before stopping.  I switched the order that the stylus and touch were identified in xorg.conf and found out that X will crash.  So this is why the .fdi is not working.  The touch is being identified first so the touch fails.

Is there a way to get HAL to identify the stylus first, then the touch?

---

### Post by Favux on 2009-06-21
Hi Ayuthia,

I thought I reversed the order in the .fdi and put stylus first.  I also changed the match identifications to try and be sure to pull up the correct HAL sections.  Did I upload the wrong thing?

---

### Post by Favux on 2009-06-21
Hi Ayuthia,

I though I had a link to the 0.5.2 HAL spec.  Can't find it.  So here's the 0.5.1 HAL spec.

[http://people.freedesktop.org/~david/hal-spec/hal-spec.html](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)

[http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi](http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi)

---

### Post by Ayuthia on 2009-06-21
> **Favux said:**
> Hi Ayuthia,

I thought I reversed the order in the .fdi and put stylus first.  I also changed the match identifications to try and be sure to pull up the correct HAL sections.  Did I upload the wrong thing?

No, the information looks correct and in the correct order.  HAL still finds the touch portion first and tries to apply it.  X.org rejects it and then applies the stylus.

Thanks for the links to the HAL specs.  I will try to take a look at them later today.

---

### Post by Favux on 2009-06-21
Hi Ayuthia,

OK, the parent is:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial'

The first daughter is:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if2'
  it's a
usb.product = 'USB Interface'  (string)
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.2'  (string)

The second daughter is:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'
  it's a
usb.product = 'USB HID Interface'  (string)
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1'  (string)

Then comes two sub-daughter sections where I guess the .fdi is attempting to configure touch:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_hiddev'
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/usb/hiddev1'  (string)
  and
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input7/event7'  (string)

Finally the third daughter:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'
  it's also a
usb.product = 'USB HID Interface'  (string)
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0'  (string)

And it's two sub-daughter sections configuring stylus:
> udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_hiddev'
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/usb/hiddev0'  (string)
  and
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  with
linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input6/event6'  (string)

I don't know why there are three daughters.  I don't know why they are listed in this order.  But since HAL lists 'if2' first is it seeing it first?

So 'if1' and 'if0' seem to be stylus and touch.  How did you choose 'if0' for stylus and 'if1' for touch?  The lshal you posted was with your .fdi that you posted correct?  Have you looked at a lshal with no 10-wacom.fdi (N-trig) present?  Or one with the default Jaunty N-trig subsection in the 10-wacom.fdi present?  Your lshal looks similar to Keeper of the Keys in post #103 although the order is different.  The default wacom.fdi was configuring stylus in 'if0'.

I'm wondering what would happen if we changed the 'if*' assignment.  Say 'if1' stylus and 'if0' touch.  Or even trying 'if2' as touch.  And I'm back to wondering if with N-trig are they both suppose to be on the same path?  Maybe treating one as a subdevice and appending it to the other.  That would seem to conflict with how the linuxwacom drivers want things and that may be the problem.  And why it works in xorg.conf.

It seems to me we're back to the discussion Keeper of the Keys and I had from post #94 to #121 on this thread.  Maybe you can figure out where we got stuck.

---

### Post by Ayuthia on 2009-06-24
I have added the 64-bit .deb files for the 2.6.28-13-generic kernel in this link:
[http://ubuntuforums.org/showpost.php?p=7486766&postcount=158](http://ubuntuforums.org/showpost.php?p=7486766&postcount=158)

Like the 32-bit version, the linuxwacom package needs to be patched and the xorg.conf file still needs to be used.

The only thing that I have found so far with the .fdi and xorg.conf files is that the xorg.conf is using only one /dev/input/eventX where the .fdi version reflects that there are two different /dev/input/eventX versions.  If the system uses evdev, both the if1 version is for the touch and works like a mouse touchpad.  However, if1 does not seem to work with the wacom.  My guess is that the data is not laid out correctly for the touch when if1 is used.

If there is a way to get the if0 one to use the touch and stylus while having the system ignore the if1, it might work.  Hopefully this makes some sense.  Too many late nights...

---

### Post by Favux on 2009-06-24
Hi Ayuthia,

Sounds like a lot of work.  It also seems it has been productive.  I'm sure the important thing is the 64-bit .deb files.  That should be a lot of help to HP TX2z users.

I think I'm following you and it makes sense.  You may have already looked at the following possibilities.  Hopefully there's something useful in them.

The simplest and "naive" approach is to assume the N-trig logic will handle things.  So in the test 1 .fdi I just define both devices (stylus and touch) in their own sections, both 'if0'.  We've seen that it may matter which order they are in.  So maybe the order stylus and touch appear in needs to be flipped.  The same may apply to the coordinates.

In the second test .fdi I assume that one or the other needs to be a sub-device appended to the other.  The same caveat applies.  Maybe stylus should be appended to touch.  Maybe the coordinates should then be with stylus.

You may also want to change the match lines.

---

### Post by Favux on 2009-07-04
Hi everyone,

Sorry, I should have mentioned earlier that Ayuthia and myself have given up on getting a .fdi to work.  We'll have to settle for the xorg.conf in Jaunty.  I guess we feel the "infrastructure" isn't quite complete enough to allow a n-trig .fdi to configure the n-trig digitizer correctly.

Of course I'd love to be proven wrong!

---

### Post by Favux on 2009-07-05
Hi Ayuthia and eveyone,

After poking around a little I wonder if the problem doesn't localize to hal-setup-wacom.c.  Apparently it installs to "/usr/lib/hal/hal-setup-wacom".  Ron at Debian posted a new version on 4-19-09 under the title "Enable X Options to be set on the secondary devices also" here:  [http://git.debian.org/?p=users/ron/wacom-tools.git;a=commit;h=a13e95da64013d403037d907c1932e5ff3181dfb](http://git.debian.org/?p=users/ron/wacom-tools.git;a=commit;h=a13e95da64013d403037d907c1932e5ff3181dfb)  The source code is here:  [http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob;f=linuxwacom/src/util/hal-setup-wacom.c;h=71f863e615acd9fb2d06eaaa847cb42447e02359;hb=a13e95da64013d403037d907c1932e5ff3181dfb](http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob;f=linuxwacom/src/util/hal-setup-wacom.c;h=71f863e615acd9fb2d06eaaa847cb42447e02359;hb=a13e95da64013d403037d907c1932e5ff3181dfb)

Failing getting Rafi Rubin to look at this and fix it if it is the problem I wonder...  Could the 0.8.3-6 linuxwacom version be more "advanced" than the Jaunty 0.8.2-2's.  What would happen if you compiled the 0.8.3-6 hal-setup-wacom.c and copied hal-setup-wacom over the 0.8.2-2 version?  Would it break the rest of 0.8.2-2?  Would it be an improvement in terms of setting up the .fdi?

I doubt this is worth pursuing.  But I felt motivated to share.

---

### Post by Ayuthia on 2009-07-16
I have created the patch for the touch portion so that the cursor will follow the finger when the finger is touched on the screen.  I have created a different post for this one because the hid-ntrig.c-2.6.28-13-generic.patch is not a backport, but one created.  It differs slightly from the 0001-ntrig-tool-separation-and-pen-usages.patch that was created by Rafi Rubin. 

To extract the file:
```
tar -xvjf ntrig-v3.tar.bz2
```
It will extract the files into a folder called ntrig.  You will need to download the source by using this [guide]("https://help.ubuntu.com/community/Kernel/Compile").

Once you have downloaded the source, you can then go into the source directory:
```
cd linux-2.6.28
```
You will then need to copy the patches into this directory:
```
sudo cp ../ntrig/*.patch .
```
You will then need to copy the hid-ntrig.c in the proper place:
```
sudo cp ../ntrig/drivers/hid/hid-ntrig.c drivers/hid/hid-ntrig.c
```

Now the patches need to be applied:
```
sudo patch -p1 < hid-core.c-2.6.28-13-generic.patch
sudo patch -p1 < hid.h-2.6.28-13-generic.patch
sudo patch -p1 < hid-ids.h-2.6.28-13-generic.patch
sudo patch -p1 < input.c-2.6.28-13-generic.patch
sudo patch -p1 < input.h-2.6.28-13-generic.patch
sudo patch -p1 < Kconfig-2.6.28-13-generic.patch
sudo patch -p1 < Makefile-2.6.28-13-generic.patch
sudo patch -p1 < hid-ntrig.c-confidence-2.6.28-13-generic.patch
```

You can then update the config files (from the kernel compile guide) and then compile the kernel.

**If you want the .deb version**
Here are the 2.6.28-13.45 kernels with the patches applied:

32-bit:
[linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.45_i386.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-headers-2.6.28-13-generic_2.6.28-13.45_i386.deb")

To install them:
```
sudo dpkg -i linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb
sudo dpkg -i linux-headers-2.6.28-13-generic_2.6.28-13.45_i386.deb
```

64-bit:
[linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb")

To install them:
```
sudo dpkg -i linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb
sudo dpkg -i linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb
```

EDIT:  I have made a new update to this set.  It includes some changes that will allow you to be able to rest your palm on the screen while you are writing.  It is not perfect yet, but it does create the odd lines from the pen to your palm.[ATTACH]122437[/ATTACH]

---

### Post by gunghogarrett on 2009-07-16
Hi everyone, 

I've been following this thread and it's been a great help!  But, unfortunately, I still can't get anything to work perfectly.  I have a tx2 1025dx and have 9.04 running.  Out of the box, the stylus works perfectly other than the right-click button.  HOwever, after applying some of the patches on this thread, I was able to get the touch to work, sort of like a touchpad.  But there's no clicking, and i can't just touch something i want to select.  I have to drag the arrow over.   This configuration also screwed up the stylus, so that it does the same thing.  

It appears that things were moving in the right direction, so that I can now actually get the touch to respond, but it's still not useable.  

If it would be possible, I'd really appreciate a step-by-step guide from someone who's gotten it to work.  I'm still quite in the learning phases with ubuntu, so any help would be great!  

Thanks all!

---

### Post by synace on 2009-07-18
> **Ayuthia said:**
> 
64-bit:
[linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb")

do we still have to comment out n-trig in the fdi file? that's what got things working for me finally.

---

### Post by synace on 2009-07-18
> **gunghogarrett said:**
> Hi everyone, 

I've been following this thread and it's been a great help!  But, unfortunately, I still can't get anything to work perfectly.  I have a tx2 1025dx and have 9.04 running.  Out of the box, the stylus works perfectly other than the right-click button.  HOwever, after applying some of the patches on this thread, I was able to get the touch to work, sort of like a touchpad.  But there's no clicking, and i can't just touch something i want to select.  I have to drag the arrow over.   This configuration also screwed up the stylus, so that it does the same thing.  

It appears that things were moving in the right direction, so that I can now actually get the touch to respond, but it's still not useable.  

If it would be possible, I'd really appreciate a step-by-step guide from someone who's gotten it to work.  I'm still quite in the learning phases with ubuntu, so any help would be great!  

Thanks all!

try following this post:
[http://ubuntuforums.org/showpost.php?p=7612924&postcount=84](http://ubuntuforums.org/showpost.php?p=7612924&postcount=84)

also, you can try the new debs too: [http://ubuntuforums.org/showpost.php?p=7625055&postcount=186](http://ubuntuforums.org/showpost.php?p=7625055&postcount=186)

---

### Post by synace on 2009-07-18
> **Ayuthia said:**
> 
64-bit:
[linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb")
[linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb]("http://linuxfans.betaserver.org/packages/experimental/linux-headers-2.6.28-13-generic_2.6.28-13.45_amd64.deb")


thanks! this driver is transitioning between stylus/touch much better now. going to test suspend and rotation.

... suspend is good (touch was dead on login screen, stylus re-activated it though).

... rotation is good!

xsetwacom set touch touch off
xsetwacom set touch touch on
... is good!

much better.

2 more things and this driver is perfect:

a. when stylus is in play, automatically kill touch.
b. multi-touch (wishful thinking.. MPX isn't even integrated yet, is it?)


side note: i'm having problems with hibernate, likely related to the xorg configuration and/or fglrx

/etc/default/acpi-support
```

    SAVE_VBE_STATE=false

```

fixed hibernate for me w/ fglrx.

touch works!

---

### Post by Keeper of the Keys on 2009-07-20
Hello everyone, so I just downloaded Ayuthia's kernel build and am now happily touching away, thanks!

I was wondering though, my restricted modules seem to have decided that since this is not an official build they won't play nicely (which is annoying as wireless is in restricted). Is there a way other that now building my own restricted modules from source to make them play nicely?
It would seem to me that since the change for n-trig does not modify driver interaction it should be possible to just use the installed modules....

synace as far as multitouch is concerned you will probably have to wait a bit longer, however it has been implemented by some people in France (I think there is a link to their article somewhere higher up in the thread) as proof of concept in the 2.6.30/31 kernels, so in Ubuntu 9.10 which afaik will also feature MPX multitouch may just work....

---

### Post by Ayuthia on 2009-07-20
> **synace said:**
> 
2 more things and this driver is perfect:

a. when stylus is in play, automatically kill touch.
b. multi-touch (wishful thinking.. MPX isn't even integrated yet, is it?)


I am still looking into these two items.  For some reason, I am not getting the multitouch event to trigger so I am going to see if I can get a hold of Rafi Rubin to see what he knows about it.  I can see it in /dev/hidraw0, but the event never seems to come through.

The trick with 2a is that I am seeing sometimes the multitouch is triggered instead of the stylus.  If the stylus is triggered, I am thinking that it might be possible to turn off the touch, however if it is the other way around (the hand touches the screen before the stylus), it might be harder to track it down and flip off the touch.  

The other part of it is that we would most likely want that to be an option instead of something built-in.  If that is the case, it will have to be integrated in the linuxwacom portion.  So that might mean that we might need to fork from the linuxwacom so that we can get a working NTrig.  It would be hard to integrate NTrig changes with the Wacom and make sure that the Wacom portion is still stable.  I am trying to see if I can create this or not.  There is a lot of code in the Wacom portion that the NTrig does not need, but trying to figure out what is needed and what is not needed has been quite the challenge.

---

### Post by Ayuthia on 2009-07-20
> **Keeper of the Keys said:**
> Hello everyone, so I just downloaded Ayuthia's kernel build and am now happily touching away, thanks!

I was wondering though, my restricted modules seem to have decided that since this is not an official build they won't play nicely (which is annoying as wireless is in restricted). Is there a way other that now building my own restricted modules from source to make them play nicely?
It would seem to me that since the change for n-trig does not modify driver interaction it should be possible to just use the installed modules....

synace as far as multitouch is concerned you will probably have to wait a bit longer, however it has been implemented by some people in France (I think there is a link to their article somewhere higher up in the thread) as proof of concept in the 2.6.30/31 kernels, so in Ubuntu 9.10 which afaik will also feature MPX multitouch may just work....

You might try the following:
```
sudo depmod -a
```
I have found that when I created and installed the .deb, it is not running the depmod -a automatically.  Because of that, the Broadcom STA module was not loading.  Is that your problem?  If not, let me know.

---

### Post by Keeper of the Keys on 2009-07-20
I think that was the problem... 
I just installed catalyst 9.6 which runs depmod -a and after that I again had access to the STA kernel module...

Thanks.

---

### Post by Ayuthia on 2009-07-25
> **synace said:**
> 
2 more things and this driver is perfect:

a. when stylus is in play, automatically kill touch.
b. multi-touch (wishful thinking.. MPX isn't even integrated yet, is it?)


I have been able to make some updates for item 2a.  I was able to figure out how one of the events in hid-ntrig.c (HID-DG-CONFIDENCE) works so I have incorporated that into a new patch and it can be found [here]("http://ubuntuforums.org/showpost.php?p=7625055&postcount=186").  It helps ignore some of the touch events that are coming through from the palm.  It appears that the firmware in the touchscreen is able to tell that it is not supposed to be there.  However, these changes are not perfect yet.  It will occasionally leave dots on the screen in Xournal (or any other stylus application).

Please let us know how it works for you if you try it out.

---

### Post by Vincent_Lin on 2009-07-27
Hi all,

Installed the patched 64 bit kernel and copied in xorg.conf.

1. I need to install fglrx driver again then the xorg.conf would work.
2. pen and touch both work fine.  A tap of finger would not trigger touch, but a slight move(slide) of finger on screen makes it work.

Pretty impressive.  Thanks a lot.

A multi-touch capability would be fun indeed.  

Thanks again.

Vincent

---

### Post by Nimless on 2009-07-27
> **Vincent_Lin said:**
> Hi all,

Installed the patched 64 bit kernel and copied in xorg.conf.

1. I need to install fglrx driver again then the xorg.conf would work.
2. pen and touch both work fine.  A tap of finger would not trigger touch, but a slight move(slide) of finger on screen makes it work.

Pretty impressive.  Thanks a lot.

A multi-touch capability would be fun indeed.  

Thanks again.

Vincent


Be sure to have the 2.6.28-13.45 patched kernel , since the problem with taps has been solved :-P

---

### Post by Mike_H on 2009-07-28
This is fantastic, but I'm having two odd problems. This first is that the cursor breaks whenever I use the stylus or touch. The graphic gets all corrupted and weird.

The second is that the rotate script won't work because for some reason, xrandr stops the screen from updating. The cursor will move on stylus or touch, but its the only thing on the screen being updated. In order to get back to normal, I have to blindly do an alt-f2 and run xrandr -o normal. Any idea why these are happening?

---

### Post by Nimless on 2009-07-28
> **Mike_H said:**
> This is fantastic, but I'm having two odd problems. This first is that the cursor breaks whenever I use the stylus or touch. The graphic gets all corrupted and weird.

Never heard of this problem before,are you using a custom cursor or something like that?
> **Mike_H said:**
> 
The second is that the rotate script won't work because for some reason, xrandr stops the screen from updating. The cursor will move on stylus or touch, but its the only thing on the screen being updated. In order to get back to normal, I have to blindly do an alt-f2 and run xrandr -o normal. Any idea why these are happening?

What script are using to rotate? Try with the script i attached that someone made on another thread ,credit to him :P .

---

### Post by ktechkio on 2009-07-28
Ubuntu 8.10? Why not 9.04.

8.10 is quite old now!

---

### Post by Keeper of the Keys on 2009-07-28
If you would have read the thread you would have seen that it has long since moved into 9.04 (even before 9.04 was released).

[SIZE="1"]Maybe the name of the thread should be changed or a new thread...[/SIZE]

My custom kernel (from this thread) was recently replaced by stock again... I am in doubt whether to switch back or maybe I 'll try to patch...

BTW as far as weird quircks are concerned I found that when I tap the same location on the screen multiple times in a row the cursor may jump and 'click' somehwere totally different on the screen....

---

### Post by Mike_H on 2009-07-28
> **Nimless said:**
> Never heard of this problem before,are you using a custom cursor or something like that?

Nope, it is a fresh install. Strange thing is, when using the trackpad, the cursor is fine. First time I use stylus on a reboot, it corrupts the cursor. Its purely cosmetic but still really annoying. It seems to be the exact same bug as this: [https://bugzilla.redhat.com/show_bug.cgi?id=498738]("https://bugzilla.redhat.com/show_bug.cgi?id=498738")


> **Nimless said:**
> What script are using to rotate? Try with the script i attached that someone made on another thread ,credit to him :P .

I was using that same script. I'm going to try to update to the newest ATI drivers and see if that helps any. It seems very much a video driver issue.

---

### Post by Favux on 2009-07-28
Hi Mike_H,

Did you comment out the n-trig subsection of the 10-wacom.fdi?

For rotation did you use the aticonfig command?  Are you using Compiz?

---

### Post by anonymusius on 2009-08-04
To the Ayuthia post with the n-trig patch in it.
Your links are broken. Seems like the files were moved or deleted.

I also tried compiling with the n-trig patch you provided, the last file was misstyped and the patched linked to somewhere else. I think I did it correctly in the end, but failed to install the produced deb's (More likely because I don't really know what I'm doing compiling kernels then because of your patch).

So could you please provide new 64 bit n-trig patched kernels?

---

### Post by Ayuthia on 2009-08-04
> **anonymusius said:**
> To the Ayuthia post with the n-trig patch in it.
Your links are broken. Seems like the files were moved or deleted.

I also tried compiling with the n-trig patch you provided, the last file was misstyped and the patched linked to somewhere else. I think I did it correctly in the end, but failed to install the produced deb's (More likely because I don't really know what I'm doing compiling kernels then because of your patch).

So could you please provide new 64 bit n-trig patched kernels?

I talked with the person who is letting me use this site and found that everything was deleted.  He does not think that the host company is going to recover it for us so I am going to need to find another place to store them.  Does anyone know where I might be able to place the .deb files?

---

### Post by synace on 2009-08-05
could you create a PPA or something like that?

side note: is anyone putting this code in up-stream into the next kernel?

---

### Post by Ayuthia on 2009-08-05
> **synace said:**
> could you create a PPA or something like that?

side note: is anyone putting this code in up-stream into the next kernel?

I'll have to study the PPA a little more before I can start placing things there. 

As for the changes being submitted, I have not done that yet because I need to contact Rafi Rubin to see if his changes were accepted or not.  I am not for sure which version I need to create my diff file.

---

### Post by Nimless on 2009-08-05
> **Ayuthia said:**
> I'll have to study the PPA a little more before I can start placing things there. 

As for the changes being submitted, I have not done that yet because I need to contact Rafi Rubin to see if his changes were accepted or not.  I am not for sure which version I need to create my diff file.

I think making a quick guide for patching the ubuntu kernel source would be better instead of finding an host for the debs :P

---

### Post by Ayuthia on 2009-08-06
> **Nimless said:**
> I think making a quick guide for patching the ubuntu kernel source would be better instead of finding an host for the debs :P

The 2.6.28-16.55 version is now available.  Here is a [guide]("http://linuxfans.keryxproject.org/?page_id=6") for those who want to compile it on their own.  Please reply here if you have any questions about the guide.

For those who want the deb files:

**32-bit**
[linux-image-2.6.28-16-generic_2.6.28-16.55_i386.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-image-2.6.28-16-generic_2.6.28-16.55_i386.deb")
[linux-headers-2.6.28-16-generic_2.6.28-16.55_i386.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-headers-2.6.28-16-generic_2.6.28-16.55_i386.deb")

**64-bit**
[linux-image-2.6.28-16-generic_2.6.28-16.55_amd64.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-image-2.6.28-16-generic_2.6.28-16.55_amd64.deb")
[linux-headers-2.6.28-16-generic_2.6.28-16.55_amd64.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-headers-2.6.28-16-generic_2.6.28-16.55_amd64.deb")

This version does come with a revised version of the hp-wmi patch so if you want to use Red_Lion's rotate script, you will need to change:
```
/sys/devices/platform/hp-wmi/dock
```
to
```
/sys/devices/platform/hp-wmi/tablet
```

If your Broadcom wireless card stops working after you start up with this kernel, please do the following:
```
sudo depmod -a
```and you can restart or if you just want to load the wl.ko module yourself (you won't need to after this one time):
```
sudo modprobe wl
```and after several seconds, NetworkManager should find the wireless site and connect.

---

### Post by Keeper of the Keys on 2009-08-06
Just in case something happens again I copied the kernel packages to my server:
[http://kotk.nl/tx2stuff](http://kotk.nl/tx2stuff)

md5sums:
```

1c4aba65c651c415f56a5bbbdb3c435c  linux-headers-2.6.28-14-generic_2.6.28-14.47_amd64.deb
8eff74c1da2e569dc48da7573f1bb9b3  linux-headers-2.6.28-14-generic_2.6.28-14.47_i386.deb
d25f4fd64ccb19011166d4f384d60447  linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb
65535a6906bb3e772a916917e8378ea9  linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb

```

---

### Post by Favux on 2009-08-08
Hi everyone,

The Auto-magic Rotation HOW TO (swivel hinge triggered) is here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  If you use Ayuthia's kernel deb.s you'll have to make a couple changes to the script.  His deb.s include the patched HP-WMI and the changes he alludes to are further described near the bottom of the HOW TO.

---

### Post by nema.arpit on 2009-08-09
Did anyone compile the 2.6.30 kernel for tx2? I am having trouble with it.It compiles and installs fine ( I think ) but post installation,during boot up it just dies.... .After the ubuntu splash screen it just shows a scrambled screen; similar to what I get if xorg.conf is messed up. Any ideas?
I do have the proprietary ATI drivers installed (catalyst 9.7).

In case anyone's wondering,I need to compile the kernel to get the cpufreq modules.... this machine needs to be undervolted to survive :(

Also does any one have the inbuilt mic working? And temperature sensors? 
I only have the hddtemp sensors listed in gnome-sensors ,nothing else. I have the following packages installed related to sensors: digitemp,libsensors(3,4),lm-sensors,mbmon,xmbmon.

---

### Post by Keeper of the Keys on 2009-08-09
afaik the kernels newer than .28 are still not supported by fglrx (Catalyst) so if you want to use them you should stick to recompiling .28, if you don't care for the propriatary drivers you could remove them (with the --purge option so nothing gets left behind) and use radeonhd or ati....

As far as touch goes the patches that we are applying to the .28 kernel should have been merged with .30 and newer.

---

### Post by nema.arpit on 2009-08-09
Thanks a lot for the clarification.
Any ideas for the temperature issue? Could it be a hardware fault? In windows 7 HWmonitor detects at least the temps of the cores....

---

### Post by Ayuthia on 2009-08-09
> **nema.arpit said:**
> Thanks a lot for the clarification.
Any ideas for the temperature issue? Could it be a hardware fault? In windows 7 HWmonitor detects at least the temps of the cores....

This is just a guess, but I am thinking that the issue is with the ATI driver.  I thought that I saw in some threads somewhere in this forum, xorg 1.6 is not playing well with the catalyst driver also.  They downgraded to 1.5.

I am seeing that my laptop runs cooler in Gentoo than in Ubuntu.  This is based on the feel of the laptop and not with any temp sensor.  I have just recently installed xorg-server to 1.6 but I have not seen any issues yet.  I also do have a patched up version of the fglrx driver that I am using so that could be the other difference.  I have not tried patching the Ubuntu fglrx driver to see if it will perform better.

As for temperature sensors, I have not tracked down that information in the system yet.  I know that lm-sensors cannot find the info yet and the hdtemp seems to be in the hp-wmi section but it has not been reporting anything either.

---

### Post by nema.arpit on 2009-08-12
The step to download the patch in the guide is a bit incorrect
step 2 should be :
```
wget linuxfans.keryxproject.org/packages/experimental/ntrig-v4.tar.bz**2**
```

Also if i want to configure the kernel after which step should I run xconfig or menuconfig?

---

### Post by Nimless on 2009-08-12
> 
Also if i want to configure the kernel after which step should I run xconfig or menuconfig?

I haven't been able to configure my own kernel with that method, but i think you need to manually edit the .config files for your architecture otherwise the debian/rules script will complain if you make a custom .config.

Maybe someone else can help you better :-P

---

### Post by nema.arpit on 2009-08-12
Would this work:
```
[SIZE=2]cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
make xconfig
make-kpkg clean
CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-mk kernel_image kernel_headers modules_image
[/SIZE]
```I picked it up from the master kernel thread......

---

### Post by Nimless on 2009-08-12
> **nema.arpit said:**
> Would this work:
```
[SIZE=2]cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
make xconfig
make-kpkg clean
CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-mk kernel_image kernel_headers modules_image
[/SIZE]
```I picked it up from the master kernel thread......

If your point is to make a custom kernel patched for N-trig it will work, if you're trying to have a kernel with same name-version as Ubuntu official one to keep the restricted modules it won't ;)

---

### Post by Favux on 2009-08-12
Hi nema.arpit,

> And temperature sensors?
I only have the hddtemp sensors listed in gnome-sensors ,nothing else. I have the following packages installed related to sensors: digitemp,libsensors(3,4),lm-sensors,mbmon,xmbmon.
It's possible your DSDT is part of the problem.

Red_Lion submitted a decompiled TX2500 DSDT to 67GTA on his "Re: HOWTO Fix A Buggy DSDT File" thread.  He compiled and optimized it and said:
> Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 18 Optimizations

I fixed a warning that kept the kernel from reading your CPU temps. It should run quieter/cooler.
You may want to look into that at:  [http://ubuntuforums.org/showthread.php?t=1036051&page=25&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=1036051&page=25&highlight=tx2*)

Although I should point out earlier on post #571 and 573 here:  [http://ubuntuforums.org/showthread.php?t=845911&page=58](http://ubuntuforums.org/showthread.php?t=845911&page=58)  tannalv said:
> Ok. Try adding acpi_osi="!Windows 2006".
! means "not", i.e. you are NOT booting "windows 2006" (Vista).
Simple as that. No decompiling of DSDT needed. . .
However now you have thermal and everything else that you need.

---

### Post by Ayuthia on 2009-08-12
> **nema.arpit said:**
> The step to download the patch in the guide is a bit incorrect
step 2 should be :
```
wget linuxfans.keryxproject.org/packages/experimental/ntrig-v4.tar.bz**2**
```

The page is now updated to reflect the bz2 extension.  Thanks for finding it!

---

### Post by Ayuthia on 2009-08-12
> **nema.arpit said:**
> Did anyone compile the 2.6.30 kernel for tx2? I am having trouble with it.It compiles and installs fine ( I think ) but post installation,during boot up it just dies.... .After the ubuntu splash screen it just shows a scrambled screen; similar to what I get if xorg.conf is messed up. Any ideas?
I do have the proprietary ATI drivers installed (catalyst 9.7).

In case anyone's wondering,I need to compile the kernel to get the cpufreq modules.... this machine needs to be undervolted to survive :(

Also does any one have the inbuilt mic working? And temperature sensors? 
I only have the hddtemp sensors listed in gnome-sensors ,nothing else. I have the following packages installed related to sensors: digitemp,libsensors(3,4),lm-sensors,mbmon,xmbmon.

I tried the folowing in my boot parameters(without recompiling the DSDT file):
```
acpi_osi="Linux"
```
based on the information that Favux recommended:
[http://ubuntuforums.org/showpost.php?p=6527653&postcount=1](http://ubuntuforums.org/showpost.php?p=6527653&postcount=1)

It was able to find that /proc/acpi/thermal_zone/THRM now exists and provides the temperature information.  However, the trip_points information still shows that not all is reporting correctly yet.  I still have not found the CPU core temps yet though.

---

### Post by nema.arpit on 2009-08-13
So how do I make a custom kernel from the 2.6.28??
I could not find the .config file anywhere without running the **make xconfig** command.

---

### Post by Nimless on 2009-08-13
> **nema.arpit said:**
> So how do I make a custom kernel from the 2.6.28??
I could not find the .config file anywhere without running the **make xconfig** command.

You can find the .config files in /debian/config/i386 , you can manually edit them, i'm not sure if there is a way to do a make menuconfig.

---

### Post by nema.arpit on 2009-08-13
I would like to report that I have succeeded in adding the cpufreq modules into the 2.6.28-14.47 kernel by editing the config and config.generic files in debian/config/amd64 and debian/config/i386.Thank you nimless for the info.First kernel compile success=D>.

---

### Post by Nimless on 2009-08-14
> **nema.arpit said:**
> I would like to report that I have succeeded in adding the cpufreq modules into the 2.6.28-14.47 kernel by editing the config and config.generic files in debian/config/amd64 and debian/config/i386.Thank you nimless for the info.First kernel compile success=D>.

Good to hear :-) You're welcome

---

### Post by Snepscheut on 2009-08-16
Hello all,

As a proud owner of a HP TouchSmart tx2 I have been reading (a lot) on this forum and I have been trying a lot (downloading, installing, upgrading etc) to make this tabet work with pen and touch under linux (yes I don't like windows, though I must say sometimes I'm a bit jealous things working well :-( , sorry)

Reading this thread I understand you guys have the brains to make the tabet work.

Unfortunately I'm more an end user with not enough knowledge to understand what you are writing on how to implement a patch or howto recompile the kernel.

So my big question is: is there a kernel available witch I easily can install and if so how do I get it?

If there is no kernel available in the "mainstream?" can someone make me one (64 bit) or if you find this to easy for me (or lazy) can you please provide me with the needed files and a (very) simple howto for compiling the kernel myself.

With a big PLEASE and thanks,

Greetings,

Jos vd Snepscheut.

---

### Post by Nimless on 2009-08-16
> **Snepscheut said:**
> Hello all,

As a proud owner of a HP TouchSmart tx2 I have been reading (a lot) on this forum and I have been trying a lot (downloading, installing, upgrading etc) to make this tabet work with pen and touch under linux (yes I don't like windows, though I must say sometimes I'm a bit jealous things working well :-( , sorry)

Reading this thread I understand you guys have the brains to make the tabet work.

Unfortunately I'm more an end user with not enough knowledge to understand what you are writing on how to implement a patch or howto recompile the kernel.

So my big question is: is there a kernel available witch I easily can install and if so how do I get it?

If there is no kernel available in the "mainstream?" can someone make me one (64 bit) or if you find this to easy for me (or lazy) can you please provide me with the needed files and a (very) simple howto for compiling the kernel myself.

With a big PLEASE and thanks,

Greetings,

Jos vd Snepscheut.

Hi!

Check this post for the updated kernel .debs patched for the N-trig digitizer

[http://ubuntuforums.org/showpost.php?p=7741663&postcount=209](http://ubuntuforums.org/showpost.php?p=7741663&postcount=209)

Check this post for the xorg.conf modifications for the TX2

[http://ubuntuforums.org/showpost.php?p=7488294&postcount=159](http://ubuntuforums.org/showpost.php?p=7488294&postcount=159)

Last one download the patched wacom from here Rene Mayrhofer page :

32 version [http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb](http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb)

64 version [http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_amd64.deb](http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_amd64.deb)

---

### Post by Snepscheut on 2009-08-16
> **Nimless said:**
> Hi!

Check this post for the updated kernel .debs patched for the N-trig digitizer

[http://ubuntuforums.org/showpost.php?p=7741663&postcount=209](http://ubuntuforums.org/showpost.php?p=7741663&postcount=209)

Check this post for the xorg.conf modifications for the TX2

[http://ubuntuforums.org/showpost.php?p=7488294&postcount=159](http://ubuntuforums.org/showpost.php?p=7488294&postcount=159)

Last one download the patched wacom from here Rene Mayrhofer page :

32 version [http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb](http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_i386.deb)

64 version [http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_amd64.deb](http://www.mayrhofer.eu.org/downloads/misc/latitude-xt/xserver-xorg-input-wacom_0.8.1.4-0ubuntu3.rm1_amd64.deb)

Hi Nimless!

Thank you for the fast reply.
I followed your steps:
step 1 dowloading and installing .deb files no problem
step 2 reconfigure xorg.conf took me some time (trying, log off log on reboot etc) but now with this:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for HP TX2z.  Switch comments if you have the Dell Latitude XT.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
#   The by-path below is for the HP TX2z
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
        Option          "Touch"         "on"
        Option          "Mode"          "Absolute"
#	Option		"USB"		"on"
#	Option		"Button2"	"3"	# make stylus button R mouse click
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
#   The by-path below is for the HP TX2z
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"Touch"		"on"
        Option          "Supress"       "0"
        Option          "Mode"          "Aboslute"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
#   The line below is for the Dell Latitude XT (ATI Radeon Xpress 1250 Integrated Graphics)
#	Option		"UseFBDev"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"	# New for Jaunty?  For TX2z not XT?
#	Identifier	"Default Layout"	# Not needed in Jaunty?  For XT not TX2z?
#	Screen		"Default Screen"	# Not needed in Jaunty?  For XT not TX2z?
	InputDevice	"stylus"	        #"SendCoreEvents"
	InputDevice	"touch"		        #"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
#   Dell XT "UseFBDev" line default in video Section per Nimless. 

pen and touch are working quite well but sometimes double tapping brings the cursor on top of the screen (Do I need to adjust something?)

3 step Installing the patched wacom from here Rene Mayrhofer
gives me an error "newer version already installed" something like that.

But as I wrote things are working, so thank you AGAIN for making it possible for me to make this work!!! :guitar:

And now do I dare ask you for also understandable instructions for the magic-rotation of the screen?

This would be great!

Tanks and greetings

Jos.

---

### Post by Nimless on 2009-08-16
Hi!

For magic rotation you mean a script to rotate the screen? 

If so check my post here [http://ubuntuforums.org/showpost.php?p=7691549&postcount=199](http://ubuntuforums.org/showpost.php?p=7691549&postcount=199) and the attached script there.

You can then put an icon on the panel/desktop or a keyboard shortcut for launching it.

---

### Post by Snepscheut on 2009-08-16
> **Nimless said:**
> Hi!

For magic rotation you mean a script to rotate the screen? 

If so check my post here [http://ubuntuforums.org/showpost.php?p=7691549&postcount=199](http://ubuntuforums.org/showpost.php?p=7691549&postcount=199) and the attached script there.

You can then put an icon on the panel/desktop or a keyboard shortcut for launching it.

Hello, your very fast!

And yes the script works.... but the cursor is not following witch makes it like a game to work with the pen and touch :lolflag:

What I really meant is how to make the screen rotate when one rotates the display (hing rotation?)

Maybe you can help me with that?

Jos.

---

### Post by Nimless on 2009-08-16
> **Snepscheut said:**
> Hello, your very fast!

And yes the script works.... but the cursor is not following witch makes it like a game to work with the pen and touch :lolflag:

What I really meant is how to make the screen rotate when one rotates the display (hing rotation?)

Maybe you can help me with that?

Jos.

What do you mean the cursor is not following?

Have you installed wacom-tools?

```

sudo apt-get install wacom-tools

```

For the Hinge rotation you should really contact Ayuthia, since he made a daemon and a script to make it work, i don't use that since manual rotation works for me :-P

---

### Post by Favux on 2009-08-16
Hi Snepscheut,

The auto-magic rotation HOW TO is on post #225 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  Since you have Ayuthia's kernel deb.s the patched hp-wmi is already included.  So use the info. near the bottom of the HOW TO to modify the script for your use.

Did you comment out the n-trig subsection of the 10-wacom.fdi?

---

### Post by Snepscheut on 2009-08-16
> **Nimless said:**
> What do you mean the cursor is not following?

Have you installed wacom-tools?

```

sudo apt-get install wacom-tools

```

For the Hinge rotation you should really contact Ayuthia, since he made a daemon and a script to make it work, i don't use that since manual rotation works for me :-P

Hello,

You're right again: wacom-tool does the trick!

Tanks,

Jos

---

### Post by Snepscheut on 2009-08-16
> **Favux said:**
> Hi Snepscheut,

The auto-magic rotation HOW TO is on post #225 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  Since you have Ayuthia's kernel deb.s the patched hp-wmi is already included.  So use the info. near the bottom of the HOW TO to modify the script for your use.

Did you comment out the n-trig subsection of the 10-wacom.fdi?

Hello Favux,

Thanks for pointing me to the hing-rotation.

I didn't comment out in 10-wacom but I did now.

Although modprobe -l | grep hp-wmi gives me:
kernel/drivers/misc/hp-wmi.ko I cannot find /sys/devices/platform/hp-wmi
So no hing-rotation working now

In the tail of /var/log/messages I find
Aug 16 23:47:22 jos-laptop kernel: [   27.762665] Buran hp-wmi eventcode: 1
and
Aug 16 23:47:10 jos-laptop kernel: [   11.860393] input: HP WMI hotkeys as /devices/virtual/input/input11
with the pc in tablet-mode starting up

So hp-wmi seems to be present?

Maybe I have to change the script at this point?
 if [[ -e /sys/devices/platform/hp-wmi/dock ]]; then

I hope you have any clou because I don't have....

Greetings and thanks,

Jos

---

### Post by Favux on 2009-08-16
Hi Snepscheut,

Did you change 'dock' to 'tablet' and 4 to 1 like it says to near the bottom of the HOW TO?

---

### Post by Keeper of the Keys on 2009-08-20
Anyone been playing with karmic yet?

I tried the alpha-3 live cd last month but that wouldn't even boot yet...
Just got a4....

---

### Post by Keeper of the Keys on 2009-08-21
Alas regular live-cd booting still fails for me and I don't have a free partition at the moment to just install karmic from an alternate disc and try...

---

### Post by Ayuthia on 2009-08-21
I am working on it.  I was able to get it installed using daily live version.  I made the mistake of trying to get fglrx to run on it and spent a portion of the day cleaning that up.

---

### Post by Ayuthia on 2009-08-21
I have finally gotten it to work again.  It looks like linuxwacom-0.8.4 will need an additional patch at this point to get it to build correctly.  The current kernel is still missing one patch that will make the touch respond better.  However, since a lot of updates are there and only one patch is needed in hid-ntrig.c, it will be easier to just build the hid-ntrig.ko file to make things work.  We should not need to have to download an entire kernel .deb to add the functionality.

It was harder to get this working in Karmic mainly because the console terminals (control-alt-F1) does not work so whenever X crashes, it goes there and dies.

We still will need to use xorg.conf to configure the touch and stylus.  They have taken out the fdi entry so the touchscreen defaults to synaptic without the xorg.conf entry. 

For the swivel, it does look like the tablet entry is there so if you are using the automagic swivel script, it should work.

I am now going to see if I can get fglrx to work here.

---

### Post by Kiwinote on 2009-08-22
Hi there Ayuthia,

Good to hear that you got linuxwacom-0.8.4 to build in Karmic. I have been running Karmic on my tx2 for a while now, but got stuck when linuxwacom wouldn't build.

I have also opened a bug rapport to hopefully get linuxwacom-0.8.4 included in Karmic: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/405800](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/405800)

Would you perhaps be able to write a short guide to getting things running in Karmic? (Starting a new thread for Karmic may be a good idea.) If you need someone to test the guide, feel free to let me know.

Thanks a lot,
Kiwinote

---

### Post by Ayuthia on 2009-08-22
> **Kiwinote said:**
> Hi there Ayuthia,

Good to hear that you got linuxwacom-0.8.4 to build in Karmic. I have been running Karmic on my tx2 for a while now, but got stuck when linuxwacom wouldn't build.

I have also opened a bug rapport to hopefully get linuxwacom-0.8.4 included in Karmic: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/405800](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/405800)

Would you perhaps be able to write a short guide to getting things running in Karmic? (Starting a new thread for Karmic may be a good idea.) If you need someone to test the guide, feel free to let me know.

Thanks a lot,
Kiwinote

I will try to get one up within the next few days.  I am currently out of town so I am not for sure when I can get it written up.  Since Karmic has not been released yet, hopefully it will be easier to get linuxwacom-0.8.4 built.  I had to copy over the hid files from the kernel source and install autoconf and libtools.  xf86config does not seem to compile well in 2.6.31 so a patch was needed to get it to compile.  I will write this up a little better but I just wanted to let you know what other things I needed outside of the normal guide to make it work.

---

### Post by rorydog1 on 2009-08-23
Hi,

I have been following these forums and now have my touch and pen working on a tx2z however it seems that when I use Xournal to write and fingers touch the screen at the same time as the stylus the cursor jumps around or disables, which makes writing almost impossible. 

This is also the case with: 
xsetwacom set touch touch off 
and as an experiment I comment out InputDevice    "touch"                #"SendCoreEvents" in the xorg file. On startup the touch is dead but the stylus works, yet in Xournal drawing with the stylus and touching the screen with fingers or the plam at the same time will still cause the cursor to jump around randomly. This makes me think that maybe the multitouch may be causing bad events.

FYI: I did a clean install of 9.04, then downloaded Ayuthia patched kernel 2.6.28-14.47. Next I changed my xorg file to the one used by Snepscheut from post# 229 in this thread (see the end of this post for a copy)

I used the default ubuntu version of xserver-xorg-input-wacom 1:0.8.2.2-0ubuntu2 and this works.

I tried with the ntrig section and the ntrig section commented out in the10-linuxwacom.fdi file but this had no effect on the jumping in Xournal

Apart for taking notes, this setup is working great now and having touch working under Ubuntu on this laptop is really cool. Congratulations to everyone who worked so hard to get all this working.

Here is a copy of the Xorg file:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for HP TX2z.  Switch comments if you have the Dell Latitude XT.

Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
#   The by-path below is for the HP TX2z
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "stylus"
        Option          "Touch"         "on"
        Option          "Mode"          "Absolute"
#    Option        "USB"        "on"
#    Option        "Button2"    "3"    # make stylus button R mouse click
EndSection

Section "InputDevice"
    Identifier    "touch"
    Driver        "wacom"
#   The by-path below is for the HP TX2z
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "touch"
    Option        "USB"        "on"
    Option        "Touch"        "on"
        Option          "Supress"       "0"
        Option          "Mode"          "Aboslute"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "9600"
    Option        "BottomY"    "7200"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
#   The line below is for the Dell Latitude XT (ATI Radeon Xpress 1250 Integrated Graphics)
#    Option        "UseFBDev"    "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"    # New for Jaunty?  For TX2z not XT?
#    Identifier    "Default Layout"    # Not needed in Jaunty?  For XT not TX2z?
#    Screen        "Default Screen"    # Not needed in Jaunty?  For XT not TX2z?
    InputDevice    "stylus"            #"SendCoreEvents"
    InputDevice    "touch"                #"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
#   Dell XT "UseFBDev" line default in video Section per Nimless.

---

### Post by Nimless on 2009-08-23
> **rorydog1 said:**
> 

This is also the case with: 
xsetwacom set touch touch off 

 

Hi!

Be sure you have wacom-tools installed
```

sudo apt-get install wacom-tools

```

> **rorydog1 said:**
> 

I used the default ubuntu version of xserver-xorg-input-wacom 1:0.8.2.2-0ubuntu2 and this works.



You should use the patched wacom version, see my post here 

[http://ubuntuforums.org/showpost.php?p=7795415&postcount=228](http://ubuntuforums.org/showpost.php?p=7795415&postcount=228)

and download and install the .debs

---

### Post by Favux on 2009-08-23
Hi rorydog1,

We already fixed this one, you just need to toggle touch off when using Xournal.  See first post on this page:  [http://ubuntuforums.org/showthread.php?t=1206355&page=9](http://ubuntuforums.org/showthread.php?t=1206355&page=9)  And read throught the page.  There's a couple of slants on how to do it.

---

### Post by Favux on 2009-08-23
Hi everyone,

I would appreciate it if someone with an XT and TX2z could show me the relevant sections of the:
```
more /proc/bus/input/devices
```
output.  Or if you're not sure, the whole thing.

I'm looking for the n-trig Vendor and Product ID's.  I'm wondering if the problem with getting a .fdi to work isn't due to the symlink in udev.  And if you know where the n-trig symlink is I would appreciate you posting it so I can take a look.

---

### Post by Ayuthia on 2009-08-23
> **Favux said:**
> Hi everyone,

I would appreciate it if someone with an XT and TX2z could show me the relevant sections of the:
```
more /proc/bus/input/devices
```
output.  Or if you're not sure, the whole thing.

I'm looking for the n-trig Vendor and Product ID's.  I'm wondering if the problem with getting a .fdi to work isn't due to the symlink in udev.  And if you know where the n-trig symlink is I would appreciate you posting it so I can take a look.

Here is mine:
```

I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9
U: Uniq=
H: Handlers=mouse2 event9
B: EV=1b
B: KEY=2c03 1 0 0 0 0
B: ABS=73000001000003
B: MSC=10

```

I think the issue with the .fdi is mainly due to the fact that the stylus and touch are currently sharing the same udi.  I think that HAL only takes the last entry only for that udi.  I could be wrong about this though.

---

### Post by Kiwinote on 2009-08-23
Here is the whole thing for a tx2 (with an additional wireless keyboard & mouse) in karmic:
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
U: Uniq=
H: Handlers=event3 
B: EV=21
B: SW=1

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=20000 20 0 0 500f02100003 3803078f900d401 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:12.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:12.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input8
U: Uniq=
H: Handlers=kbd mouse1 event8 
B: EV=1f
B: KEY=837fff042c332f bf08444400000000 ff0001 1f848a37cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=1b
B: KEY=2401 0 0 0 0 0
B: ABS=73000001000003
B: MSC=10

I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input10
U: Uniq=
H: Handlers=mouse3 event10 
B: EV=1b
B: KEY=2401 0 0 0 0 0
B: ABS=73000001000003
B: MSC=10

I: Bus=0003 Vendor=064e Product=a104 Version=0320
N: Name="HP Webcam"
P: Phys=usb-0000:00:13.2-2/button
S: Sysfs=/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11
U: Uniq=
H: Handlers=kbd event11 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input12
U: Uniq=
H: Handlers=mouse4 event12 
B: EV=b
B: KEY=420 70000 0 0 0 0
B: ABS=11000003

I: Bus=0001 Vendor=10ec Product=0268 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:14.2/input/input13
U: Uniq=
H: Handlers=kbd event13 
B: EV=40001
B: SND=6

```

---

### Post by Favux on 2009-08-23
Hi Ayuthia and Kiwinote,

Thank you!  Now if I could get the XT.  Nimless?

> I think the issue with the .fdi is mainly due to the fact that the stylus and touch are currently sharing the same udi. I think that HAL only takes the last entry only for that udi.
And you could very well be right.

Seeing the n-trig symlink would be good.

It's just it took the LWP and Debian folks a couple of months to figure out how to add the symlink for wacom tablets with touch, so it wasn't trivial.  I'm not saying they worked on it full time or anything.  But what if we pattern a n-trig symlink on the wacom one they came up with?  HAL is generating, I think, two extra sections.  One looks like it is suppose to be touch and we tried including it in the test .fdi's we made.

And Kiwinote is showing two sections!
```
I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=1b
B: KEY=2401 0 0 0 0 0
B: ABS=73000001000003
B: MSC=10

I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input10
U: Uniq=
H: Handlers=mouse3 event10 
B: EV=1b
B: KEY=2401 0 0 0 0 0
B: ABS=73000001000003
B: MSC=10

```

Edit:  And not surprisingly '1b96' isn't in the '50-xserver-xorg-input-wacom.rules' symlink table.

---

### Post by Favux on 2009-08-23
Hi everyone,

Basically I want to try adding:
```
ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001",  SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"
```
To the big symlink table in &#8220;50-xserver-xorg-input-wacom.rules&#8221; at "/etc/udev/rules.d/".  By the way in Jaunty it's now located in "/lib/udev/rules.d/" instead of "/etc/udev/rules.d/" and I think they changed the 50 to 40.  Like so:
```
KERNEL!="event[0-9]*", GOTO="wacom_end"

# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"

# Multiple interface support for stylus and touch devices.
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="00", ENV{WACOM_TYPE}="stylus"
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="01", ENV{WACOM_TYPE}="touch"[/QUOTE]

Then there is a big table of symlinks including two tablet pc's with touch, one of which is mine:

ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0093",  SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="009a",  SYMLINK="input/tablet-tpc9a-$env{WACOM_TYPE}"
ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001",  SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"

And then to finish:

# Convenience links for the common case of a single tablet.  We could do just this:
#ATTRS{idVendor}=="056a", SYMLINK+="input/wacom-$env{WACOM_TYPE}"
# but for legacy reasons, we keep the input/wacom link as the generic stylus device.
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}=="touch", SYMLINK+="input/wacom-touch"

# Check and repossess the device if a module other than the wacom one
# is already bound to it.
ATTRS{idVendor}=="056a", ACTION=="add", RUN+="check_driver wacom $devpath $env{ID_BUS}"

LABEL="wacom_end"
```

Edit:  And then the 90-hal.rules copies everything in udev/rules.d to HAL, I think.

---

### Post by Favux on 2009-08-23
Hi Ayuthia and everyone,

But there may be a problem with:
```
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"
```
and several other lines.  I don't know if it's possible to add another vendor to the ATTRS.

You may have to redo everything with the N-trig info. and construct your own symlink rules.  I think the READ ME says you add custom .rules to the old location.  So something like '90-n-trig.rules'?

It seems to me you'll have to do something like this anyway if you are going to fork the linuxwacom drivers for N-trig, especially to add multi-touch.

---

### Post by Nimless on 2009-08-23
Hi Favux ! 

This is mine for the Latitude XT

```

I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:13.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=1b
B: KEY=2c03 0 1 0 0 0 0 0 0 0 0
B: ABS=730000 1000003
B: MSC=10

```

Windows 7 firmware here

---

### Post by Favux on 2009-08-23
Hi Nimless,

Thank you!  And thanks for specifying Win 7 firmware.  That's going to change the input, mouse, and event I imagine.

So the TX2z & XT have the same Vendor and Product id's, even the same Version.

---

### Post by Favux on 2009-08-24
Hi everyone,

The problem is a lot of folks are blowing up X installing the xorg.conf.  Video section errors will do it and so will using the wrong usb by-path, whether XT for TX2z, or vice versa, or Vista v.s. Win 7 firmware.  There may be other things going on but I can't pin them down.  If we get a symlink working we should be able to prevent the usb by-path problems.  Then it won't matter if you have an XT or TX2z or which firmware you're using.  That seems worthwhile by itself.

This (the wacom version) worked for me.  Call it 90-n-trig.rules (locate in /etc/udev/rules.d/).  I think 90 is OK based on the READ ME.:
```
# Link N-trig USB tablet to "/dev/input/wacom"
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK="input/wacom"
```
And use in the xorg.conf instead of the by-path:
```
	Option "Device" "/dev/input/wacom"
```
Well it worked for the stylus and eraser anyway, not touch.  Be interesting to see what it does for the n-trig.

Next I tried:
```
# Link N-trig USB tablet to "/dev/input/wacom" & "/dev/input/wacom-touch"
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK+="input/wacom"
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK+="input/wacom-touch"
```
And changing the touch section symlink in xorg.conf to:
```
	Option		"Device"	"/dev/input/wacom-touch"
```
This time touch actually worked until I used the stylus.  Sound familiar?  Looking back I wonder if the syntax is wrong.  Maybe?:
```
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK="input/wacom"
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK+="input/wacom-touch"
```
It would be fun to try this one on the n-trig also.

A useful reference is Writing Udev Rules:  [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)  Of course it would help to have the output of udevinfo for the n-trig digitizer (need the sysfs device path) to construct these.

Back to the mystery.  What I would like to know is what does this mean?:
```
# Port specific link for users of multiple tablets of the same type.
# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"
```
This is in the Intrepid 50-xserver-xorg-input-wacom.rules at the beginning and the Jaunty 40-xserver-xorg-input-wacom.rules.  My guess is the "earlier rule file" they are talking about is 20-names.rules in Intrepid.  It seems to set up how the usb device is to be "handled", among other devices.  But 20-names.rules isn't there in Jaunty.  There are some new files in /lib/udev/, one of which is usb_id.  Maybe that's it?  It must be somewhere in there since the comment and line is the same.  Do the rules it (or the Jaunty equivalent) sets up make a difference in how the linuxwacom code interacts with wacom.ko v.s. n-trig.ko?   And does that then matter to HAL?  Or maybe I should be asking does that make a difference to the linuxwacom hal-setup-wacom?  So touch in a n-trig .fdi isn't picked up?  Or is it how the code handles things or because the n-trig is on the same usb by-path/uid?

But then where are the extra HAL sections in lshal coming from?  They do have different udi's and linux.sysfs_path's. with the udi's labeled _if0, _if1, like the Wacom usb tablet pc's.  And then there is of course the mystery _if2.

---

### Post by Keeper of the Keys on 2009-08-25
> **Favux said:**
> Hi Nimless,

Thank you!  And thanks for specifying Win 7 firmware.  That's going to change the input, mouse, and event I imagine.

So the TX2z & XT have the same Vendor and Product id's, even the same Version.
To the best of my knowledge the DuoSense is N-trigs' first commercial product and the only difference between the XT(2) and the tx2z is the stylus (the XT(2) has 2/3 buttons on the stylus adding the eraser function)...

---

### Post by Favux on 2009-08-25
Hi Keeper of the Keys,

I can see why the XT and TX2z have the same digitizer.  So the same Vendor and Product id make sense, but the same Version surprised me.  So you're saying you think the new XT2 still has the same digitizer, even to version?  I thought it was newer and so would have a different Product id.  Something with the n-trig circuitry at least being updated to support the eraser.  And you say the eraser is actually a second stylus button (on the side of the stylus)?  So the n-trig still won't have an eraser with pressure?

Well the n-trig digitizer they are manufacturing with Fujitsu has to be a new version, doesn't it?

---

### Post by Keeper of the Keys on 2009-08-25
Favux,
The xt(2) has an eraser, it is only the tx2z that does not...

What Fujitsu has I don't know....

---

### Post by Nimless on 2009-08-25
> **Favux said:**
> Hi Keeper of the Keys,

I can see why the XT and TX2z have the same digitizer.  So the same Vendor and Product id make sense, but the same Version surprised me.  So you're saying you think the new XT2 still has the same digitizer, even to version?  I thought it was newer and so would have a different Product id.  Something with the n-trig circuitry at least being updated to support the eraser.  And you say the eraser is actually a second stylus button (on the side of the stylus)?  So the n-trig still won't have an eraser with pressure?

Well the n-trig digitizer they are manufacturing with Fujitsu has to be a new version, doesn't it?

It will be a different version because it's going to support 10 fingers or more i heard, ours support less :P

---

### Post by Ayuthia on 2009-08-25
> **Nimless said:**
> It will be a different version because it's going to support 10 fingers or more i heard, ours support less :P

From what I have been reading, it looks like the 10 fingers is going to be a firmware upgrade.

I think that the main difference will be with firmware versions.  The  Windows 7 version that I have (4.3.6.8.5) is able to work with up to four fingers.  The Vista version (3.5.9.8.5) only supported two fingers.  There were some prior Windows 7 versions where the pen does not work.

---

### Post by Favux on 2009-08-25
Hi everyone,

Let me get this straight:
```
HP TX2z		ID's	Vendor=1b96	Product=0001	Version=0110
Dell XT		ID's	Vendor=1b96	Product=0001	Version=0110
Dell XT(2)	ID's	Vendor=1b96	Product=0001	Version= ?
```
```
HP TX2z		AMD dual core		1 stylus button		no eraser
Dell XT		Intel core 2 duo	1 stylus button		no eraser
Dell XT(2)	Intel core 2 duo	1 stylus button		eraser (stylus button)
```
So in addition to updating the motherboard, video, CPU, etc. the XT(2) has a new stylus button/eraser?  But it's the same digitizer?  Even to the version?

And a few months ago N-trig and Fujitsu announced the joint manufacturing of a new N-trig digitizer.  Well actually Fujitsu is going to manufacture N-trig's new design.

---

### Post by Ayuthia on 2009-08-25
I tried out the udev changes and found that the following works:
```
# Link N-trig USB tablet to "/dev/input/ntrig"
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", SYMLINK="input/ntrig"
```

I also made the changes in /etc/X11/xorg.conf for the stylus and touch to use:
```
	Option		"Device"	"/dev/input/ntrig"
```

I tried to use the ntrig-touch but when I did, the driver could not initialize the device.

---

### Post by Favux on 2009-08-25
Thank you Ayuthia!

Well I think the linuxwacom drivers are looking for 'wacom-touch'.  I originally tried just 'touch' until I realized they wanted 'wacom-touch' in xorg.conf.

So no change in functionality with the symlink?  In other words both stylus and touch work as before.  Good deal.  So at a minimum we can get around the by-path and firmware problems.  Hopefully.

I would kinda like to see what using 'wacom' does, if anything.  And of course 'wacom-touch' if anyone wants to try it.

And then maybe trying in the .fdi something like:
```
<merge key="input.x11_options.Device" type="string">/dev/input/wacom</merge>
```
for the stylus section and for the touch section:
```
<merge key="input.x11_options.Device" type="string">/dev/input/wacom-touch</merge>
```
Just a thought.  I know I'm getting ahead of things.

---

### Post by Ayuthia on 2009-08-25
I'll try those in a little bit.  I think the difficulty is going to be those that have the Vista firmware in use.  There is not too much that distinguishes the two different events (except that one is producing data and the other is not).

I was able to get some udev info for the N-Trig device by using udevadm:
```
sudo udevadm info --path=/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9/event9 --query=all
```I grabbed the path by using the linux-sysfs-path from lshal.  Here were my results:
```
P: /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9/event9
N: input/event9
S: input/ntrig
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9/event9
E: MAJOR=13
E: MINOR=73
E: DEVNAME=/dev/input/event9
E: ID_VENDOR=1b96
E: ID_VENDOR_ENC=1b96
E: ID_VENDOR_ID=1b96
E: ID_MODEL=0001
E: ID_MODEL_ENC=0001
E: ID_MODEL_ID=0001
E: ID_REVISION=0000
E: ID_SERIAL=1b96_0001
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:000000:
E: ID_USB_INTERFACE_NUM=01
E: ID_USB_DRIVER=usbhid
E: ID_CLASS=mouse
E: ID_PATH=pci-0000:00:14.5-usb-0:2:1.1
E: DEVLINKS=/dev/input/ntrig

```

Based on that information above, the following:
```
# Port specific link for users of multiple tablets of the same type.
# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"
```appears to take all the the wacom tablets and creates symlinks that include their ID-PATH as a prefix before -wacom.  So my device would look like:
```
/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-wacom
```At least that is my guess on it.  However I do have to say that the ID_PATH for my device is quite long.  Hopefully the wacom tablets are smaller in length.

---

### Post by Ayuthia on 2009-08-25
> **Favux said:**
> 
I would kinda like to see what using 'wacom does', if anything.  And of course 'wacom-touch' if anyone wants to try it.

Here are the results by changing them to wacom/wacom-touch and using xorg.conf:
```
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
BEGIN xf86WcmProc dev=0x2c77a50 priv=0x2c6bfd0 type=eraser(touch) flags=16642 fd=-1 what=INIT
xf86WcmDevOpen
opening /dev/input/wacom-touch
(**) Option "Device" "/dev/input/wacom-touch"
usbDetect
touch Wacom X driver can't grab event device, errno=16
initializing USB tablet
(**) /dev/input/wacom-touch: Touch is enabled
WACOM: touch max value(s) was wrong MaxTouchY = 0 MaxTouchY = 0.
Failed to open device (fd=-1)
xf86WcmProc INIT FAILED
(EE) Couldn't init device "touch"
xf86WcmUninit
(II) UnloadModule: "wacom"

```Most likely the .fdi will produce the same results.  I can try them if you still would like to know.

---

### Post by Favux on 2009-08-25
Thanks Ayuthia,

Stymied!

So maybe 'wacom' and 'wacom-touch' are invoking wacom.ko also?  Which is why 'n-trig', invoking n-trig.ko, works?  I'll have to look at your stuff above some more.  I wonder what would happen if you removed wacom.ko? 

It probably won't work trying to sneak the n-trig symlinks into the udev wacom.rules.  The manual says:
> This is to demonstrate that while it is legal to combine the attributes from the device in question and a single parent device, you cannot mix-and-match attributes from multiple parent devices - your rule will not work.
But it also says you can:
> Rename a device node from the default name to something else
Now to the heart of it.  Could n-trig.ko be renamed wacom.ko by a symlink?  Probably not.  Would linuxwacom/HAL then interact with it correctly?  Probably not.  Or would it just sever communication from the digitizer.  Probably.

If you want to, for fun, you could try the .fdi lines.  It should tell us something.

Edit:  Oh, and you changed the symlink from SYMLINK="input/ntrig" to SYMLINK="input/wacom", correct?  And for the wacom-touch Option in xorg.conf to have a chance of working there'd have to be a second symlink ending in wacom-touch, of course.

---

### Post by Ayuthia on 2009-08-25
> **Favux said:**
> Thanks Ayuthia,

Stymied!

So maybe 'wacom' and 'wacom-touch' are invoking wacom.ko also?  Which is why 'n-trig', invoking n-trig.ko, works?  I'll have to look at your stuff above some more.  I wonder what would happen if you removed wacom.ko? 

It probably won't work trying to sneak the n-trig symlinks into the udev wacom.rules.  The manual says:

But it also says you can:

Now to the heart of it.  Could n-trig.ko be renamed wacom.ko by a symlink?  Probably not.  Would linuxwacom/HAL then interact with it correctly?  Probably not.  Or would it just sever communication from the digitizer.  Probably.

If you want to, for fun, you could try the .fdi lines.  It should tell us something.

I have a customized version of linuxwacom where I have removed the wacom.ko file out and the wacom driver for xorg still works for the N-Trig device.

As for sneaking in the n-trig symlinks to the wacom file, I don't think that it really matters (at least for the n-trig devices).  It is just a symlink to the event file.  From what I can tell, it looks like the touch device is tied into the stylus somewhere in the wacom code because the touch cannot be started without having the stylus initializing it.  Whenever the touch is using a different event than the stylus, it keeps failing during the initialization stage.

---

### Post by Favux on 2009-08-25
Hi Ayuthia,

> From what I can tell, it looks like the touch device is tied into the stylus somewhere in the wacom code because the touch cannot be started without having the stylus initializing it. Whenever the touch is using a different event than the stylus, it keeps failing during the initialization stage.
Thank you again.  Enlightening as usual.

---

### Post by Ayuthia on 2009-08-25
> **Favux said:**
> 
If you want to, for fun, you could try the .fdi lines.  It should tell us something.
The .fdi lines still do not work (with the wacom and wacom-touch changes).  With the Windows 7 firmware, it uses the same udi (if1) so whatever is the last entry in the .fdi file is the one that it uses.  So I tried it first with the stylus first and Xorg.0.log fails for the touch and there is no entry for the stylus.  When I tried it with the touch first, Xorg.0.log ignored the touch but the stylus works.


> Edit:  Oh, and you changed the symlink from SYMLINK="input/ntrig" to SYMLINK="input/wacom", correct?  And for the wacom-touch Option in xorg.conf to have a chance of working there'd have to be a second symlink ending in wacom-touch, of course.
I did change the symlink to "input/wacom" and "input/wacom-touch".  The links for both of them showed up in /dev/input/.

---

### Post by Favux on 2009-08-25
Hi Ayuthia,

Not surprising from what you said earlier.

Well at least we now have a symlink for n-trig like the wacom folks have.

---

### Post by Keeper of the Keys on 2009-08-25
Sorry I am quickly skipping all the conversation will read it tomorrow I guess...

I just wanted to point out several things:

Our digitizer supports at least 5 (probably 10 and possibly even more) fingers. Back when Dell was showing off the XT(1) and telling everyone about how the digitizer actually supported multi-touch and they just had to add OS/software support to it they showed a demo app to prove it which basically only showed what the digitizer was sensing (ie. a bunch of dots on a grid). I distinctly remember at least one and possibly two whole hands being demonstrated.
It is the synaptic multi-touch digitizers for cellphones that were limited to two fingers until recently.

As far as the eraser is concerned, to the best of my knowledge the XT1 also has one, there is a section in the FAQ of n-trig about "why does my device lack an eraser" in which they explain that that is purely due to what the OEM (hp) ordered.

Edit:
Found a youtube video, this is one of the first demos of the latitude XT, at 1:30 they show 5 fingers concurrently, tehy don't go beyond that in the movie...:
[http://www.youtube.com/watch?v=00mKTEqnzbs](http://www.youtube.com/watch?v=00mKTEqnzbs)

---

### Post by Favux on 2009-08-25
Hi Keeper of the Keys,

Thanks for helping clear that up.  Is the eraser on the XT and XT(2) a "button" on the back of the stylus where a regular eraser would be?  It retracts into the stylus barrel?  And gives you pressure in Gimp like the stylus tip does?

---

### Post by Keeper of the Keys on 2009-08-26
Favux,
I don't know exactly how it works as I don't own an XT, my budget only allowed for a tx2.
However all reviews, sources and videos mention the eraser.

As a side note I just found out you could use the XT stylus on the tx2 an like that you gain an eraser:
[http://reviews.dell.com/2341-en_bm/412-1042/reviews.htm](http://reviews.dell.com/2341-en_bm/412-1042/reviews.htm)

---

### Post by Ayuthia on 2009-08-28
I have compiled the 2.6.28-15-generic versions and they are now available.  I have updated the previous [2.6.28-14-generic post]("http://ubuntuforums.org/showpost.php?p=7741663&postcount=209") to reflect the new kernel version.

---

### Post by Nimless on 2009-08-28
> **Ayuthia said:**
> I have compiled the 2.6.28-15-generic versions and they are now available.  I have updated the previous [2.6.28-14-generic post]("http://ubuntuforums.org/showpost.php?p=7741663&postcount=209") to reflect the new kernel version.

Thanks!

---

### Post by Favux on 2009-08-28
Hi everyone,

Because things are admittedly kind of scattered I posted a little HOW TO.  Hopefully it will make things easier for folks setting up for the first time.  It's located here:  [http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)

It would be greatly appreciated if you felt free to participate and help posters.  Needless to say feedback would be good.  I'm sure there's a lot on it that can be improved.

Thanks.

---

### Post by Keeper of the Keys on 2009-08-29
Hi All,
I just noticed a few things that may have been addressed but I don't remember so...
It seems that the patched kernel does not turn of sound output to speakers when headphones are plugged in.
And also (though I am less sure of this one) the remote seems to cease working....

Also I updated the mirrored files...

---

### Post by Ayuthia on 2009-08-30
> **Keeper of the Keys said:**
> Hi All,
I just noticed a few things that may have been addressed but I don't remember so...
It seems that the patched kernel does not turn of sound output to speakers when headphones are plugged in.
And also (though I am less sure of this one) the remote seems to cease working....

Also I updated the mirrored files...

I just tested out the sound for the 32 and 64 bit.  The 32-bit had no problems but the 64-bit needed me to disconnect the jack and then reconnect it so that it will work.  I am going to try it again with the unpatched kernel to see if there is a difference.

---

### Post by Ayuthia on 2009-08-30
I just tested the 64-bit with the Ubuntu supplied kernel (without the patches) and the issue was duplicated.  

As for the remote, I did not test it with any media applications, but with xev and all the keys responded.  I did learn today that you should pay attention to which button you push.  My first key that I pressed was the power button...

---

### Post by Keeper of the Keys on 2009-08-31
What I mean is that when you plug in headphones on an unpatched kernel it mutes the front channel on the patched one it did not seem to do that, I will recheck tomorrow....

As far as the remote is concerned I am less sure it could be that it just kicked the bucket for no good reason or that the battery dies, anyone any idea how long it's supposed to last? (I barely use the remote)

Favux, is this still the 'main' tx2 thread or should we be moving to the new one you created?

---

### Post by Favux on 2009-08-31
Hi Keeper of the Keys,

Up to you.  I don't see why we can't have two.  Actually there were at least three or four more threads going before I put up the HOW TO.

My thought is that it is mainly for folks just setting up.  But it doesn't have to be only that.  I'm hoping you and others will help out people posting there.

---

### Post by Keeper of the Keys on 2009-09-02
I'm happily puzzled both problems I described above have gone away :)

---

### Post by iboot on 2009-09-08
Anyone set up an on-screen keyboard for tx2z? I would like to know how to get one to show up during the login screen. I am using onboard.

Thanks!

---

### Post by Keeper of the Keys on 2009-09-11
Cellwriter as an onscreen keyboard, but that's not available at the gdm stage I think.

If you have a fingerprint scanner you can use that, though I find that the annoying position of the scanner makes making two identical scans very hard.

---

### Post by otakuj462 on 2009-09-23
Hi,

First, my apologies for cross-posting this in a new thread. I'm running out of time, and if I can't get this issue resolved soon, a Vista reinstall seems likely.

My question is, does anyone have any information on how to get audio capture to work with the headphone jack under Jaunty? I've set "options snd-hda-intel model=toshiba" in alsa-base.conf, and audio playback now works flawlessly, but sound capture still does not work at all. I've tried arecord, gnome-sound-recorder, and Skype, and none of these programs successfully capture audio.

I'd appreciate any guidance anyone can offer. Thanks,

Jake

Update 09/23/09 1:49AM: Capture seems to be working better now. I'm still using the same alsa-base.conf. gnome-sound-recorder is working great when I use an external mic; it can't seem to capture any audio from the internal mic, though. Skype and arecord, however, only capture very muffled, unintelligible audio that's full of static. If it was just Skype, I would say that it was just a Skype problem, but because Skype and arecord are manifesting the same symptoms, it seems likely to be something deeper than that.

---

### Post by iboot on 2009-11-04
Hi,

I have installed 9.10 (fresh install) on my ** HP tx2z**. Before, when I was running on 9.04 "touch" input was working. After 9.10 installation, I am not able to get touch to work. I updated the xorg.conf but I can't install the kernel debs due to the follwing error in the package installer status:

Error: Dependency is not satisfiable: linux-headers-2.6.28-16

Any help is greatly appreciated.

Thanks!

---

### Post by Favux on 2009-11-04
Hi iboot,

Karmic has kernel 2.6.31.  And other things changed too.  See this [HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by iboot on 2009-11-06
> **Favux said:**
> Hi iboot,

Karmic has kernel 2.6.31.  And other things changed too.  See this [HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

Hi Favux,

I installed the kernel patches but on reboot, the system recycled itself with a blank screen on startup. I booted with CD and commented out /etc/X11/xinit/xinirc file but I still could not recover from the kernel patch. I am now reinstalling karmic 9.10.

Is there a safer way to do this or is the kernel patch required to get touch to work?

Thanks.

---

### Post by Favux on 2009-11-06
Hi iboot,

There's only the one kernel patch for Karmic using the hid-ntrig.c-confidence.patch to generate the hid-ntrig.ko.  Try one of the pre-compiled ones for your 2.6.31 kernel.  They're linked the the "1) Karmic: Patching hid-ntrig.c with hid-ntrig.c-confidence.patch & compiling linuxwacom" section.

Could you be using the Jaunty (2.6.28 ) patches?

---

### Post by iboot on 2009-11-06
Hi Favux,

I tried the pre-compiled one with identical result. As soon as the patch is applied, the blank screen recycle begins and I have to reinstall OS.

Is there a set of instructions starting from a fresh install of 9.10?

Thanks.

---

### Post by Favux on 2009-11-07
Hi iboot,

That HOW TO should apply to a fresh install.  Have you installed Win7 on your TX2z?  You haven't changed the xorg.conf yet?  What it sounds like is that for the first time it happened is you had the wrong  usb pci by-path in the xorg.conf for the n-trig firmware you have installed.

Also are you using 64-bit or 32-bit?

Have you tried commenting out the n-trig section of the 10-linuxwacom.fdi (if it's there) before changing the hid-ntrig.ko?

On this [thread]("http://ubuntuforums.org/showthread.php?t=1310611") akand074 seems to have a similar problem, although he updated rather than doing a fresh install.

I wonder if you have a corrupted Ubuntu install disk?

---

### Post by iboot on 2009-11-07
Hi Favux,

Is there a quick command line way to recover to original state after applying the kernel patch if I get the same problem? Reinstalling ubuntu takes a while and then I have to reinstall my apps too.

My xorg is attached. What sections do I need to add for just pen and touch? I don't have eraser and don't need rotation.

I did not install win 7. I am using 32 bit. I found the fdi file under /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi. It is attached. I will try commenting the n-trig sections. I don't think the ubuntu install cd is curropt since it installs without errors.

So from a fresh install, I should I patch the kernel or just apply the pre-compiled one? Do I need to comment out n-trig before applying kernel patch?

Thanks!

---

### Post by Favux on 2009-11-08
Hi iboot,

```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko $HOME
sudo depmod -a
```
The first line moves/removes the module and the second line rebuilds the module list.  Remember with the patch to hid-ntrig.c and then compiling the hid-ntrig.ko you are not patching the kernel.  The .ko indicates that it is a kernel module/driver.

So the only windows you've ever had on your system is Vista?  You didn't test out Win7 rc or anything, did you?  See that would change the n-trig firmware and cause the sort of boot failure you describe if the wrong line is used in the xorg.conf.

If you use a pre-compiled hid-ntrig.ko make sure it is for your exact kernel:
```
cat /proc/version_signature
```
and your bit, 32 or 64:
```
uname -m
```
There's been some problems with the 32-bit hid-ntrig.ko.  But Ayuthia thinks he's fixed it in his latest instructions.  So maybe you should try patching.

Answer the questions and let me know when you've done a fresh install and we'll go from there.  You might want to check if there is stylus activity with the fresh install before we do anything.

---

### Post by iboot on 2009-11-09
Hi Favux,

I have installed 9.10 fresh and am ready to begin the patch.

cat /proc/version_signature
Ubuntu 2.6.31-14.48-generic-pae




uname -m
i686


I never tried Win7. Just wiped out the oem vista install and installed 9.04 with dedicated root partition and separate /home. On each fresh install of 9.10, I have mounted the old /home partition that I had installed under 9.04. I had touch and stylus working underr 9.04.

If there are problems with pre-compiled version, I can proceed with patching.

Now I can't test stylus since I have lost it. Just want to get touch for now and will test stylus once I have purchased a new one. Touch is a lot more useful for me.

Thanks!

---

### Post by Favux on 2009-11-09
Hi iboot,

OK.

It appears you're on 32-bit Ubuntu (i686) using the server kernel.  I gather the PAE (physical address extension) is enabled.  So you have more than 3.2 GB of memory?

I have no idea whether the n-trig stuff works with the server kernel.  I think you're the first person who has reported trying it.

---

### Post by iboot on 2009-11-10
Hi Favux,

I downloaded the desktop edition from ubuntu.com. How come it is the server kernel? Yes, I have 3.7 GB of available RAM on this machine according to the system monitor.

Thanks.

---

### Post by Favux on 2009-11-10
Hi iboot,

I don't know.  I thought that was something you were doing deliberately.  My guess was that's why the pre-compiled hid-ntrig.ko blew you up.  It was compiled to the wrong kernel, 32-bit -generic instead of 32-bit -generic-pae.  Did you enable pae?

It'll probably be OK if you compile it to your kernel, either way.

---

### Post by Ayuthia on 2009-11-10
I agree with Favux.  There should not be any problems with you manually compiling the kernel module with your current kernel.  I will say that I did update the patch because I ran into an issue with the kernel module not working in the 32-bit version.  However, I am pretty sure that the issue was with the compiler instead of the kernel itself so the current set of patches should work fine.  If for some reason it does not work, let us know and I can install the same version and test it out.

---

### Post by iboot on 2009-11-10
Hi Ayuthia,

Thanks for the confirmation. My plan is to execute the commands as documented by on:
[URL="http://linuxfans.keryxproject.org/?page_id=6"]
http://linuxfans.keryxproject.org/?page_id=6[/URL]
To patch the kernel with n-trig support

Then followed by the commands documented on:

[http://linuxfans.keryxproject.org/?page_id=44](http://linuxfans.keryxproject.org/?page_id=44)
To compile and install linuxwacom

Q: Will I need to make any changes to xorg.conf or **10-wacom.fdi**?

In case of failure and a need to revert, I can use the following to revert the patch:

sudo mv /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko $HOME
sudo depmod -a
Please let me know if my assumptions are faulty.

Thanks!

---

### Post by Ayuthia on 2009-11-11
> **iboot said:**
> Hi Ayuthia,

Thanks for the confirmation. My plan is to execute the commands as documented by on:
[URL="http://linuxfans.keryxproject.org/?page_id=6"]
http://linuxfans.keryxproject.org/?page_id=6[/URL]
To patch the kernel with n-trig support

Then followed by the commands documented on:

[http://linuxfans.keryxproject.org/?page_id=44](http://linuxfans.keryxproject.org/?page_id=44)
To compile and install linuxwacom

Q: Will I need to make any changes to xorg.conf or **10-wacom.fdi**?

In case of failure and a need to revert, I can use the following to revert the patch:

sudo mv /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko $HOME
sudo depmod -a
Please let me know if my assumptions are faulty.

Thanks!

You might want to configure the xorg.conf to contain:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        InputDevice    "stylus"
        InputDevice    "touch"
EndSection

Section "InputDevice"
        Identifier  "touch"
        Driver      "wacom"
        Option      "Mode" "Absolute"
        Option      "Type" "touch"
        Option      "Device" "/dev/input/eventX"
        Option      "MaxX" "9600"
        Option      "MaxY" "7200"
        Option      "ResX" "1280"
        Option      "ResY" "800"
        Option      "Touch" "on"
        Option      "USB" "on"
        Option      "TopX" "0"
        Option      "TopY" "0"
        Option      "BottomX" "9600"
        Option      "BottomY" "7200"
        Option      "Buttons" "5"
        Option      "Button1" "1"
        Option      "Button10" "1"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Mode" "Absolute"
        Option      "Type" "stylus"
        Option      "Device" "/dev/input/eventX"
        Option      "MaxX" "9600"
        Option      "MaxY" "7200"
        Option      "ResX" "1280"
        Option      "ResY" "800"
        Option      "Button2" "3"
        Option      "USB" "on"
EndSection


```
You will need to replace the event number with the one that corresponds to your system.  If you are not for sure, please post the results of:
```
ls -l /dev/input/by-path
```

---

### Post by iboot on 2009-11-11
Thanks Ayuthia. What should be EventX in my case? I assume it would be separate for the touch and stylus sections. Code results below.

```

$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 pci-0000:00:13.2-usb-0:2:1.0-event -> ../event9
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 pci-0000:00:14.5-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 pci-0000:00:14.5-usb-0:2:1.1-event-mouse -> ../event8
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 pci-0000:00:14.5-usb-0:2:1.1-mouse -> ../mouse2
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 10 2009-11-11 09:27 platform-i8042-serio-1-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2009-11-11 09:27 platform-i8042-serio-1-mouse -> ../mouse3


```

---

### Post by Favux on 2009-11-11
Hi iboot and Ayuthia,

It looks like /event7 to me.

I'm not sure using event is such a good idea.  At least in the past you haven't been able to rely on it being reproducible.

---

### Post by iboot on 2009-11-11
Hi Favux and Ayuthia,

I am getting some errors while attempting Step 6 of ntrig patch. Also what should I answer when previously applied patch is detected?

```

sudo patch -p1 < ../ntrig/hid-core.c.patch
patching file drivers/hid/hid-core.c
Hunk #1 FAILED at 1297.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-core.c.rej
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid.h.patch
patching file include/linux/hid.h
Hunk #1 succeeded at 274 with fuzz 2 (offset 36 lines).
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid-ids.h.patch
patching file drivers/hid/hid-ids.h
Reversed (or previously applied) patch detected!  Assume -R? [n] ^C
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid-core.c.patch
patching file drivers/hid/hid-core.c
Hunk #1 FAILED at 1297.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-core.c.rej

```

---

### Post by Ayuthia on 2009-11-11
> **iboot said:**
> Hi Favux and Ayuthia,

I am getting some errors while attempting Step 6 of ntrig patch. Also what should I answer when previously applied patch is detected?

```

sudo patch -p1 < ../ntrig/hid-core.c.patch
patching file drivers/hid/hid-core.c
Hunk #1 FAILED at 1297.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-core.c.rej
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid.h.patch
patching file include/linux/hid.h
Hunk #1 succeeded at 274 with fuzz 2 (offset 36 lines).
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid-ids.h.patch
patching file drivers/hid/hid-ids.h
Reversed (or previously applied) patch detected!  Assume -R? [n] ^C
lahiri@hptx2z:~/linux-2.6.31$ sudo patch -p1 < ../ntrig/hid-core.c.patch
patching file drivers/hid/hid-core.c
Hunk #1 FAILED at 1297.
1 out of 1 hunk FAILED -- saving rejects to file drivers/hid/hid-core.c.rej

```

Since you are using 2.6.31, you only need to use the hid-ntrig.c-confidence.patch.  The other patches should already be there.  Sorry about that.

---

### Post by iboot on 2009-11-11
Hi Ayuthia,

Step 7 is also failing:

```

$ sudo chmod 744 debian/scripts/misc/splitconfig.pl
chmod: cannot access `debian/scripts/misc/splitconfig.pl': No such file or directory

```

---

### Post by Ayuthia on 2009-11-11
> **iboot said:**
> Hi Ayuthia,

Step 7 is also failing:

```

$ sudo chmod 744 debian/scripts/misc/splitconfig.pl
chmod: cannot access `debian/scripts/misc/splitconfig.pl': No such file or directory

```

You should be able to skip that step.  The error message should come up on the next step and it will tell you where that file is located.

---

### Post by iboot on 2009-11-12
Hi Ayuthia,

I am getting an error in make

```

make[2]: *** [sub-make] Error 2
make[1]: *** [/home/lahiri/linux-2.6.31/debian/stamps/stamp-build-generic] Error 2
make: *** [binary-generic] Error 2

```

I also did not get any n/m/y questions mentioned on step 9.

Thanks.

---

### Post by Ayuthia on 2009-11-12
Maybe I should not drink coffee anymore.  If you are using the 2.6.31 kernel, you should only need to patch hid-ntrig.c and then do the following:
```
cd drivers/hid
make -C/lib/modules/$(uname -r)/build M=$(pwd) modules
```
You should not need to spend the time compiling the code (which will take about 1.5 hours or so).

---

### Post by iboot on 2009-11-13
Hi Ayuthia and Favux,

I was able to apply the changes, but I am now back to the same problem of screen recycling with login prompt. How do I recover? I am able to drop to the root shell but the recover command you provided does not seem to work.

mv: cannot stat '/lib/modules/2.6.31.-14-generic-pae': No such file or directory
mv: cannot stat '/kernel/drivers/hid/hid-ntrig.ko': No such file or directory

In my /lib/modules/2.6.31.-14-generic/build/drivers/hid directory I get the following files:

Kconfig
Makefile
usbhid (directory)

Thanks.

---

### Post by Ayuthia on 2009-11-13
> **iboot said:**
> Hi Ayuthia and Favux,

I was able to apply the changes, but I am now back to the same problem of screen recycling with login prompt. How do I recover? I am able to drop to the root shell but the recover command you provided does not seem to work.

mv: cannot stat '/lib/modules/2.6.31.-14-generic-pae': No such file or directory
mv: cannot stat '/kernel/drivers/hid/hid-ntrig.ko': No such file or directory

In my /lib/modules/2.6.31.-14-generic/build/drivers/hid directory I get the following files:

Kconfig
Makefile
usbhid (directory)

Thanks.

It looks like your move command might have had a space because it looks like there was a split between /lib/modules/2.6.31.-14-generic-pae and the /kernel... portion.  Try:
```
mv /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko $HOME
sudo depmod -a
```
again.

Do you have a /lib/modules/2.6.31-14-generic-pae/build/drivers/hid directory?  The one that you mentioned was 2.6.31-14-generic.  The reason why I ask is because it looks like the hid-ids.h file is not there.

---

### Post by iboot on 2009-11-13
Hi Ayuthia,

I tried the modified command and this time I get 1 error:

mv: cannot stat ' /lib/modules/$2.6.31-14-generic-pae/kernel/drivers/hid/hid-ntrig.ko' : No such file or directory.

> **Ayuthia said:**
> 
Do you have a /lib/modules/2.6.31-14-generic-pae/build/drivers/hid directory?  The one that you mentioned was 2.6.31-14-generic.  The reason why I ask is because it looks like the hid-ids.h file is not there.

The only directory under my /lib/modules is 2.6.31-14-generic

Thanks.

---

### Post by Ayuthia on 2009-11-14
> **iboot said:**
> Hi Ayuthia,

I tried the modified command and this time I get 1 error:

mv: cannot stat ' /lib/modules/$2.6.31-14-generic-pae/kernel/drivers/hid/hid-ntrig.ko' : No such file or directory.



The only directory under my /lib/modules is 2.6.31-14-generic

Thanks.

Something does not look right.  Based on [packages.ubuntu.com]("http://packages.ubuntu.com/karmic/i386/linux-image-2.6.31-14-generic-pae/filelist"), you should have a /lib/modules/2.6.31-14-generic-pae.

You might try reinstalling linux-image-2.6.31-14-generic-pae to see if you can get the modules back.

---

### Post by iboot on 2009-11-16
> **Ayuthia said:**
> Something does not look right.  Based on [packages.ubuntu.com]("http://packages.ubuntu.com/karmic/i386/linux-image-2.6.31-14-generic-pae/filelist"), you should have a /lib/modules/2.6.31-14-generic-pae.

You might try reinstalling linux-image-2.6.31-14-generic-pae to see if you can get the modules back.

Hi Ayuthia,

Ok. I have reinstalled Ubuntu 9.10 using ubuntu-9.10-desktop-i386.iso downloaded from ubuntu.com. I don't have a /lib/modules/2.6.31-14-generic-pae.

My uname -r command also shows 2.6.31.14-generic. The pae must have come with an update. This time I want to try install without getting all the available updates first. 

As you recommended earlier, I will only need to patch hid-ntrig.c and the make command that you provided. Afterwards I only need linuxwacom driver install and the xorg.conf and 10-linuxwacom.fdi changes.

Any other recommendations?

Thanks.

---

### Post by iboot on 2009-11-18
Hi Ayuthia,

I tried it one more time and I am getting the same problem after applying this patch. Can you please try to reproduce on your side? Please let me know if I can provide any other information from my system.

Thanks.

---

### Post by Nimless on 2009-11-19
> **iboot said:**
> Hi Ayuthia,

I tried it one more time and I am getting the same problem after applying this patch. Can you please try to reproduce on your side? Please let me know if I can provide any other information from my system.

Thanks.

Hi what error are you getting ?

---

### Post by iboot on 2009-11-20
> **Nimless said:**
> Hi what error are you getting ?

The system keeps cycling with a blank screen on restart after applying the patch. I can drop to root shell, but can't start gnome.

---

### Post by Nimless on 2009-11-20
> **iboot said:**
> The system keeps cycling with a blank screen on restart after applying the patch. I can drop to root shell, but can't start gnome.

I'm pretty sure it's a problem on your part since nobody here has that kind of behaviour after patching.
Are you sure you executed the commands correctly? i suggest you copy the command right as they are ( with CTRL+C and CTRL+V in console) to be sure you are doing the exact steps.

Have you done all the steps here [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23)
without errors?

---

### Post by iboot on 2009-11-30
> **Nimless said:**
> I'm pretty sure it's a problem on your part since nobody here has that kind of behaviour after patching.
Are you sure you executed the commands correctly? i suggest you copy the command right as they are ( with CTRL+C and CTRL+V in console) to be sure you are doing the exact steps.

Have you done all the steps here [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23)
without errors?

Hi Nimless,

I have always used copy and paste for the commands. I had some errors as documented in the previous posts, but as Ayuthia pointed out, I did not need to do all the steps. The compiles worked, but the boot after the depmod crashes my machine and I have to reinstall karmic everytime.

Is there likely to be a more user friendly way to do this anytime soon? It would be nice if the pen and touch were included as a patch and Karmic was able to detect the input devices.

Thanks.

---

### Post by Nimless on 2009-11-30
> **iboot said:**
> Hi Nimless,

I have always used copy and paste for the commands. I had some errors as documented in the previous posts, but as Ayuthia pointed out, I did not need to do all the steps. The compiles worked, but the boot after the depmod crashes my machine and I have to reinstall karmic everytime.

Is there likely to be a more user friendly way to do this anytime soon? It would be nice if the pen and touch were included as a patch and Karmic was able to detect the input devices.

Thanks.

It's not so hard as it sounds,it's pretty strange that you are getting a boot error when booting the kernel after the patch...one wrong kernel module shouldn't stop everything like that.

Have you tried to blacklist the hid_ntrig module in /etc/modprobe.d/blacklist.conf to check that's the module that is actually having problems?

Also you could  try to remove the "quiet" and "splash" option in your grub configuration to have a more proper debug of what is causing  that behaviour :)
Tell me if you need istructions for that.

---

### Post by iboot on 2009-12-01
> **Nimless said:**
> It's not so hard as it sounds,it's pretty strange that you are getting a boot error when booting the kernel after the patch...one wrong kernel module shouldn't stop everything like that.

Have you tried to blacklist the hid_ntrig module in /etc/modprobe.d/blacklist.conf to check that's the module that is actually having problems?

Also you could  try to remove the "quiet" and "splash" option in your grub configuration to have a more proper debug of what is causing  that behaviour :)
Tell me if you need istructions for that.

Yes, please provide link to instructions to blacklist the hid_ntrig module and how to get grub into a more verbose mode during boot up. I would really like to get the touch to work with karmic. Is there are way to bypass the wrong kernel module while booting up?

Thanks.

---

### Post by Nimless on 2009-12-01
> **iboot said:**
> Yes, please provide link to instructions to blacklist the hid_ntrig module and how to get grub into a more verbose mode during boot up. I would really like to get the touch to work with karmic. Is there are way to bypass the wrong kernel module while booting up?

Thanks.

Yes you can edit /etc/modprobe.d/blacklist.conf and add a line at the end

```


blacklist hid_ntrig


```

If it boots up that it's the module that is causing problem...otherwise it's something else.

---

### Post by dranorter on 2010-01-05
Hi all,

I've had my tx2 for six months or so and finally got the chance to remove Windows for good. I went with Ubuntu 8.10 because I'd formerly (using Wubi) had little luck getting the touchscreen & tablet input working within 9.10 or 9.04.

So, everything works nicely in 8.10 (except "palm rejection" ie ignoring the touch when the stylus is in use), but I've got a copy of Windows 7 I never tried and I specifically partitioned a little space for it. Would it be safe to try? I've heard uninstalling tablet drivers within Windows 7 can restore the firmware to its original state?

---

### Post by dranorter on 2010-01-10
So something I failed to notice for a surprising number of days:

My wireless stops working after a suspend/resume. Actually it says it can see two wireless networks, but the light in front is orange and it consistently fails to connect.

I've tried both the proprietary drivers and the default ones; the default ones don't seem to work at all actually, the proprietary ones don't work on restart.

---

