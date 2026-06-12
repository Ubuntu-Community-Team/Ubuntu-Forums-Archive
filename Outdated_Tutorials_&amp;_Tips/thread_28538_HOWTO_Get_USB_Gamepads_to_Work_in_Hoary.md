---
title: "HOWTO: Get USB Gamepads to Work in Hoary"
date: 2005-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-04-20
How to Get Gamepads to Work in Hoary

First let me say that most of the credit for this goes to Randabis:

[http://www.ubuntuforums.org/member.php?u=4323](http://www.ubuntuforums.org/member.php?u=4323)

He was the first person to post on here how to get my gamepad to work. I need my Zsnes fix!!! I currently use a Thunder General USB-PS2 adaptor with a Dualshock2 (the best controller ever IMHO), but this should apply to all USB gampads that work without drivers in Windows XP. You need an internet connection to do this FAQ.

First, open up a terminal and type:

> sudo apt-get update 

then

> sudo apt-get install joystick 

tell it to load at boot.

then

> sudo apt-get install jscalibrator 

tell apt-get yes when it asks something.

Then, after these packages are installed, plug in you USB gamepad. Wait a minute. Then type in the terminal:

> sudo chmod 666 /dev/input/js0 

EDIT: If you have more than one gamepad, plug it in now, wait a minute and type:

> sudo chmod 666 /dev/input/js1 

If you get no errors, you gamepad should now work!!! Enjoy.

---

### Post by ming0 on 2005-04-20
Just figured I'd chime in and report that I have tried 3 different Logitech 'wingman' pads (one regular, one w/ single analog, and one w/ dual analog that looked like ps2), and all of them have worked smashingly! 

Just plug in the usb cable, fire up zsnes, and you're ready to rock!

Also, you can find them on ebay, but watch out for jacked up shipping prices :-| 

(I got all 3 of mine for $30, and then gave 2 of them away to friends for christmas. Now we have cross coast Mario Kart matches, it's so sweet!)

---

### Post by Brian McConnell on 2005-04-21
Thanks for the tips and my new sig. I'll have to check oput ZSnes... I've yet to game on ubuntu. 

Mario Kart on a network sounds too cool.....

---

### Post by graigsmith on 2005-04-21
hmm, wierd, i just jabbed the controller in the usb port. 

and changed the device from /dev/js0  to /dev/input/js0

and it worked.

---

### Post by poofyhairguy on 2005-04-21
[QUOTE=graigsmith]hmm, wierd, i just jabbed the controller in the usb port. 

and changed the device from /dev/js0  to /dev/input/js0

and it worked.[/QUOTE]


Ok. Let it be known then that this might not be necessary in every case. Worked for me though.

---

### Post by TheStyle on 2005-04-22
It's a no go with my Gravis GamePad Pro :-?

---

### Post by poofyhairguy on 2005-04-22
[QUOTE=TheStyle]It's a no go with my Gravis GamePad Pro :-?[/QUOTE]

Have you tried pluging it into a different USB port. It sounds dumb, but it worked for me a few days ago.

EDIT: Do you know if it needs drivers in windows to work, or is it plug and play there?

---

### Post by Sniffer on 2005-04-26
Great Tut, it works for me  :) 

Logitech Wing Pad

---

### Post by N'Jal on 2005-04-26
Either my USB pad aint supported or im testing it in the wrong things. I have the MS Sidewinder Game Pad Pro. It's not terrible important to get it working as i have never really used it for anything im just confirming if it will work. I followed the instructions all the way though and sure enough on /dev/input/ there is a js1 now i just can't seem to make this run.

I have tryed Neverwinter Nights and Tux Racer neither has worked.

As i said its not importand, but its worth knowing if its supported or not, in case someone else has the same pad.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=N'Jal]Either my USB pad aint supported or im testing it in the wrong things. I have the MS Sidewinder Game Pad Pro. It's not terrible important to get it working as i have never really used it for anything im just confirming if it will work. I followed the instructions all the way though and sure enough on /dev/input/ there is a js1 now i just can't seem to make this run.

I have tryed Neverwinter Nights and Tux Racer neither has worked.

As i said its not importand, but its worth knowing if its supported or not, in case someone else has the same pad.[/QUOTE]

Make sure that the controller actually works before you blow time on it. I spent a while trying to fix my friends USB pad only to find out that it didn' even work in XP. It was broken.

Also try opening nautilus with sudo and change the permission on js1.

---

### Post by penvzila on 2005-05-09
I have a USB Gravis Eliminator Gamepad Pro, and it actually works better in ZSNES in Ubuntu than it does in Windows with the gravis drivers.

---

### Post by apollyonis on 2005-05-20
I'll just add the Logitech Precision USB gamepad I managed to pick up at the local Frye's for $10 to the list of working hardware. Just plug and play...except the emulators needed to be correctly setup, which really was no hassle with ZSnes and Gnomeboyadvance.  ;-)

