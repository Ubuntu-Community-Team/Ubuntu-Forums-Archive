---
title: "Reboots without notice + System errors on most logins"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by linuxconvert2 on 2015-09-02
Is there a place, like Windows has, where crash reports are filed that I can review and research? 

At first, I thought the issue might be system temp, but from all the documentation I can find, my machine is running within the temperature range it's allowed to. It's a little hot to the touch, but the temp sensor I installed (Psensor - Temperature Monitor) hasn't tracked any spikes (or recurring temps) outside what the system should be able to handle. The only thing I've done is just report the error with the prompt, and  gone on my merry way. I've just run out of patience, though, at the  constant system (and browser - but that will probably be a different  thread) crashes.

I'm not even 100% sure it's reboots. I don't see the POST/BIOS screens like you would on a normal reboot. I just get dumped out, hear the drums, and then see the login screen. With no one logged in.

Where can I go hunting for where errors should be logged (if they were) on these sudden reboots? Once I have those in hand, I can learn the why.

---

### Post by v3.xx on 2015-09-02
> I'm not even 100% sure it's reboots.

Will it return to a usable desktop?  If not, then got to go to console.

When you get to the login screen can you press..

Ctrl + Alt + F1

And log into  console?

If so, enter the command

```
startx
```

See if that will produce any error reports.

---

### Post by Double.J on 2015-09-02
Hi there, and welcome to the forums!

Linux is actually very good at generating logs. 
Now, we're at a bit of a crossroads in how these things are to be done. Up until 14.04 (the long term support release) ubuntu used something called upstart to boot the system. This is being replaced witht he current 15.04 release and going forward with something called systemd. The details are a bit technical, but essentially the old system is the classic unix approach (almost) and the new system is essentially replacing all that with a kind of mini operating system in itself under linux, but has some modern features.

Do you know which version you are using?
You can check with
```
lsb_release -a
```

If you have the new ones based on systemd (ubuntu 15.04), you can use
```
sudo journalctl -r
```
just after the event to see recent logs in reverse order. 

You can quickly see what happened at the last boot with the -b option, athough it doesn't sound like the system is rebooting, but the times on the log atleast should narrow it down for you!

For Ubuntu 14.04 and earlier, the logs are in 
```

/var/log/syslog
```
/var/log is the primary logging area, so it might be worth checking out a few files. 

let us know how you get on

JJ

---

### Post by ian-weisser on 2015-09-02
> **linuxconvert2 said:**
> Is there a place, like Windows has, where crash reports are filed that I can review and research?

Look in /var/crash
If you find a recent crash file, attach it to this thread.


> **linuxconvert2 said:**
> I'm not even 100% sure it's reboots. I don't see the POST/BIOS screens  like you would on a normal reboot. I just get dumped out, hear the  drums, and then see the login screen. With no one logged in.
That usually indicates an X server crash, not a reboot. The X server creates the graphical display.
Also look for /var/Xorg.0.log  if you see a bunch of '(EE)' entries, attach the file to this thread.

How long have you had this install of Ubuntu?

---

### Post by linuxconvert2 on 2015-09-03
**Version:** 10.04.3 LTS

**systemd:** "journalctl" was a command not found

