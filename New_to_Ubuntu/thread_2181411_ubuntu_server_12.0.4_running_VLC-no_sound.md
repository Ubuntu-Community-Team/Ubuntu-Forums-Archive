---
title: "ubuntu server 12.0.4 running VLC-no sound"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by dFyLXEd on 2013-10-17
So I am a total beginner, this was a little diy project i had for the summer.
I followed an only guide to make a media server/stream device for my home network.
I installed ubuntu server 12.0.4 on a hp d530 mini and removed the optical drive, floppy drive, and pci expansion card and added an extra fan in it.
It specs are Pentium 4 2.4Ghz with 2Gb of RAM and 40 GB of HDD.
Now, I installed PlexMedia server first but i didn't like it...or maybe its not what i expected.
After that, i search for some weeks for a media streamer that had http support. Thats when i ran into VLC 2.0.8, love the app, its pretty
straight forward and simple to use. 

Problem 1: [solved]
First problem i encountered was that the [.hosts] file had to enable port[8080] without doing that the when accessing the [IPaddress:8080] on my browser would throw a 403 forbidden permission. ok but the problem isn't that.

MAIN PROBLEM:
The problem was when i got it to finally work and my browser even showed the album art i was so happy until i turned my speakers on to listen to the song. NO SOUND!
i have literally searched everywhere and i CAN'T find anything yet.
HELPPPPPPPP!!!!!!

so here are some of the things i have done so far:

gonzo_48@ubuntu-gonzo:~$ aplay -l
aplay: device_list:252: no soundcards found...



gonzo_48@ubuntu-gonzo:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/E         R (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company d330 uT
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1000 [size=256]
        I/O ports at 1400 [size=64]
        Memory at fc480400 (32-bit, non-prefetchable) [size=512]
        Memory at fc480600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: snd_intel8x0
        Kernel modules: snd-intel8x0

---