---

### Post by ganatronic on 2005-06-08
Excellent. Stunt Race FX and Super Metroid, here I come.

*However*, my second controller is still not working. I only have input#1 working. Any idea what gives? I plugged it in and set js1, and didn't get any errors. I'll keep with messing with it in the meantime.

---

### Post by rabidninjawombat on 2005-06-08
Works great!   Just using a generic 10 dollar USB game pad.

---

### Post by ganatronic on 2005-06-08
Rabidninjawombat, I'm using a generic one also. A "Thrustmaster" in fact. It fits perfect for snes games. Do you have your second input working?

---

### Post by hohllp on 2005-06-13
Hi all,

I've been trying to configure a logitech dual action game pad to work. I followed the steps mentioned in the post on this forum:

[http://ubuntuforums.org/showthread....ght=usb+gamepad](http://ubuntuforums.org/showthread....ght=usb+gamepad)

but I have only been able to get the buttons to work, not the analog sticks, or the d-pad (in xmame 0.96).

When using jcal -c /dev/input/js0 to calibrate the pad I get a "broken line" error at the end of the calibration

I read somewhere that I may need to apply a patch "badpad". Do I still need to do this... the message I read was concerning kernel 2.4, not 2.6. I also have the same problem using a gravis gamepad pro.


Thanks for the help.

Vince

---

### Post by hohllp on 2005-06-15
Just a followup to my "logitech dual action" question:

After some hacking, slashing, and googling I found "xjoypad". Using this seems to solve the problem, but it's more of a workaround. The analog sticks work, but the dpad still doesn't. Hopfully with some tweaking I can get that to work too.

Vince

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=hohllp]Just a followup to my "logitech dual action" question:

After some hacking, slashing, and googling I found "xjoypad". Using this seems to solve the problem, but it's more of a workaround. The analog sticks work, but the dpad still doesn't. Hopfully with some tweaking I can get that to work too.

Vince[/QUOTE]

If you can work out a solution, I'll add it to my howto.

---

### Post by lol on 2005-07-30
For some reason, my gamepad is working correctly only when I am root...

Those who have haven't been able to make their joystick work should try this: "sudo jscalibrator", and check if it's not working better. Also try to see if it's working when starting the games like this: "sudo /usr/games/tuxracer", for example. This could be a good trouble shooting step.

As for how to solve this problem, I don't know. This is really a mystery for me: in fact, jscalibrator is working, both for root and my other users. But when I start a game as a user, only the buttons are still working (same as hohllp), whereas if I start it as root, everything is fine.

I already tried to change the permissions on the devices but it really doesn't make any difference. Anyway, the users are actually able to access the device since the buttons are working... So? What can make things work as root but not as a regular user beside the permissions?
And my gamepad used to work (back when I was still running a Debian unstable).

---

### Post by lol on 2005-07-30
I also forgot to mention the fact that "cat /dev/input/js0" as a user actually display stuff when using the gamepad.

---

### Post by bored2k on 2005-07-30
I haven't played anything on it, but it detected my Sony Playstation 2 controller pretty good (I did move and push some buttons on the hardware manager test).

---

### Post by lol on 2005-07-30
oups! sorry, next time I will read the thread from beginning to end...

I pluged my gamepad on another USB port, that solved the problem...

---

### Post by ePierre on 2005-07-31
I did not tested this method yet, but since you told it only works with plug and play controllers, I am afraid it won't work for me...