**/var/log/syslog: **
```

Sep  3 01:58:42 Enterprise anacron[967]: Job `cron.daily' terminated
Sep  3 01:58:42 Enterprise anacron[967]: Normal exit (1 job run)
Sep  3 02:12:39 Enterprise kernel: [ 2034.815988] compiz[1907]: segfault at 7f94fa2914a0 ip 00007f94fa06efd0 sp 00007fffbb017ca8 error 7 in libcompiz_core.so.0.9.11.3[7f94f9fe0000+ae000]
Sep  3 02:13:01 Enterprise gnome-session[1708]: WARNING: Application 'compiz.desktop' killed by signal 11
Sep  3 02:13:01 Enterprise gnome-session[1708]: WARNING: App 'compiz.desktop' respawning too quickly
Sep  3 02:13:01 Enterprise gnome-session[1708]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Sep  3 02:13:01 Enterprise colord: device removed: xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:01 Enterprise colord: device removed: xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:01 Enterprise colord: Profile removed: icc-b5d2eef9e28519444cc195805db9f9d4
Sep  3 02:13:01 Enterprise colord: Profile removed: icc-9f41cee51ea5a17de6d22d6d74fab1a4
Sep  3 02:13:01 Enterprise pulseaudio[3225]: [pulseaudio] main.c: User-configured server at {03039f5e3bc8cad02844190255afe6ed}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Successfully made thread 3237 of process 3237 (n/a) owned by '1000' high priority at nice level -11.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Supervising 1 threads of 1 processes of 1 users.
Sep  3 02:13:01 Enterprise pulseaudio[3237]: [pulseaudio] pid.c: Stale PID file, overwriting.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Successfully made thread 3238 of process 3237 (n/a) owned by '1000' RT at priority 5.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Supervising 2 threads of 1 processes of 1 users.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Successfully made thread 3239 of process 3237 (n/a) owned by '1000' RT at priority 5.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Supervising 3 threads of 1 processes of 1 users.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Successfully made thread 3240 of process 3237 (n/a) owned by '1000' RT at priority 5.
Sep  3 02:13:01 Enterprise rtkit-daemon[1299]: Supervising 4 threads of 1 processes of 1 users.
Sep  3 02:13:01 Enterprise pulseaudio[3237]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-u9bgaYmqyW: Connection refused
Sep  3 02:13:01 Enterprise pulseaudio[3237]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-u9bgaYmqyW: Connection refused
Sep  3 02:13:02 Enterprise acpid: client 1115[0:0] has disconnected
Sep  3 02:13:02 Enterprise acpid: client connected from 3248[0:0]
Sep  3 02:13:02 Enterprise acpid: 1 client rule loaded
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Successfully made thread 3360 of process 3360 (n/a) owned by '112' high priority at nice level -11.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Supervising 5 threads of 2 processes of 2 users.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Successfully made thread 3367 of process 3360 (n/a) owned by '112' RT at priority 5.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Supervising 6 threads of 2 processes of 2 users.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Successfully made thread 3370 of process 3360 (n/a) owned by '112' RT at priority 5.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Supervising 7 threads of 2 processes of 2 users.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Successfully made thread 3371 of process 3360 (n/a) owned by '112' RT at priority 5.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Supervising 8 threads of 2 processes of 2 users.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Successfully made thread 3373 of process 3373 (n/a) owned by '112' high priority at nice level -11.
Sep  3 02:13:02 Enterprise rtkit-daemon[1299]: Supervising 9 threads of 3 processes of 2 users.
Sep  3 02:13:02 Enterprise pulseaudio[3373]: [pulseaudio] pid.c: Daemon already running.
Sep  3 02:13:03 Enterprise dbus[449]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep  3 02:13:03 Enterprise dbus[449]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep  3 02:13:03 Enterprise colord: Device added: xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:03 Enterprise colord: Device added: xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:03 Enterprise colord: Automatic metadata add icc-c365824d4bd3056dbf758ee1d03dfe4e to xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:03 Enterprise colord: Profile added: icc-c365824d4bd3056dbf758ee1d03dfe4e
Sep  3 02:13:03 Enterprise colord: Automatic metadata add icc-4a27e0b36fd09c3acb1bb1924dd25aae to xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:03 Enterprise colord: Profile added: icc-4a27e0b36fd09c3acb1bb1924dd25aae
Sep  3 02:13:12 Enterprise colord: device removed: xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:12 Enterprise colord: device removed: xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:12 Enterprise colord: Profile removed: icc-c365824d4bd3056dbf758ee1d03dfe4e
Sep  3 02:13:12 Enterprise colord: Profile removed: icc-4a27e0b36fd09c3acb1bb1924dd25aae
Sep  3 02:13:13 Enterprise dbus[449]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep  3 02:13:13 Enterprise dbus[449]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep  3 02:13:14 Enterprise colord: Device added: xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:14 Enterprise colord: Device added: xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:14 Enterprise dbus[449]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Sep  3 02:13:14 Enterprise dbus[449]: [system] Successfully activated service 'org.freedesktop.locale1'
Sep  3 02:13:14 Enterprise colord: Automatic metadata add icc-b5d2eef9e28519444cc195805db9f9d4 to xrandr-Acer Technologies-Acer H236HL-LX1AA0044210
Sep  3 02:13:14 Enterprise colord: Profile added: icc-b5d2eef9e28519444cc195805db9f9d4
Sep  3 02:13:14 Enterprise colord: Automatic metadata add icc-9f41cee51ea5a17de6d22d6d74fab1a4 to xrandr-Acer Technologies-Acer S231HL-LNZ080024237
Sep  3 02:13:15 Enterprise colord: Profile added: icc-9f41cee51ea5a17de6d22d6d74fab1a4
Sep  3 02:13:45 Enterprise gnome-session[3631]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Sep  3 02:17:01 Enterprise CRON[4389]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  3 02:19:37 Enterprise dbus[449]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Sep  3 02:19:37 Enterprise kernel: [ 2452.290358] systemd-hostnamed[4433]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Sep  3 02:19:37 Enterprise dbus[449]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

