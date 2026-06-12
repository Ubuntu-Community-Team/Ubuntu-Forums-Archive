---
title: "I do not have sound"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by swimstarguy on 2008-09-15
I searched but did not find a thread that had my problem. If you find a thread that I should have posted in please tell me and I'll move my question over there so more people can get the answer if they have this issue as well.

When I first switched to Ubuntu I did not have sound. I upgraded to Hardy and I still do not have sound.

I tried following the instructions on this site:
*[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)*
I did not get my sound to work though.

When I type in
*aplay -l*
the computer returns this

> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Dell Unknown device 01fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


The bits that stick out to me are "Unknown device 0lfc" and ",access denied>"

I'm sure I'm missing something obvious.

Any help would be appreciated.


~Zar4

---

### Post by tuxxy on 2008-09-15
Are you using ALSA as the sound output?

---

### Post by kansasnoob on 2008-09-15
> When I first switched to Ubuntu I did not have sound. I upgraded to Hardy and I still do not have sound.


So, you installed an older version of Ubuntu and had no sound?

Then you upgraded and had no sound?

Would you just try:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up under Sound & Video. Look at mine:

[ATTACH]85350[/ATTACH]

[ATTACH]85351[/ATTACH]

Lots of toggles!

---

### Post by bobnutfield on 2008-09-15
That sound chip uses the snd-hda-intel module which is very mature and used for a number of chipsets.  Are you using a laptop or desktop?

---

### Post by kansasnoob on 2008-09-15
I see from a little googling that sound card has been a problem.

Look here:

[http://ubuntuforums.org/showthread.php?t=607378](http://ubuntuforums.org/showthread.php?t=607378)

---

### Post by markbuntu on 2008-09-15
If you are having problems with the HDA card/chip you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by swimstarguy on 2008-09-16
Thanks!

---