I bought a [EMS USB2](http://www.hkems.com/product/ps2/ps2-usb2.htm)  adapter, to connect two different Playstation pads at the same time. I bought this one, cause it works fine with Dance Dance Revolution controller :)

It needs [drivers](http://www.hkems.com/download.htm)  under Windows... 

Is anybody managed to install this under Ubuntu Linux ? I really wanna try StepMania under Linux !  :grin:

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=ePierre]I did not tested this method yet, but since you told it only works with plug and play controllers, I am afraid it won't work for me...

I bought a [EMS USB2](http://www.hkems.com/product/ps2/ps2-usb2.htm)  adapter, to connect two different Playstation pads at the same time. I bought this one, cause it works fine with Dance Dance Revolution controller :)

It needs [drivers](http://www.hkems.com/download.htm)  under Windows... 

Is anybody managed to install this under Ubuntu Linux ? I really wanna try StepMania under Linux !  :grin:[/QUOTE]

Just try it. My playstation controller adaptor has drivers in Windows but "just works" after this how to in Linux.

---

### Post by dude2425 on 2005-08-04
No matter what I do, the joystick thing is telling me:
Oops, please create some joystick device nodes with MAKEDEV first!

I'm trying to get my moded xbox controller to work, (which I know it will, it has before)

I'm gonna try a few other things now, and if it still doesn't work, I'm going to be relying COMPLETELY on you're replys. (oooh, the preasure.)

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=dude2425]No matter what I do, the joystick thing is telling me:
Oops, please create some joystick device nodes with MAKEDEV first!

I'm trying to get my moded xbox controller to work, (which I know it will, it has before)

I'm gonna try a few other things now, and if it still doesn't work, I'm going to be relying COMPLETELY on you're replys. (oooh, the preasure.)[/QUOTE]

Did you try my "plug it in another USB slot" trick?

---

### Post by dude2425 on 2005-08-06
I actually did try that, but it worked for a couple day's, and then I heard reports of breezy working again, and just HAD to dist-upgrade and just screwed myself over.
It's being seen, hardware manager sees it as a S-type Xbox controller, which it most certainly is. I have a /dev/input/js0, but it still tells me to check to make sure I have used MAKEDEV. I've tryed that, still no go. I can use jstest, but stuff like zsnes don't want to recognize it anymore. It was working fine after I pluged it into another slot on hoary. (I had it in my KB cause it was easier to reach)

It could be a bug in Breezy, I'll do some searching in bugzilla and see if anybody has filed a report, and if not, I'll have to do it myself. I've never filed a bug report before, never really noticed any bugs that haven't already been reported.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=dude2425]I actually did try that, but it worked for a couple day's, and then I heard reports of breezy working again, and just HAD to dist-upgrade and just screwed myself over.
[/QUOTE]

*Smacks forehead*

Please file a bug report so that it will work when Breezy is released.

---

### Post by crane on 2005-08-06
I recieved a Thrustmaster as a gift a while back. I played with it in windows for a while but had problems getting it to act right. As I moved to linux I tried it a couple of times with different distros and it did not work. Today I tried it for the first time in Ubuntu and it worked great. I had to completely change my q3 config but still this is great. It actually works better in Ubuntu that windows !!

---

### Post by TravisNewman on 2005-08-07
For the record, the PS controller adaptors are fantastic, and I never even knew you had to do anything. When I was going through my hardware trying to get it all to work in linux, I thought "Welp, lets try to get the gamepad to work." So I fired up zsnes and it already worked, with me doing nothing at all.

So my question bored- did you try this BEFORE the howto?

That kinda sucks. I just assumed that this was something that required no configuration ;) Apparently it's only the lucky ones.,

But if you have a PS or a PS2, get that adaptor and you have the best ever gamepad.

---

### Post by dude2425 on 2005-08-08
[QUOTE=poofyhairguy]*Smacks forehead*

Please file a bug report so that it will work when Breezy is released.[/QUOTE]

Actually, it had nothing to do with breezy, my PCI card with the USB ports was going bad, and I didn't realize it. It sure had a funny way of showing it though. I connected it up to the USB ports on my mobo, and it worked just fine.

