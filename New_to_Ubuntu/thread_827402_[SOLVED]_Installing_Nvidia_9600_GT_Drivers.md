---
title: "[SOLVED] Installing Nvidia 9600 GT Drivers?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ipsi on 2008-06-12
I know this has been posted repeatedly, but I just can't get it to work. Every time I've tried to install it I just get an error saying that X isn't configured correctly..

Anyone have any idea what's going on here? I've tried the official 173 drivers, but it hasn't worked yet. I imagine I'll just have to reformat and try again... :(

Also having issues booting to XP (Can't find NTLDR...) that I'm not sure how to fix. Very frustrating. XP is on 2nd HD, Linux on First, both SATA. XP was installed first.

---

### Post by mikewhatever on 2008-06-12
While it may be tempting to solve all problems in one post, it usually doesn't work. You should post another thread about NTLDR problem.

---

### Post by ajmorris on 2008-06-12
> **ipsi said:**
> I know this has been posted repeatedly, but I just can't get it to work. Every time I've tried to install it I just get an error saying that X isn't configured correctly..

Anyone have any idea what's going on here? I've tried the official 173 drivers, but it hasn't worked yet. I imagine I'll just have to reformat and try again... :(

Also having issues booting to XP (Can't find NTLDR...) that I'm not sure how to fix. Very frustrating. XP is on 2nd HD, Linux on First, both SATA. XP was installed first.

Hi there,
For your nvidia, have you tried the nvidia-glx or nvidia-glx-new drivers from the repositories?

As for your NTLDR issue, IIRC, that is the file that the XP bootloader uses to boot... if that is missing, you will either have to re-install XP, or fix the bootloader somehow... i assume Microsoft implemented something on their Install CD (as that would be the practical option) but i am not sure.

AJ

---

### Post by ipsi on 2008-06-12
Fair enough. I'm not so worried about fixing the boot issue thing - it's a new set of drives, so I'm happy formatting them repeatedly (and am just doing so again).

ajmorris: Apparently they won't work, as they don't contain support for the 9600GT, which is why I need to install the drivers from the website.

Sadly, that hasn't worked. I just get a messed-up screen, with Ubuntu saying something about being in low resolution (but I can't see most of it, as it's below the screen).

Now, the card manual said something about installing a power-cable if it needs it, but I can't see anything that could fit (and it doesn't seem to have a power slot), so I'm not sure about that. Seems to work in Windows.

I guess I could just not use the card while in Ubuntu, but that would be admitting defeat.

I'm just not sure why it installs (with no error messages), and then decides it just won't work.

---

### Post by ajmorris on 2008-06-12
have you tried reconfiguring X after using the drivers from the site? (either sudo xfix or sudo dpgk-reconfigure -phigh xserver-xorg)

Also, for the time being, you could set the 'nv' driver in /etc/X11/xorg.conf instead of 'nvidia' just until you can get the card to work.

Also, you might like to see this:
[http://ubuntuforums.org/showthread.php?t=717978](http://ubuntuforums.org/showthread.php?t=717978)

they seem to have gotten their 9600GT to work

AJ

---

### Post by ipsi on 2008-06-12
Right, well, first: How would I tell if Ubuntu has actually installed the drivers for my card properly, such that I'll actually be getting proper 3D accelleration from it?

---

### Post by Xiong Chiamiov on 2008-06-12
Run this command
```

glxinfo | less

```
and take a look at the third line.  It should say "direct rendering: Yes".

There are quite a few different tools for generating a proper xorg.conf.  I would recommend trying:
a) having the NVIDIA installer write a new config file when it installs
b) sudo dpkg-reconfigure xserver-xorg
c) xfix

---

### Post by ipsi on 2008-06-12
Ok, Windows/Ubuntu are working now. Not installed how I wanted it (Linux on 1, XP on 2), but it works. Now XP on Partition 1, Linux on Partition 2, and /home on the bigger HD.

Still not sure about the Nvidia Drivers. The error I got was simply that X couldn't start. Reconfiguring (via dpkg-reconfigure) meant that I could start up X again, but I have no idea if that meant I had 3D accel working... So it's possible I could just be having a mental block there and assumed it wasn't working.

It shows the Ubuntu loading screen, but after that shows some lines of console output (I can't remember, at work now), the screen flickers, and it eventually tells me that X had an error. Can't remember what was in the logs. I'll have look when I get home.

Also, I'm not so good with hardware, but is it possible that I might have missed a power cable or something? It looks like it might want one, but there's no power cables in the power supply that would fit (it's black, with two rows of 4 holes). Not sure what that could mean. However, XP seems to recognise it (the Nvidia drivers installed fine there, and it booted fine, with everything displaying better after the drivers were installed), and I've got the monitor plugged into the video card (via the HD->VGA adaptor).

Anyway, thanks for your help so far guys. I really hope I can get this worked out, because I'd like to play as many games as I can under Linux, without having to reboot to XP. Compiz would be nice too.

---

### Post by nhasian on 2008-06-13
Hello ipsi,

To see what version of the nvidia drivers you are currently type:

```
cat /proc/driver/nvidia/version
```

I had a heck of a time installing the latest nvidia restricted drivers myself until i found starcannon's guide here:

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6")

let me know if that fixes your nvidia drivers problem.

---

### Post by ipsi on 2008-06-13
Haven't tried installing them yet, but could it be that I didn't realise I needed a power cable for my video card? The drivers for XP detected this and told me that I really shouldn't do this, and promptly bumped me to 800x600.

Could it simply be that the Linux drivers don't handle this as well as the XP drivers?

I'll find out in the morning I suspect, when I go to see if I can buy a converter (I think I have a 500W PSU, just didn't seem to come with a 6-pin).

I figured my 9600 was a moderately low-end card, so I didn't think I'd need this. Was I wrong in assuming it's a low-end(ish) card?

EDIT: Looks like I was completely wrong about that. The price seemed about right for what I would consider a low-to-mid-range card. Not for something that's only 4 months old (well, I guess 4 months is kinda old these days). Huh. Cool.

EDIT 2: I've obviously not been paying attention to hardware for far too long.

---

### Post by ipsi on 2008-06-13
Right! Fixed it!

It was as I wonder above: I didn't plug in the power cable for the video card. Doh. It didn't help that I didn't see a plug in my case that looked like it would fit.

Anyway: Plug in 6-pin video card power cable! Windows plays nicely with this and tells you there is insufficient power. Linux, not so much.

Anyway, thanks all for your help guys, I really appreciate it, even though the problem was ultimately my fault :).

---

