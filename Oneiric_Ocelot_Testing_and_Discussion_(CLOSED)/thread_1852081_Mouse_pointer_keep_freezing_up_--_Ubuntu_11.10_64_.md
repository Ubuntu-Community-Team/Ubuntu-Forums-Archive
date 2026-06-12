---
title: "Mouse pointer keep freezing up -- Ubuntu 11.10 64 bit"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xtracool_protik on 2011-09-29
So 2 days back I upgraded to 11.10 64bit beta.
There are few crashes which I already reported through bug reporting.

But my mouse pointer (laptop touchpad) for some reason seems to be freezing up.
I'm trying to decide the reason/moment for a freeze but can't seem to come to conclusion.

1. Mostly when I press enter for first time? or ctrl+Enter? <-- these are stones thrown in dark, as those are the things I mostly do after starting up.

But yea, has anyone else seen/read/experienced something similar?

Ohh btw my USB mouse work completely fine so I think only touchpad issue,
I would appreciate if anyone know how to remove and install touchpad kernel drivers (hopefully rmmod and modprobe) I'll see if that helps.

My lsusb looks something like this:
```

    Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
    Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

```
Thanks


[edit]: Other things that I noticed, power button (on laptop) doesn't work, and shortcuts such as ctrl+alt+L doesn't work

---

### Post by dualon on 2011-09-30
I experienced the same, but not only the mouse pointer, but everything else is frozen as well.
The music stops to play and I cannot get to the system, I have to hard reset it.
I'm not familiar with the internals, but if you tell me what and how should I check, I'll do my best.

Ubuntu 11.10 64-bit beta-2 up-to-date, clean install on a Dell Vostro 3700. Recommended nvidia driver is installed, but I haven't played enough with the system before the driver install to tell if it had any effect.

(Slightly offtopic, but there are other problems too: brightness cannot be set with keys, volume can be changed but the notification bubble shows no change.)

---

### Post by dawonn on 2011-09-30
I have the same problem with my touchpad freezing after upgrading form 11.04 to 11.10.

I am only able to Alt+SysRq+K and then log in again and it's fine. This indicates its a problem with X.org to me.

It occurs at random, but has happened three times in the past two hours.

---

### Post by xtracool_protik on 2011-10-01
Does it work after u re-login without any issue.
And thanks I'll try re-login instead of reboot :P 
There is other workaround on forums for USB mouse:

```
sudo modprobe -r usbhid
sudo modprobe usbhid
```

I've not tried this one yet though

---

### Post by dawonn on 2011-10-02
interestingly, I ran lsusb after it happened last and my bluetooth dongle was missing. Bouncing it did not help. I changed usb ports and it came back up. 

A while after my mouse died again and the same results. I put my dongle back into the original port and it started working again.... *Confused*

I'll post anything else I come across...

---

### Post by xtracool_protik on 2011-10-03
Ohh well I don't have anything else connected to USB at all :-/

---

### Post by emilywind on 2011-10-03
If you have a touchpad on/off key on your laptop, try hitting that after it stops working and see if it starts working again. Other than that, I am not sure.

As for the others, I doubt the underlying cause of those freezes are the same issue the OP is having. lol

---

### Post by dawonn on 2011-10-03
you're right, I just realized that I had two issues happen at the same time. One was that my touchpad just stopped working and I had to SysRq+K to get it back. This is the OP's issue as well I think. But it hasn't happened for two days now. perhaps there was an update that fixed the issue?

I wonder if the OP is still having the problem?

---

