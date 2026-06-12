---
title: "Initial query"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by Charles_Moran on 2014-06-27
Hello!
I've just installed Lubuntu on an old, spare PC (when I say old, I mean new enough to have been running Win XP before), in order to find out what the fuss is all about. A couple of things puzzle me: I noticed, during installation, that when I clicked radio buttons or ticked boxes, they sometimes seemed to disappear - i.e. become invisible. Also, when I open a window, the icons within it are sometimes visible, sometimes not, with no apparent pattern to this behaviour. Is it supposed to happen, for a reason, or is it a hardware/firmware compatibility issue?
Thanks,
Charlie

---

### Post by grahammechanical on 2014-06-27
The installation runs from a DVD or USB Memory stick with the program running in memory. Another thing, the live session/install session uses an open source video adapter. A lot depends upon the power of the CPU, the amount of RAM and the power of the graphic adapter and the amount of memory of its own that the graphic adapter has.

If, at the start of the installation process we ticked "Install Third Party Software" then we will get a proprietary video driver installed and that may give a better experience than the open source video driver. But really, there is not much point is discussing the live session experience as we should expect the live session not to work as efficiently as an OS that is installed onto a hard disk.

What is you user experience like now that you have installed Lubuntu? A problem you might run into with old hardware is that the video adapter manufacturer may have dropped support for the video card from its latest video drivers and an install of Ubuntu and its flavours like Lubuntu will install the latest video drivers and not an older driver that might be more suitable for that video card.

Regards.

---

### Post by 3rdalbum on 2014-06-27
> **Charles_Moran said:**
> Hello!
I've just installed Lubuntu on an old, spare PC (when I say old, I mean new enough to have been running Win XP before)

That could still be up to thirteen years old!

> A couple of things puzzle me: I noticed, during installation, that when I clicked radio buttons or ticked boxes, they sometimes seemed to disappear - i.e. become invisible. Also, when I open a window, the icons within it are sometimes visible, sometimes not, with no apparent pattern to this behaviour. Is it supposed to happen, for a reason, or is it a hardware/firmware compatibility issue?
Thanks,
Charlie

Definitely not supposed to happen, I would imagine it might be a graphics hardware problem or a graphics driver problem. Do you know what graphics card you have in that computer?

Also, now that the system is installed does the same thing happen?

---

### Post by Charles_Moran on 2014-06-27
Thanks for your replies! I'll check what graphics card is in there and get back to you - although there may be a few days' delay due to work commitments.
Cheers,
Charlie

---

### Post by Charles_Moran on 2014-07-02
Hi again,
I have more details regarding my query:
I do have Lubuntu installed on the hard disk, and did not experience any installation problems, except that it would not reboot the pc immediately after installing - I had to reset it.
About the "invisible" icons: when I open a window, such as file manager, all the file names are present where you'd expect them to be, but some or all of the icons themselves are invisible, and may or may not appear when I click on/hover/pass over the spot where they should be. Anyone else experience this?
The graphics card installed is a GeForce2 mx-400. I do have a couple of other cards I could try, a 3D Rage II and an Nvidia TNT2, but I wonder, would Lubuntu recognise the change of hardware and reconfigure itself accordingly, or would I have to do a full reinstall?
Cheers,
Charlie

---

### Post by Charles_Moran on 2014-07-12
Is anyone out there? Where's everybody gone? :)
For the possible benefit of anyone who may encounter the same display problem (see earlier posts) I solved it.
I tried replacing the GeForce2 graphics card with the TNT2, and found that icons were no longer disappearing at random - BUT that there was now a problem with colour resolution at startup (when the "Lubuntu" logo first appears).
I put the original card back in and, with a little experimentation, finally found that disabling anti-aliasing solved the icon problem. I'm curious why that worked (?), but it worked. To compensate for the change, I found I also needed to enable full "hinting".
As it turned out, then, the age of the pc had no bearing on the problem. From what I've read about Lubuntu (and the other Linux o/s's) part of their ethos is that they cover a wide spectrum of equipment capabilities - certainly including the pc I'm using.
Cheers,
Charlie

---

### Post by sudodus on 2014-07-12
As long as you have the built-in drivers (that is, you have not installed any proprietary driver), Lubuntu will select the best possible driver, when you change card. When I started using linux, I was very surprised that it works like this, but it does :-)  Still it is sometimes necessary to tweak something.

I'm glad you solved the problem, and thanks a lot for sharing your solution.

Edit: Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Bucky Ball on 2014-07-12
> **Charles_Moran said:**
> For the possible benefit of anyone who may encounter the same display problem (see earlier posts) I solved it.


In light of this and the fact you don't drop by often by the looks, I have marked it as solved for you so it might be of maximum benefit. Nice work figuring it out and good luck. ;)

---