**/var/crash/:** I have a LOT of crash files. A number of them have xorg and linuximage and pulseaudio as part of the filename. Which are you most interested in me attaching for viewing?

**/var/Xorg.0.log:** I could not find this file in /var/
[B]
How long have you had this install?[/B] A few weeks. Not long. I thought firefox was bringing the system down somehow. It has seemed really buggy on all my plaforms since one of the last big updates this summer. Doesn't seem like it, with the questions you're pointing, though.

---

### Post by ian-weisser on 2015-09-03
> **linuxconvert2 said:**
> **Version:** 10.04.3 LTS

Are you sure?
10.04.3 reached End of Life in July, 2011 and is no longer supported. See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I recommend against putting such an old system on a network. A 10.04.3 system has not received any security updates in four years, and is vulnerable to several published attacks.

The simplest and fastest solution is to backup your data and install a supported version of Ubuntu.

---

### Post by linuxconvert2 on 2015-09-03
I apologize. That was a typo from I-don't-know-where.

To confirm, here's my terminal output.

```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
:~$ 
```

---

### Post by ian-weisser on 2015-09-03
Well, that's a relief!

> **linuxconvert2 said:**
> **systemd:** "journalctl" was a command not found
That's expected behavior for a 14.04 system.

> **linuxconvert2 said:**
> Sep  3 02:12:39 Enterprise kernel: [ 2034.815988] compiz[1907]: segfault at 7f94fa2914a0 ip 00007f94fa06efd0 sp 00007fffbb017ca8 error 7 in libcompiz_core.so.0.9.11.3[7f94f9fe0000+ae000]
Sep  3 02:13:01 Enterprise gnome-session[1708]: WARNING: Application 'compiz.desktop' killed by signal 11
Sep  3 02:13:01 Enterprise gnome-session[1708]: WARNING: App 'compiz.desktop' respawning too quickly
Sep  3 02:13:01 Enterprise gnome-session[1708]: CRITICAL: We failed, but the fail whale is dead. Sorry...

A Compiz segfault killed the session. There should be a corresponding compiz .crash file in /var/crash

> **linuxconvert2 said:**
> Sep  3 02:13:01 Enterprise pulseaudio[3237]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-u9bgaYmqyW: Connection refused
Sep  3 02:13:01 Enterprise pulseaudio[3237]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-u9bgaYmqyW: Connection refused
While resetting, Pulseaudio seemed to try to connect to the wrong dbus session. Perhaps subsidiary failure or an otherwise wholly separate problem.

> **linuxconvert2 said:**
> **/var/crash/:** I have a LOT of crash files. A number of them have xorg and linuximage and pulseaudio as part of the filename. Which are you most interested in me attaching for viewing?
Start with compiz and xorg.

---

### Post by linuxconvert2 on 2015-09-03
I am unable to attach any of my crash files to this post. The manager for uploading files reported that .crash was not a valid file.

As I'm new to the forums, I didn't know that. Is there a usual procedure for attaching those kinds of files that I missed earlier?

---

### Post by howefield on 2015-09-04
> **linuxconvert2 said:**
> I am unable to attach any of my crash files to this post. The manager for uploading files reported that .crash was not a valid file.

