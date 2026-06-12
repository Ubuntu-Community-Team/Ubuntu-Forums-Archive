---
title: "Installed 12.10, bootup, no desktop."
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Kittenrocksjj on 2012-12-08
I am new to Ubuntu, but have experience with winxp. I installed
ver. 12.10 on my laptop. It boots fine, then the wallpaper shows,
but the desktop doesnt load. No icons, nothing else.  Can not
shut down easily.
Please help if you know why it wont work. I would like to completely switch to ubuntu only os.
Thank you:KS

---

### Post by LuisGMarine on 2012-12-08
Hello and welcome to the forums!

First of all what type of video card are you currently running?  nvidia or ATI?

---

### Post by DuckHook on 2012-12-08
To shut down:
1. Bring up a terminal window with <Ctrl>+<Alt>+<t>
2. Then type:
```
sudo shutdown -h now
```type in your password at the prompt (the cursor will show nothing while you type, not even a string of ******, but it is still accepting your password). This will shut down the machine elegantly and immediately.

If you cannot bring up a terminal with <Ctrl>+<Alt>+<t>, then try <Ctrl>+<Alt>+<F1>. This will switch you into a separate command line console. After logging in, typing the same command as above will also shut down elegantly.

Re: no desktop.

1. Run your system from a LiveCD. Tell us if this works.
2. Are you using Ubuntu, Kubuntu or Lubuntu?
3. Did you install as dual boot?
4. Have you already tried reinstalling from scratch?
5. If the same issue exists after reinstall, or you are set on chasing down the problem on your current install, then need the following info:

Open up a terminal as per above instructions and type:

```
cat /var/log/syslog | grep segfault
```Post results back to this thread.

---

### Post by audiomick on 2012-12-08
> **DuckHook said:**
> 
2. Then type:
```
sudo shutdown -h now
```

In my experience, that does not always turn the power off. I can't remember if it does on my current desktop, but it didn't on the old one. I had to manually switch of the power. The option -h is "halt" which shuts down the system cleanly, but, as I said, doesn't necessarily power off. 

From the man page
> -h     Requests that the system be either halted or powered off after it has been brought down, [COLOR="Red"]with the choice as to which left up to the system.[/COLOR]



I use the -P option, for "power off".

```
sudo shutdown -P now
```

or
```
sudo shutdown -r now
```

to reboot.

Do
```
man shutdown
```
to look at the options yourself on the man page.

You can use
```
man <command name>
```
to get a description of any command.

---

### Post by DuckHook on 2012-12-08
Thanks kindly for your correction. I do use the *-P* option for my own shutdown. Don't know why advice differed from practice here. Must be losing my grip in my decrepitude.

Any ideas about what could be causing OP's issues? I was only guessing that Unity could not load because it was crashing with segmentation fault. This happened to me with a Lubuntu upgrade, but I'm frankly not the best at this sort of detective work.

---

### Post by squakie on 2012-12-08
> **Kittenrocksjj said:**
> I am new to Ubuntu, but have experience with winxp. I installed
ver. 12.10 on my laptop. It boots fine, then the wallpaper shows,
but the desktop doesnt load. No icons, nothing else.  Can not
shut down easily.
Please help if you know why it wont work. I would like to completely switch to ubuntu only os.
Thank you:KS

If you press ctrl/alt/F1 do you get a terminal login screen?  If so, use your normal userid and password to log in (the password won't show when you type it - just press enter when done). 

Type:
lspci  | grep VGA  <press enter>

BTW - that's a piping symbol "|" - on my keyboard it's above the "\" key.

Copy that line and post it back here.

---

### Post by squakie on 2012-12-08
> **DuckHook said:**
> Thanks kindly for your correction. I do use the *-P* option for my own shutdown. Don't know why advice differed from practice here. Must be losing my grip in my decrepitude.

Any ideas about what could be causing OP's issues? I was only guessing that Unity could not load because it was crashing with segmentation fault. This happened to me with a Lubuntu upgrade, but I'm frankly not the best at this sort of detective work.

I'm guessing, since they don't get the desktop, that it may be a video driver problem.  Getting the info back from the OP might help us determine more.

---

### Post by audiomick on 2012-12-08
> **DuckHook said:**
> Any ideas about what could be causing OP's issues?

Not really. I have been seeing a lot of similar posts, I think all on 12.10. It seems that the system comes up, but none of the panels are visible. One bloke reported that his resolution was bigger than the physical size of the monitor, so the panels were outside the visible area on the monitor. I have the impression that it is usually related to the video drivers, but that is about all I can say about it. Not much help, I know...

---

### Post by LuisGMarine on 2012-12-08
> **audiomick said:**
> Not really. I have been seeing a lot of similar posts, I think all on 12.10. It seems that the system comes up, but none of the panels are visible. One bloke reported that his resolution was bigger than the physical size of the monitor, so the panels were outside the visible area on the monitor. I have the impression that it is usually related to the video drivers, but that is about all I can say about it. Not much help, I know...

I've had the same situation happen to me on more than a few 12.10 installs.  Usually I would have to boot up in nomodeset, and install the nvidia drivers/ATI.

I also fixed it on my desktop PC by installing this package:
```
sudo apt-get install linux-headers-generic
```

---

### Post by squakie on 2012-12-09
Audiomick, I've had that "desktop too big for the screen" issue in the past (back about version 7, maybe even 8) and as you said it is a combination of the video driver as well as timing settings and resolution settings.  Used to be able to work those out with the now obsolete xorg.conf.  I would assume there is a similar way of doing things with the new xorg, but I've just never had a need now to mess with that.

LuisGMarine, that's exactly why we've asked for the information on the video adapter, if the user is able to get it.

Also, I seem to remember reading some problems I believe in version 11 at least where if the firmware was "missing" (eg no driver and supporting files) from certain network adapters that they also wouldn't boot.

Sometimes it just takes nomodeset, some times it takes i915.modeset=0 or i915.modeset=1 (I don't know if this has somehow been all encompassed in nomodeset now or not, but it used to be a separate option for certain Intel adapters).  Sometimes it requires ACPI=no, sometimes NOAPIC, etc..

So, if the OP can post back the information, it can help tell us if it's a video problem or something beyond that.  

Considering all they get is the initial boot id line from the boot, I would suspect something much different, as it wouldn't be to the point of trying X yet, so a driver shouldn't matter.

Perhaps they could try the alternate CD and see if that helps.

---