Now my problem is, in most games, the Y axis is inverted (even in the menu's) and it is SO irritating. I tryed calibrating it so that up is down and vise versa, but it never sticks, but it does sometimes work. Is there a tool that will allow me to adjust everything just like XBCD Setup for windows (by redcl0ud)
jscalibrator isn't working any, and `jscal -c /dev/input/js0` makes me set up EVERY axis before I can actually get to the one that's causing me problems.

Good news though, I can play neverball, supertux, zsnes, flightgear, gish, tux racer, and a whole slew of other good games with my controller again.

---

### Post by Pixman on 2005-09-02
Has anybody a clue about the Speed Link First Strike USB gamepad? This gamepad rocks for sure, it's designed just like the normal PS gamepad... exactly :) But it won't work under Ubuntu. I have no ideas... tested it with the Howto, checked for modules, everything... in SuSE it worked but I don't know what modules it loaded back then.

Help appreciated :)

---

### Post by Pixman on 2005-09-03
Wow. Downloaded a new kernel-image.. 2.6.12-8-686... in all of a sudden it works with joydev =)
Great stuff... even the 2 analog sticks work perfectly.

Ubuntu rox.. user friendly as hell ;)

---

### Post by sir_mud on 2005-09-08
I have a Game Elements Gemini Recoil Pad from Wal-Mart. It was $15 has dual analog and force feedback. Only required a driver for the feedback under 98SE. I'm trying to get it to work under Snes9x, so far without luck. I'm going to try Zsnes real quick. It was detected by the kernel before I installed joystick and jscalibration. I really want to get this one to work because it has nice rubber grips and a retracting cable.

*Edit*
It shows up in Zsnes as a Jess Tech USB 4-axis 12-button Gamepad. All the buttons work except the D-pad....progress I guess.
](*,) 
I'm still working on it.

---

### Post by sir_mud on 2005-09-08
Got my pad working, at first I had to be root for the D-pad to work, changed USB port and it worked correctly as a user. Anyone have an idea about why it does that?

And now back to Yoshi's Island...take that Baby Mario

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=sir_mud]Got my pad working, at first I had to be root for the D-pad to work, changed USB port and it worked correctly as a user. Anyone have an idea about why it does that?
[/QUOTE]


No...its odd....but at least it works for you now.

---

### Post by samakv on 2005-11-29
Hello there poofyhairguy.

What's your hardware specs? M/B, CPU, display card, and sound card? I could not get cubeengine to play, nvidia-glx-config enbable makes X stop responding.

samakv

[QUOTE=poofyhairguy]How to Get Gamepads to Work in Hoary

First let me say that most of the credit for this goes to Randabis:

