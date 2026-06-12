---
title: "No sound at all in Oneiric 11.10 [64 bit]"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by reaper_rr on 2011-09-17
I've just updated my Kubuntu installation to the latest 11.10 Beta version available and there is no sound at all. 
My soundcard though, is correctly detected by the system.

Here is some additional info:

I've tried booting the system with the old 2.6.38 kernel too, and the sound is still gone. That means that the problem is not kernel-related.

Soundcard model: ALC662

[http://www.alsa-project.org/db/?f=d12b98a88585033f8f85fb4ccaaefcedfe8cd018](http://www.alsa-project.org/db/?f=d12b98a88585033f8f85fb4ccaaefcedfe8cd018)

---

### Post by howefield on 2011-09-17
Thread moved to the development forum "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by clivejo on 2011-09-17
+ 1

Sound seems to have stopped working in last update.

---

### Post by clivejo on 2011-09-17
> **clivejo said:**
> + 1

Sound seems to have stopped working in last update.

UPDATE : Just finished a current update and its working again!

---

### Post by reaper_rr on 2011-09-17
> **clivejo said:**
> UPDATE : Just finished a current update and its working again!

Nope, updating didn't solved my problem.

---

### Post by reaper_rr on 2011-09-17
UPDATE:

Deleting the /home/username/.pulse directory fixed the problem for me.

---

### Post by c3apollyon on 2011-09-29
I'm also having sound problems and I've updated up to Thurs. Sept 29 with no improvements.

When I do an 'lspci' I get the following result:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

However, when I enter the Sound Settings via the taskbar icon in Ubuntu 11.10 there is nothing detected under Hardware and, consequently, no volume settings or sound.

Can anyone give me a suggestion on how to fix this?  I deleted the .pulse directory as suggested but it did not help.

---

### Post by paul_in_london on 2011-09-29
Had the same problem earlier.

```
rm -rvf ~/.pulse/
```

and then a reboot solved it.

---

### Post by c3apollyon on 2011-09-29
> E: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
E: [pulseaudio] module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: [pulseaudio] module.c: Failed to load module "module-console-kit" (argument: ""): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.



Seems my problem lies in all the DBus crashes I'm having...

---

### Post by c3apollyon on 2011-09-29
I re-installed pulseaudio and some related packages and that fixed the problem.  I think I might have created the problem to begin with when I chmodded /usr root.root to fix a problem I was having with VirtualBox complaining about permissions!  Oye!

---

### Post by ksamuel on 2011-10-11
[URL="http://ubuntuforums.org/member.php?u=665525"]Same problem but paul_in_london's solution solved it.
[/URL]

---

