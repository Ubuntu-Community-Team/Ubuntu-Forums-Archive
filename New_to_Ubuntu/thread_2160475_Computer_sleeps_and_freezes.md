---
title: "Computer sleeps and freezes"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by Lappert on 2013-07-07
I just installed Kubuntu 13.04 on an old HP laptop (dv5000) for testing. I had the same problem with Ubuntu. After I power-up and log on, I leave the computer on unattended for a while. I would expect the screen to go dark, and I would expect a squiggle with the mouse or some key activity would bring it back. I don't know if it's just the screen blcking out, or full scale sleeping.

Either way, it should come back. But it doesn't.

Once the screen blanks, it won't come back. No amount of key activity will bring it back. My only option is to power down the computer and reboot.

Any ideas on how to fix this will be appreciated. Thank you.

---

### Post by Feathers McGraw on 2013-07-07
Hi there,

You want to have a look at your Energy Saving settings (click the Kickoff icon in the bottom left and search for it).

What I expect is happening is that your computer is suspending the session after a few minutes. This does not work as it should on quite a few laptops (mine included) and I haven't found a way to get it to resume properly.

Thus, the workaround is to simply turn it off. Uncheck the suspend session tickboxes on the three tabs for AC power, battery and low battery.

While you're at it, you may also want to set the laptop to turn the screen off when the lid closes instead of suspending.

Feathers

[IMG]http://i.imgur.com/VarpIhv.png[/IMG]

---

### Post by Lappert on 2013-07-12
Thanks for the help. I tried your suggestion, but it didn't completely solve the problem. On further watching, I suspect it's a hardware problem. In some instances, the screen blanks even when I'm in the middle of writing something. Then about ten minutes later, it comes back. I have a feeling this is a hardware issue. The laptop is from 2006, so it's about 7 years old.

I'm only using this laptop for testing in anticipation of setting up a new workstation I'm building. I'm not a fan of Unity. Mint is OK, but not impressive. So far I sort of like Kubuntu.

---

### Post by edb66083 on 2013-07-12
If you have an older laptop, you may want to try something a bit lighter then either Kubuntu or Ubuntu, like Xubuntu or Lubuntu. I was using those on my 9 year old laptop, but can't any longer since it doesn't support pae. It might be worth a try.

---

### Post by Feathers McGraw on 2013-07-12
Yup, +1 to Lubuntu and Xubuntu.

I tried both of them (settled on Lubuntu) on an old laptop of my friend's and completely transformed it, he'd given up on it and bought a new one (it was about 6yrs old and could barely function on Win7, took 5mins to open a browser etc.).

He now uses it with [mixxx]("http://www.mixxx.org") and a MIDI controller as a simple DJ setup that he wouldn't mind someone spilling a pint on ;).

Not bad for something he was about to throw out!

Feathers

---

### Post by leunam12 on 2013-07-12
You need to install a different video driver (most likely).

---

### Post by Feathers McGraw on 2013-07-12
> **leunam12 said:**
> You need to install a different video driver (most likely).

You're probably right!

Lappert, if you would like to try a different driver could you enter this into a terminal and post the output here for us please?

```
sudo lshw -c video
```

Thanks,

Feathers

---