[http://www.ubuntuforums.org/member.php?u=4323](http://www.ubuntuforums.org/member.php?u=4323)

He was the first person to post on here how to get my gamepad to work. I need my Zsnes fix!!! I currently use a Thunder General USB-PS2 adaptor with a Dualshock2 (the best controller ever IMHO), but this should apply to all USB gampads that work without drivers in Windows XP. You need an internet connection to do this FAQ.

First, open up a terminal and type:

 

then

 

tell it to load at boot.

then

 

tell apt-get yes when it asks something.

Then, after these packages are installed, plug in you USB gamepad. Wait a minute. Then type in the terminal:

 

EDIT: If you have more than one gamepad, plug it in now, wait a minute and type:

 

If you get no errors, you gamepad should now work!!! Enjoy.[/QUOTE]

---

### Post by bdrevn on 2006-03-12
I realize that this thread is sort-of old, but here goes.  I have what I think is a functioning 10-key usb gamepad.  With gxmame, I can get the buttons to function, but not the d-pad.  This is odd, it seems like if one set works the other should.  All the keys work in jscalibrator, including the d-pad.  Zsnes states that it knows I have a gamepad with two axes and 10 keys, but will also not recognize the d-pad.  One thing I notice is that the directional buttons move the on-screen pointer, and this continues when either gxmame or zsnes are played.
I am using dapper.
Thanks

---

### Post by Ruskie on 2006-03-13
[QUOTE=poofyhairguy]
tell it to load at boot.
[/QUOTE]

Excuse me, how do you tell it to load at boot?

Thanks

---

### Post by stateq2 on 2006-04-02
[QUOTE=bdrevn]I realize that this thread is sort-of old, but here goes.  I have what I think is a functioning 10-key usb gamepad.  With gxmame, I can get the buttons to function, but not the d-pad.  This is odd, it seems like if one set works the other should.  All the keys work in jscalibrator, including the d-pad.  Zsnes states that it knows I have a gamepad with two axes and 10 keys, but will also not recognize the d-pad.  One thing I notice is that the directional buttons move the on-screen pointer, and this continues when either gxmame or zsnes are played.
I am using dapper.
Thanks[/QUOTE]

I have the same problem....the dpad or analog axis are not recognized in any emulator/program that I use...only the buttons.  This is a big problem for me, because my laptop only has one usb port...so I can't try the "switch usb ports" trick:(

---

### Post by electroconvulsive on 2006-08-01
How exactly do you tell "joystick" to load at boot?

---

### Post by Tonren on 2006-09-17
I'm having the exact same problem... I have an HP Compaq v2565us and a Logitech Dual Action controller, and the d-pad/joystick don't work right.  I've tried plugging it into both USB ports and the one USB 2.0 port, but it didn't work on any of them.  On USB 2.0, it was as though the right d-pad was constantly being pressed; if I hit left on the d-pad, it cancelled it out.  I've tried running games as sudo; didn't work.  What could be causing this problem?

Oh, bloody hell.  This was in Hoary... looks like I ought to make a new post.

---

### Post by argash on 2006-09-18
> **Tonren said:**
> I'm having the exact same problem... I have an HP Compaq v2565us and a Logitech Dual Action controller, and the d-pad/joystick don't work right.  I've tried plugging it into both USB ports and the one USB 2.0 port, but it didn't work on any of them.  On USB 2.0, it was as though the right d-pad was constantly being pressed; if I hit left on the d-pad, it cancelled it out.  I've tried running games as sudo; didn't work.  What could be causing this problem?

Oh, bloody hell.  This was in Hoary... looks like I ought to make a new post.
actually it'd be nice if someone could update this for dapper.  I've been searching through the forums but no luck so far.  Are the instructions in this thread still applicaple in dapper?

---

### Post by rcatman on 2006-09-23
> **argash said:**
> actually it'd be nice if someone could update this for dapper.  I've been searching through the forums but no luck so far.  Are the instructions in this thread still applicaple in dapper?

I searched thru the dapper forums, no luck so far, although i never go by which release the post is in. I've found all forums to be helpful.



I am having the SAME problem. D-pad is not working. jscalibrator detects it, d-pad works fine. 

I got the d-pad to work in zsnes by ```
sudo zsnes
``` and the d-pad works. A lot of people have had the same issue, the d-pad requires root privelages??

I've even changed the permissions of the file (chmod 666 /dev/input/js0) and I still have to run zsnes as root. 

Any solutions?

---

### Post by adamissimo on 2006-09-24
I am having this same problem as well.  I am completely new to Ubuntu.  So far I love it, although it's been a bit of a steep learning curve.  I am using a RedOctane Ignition Pad 3.0.  All of the buttons are recognized, but the joypad doesn't do anything.  I tried running jscal and jscalibrator, and neither one seems to help with this problem.  Has anyone out there figured out a solution?

Thanks!!
Adam

---

### Post by smee_187 on 2006-09-26
Hey I have the smartJoy Plus adapter and I need some help, jstest reports the name and tells me I it has 6 axis, then throws a segmentation fault.:twisted: .. jscal works fine :D  and so does jcalibrate but cedega seems to use jstest..... I can't get this working!! any ideas?:confused:

---

### Post by gcranston on 2007-06-24
I have a problem with an SNES controller rewired to USB.  4 of the buttons don't work, at all.  I've done

```
cat /dev/input/js0
```

and get symbols back on every button, but all the utilities like jstest, jscal, and jscalibrate proclaim that there are only 4 buttons instead of the 8 I should have.  (I'm missing B, Y, Start, and Select).   I don't think joy2key will work if the driver doesn't recognise the 4 missing buttons.  I have tried all this as root and with permissions on the device set to 666.

The worst thing is, it used to work just fine under Dapper (I think it was Dapper).  I hadn't pulled it out in a while and was just sitting down for some nice Chronotrigger only to find out that those 4 buttons didn't work.

One last note: obviously, the pad is detected, but here's dmesg:

```
[271299.476000] usb 2-1: new low speed USB device using uhci_hcd and address 5
[271299.648000] usb 2-1: configuration #1 chosen from 1 choice
[271299.676000] input: RetroUSB.com RetroPad as /class/input/input12
[271299.676000] input: USB HID v1.00 Gamepad [RetroUSB.com RetroPad] on usb-0000:00:1d.1-1

```

---