Copy the contents of your file to somewhere like [http://pastebin.com/](http://pastebin.com/) and post the link here.

---

### Post by linuxconvert2 on 2015-09-06
I was having some trouble opening the files to put them in pastebin. I found and followed the instructions I discovered [here]("http://askubuntu.com/questions/346953/how-to-read-and-use-crash-reports"). When installing apport-retrace, I saw a couple things I'd like to ask about: terms like python-secrestorage, libfakeroot, and fakeroot. I'm not going to instantly panic, since it came from a reliable source, but I am curious what those are.

Also, I got denied permission. I was able to create and write to a folder in, but not when I did it through the command line?

```
:~$ apport-retrace --confirm --gdb --sandbox system --verbose --cache /var/crash/reports/cache/apport-retrace --output /var/crash/reports/_usr_bin_Xorg.0.crash /var/crash/_usr_bin_Xorg.0.crash
ERROR: Cannot open report file: [Errno 13] Permission denied: '/var/crash/_usr_bin_Xorg.0.crash'
:~$ 

```

I may be a convert, but I'm feeling pretty stone dumb right about now. Please tell me this isn't what entry-level linux is supposed to be like normally. >_<

---

### Post by ian-weisser on 2015-09-06
.crash files are simply text files.

In a GUI, right-click on the crash file and open it in any convenient text editor (like gedit or mousepad or leafpad, etc.)
In a shell environment, simply 'cat' or 'more' or 'less' the .crash file.

---

### Post by tgalati4 on 2015-09-06
Let's reduce the Agony Units.  Open a terminal and post the output of:

```
grep EE /var/log/Xorg.0.log
```

A hardware problem can cause several, conflicting, log messages.  So be mindful that log messages are not really useful for an underlying, intermittent, hardware problem.  Perhaps your graphics card is failing.  Perhaps your motherboard needs cleaning.  Perhaps you have a bad battery or power supply.

---

### Post by linuxconvert2 on 2015-09-07
```
:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
:~$ 
```

<Right-click, open with, gedit>
Could not open the file "/var/crash/_usr_bin_Xorg.0.crash".
You do not have the permissions necessary to open the file.

<Right-click, open with, Libre Office>
Access to /var/crash/_usr_bin_Xorg.0.crash was denied.

---

### Post by ian-weisser on 2015-09-07
Change the permission of the crash file so you can read it:
```
sudo chmod 744 /var/crash/_usr_bin_Xorg.0.crash
```
Then try opening it in gedit.

---

### Post by tgalati4 on 2015-09-07
So we know that Xorg (the graphics server) did not crash with an error (EE).  Or at least, there was not enough time to write to the log file--also indicative of a hardware fault.

Look in dmesg for system errors.  Don't post the file, just the error--if any:

```
dmesg | tail -50
```

---

### Post by linuxconvert2 on 2015-09-07
sudo chmod 744 /var/crash/_usr_bin_Xorg.0.crash

[http://pastebin.com/BeKkCsnz](http://pastebin.com/BeKkCsnz) (the core dump is missing, because it's too big for pastebin... I'm trying to make a second pastebin)



dmesg | tail -50
```
[28083.985551] chrome[2762]: segfault at 96 ip 00007fc134c8ebf3 sp 00007ffc9c991680 error 6 in libpepflashplayer.so[7fc13457c000+fc2000]
[77743.590605] traps: chrome[4534] general protection ip:7fc134bbda23 sp:7ffc9c9912f0 error:0 in libpepflashplayer.so[7fc13457c000+fc2000]
[99464.601328] Chrome_ChildThr[11790]: segfault at 0 ip 00007efc060f9138 sp 00007efbf5b40440 error 6 in plugin-container[7efc060f1000+38000]
[102788.596237] chrome[11512]: segfault at 18 ip 00007fc13502c964 sp 00007ffc9c991490 error 4 in libpepflashplayer.so[7fc13457c000+fc2000]
[119255.403967] Chrome_ChildThr[13750]: segfault at 0 ip 00007f2336227138 sp 00007f2325c40440 error 6 in plugin-container[7f233621f000+38000]
```

---

### Post by tgalati4 on 2015-09-07
So Google Chrome is crashing(segmentation fault) with an error in Adobe Flash Player.  What is the webpage that is causing the crash?  Try using *firefox* as a test against that page.

What is strange is that an application crash is taking out your desktop.

Run *google-chrome* or *firefox* in a terminal and keep it visible at all times.  Use the --debug switch to get more output.  Pay attention to the errors before your desktop freezes.  It's possible that you have a GPU issue and your system freezes/reboots when the GPU gets too hot or locks up.  This is difficult to troubleshoot.

Open a terminal:

```
glxgears
```

Post your framerate.

---

### Post by linuxconvert2 on 2015-09-07
Firefox doesn't work with that page. I started using chrome for clickerheroes.com and pandora.com after Firefox seemed unable to handle them - wouldn't even open the pages properly with the flash players.

I tried whitelisting those sites in my firefox extensions, but it still wouldn't work. Thus chrome. And it means I'm running two browsers at once, usually one in each monitor, so I can do two things at once (or let two things run at once).

Firefox, since one of the latest updates (and getting this OS installed) has repeatedly crashed on me in a way it didn't used to, either. Sometimes the dump to login happened while running only firefox, but most often it was just firefox crashing itself.

I'll get those stats for you in a little bit.

---

### Post by linuxconvert2 on 2015-09-07
Frame rate, using glxgears, seems to be between 59.9 and 60.9 fps.

(Sorry for the delay. Had to install mesa-utils to run it.)

---

### Post by tgalati4 on 2015-09-07
I recall that firefox had turned off flash support because of a serious flash vulnerability.  Google-chrome uses there own compiled version of flash, don't know if it had a similar problem.  What version of firefox and chrome are you using?

Chrome is up to 45 now.  I'm using Mint's version of Firefox at 40.

Is your system stable when not using either browser?  You want to determine if your base system is working correctly before trying to fix application problems.  And yes, Linux does have its surprises for a new user, which is why we have these forums.

---

