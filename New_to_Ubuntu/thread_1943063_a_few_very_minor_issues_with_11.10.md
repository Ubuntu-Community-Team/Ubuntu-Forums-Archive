---
title: "a few very minor issues with 11.10"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-18
So far, my early experiences have been very positive. There are a few things I'd like to address, though:

1. My system is set to suspend after a period of inactivity. I notice, though, that quite often, it suspends (the monitor gets dark, etc.) and then immediately wakes up. Any idea what might be causing this?

2. When I choose shutdown and select "shut down" (NOT "restart"), the system shuts down and restarts. Ideas?

3. How do I set the system so I don't need to enter a password when it wakes up? For that matter, can I disable the password on my system entirely? It's a desktop, and really isn't necessary.

Thanks.

---

### Post by mzimmers on 2012-03-18
follow-up question removed. I'm still interested in the first questions.

---

### Post by chipbuster on 2012-03-19
1 and 2 sound like they may be coming from the same source...going to point out some simpler checks right now:

-Check to make sure that your BIOS doesn't have something like "wakeup on mouse" enabled. That would cause your comptuer to power up if you gave the mouse a good jiggle.
-Check log files (located in /var/log) for errors. In particular, see if pm-suspend has anything labeled with "ERROR"
-Try running sudo init 0 from terminal to shut down your computer directly from init. Does it reboot?

There's always the possibility that you shorted your headers or something, but it's not too likely.

As for passwording, that's playing a dangerous game. If I managed to ssh into your computer somehow, I could login on your user without a password, run sudo without a password, and proceed to totally rig your system up so that I could capture your information...and I'm not even a super power user. 

There's a way to do it from inside Ubuntu, but if you ever need to do some tweaking of your system (like you do right now), you'll probably be locked out.

p.s. sorry if this makes no sense, I'm kinda tired.

---

### Post by mzimmers on 2012-03-20
You make a good case for leaving the password intact. Due to this, and other reasons (documented in other threads), I've decided to leave it as is.

Ubuntu's power management isn't particularly sophisticated (at least as manifested in the control panel), but I don't think the problem arises there. I'll take a closer look at some of the stuff you suggested. 

Thanks!

---

### Post by mzimmers on 2012-03-23
OK, I took a look at the pm-suspend log file. I'm not sure I understand the contents 100%, but I see one entry where it woke up 10 seconds after suspending, due to a "running hook" involving novatel_3g_suspend resume.

There are other resumes in there that look weird, but their entries aren't timestamped. One of those is something called PulseAudio, which I'm pretty sure is something I don't need, but when I went to remove it via Synaptic, it gave me a list of other stuff it would also remove as a group. One of them was "ubuntu-desktop," so...I figured I'd better check before removing that.

---

### Post by beanhead on 2012-03-23
if you want a limited account with no password word you can do so. 

$sudo useradd -m limitedUser

the -m creates the user with no home directory.

$sudo passwd limitedUser

$sudo passwd -d

passwd wil let you creat a password for the account.

and passwd -d del eats the password making the account passwordless.

---

### Post by mzimmers on 2012-03-26
Any ideas on the sleep issue? It's getting annoying to have this thing wake up every so often for no (apparent) reason.

I'd also like to make it so I could wake the system from the keyboard, but that may be asking for too much.

---

### Post by d4m1r on 2012-03-26
> **mzimmers said:**
> Any ideas on the sleep issue? It's getting annoying to have this thing wake up every so often for no (apparent) reason.

I'd also like to make it so I could wake the system from the keyboard, but that may be asking for too much.


You should be able to specify "wake on keyboard or mouse" stuff in your BIOS (usually hitting Del when the PC is booting will get you there).

As for your PC waking up from sleep mode my itself, are you using a laser mouse? If it is really sensitive or flashes a light every x minutes, that will wake your PC up.

---

### Post by mzimmers on 2012-03-26
When the box is booted in Windows 7, I can wake up from the keyboard, so I don't think the problem is in BIOS.

My mouse is bluetooth and built into the keyboard. The wake-ups seem to be coming from programs doing something.

---

