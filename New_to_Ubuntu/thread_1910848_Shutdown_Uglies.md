---
title: "Shutdown Uglies"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by dmemphis on 2012-01-17
Hello:
Trying 11.10 on an ECS 661FX-M MB & 440MX AGP card.
On shutdown I get these screens #1 on exit, #2 after I press ENTER.
The machine never shuts off.
Things like this have been happening with UBUNTU since I started trying
it on this machine last summer; was hoping this release would be different.
So finally posting the results to see if it can be addressed.
Thanks!
Doug

---

### Post by Scott Baker on 2012-01-17
Question here. You said that you are "trying" Ubuntu on this machine. Are you continuing to run the live distro (running your computer/OS off of a CD/DVD or flash/thumb drive) or have you actually installed it on your hard drive? If it's on your hard drive, how did you install it? Did you try to install it to "dual boot " with another OS? (Like Windows XP), or was it installed to occupy the whole hard drive? Seeing the errors, I suspect a partition error, that may have happened on installation, but I'm not real sure. Please provide requested info, so that we can help. Thanks :-k

---

### Post by alkimkacmaz on 2012-01-18
Did you gave shutdown on command line? If so, you can try 
```
# poweroff
```

---

### Post by Frogs Hair on 2012-01-18
As already stated running from a live disk may be the reason and sometimes proprietary drivers can cause problems with splash and shutdown screens.

---

### Post by grahammechanical on 2012-01-18
This may be a problem due to a low specification video card. This link shows that the card has a maximum of 64Mb memory. It is also AGP.

