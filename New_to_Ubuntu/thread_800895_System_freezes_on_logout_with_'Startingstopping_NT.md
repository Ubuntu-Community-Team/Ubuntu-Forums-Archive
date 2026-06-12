---
title: "System freezes on logout with 'Starting/stopping NTP server (ntpd)'"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Theo148 on 2008-05-20
Occasionally, if one of the users on my system logs out (when there is more than one user logged on), the system freezes with something along the lines of:

```
* Stopping NTP server (ntpd)
* Starting NTP server (ntpd)
```

Sometimes these messages are repeated multiple times. I am running Ubuntu 8.04 Hardy Heron.

Is this a known problem and if so, is there a way to fix it?

---

### Post by ElTurkoGrande on 2008-08-26
I have a similar problem. At boot and at shutdown, and possibly in the middle the "starting ntp server ntpd" or "stopping ntp server ntpd" messages show up very frequently. Sometime in matched pairs, sometimes a whole bunch of starts on their own, but no apparent pattern.

I do get lockups, but those happened without ntpd installed, so I'm not convinced that ntpd is at fault in my case.

Did you, or anybody else, ever find out why ntpd's start/stop manager was misbehaving?

---

### Post by mjheagle8 on 2008-12-04
I am also having this problem in Ubuntu 8.10.  Can someone please help?  It is very frustrating to not be able to log out and be forced to reboot instead.

---

### Post by chimiasanchi on 2009-01-08
I'm having this problem under 8.10, but it only seems to happen with the realtime kernel when I'm logging out or shutting down.

---

### Post by registerdown on 2009-02-08
I have the same problem with 8.10. Can't log in to Ubuntu anymore!!!! Does anyone have a fix? This just suddenly happened, maybe related to an update????

---

### Post by sti11_learning on 2009-03-02
I just had a similar problem. I had opened up VLC (9.4.0 (from the repo)) and then executed my compiled neverputt binary (So I would hear my music instead of the standard bg Music). (I compiled from the sources tarball because the neverball/neverputt package in the repos wasn't recent enough. So, I followed the same procedure for compiling I had used before. ./configure; make; make install) 

After executing it X died and displayed "Stopping NTP server", followed by "Starting NTP server" on a newline. As of now that VT is still displaying that and I am typing though VT 9. (I switched by hitting Ctrl+alt+f9) I will reboot in few minutes and see if it happens again. I doubt it will, as, I had done that same thing before and this had not happend. I also checked xorg.0.log and there is nothing new there. I have to wonder however, how NTP would affect the X Window System as NTP is Network Time Protocol Deamon (At least, according to a google search and Wikipedia). So, any ideas?:confused:

Edit:Just rebooted, Did the same thing as before and no problems. However, everything I have learned about computers tells me things just don't crash "out of the blue." Something had to have caused it and I would like to know what.

---

### Post by Von-Dyke on 2009-03-12
I'm having this same problem when logging out. When i log out i get a black screen with white, vertical blocks interspersed throughout it.
Any fixes?

---

### Post by skippuff54 on 2009-03-14
Similar problems on my Toshiba Satellite with intel centrino. Related issues I've examined on my system are a)ntfs mounts and b)wireless network interfaces. That has given me some perceived relief but could be confounding issues.

On the former, I lost the thread but in general I added a couple of lines to the shutdown processes to make sure my ntfs shares had unmounted.

On the latter, I just implemented the change listed here: [http://ubuntuforums.org/showthread.php?t=965935]("http://ubuntuforums.org/showthread.php?t=965935")

The laptop screen will go blank and the fan speeds up rapidly every 10 seconds or so. I'm forced to hold the power switch to shutdown.

Usually when I see the shutdown splash screen and the status bar moves completely from left to right, the system shuts down properly.

NTPD, however, seems to be the prevailing issues. Sometimes I catch messages on shutdown that refer to stuff like libhal1 but I don't know what logs to check - ideas anyone?

---

### Post by skippuff54 on 2009-04-08
Update: Some of this is arbitrary but here is the gist:

After little to no networking activity, e.g. simple web/e-mail or instant messages, I can shut the computer down (with the aforementioned changes) either by GUI or command line: ```
sudo shutdown -h now
```

After substantial network activity, e.g. file transfers, music playback on home network, multimedia web browsing, etc., I find that the hang usually still occurs.

What helps is telling the computer to wait some random amount of time before shutting down. For good luck, I usually go with 7 minutes: ```
sudo shutdown -h 7
```

Naturally, I started with 1 minute and got up to 7 before I noticed a reliable response.

---

