---
title: "Hi everyone! Installing on broken laptop; system works fine, screen is broken tho"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by marco.a.polanco on 2013-12-24
[FONT=courier new]**Hi all, and Merry Christmas!**

I'd like to greet everyone in this community and introduce myself. I used Ubuntu a few years ago as a "computer programming enthusiast" in high school, but soon switched back to Windows as I loved to play PC games. I gave myself a reality check, and my liking for both programming *and *video games withered as I'm looking towards starting this new year fresh! I'm pretty much done with Windows. I don't like it anymore. Only thing that kept me tethered to it was the games. I'm done. Thanks, Microsoft.

Now I would ***LOVE*** to be reacquainted with this sultry, seductive, resilient OS, for all the great times decoding that newfangled Linux Lingo, hours spent on exhausting troubleshooting... Yet— I can't install it!

_***—————MY ISSUE—————***_

Alright, so the machine I'm using is a Dual-Core [SIZE=2]Pentium[/SIZE] Laptop made by *ACER. *This tiny laptop is awesome -aside from the fact that the lid monitor screen is broken -which I didn't mind anyways since there's an HDMI port that can output the display to another monitor (Windows 7 does this in a very friendly manner) and still use it.

_**QUESTION**_[B]: Booting off the Live CD, how do I display the "Main Screen" through the HDMI output to my monitor?

[SIZE=2]_[COLOR=#000000]¿[/COLOR]SIMPLER QUESTION?_[/SIZE]: Booting off the Live CD, how do I clone my display?

[/B]Normally, as I boot off the Live CD, everything loads okay (to my knowledge). The display monitor (a 21" Dell) is plugged in the laptop through HDMI. The backlight from the lid is on, but you can't see squat 'cause it's broken (all you see are shards and edges of purple and grey on white). What I see through my display monitor (when everything loads) is the **right side** of the desktop, because apparently, the OS recognizes **both** "display devices" and outputs the **left side** of the desktop to the broken lid. The left side has all the stuff I need for OS install, and I can't interact with it, because I can't see it.

I know t[SIZE=2]hat the [/SIZE]simplest solution would be to enter Terminal Mode before the Live CD and to just install Ubuntu through input commands, but I don't want to do that. I would like to enjoy the novelty of being directed through this new experience (yet again). To start fresh, yo!

Thanks for reading! [SIZE=1]******* WINDOWS *cough****[/SIZE]

**[SIZE=1]...Or maybe I should just tear that damn lid off...[/SIZE]**[/FONT]

---

### Post by ian-weisser on 2013-12-24
Many motherboards with VGA ports will clone the display upon boot if they detect a monitor on that port.
But I have not seen the same feature on HDMI ports. They may exist...but I haven't seen it.
That's a hardware issue, not a Live environment setting.

The Live image is designed to be a demo environment. It is handy for repair/recovery, but that's not what it's designed for.

---

### Post by marco.a.polanco on 2013-12-24
Ah...! My laptop does come with a VGA port. I will test that and see if it works, thanks!

---

### Post by Bucky Ball on 2013-12-24
Welcome. Yea, try with the the dv/dvi/vga plug rather than hdmi. That should be a straight clone.

Just a heads up: The bold is fine, but please use default font and size. Thanks.

---

### Post by marco.a.polanco on 2013-12-24
Success! Thanks, Ian, for the help! I restarted the PC with the VGA port in, got to install Ubuntu, and switched back to HDMI. I'm typing this on Ubuntu right now. Yay! All that's left is to migrate the few programs I was used to working with under Windows... There's always Wine to help!

And no problem Mr. Mod, thanks for the help!

EDIT1: One last question- how do I mark a Solved Thread?

EDIT2: And yet another- what's a good resource for configuring fresh installs?

---

### Post by Bucky Ball on 2013-12-24
Follow link in my signature to mark thread as solved. Enjoy!

---

### Post by ian-weisser on 2013-12-24
> **marco.a.polanco said:**
> EDIT2: And yet another- what's a good resource for configuring fresh installs?

Depends on what you wish to configure or customize. [http://help.ubuntu.com](http://help.ubuntu.com) is good for most common subjects.

---

### Post by Bucky Ball on 2013-12-25
> **marco.a.polanco said:**
> EDIT2: And yet another- what's a good resource for configuring fresh installs?

Please post a new thread regarding this as it is off-topic to this one's title. This will increase your chances of getting support.

Use a descriptive title and as much detail as poss about what you want to configure. Good luck.

---

