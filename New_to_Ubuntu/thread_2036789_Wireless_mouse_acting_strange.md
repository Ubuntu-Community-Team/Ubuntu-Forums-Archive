---
title: "Wireless mouse acting strange"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by NoGumption on 2012-08-02
I installed Ubuntu 10.04 i386 on an old desktop about 5 days ago. It was working fine up until today.

My mouse isn't working properly. I tried putting new batteries in it - a few different sets and brands, Energizer, Duracell, and Rayovac if it matters. I also tried 2 other... mice? which acted the same way. The initial one is a Microsoft mouse/keyboard combo, one of the others is a Logitech mouse/keyboard combo, and the other is just a Logitech mouse. The keyboards work fine - no problems, but the mice act like the batteries are almost dead or there's a bad connection. I also tried rebooting, which didn't help.

There's about 2-6 feet between the piece that plugs into the computer and the mouse depending on how I'm sitting. The movement is mostly fine, with some non-responsiveness every now and then. Same for the right-click. The scroll-wheel works fine, don't know about the button, though, but I don't use that anyway.

The left-click, however, is really weird. It'll work fine for about 3 seconds here and there then either doesn't work at all, clicks when I'm not clicking, or treats a normal click as a double-click.

Any ideas?:confused:

---

### Post by gifford on 2012-08-02
I assume you are using a usb dongle for connection to the pc?

Have you tried using a different USB port to see if it changes anything?

---

### Post by mansonfan78 on 2012-08-02
Actually Ubuntu has issues with several models of Logitech mice, don't know about the Microsoft ones, but could be.  I had the same types of problems (particularly the single/double-click issue) with two different Logitech mice, solved it (sort of) by buying a new HP mouse.

---

### Post by NoGumption on 2012-08-03
> **gifford said:**
> I assume you are using a usb dongle for connection to the pc?

Have you tried using a different USB port to see if it changes anything?

I've tried all four USB ports on the back of the computer, all with the same weird problem.

[QUOTE=mansonfan78]Actually Ubuntu has issues with several models of Logitech mice...[/QUOTE]

Didn't know that. I'll see what other brands I can round up and post the results.

---

### Post by UltimateCat on 2012-08-03
I too have Ubuntu 10.04.  I put my old wired microsoft mouse back in the box. It worked but would consistently not work. (trackball)  So, I than purchased a wireless logitech and have not had another problem since.

Maybe you could consider a wireless mouse.

HTH

---

### Post by mansonfan78 on 2012-08-03
> **UltimateCat said:**
> I too have Ubuntu 10.04.  I put my old wired microsoft mouse back in the box. It worked but would consistently not work. (trackball)  So, I than purchased a wireless logitech and have not had another problem since.

Maybe you could consider a wireless mouse.

HTH
Both of my Logitech mice (that didn't work right) are wireless, the HP is wired.  And I'm actually running Xubuntu 12.04 but they won't let me change that in my profile until I have 50 posts (isn't that silly?)

---

### Post by gifford on 2012-08-04
I'm wondering if the issue is related to the USB port standard. With an older computer, it might be USB 1.0 specs and your mouse may be wanting a higher standard and data rate.

Could the easiest solution just be to use a corded mouse?

---

### Post by NoGumption on 2012-08-06
Alright. Sorry this took so long, ended up being gone for the weekend. A complete list of what I've tried so far with some additional information I didn't think to include before:

Microsoft wireless mouse/keyboard combo - laser mouse
Logitech wireless mouse/keyboard combo - invisible optic mouse
Logitech wireless mouse - invisible optic mouse
Microsoft wireless mouse - led
hama wired mouse - optical
Dell wired mouse - led

Every one of them has the same issues. I'm noticing there seems to be more of a problem in the main desktop area of the screen. That is, I have less problems clicking on things in the top bar. I can consistently open things without much (if any) trouble, but closing or interacting with them using the mouse is a huge pain.

---

### Post by mansonfan78 on 2012-08-07
Well, the only thing I can think of, since it's doing the same thing with every mouse, is a video driver issue.   That may not sound like it makes sense, but it actually could be the problem.  What kind of video card are you using?  And what driver - the preinstalled one or a proprietary driver from the manufacturer?

---

### Post by NoGumption on 2012-08-07
I don't know what video card I have, how do I check? Same for the driver. I haven't installed anything, so whatever comes with Ubuntu 10.04(.4 LTS I think) is what I've got. I'm unable to install anything per [other problems.]("http://ubuntuforums.org/showthread.php?t=2036143")

Hoping I did the URL thing right. If it doesn't work and you just want quick, no internet. If you'd like to look:

[http://ubuntuforums.org/showthread.php?t=2036143](http://ubuntuforums.org/showthread.php?t=2036143)

---

### Post by GreatDanton on 2012-08-07
Open terminal and type:
```
lspci
```
or
```
lshw -c video
```Now you will be able to see which graphic card you have and which drivers are in use.

Regards.

---

### Post by NoGumption on 2012-08-07
lshw -c video

```
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Radeon R300 NE [Radeon 9500 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:f0000000-f7ffffff(prefetchable) ioport:ec00(size=256) memory:ff8f0000-ff8fffff memory:ff800000-ff81ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R300 [Radeon 9500 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e8000000-efffffff(prefetchable) memory:ff8e0000-ff8effff

```

---

### Post by mansonfan78 on 2012-08-12
Don't know much about ATI drivers.  You could try rebooting into recovery console and load "failsafe graphics mode".  It won't look very pretty, but you could try using it for a few minutes and see if you have the same problems.  If you don't, that should at least verify that the video driver is the cause.  If you do have the same problems, then we could move on from there.

---