[http://www.nvidia.com/page/geforce4mx.html]("http://www.nvidia.com/page/geforce4mx.html")

When I exit from running Ubuntu from a liveCD I also get the message "remove media and press enter" but I get it on a Ubuntu purple splash screen. Why is there no purple Ubuntu splash screen in this case?

And, I ask has the questioner tried removing the CD and pressing Enter? If we do not follow the instructions then the machine will not switch off, will it?

Regards.

---

### Post by dmemphis on 2012-01-18
Thanks everyone for your input.  Since Ubuntu 9 or so when I started  experienmenting I was installing Ubuntu to the hard disk.  This time, I  only ran off of the live CD.
 
re: # poweroff
I didn't.  I used the shutdown GUI selection.  Why should I... would it tell me something?

I used the same CD on an ancient AMD Gateway w/ a PCI MX440 video card,  the live CD exited cleanly and powered down from the shutdown menu  selection.

I guess the 661fx mb is the issue, if I can be of any service isolating the fix, I'm happy to help.

---

### Post by dmemphis on 2012-01-18
> **grahammechanical said:**
> This may be a problem due to a low specification video card. This link shows that the card has a maximum of 64Mb memory. It is also AGP.

[http://www.nvidia.com/page/geforce4mx.html](http://www.nvidia.com/page/geforce4mx.html)

When I exit from running Ubuntu from a liveCD I also get the message "remove media and press enter" but I get it on a Ubuntu purple splash screen. Why is there no purple Ubuntu splash screen in this case?

And, I ask has the questioner tried removing the CD and pressing Enter? If we do not follow the instructions then the machine will not switch off, will it?

Regards.

I did press enter, and the result is the second screen.  What I did not do was close
the drawer.... I'll try that and get back to you.  However, all the previous Ubuntu releases I tried (and these were fully installed to HD) would refuse to power down the machine.
(XP powers down the machine, so it is not necessarily a fundamental power-down issue with the MB).

---

### Post by Scott Baker on 2012-01-18
Don't forget the proper steps for shut down folks. You must remove the CD/DVD from the drive, and PHYSICALLY close the drawer to complete shut down. To those Ubuntu newbies, don't fret. Some of us went damn near nuts with this shut down issue, until we checked the forums here. Hang in there, it just gets better.

Dr Sheldon Cooper for U.S. president, 2012 \\:D/

---

### Post by dmemphis on 2012-01-18
Test Resuls:

Exchanged MX440 AGP for MX440 PCI card. 
No other mahcine changes.
Booted Live CD, used GUI shutdown from the upper right corner.
Got the same results as screenshot #1.
CD Door opened.
I removed the CD (does it actually check that the drawer is empty? Talk
about holding my hand...)
I pressed the CD button and completely closed the door.
Pressed the ENTER key.
Got the exact same result as screenshot #2, with the Halted msg.
Machine sat there running, no shut off.

---

### Post by QIII on 2012-01-18
So, just to clarify:

Other machines:  Shut down works.

This one machine:  Shut down does not work.

Correct?

---

### Post by dmemphis on 2012-01-18
> **QIII said:**
> So, just to clarify:

Other machines:  Shut down works.

This one machine:  Shut down does not work.

Correct?

Yes, correct.  Old Gateway shutsdown/off fine with 11.10.  A side note, older
releases did not shutdown/off nicely on the Gateway, so things have improved!

---

### Post by dmemphis on 2012-01-18
I have a video on youtube of the whole shutdown which I can refer to here if I am permitted.

---

### Post by mastablasta on 2012-01-18
> **dmemphis said:**
> I have a video on youtube of the whole shutdown which I can refer to here if I am permitted.

ofcourse you are permitted.

I would give those terminal commands a try. and run them from the virual terminal (crtl+alt+F1). if nothing else it would give out any possible error message before the last one.

also try

sudo shutdown -h now


i saw a similar thing happen on live 9.10, but when i installed it it worked ok.

---

### Post by QIII on 2012-01-18
Try two things.

First, while running a live session, try the following in the command line:

```
sudo reboot
```and see if it shuts down then reboots.

Also try

```
sudo shutdown -h now
```


Edit:  Dang it, Masta!

---

### Post by dmemphis on 2012-01-18
Is the UNMOUNT: /RUN/LOCK result in the last line of the screenshots normal?
Maybe that's pointing to the root cause of not powering down?

---

### Post by dmemphis on 2012-01-18
New information.
I had a PCI Rad7K card lying and tried it in the 661-FX mb machine.
The behavior changed mostly for the better. 
I noticed after choosing the LIVE selection, the screen went black, had some text on it
then the desktop came up nice and pretty.
Then in shutdown, it went orderly to the shutting down graphic and prompted for
the disk removal. I removed the disk, shut the door, pressed ENTER.
ARGH...
The machine failed to power off.  
Attached is the screen shot of it sitting there at the end.  
The dots no longer moving.

So this configuration is better, not ugly, but doesn't powering down.

Is it likely that not powering off could be a problem related to software
support for these two unrelated video cards?  Probably not, so I'd call
it a problem supporting the 661FX.

It appears as though the MX440 support causes the really ugly display. 
I imagine the developers aren't too concerned about making an old MX440
system behave well... I would understand.
On the otherhand, perhaps they would want know as to make the release as universal
as possible.

---

### Post by dmemphis on 2012-01-18
> **QIII said:**
> Try two things.

First, while running a live session, try the following in the command line:

```
sudo reboot
```and see if it shuts down then reboots.

Also try

```
sudo shutdown -h now
```
Edit:  Dang it, Masta!

OK, trying that now.

---

### Post by dmemphis on 2012-01-18
"sudo reboot"  works.  It reset and rebooted.

"sudo shutdown -h now" got all the way to halt and didn't power down.
See screenshot.
Does the halt code have the power down function?

---

### Post by QIII on 2012-01-18
Let's continue to circle in and make sure we can at least get something to work and then figure out why it won't work from the GUI.

Does 

```
sudo /sbin/poweroff
```

get you anywhere?

---

### Post by dmemphis on 2012-01-18
> **QIII said:**
> Let's continue to circle in and make sure we can at least get something to work and then figure out why it won't work from the GUI.

Does 

```
sudo /sbin/poweroff
```get you anywhere?

Good thinking.

"sudo /sbin/poweroff"

Result: no power off. See pic.

---

### Post by QIII on 2012-01-18
How about

```
sudo do-what-the-blazes-I-tell-you-to-you-stupid-machine
```

;)

OK.  I'm going to have to do some more research.  I googled the message you are getting and found nothing definitive.

I suspect someone far wiser than I will come along and call me an "idjit" and tell you exactly how to solve this before I find the answer.

I did find a few items on launchpad, but nothing that I thought quite fit your situation here.

---

### Post by dmemphis on 2012-01-19
How can I research what the Linux source code for shutdown does?
It must be making a wrong assumption about this motherboard.
I'm confident that its not a fundamental problem of the MB based
on that XP and PuppyLinux shut down & power off OK.

---

### Post by mastablasta on 2012-01-19
> **dmemphis said:**
> How can I research what the Linux source code for shutdown does?
It must be making a wrong assumption about this motherboard.
I'm confident that its not a fundamental problem of the MB based
on that XP and PuppyLinux shut down & power off OK.
 
 
Well that shutdown command worked and halted the system (its safe to turn it off), only it didn't power it off automaticly.
[http://www.computerhope.com/unix/ushutdow.htm](http://www.computerhope.com/unix/ushutdow.htm)
 
[http://linux.about.com/library/cmd/blcmdl8_poweroff.htm](http://linux.about.com/library/cmd/blcmdl8_poweroff.htm)
 
Well Puppy uses an older kernel and WindowsXP uses an even older kernel. It could be that support for your motherboard was dropped in kernel.
 
it seems that it doesn't send the poweroff command to motherboard or it does send it but motherboard doesn't recognise it. I am not certian but i think a BIOS update could provide a better chance of powering off better.
 
If you have it installed on computer you could also try to check the logs, as they might hide the asnwer to what happens (any error messages).

---

### Post by dmemphis on 2012-01-19
Thanks for the info on the kernal history, good clues.
OK, I'll see if there is an update for the BIOS. Good thinking.
However... that ancient AMP P4 erra gateway does work - that
makes one wonder about the BIOS, unless there is simply a bug
in the BIOS with respect to what Ubuntu uses for the power down.
I remembered one other data point, EasyPeasy fails to shut down,
so I guess EP uses later Ubuntu kernal.

WIll post the BIOS results...

---

### Post by dmemphis on 2012-01-19
[SIZE=4]***** BIOS update == successful power down *****[/SIZE]
ARGH!  the fundamentals!

However, the shutdown process came out as all text, not the graphic "Ubuntu 11.10"
& walking dots.  It was nice and orderly starting at the top of the screen, unlike the original screenshots.  Hard for me to understand how the bios change would change the way the output was generated.

That lack of the graphical shutdown doesn't really bother me, though fixing it might be a useful exercise.  Should I bother?  Some scripting anomally?

---

### Post by dmemphis on 2012-01-19
So I went to take a picture of the shutdown screen to post. 
But this time shutting down, the Ubuntu shutdown screen showed up
and hid all the shutdown operations, just like it should.
It shutdown beautifully.

I have no idea why the behavior changed.  
Perhaps some kind of race condition?

So I think this whole issue is closed.
Thanks for all your attention.

---

### Post by Scott Baker on 2012-01-24
Here is proof that taking a moment or two to update your BIOS can make a HUGE difference in the amount of, and types of, headaches you could experience with ANY software upgrade or update. Congrats on your discovery. Live long and prosper. \\:D/

( oh, and don't forget to mark this thread as "solved".

---