### Post by xtracool_protik on 2011-10-03
yes I still have problem :(. and yes my touchpad worked after alt+prntscrn+k but again only for a while. It is bound to freeze after login.

---

### Post by mc4man on 2011-10-04
Seen this several times on an install from yesterday, just happens out of the blue..
(laptop, touchpad

---

### Post by xtracool_protik on 2011-10-04
ohh well looks like mouse pointer freeze is fixed? Haven't seen it since y'day evening. Previously it used to happen every boot.

Anyways I've nautilus crash now few folders just can't be opened :-/ If I open any one of them nautilus just decides to crash :(

---

### Post by dawonn on 2011-10-04
haha, I'm glad to hear that I'm not alone, I also have crashes every time I try to open my 'Documents' folder.... it opens the folder fine if I launch from the terminal though....

ah, its fun watching the bugs get franticly iorned out... :popcorn:

---

### Post by xtracool_protik on 2011-10-04
ooh just got a fix,
I've been updating every 15 minutes since morning and seems I can open all folders without crash now :D

---

### Post by ventrical on 2011-10-04
Yep .. Iv'e had this on every install, laptop/tower serial/usb whatever. Looking forward to fix ! :)

---

### Post by xtracool_protik on 2011-10-05
oops I take it back mouse freeze is not fixed but nautilus crash seems to be fixed

---

### Post by Stewie2kill on 2011-10-07
Coming in to confirm that I'm having this problem as well along with many others. I was going to just revert to 11.04 but after doing some thinking I decided I'd stick with it and try and help out with bug reporting.

OP - you said you reported the bug? Can you link to it so that I can confirm it and track it's status? I'm completely up to date as I've run 'sudo apt-get update' and 'sudo apt-get upgrade' twice to make sure. It's all up to date.

I'm currently running 64-bit 11.10 on a Dell Inspiron 1545 via a wubi install. It has happened on 32 bit as well to me when I tried to revert to it to avoid the issue - again all up to date with the daily build as far as I know.

---

### Post by xtracool_protik on 2011-10-07
Hey Stewie2kill,
 I've not reported bug for mouse pointer freezing, I've reported them for nautilus crash, compiz crash etc.
 As those are the things ask me to report a problem.
 I've never reported anything without bug reporting system (cause I don't know the cause and how to reproduce the problem).
 If you can please file a bug for freezing mouse I'll confirm it but again as I said I don't know the cause as it seems completely random -- sometimes (1 in 20) works just perfectly.

---

### Post by Stewie2kill on 2011-10-08
If I can ever find the log files for when it does crash I'll be able to post up a bug report. Until then I have no way of re-creating it either, and, oddly enough it hasn't happened in a while either. It's only been 24 hours though. 

I will note however that it seemed to happen most (along with other bugs) when activating the ATI graphics driver for my card. After a fresh install I only ran into the mouse cursor issue once and used the previously mentioned alt+prtscrn+k to cure it. After that I had no issues with the cursor. It does indeed happen randomly. 

I have my suspicions that it's related to a graphics driver though.

---

### Post by mc4man on 2011-10-08
Happened here again for the 1st time in a couple of days - was just posting a reply in this forum, went to move cursor & it was frozen

A real pita bug because it occurs so infrequently & with no 1 apparent trigger.
(sometimes days between, sometimes a couple of times a day, 

Am going to revert  xserver-xorg-input-synaptics to previous version (1.4.1-1ubuntu1) for several days & see, though even that time span may prove inconclusive  - 
 that package was updated on 09/29 & I don't remember this happening prior to that.

Edit: well just happened here again with older package so not that - same scenario this time, replying to a thread

---

### Post by dawonn on 2011-10-08
I was typing in libre Office writer and my touchpad stopped working again.

I wonder if it has something to do with the feature that turns off the touchpad while typing? could something there be borked?

---

### Post by mc4man on 2011-10-08
> **dawonn said:**
> I was typing in libre Office writer and my touchpad stopped working again.

I wonder if it has something to do with the feature that turns off the touchpad while typing? could something there be borked?

Well I'm going to turn that off & see, problem is that sometimes this doesn't occur for an extended time or it may happen fairly often
(3 times today, had gone a couple of days without occurring even once

---

### Post by haresear on 2011-10-08
Just installed Oneiric 64-bit daily for Oct 7, and experienced the touchpad mouse freezeup. I had the Dash open when it froze. My usb wireless mouse continued to work. Logging out and back in restored function.

---

### Post by beforefirstlight on 2011-10-09
I'm also on 11.10 64 bit and I have exactly the same problem with the touchpad mouse freeze. I can not find exactly the reason why. It happens randomly.
I've just noticed that a session logout ( with the Ctrl Alt Suppr on my french keyboard) and a re-login the problem disappears!

---

### Post by mc4man on 2011-10-09
On previous install turned off the option to disable touchpad while typing & didn't see this for 1 day which is encoraging but not a long enough time frame.

So did a new install with 10/09 image - wanted to 1st. confirm this still occurred
Didn't take very long - about 20 sec's on 1st login while setting wireless password.
Then again disabled option, no sign of as yet...
I figure if it goes 2 -3 days that may point to the option as a factor.

If affected & wanting to try the option is in system settings - see screen
Another issue here with touchpad is the cursor speed/sensitivity  options (in screenshot) have  no affect - get 1 setting only

---

### Post by effenberg0x0 on 2011-10-09
Does the touchpad work again if you run this?

```
synclient TouchpadOff=0
```

Regards,
Effenberg

---

### Post by mc4man on 2011-10-09
> **effenberg0x0 said:**
> Does the touchpad work again if you run this?

```
synclient TouchpadOff=0
```

Regards,
Effenberg
Will have to wait till this happens again - (if it does), the history of this, at least here, is to be very sporadic
Though in all cases where I've noticed the 'freeze' occur it has been while typing

---

### Post by effenberg0x0 on 2011-10-09
When it happens, please see if you can get an error message. I only had it once (today) in a Dell Vostro 1310 laptop, but unfortunately could not locate a related error message in logs... looked everywhere but got nothing. I must have missed something. Looking at bug reports, you will see many of them are being market incomplete as no one can associate that behavior to some particular error.

Regards,
Effenberg

---

### Post by Stewie2kill on 2011-10-10
Logged on last night before bed to check and see if I still had the 'turn touchpad off while typing' box checked. Turns out I do. 

Haven't had it happen since I installed. In fact I've tried to re-produce most of the problems I was having for bug reporting purposes and haven't had any luck so that's a good sign.

However it does seem as though this particular bug is still prevalent. If it happens again I will try that command effenberg and see if it fixes it. My main problem is that I too am only just now trying to pitch in to bug reporting and haven't the slightest of clues as to where to look for an error log. 

I've got this thread pinned and will keep on the lookout.

---

### Post by mc4man on 2011-10-10
Went 2 plus days with option disabled - no occurrences.
Turned back on this morning & got one while using the terminal earlier this evening.
(still not a long enough test

There is no real indication of anything going wrong except possibly in .xsession-errors, but maybe not of any use
(unity continues to spam that file

Am going to turn the option back on for 3-4 days or so but not thru g-c-c, will use syndaemon instead to see what happens, if anything

---

### Post by shoofy on 2011-10-11
> **effenberg0x0 said:**
> Does the touchpad work again if you run this?

```
synclient TouchpadOff=0
```

Regards,
Effenberg
This did make my touchpad start working again after it froze

---

### Post by admiralspark on 2011-10-12
> **effenberg0x0 said:**
> Does the touchpad work again if you run this?

```
synclient TouchpadOff=0
```

Regards,
Effenberg

Also worked here, and none of my logs make reference to mouse/hid/touchpad errors. Seems like a major bug to not have taken care of come crunch time...

---

### Post by effenberg0x0 on 2011-10-12
Hey,

It is reported, and other people came with with the synclient workaround too, I have found bug reports that mention it. The problem so far is that no one has produced a consistent log showing what the hell is going on when it stops working... I guess we ran of time on this bug.

Regards,
Effenberg

---

### Post by beforefirstlight on 2011-10-12
For me, using this command :

synclient TouchpadOff=0

works perfectly to "un-freeze" the mouse pointer.

But after a restart the problem can appear again. I hope this bug will be fixed for the final release.

:)

---

### Post by mc4man on 2011-10-12
> **effenberg0x0 said:**
> Hey,

It is reported, and other people came with with the synclient workaround too, I have found bug reports that mention it. The problem so far is that no one has produced a consistent log showing what the hell is going on when it stops working... I guess we ran of time on this bug.

Regards,
Effenberg
Do you have a link or 2 handy to a recent bug report?

---

### Post by effenberg0x0 on 2011-10-12
@mc4man

I've been looking at a few, but can't say if these are all or the most relevant ones. Digging recent browser history:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/786463](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/786463)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/827637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/827637)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/872028](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/872028)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/863026](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/863026)
[https://bugs.launchpad.net/ubuntu/+bug/862703](https://bugs.launchpad.net/ubuntu/+bug/862703)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/859455](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/859455)

As usual, incomplete reports make it difficult to say if they are duplicates or not. 

Regards,
Effenberg

---

