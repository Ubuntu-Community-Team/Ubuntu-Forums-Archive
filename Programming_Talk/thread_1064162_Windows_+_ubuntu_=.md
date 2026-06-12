---
title: "Windows + ubuntu = ???"
date: 2009-02-08
forum: Programming Talk
---

### Post by codeking on 2009-02-08
I'm in somewhat of a sticky situation.  I'm a freelance web developer and designer.  As a developer, I favor Linux for its flexibility and usability.  As a designer, I favor Windows/Mac for having programs like Photoshop and Illustrator.  Right now I have a dual-boot running, but that can get rather tedious when I'm developing a design, I have to switch back and forth a few times.  So here are the options I have considered:

[LIST]
[*]**Leave it as-is** - As said above, not the most ideal situation.
[*]**Run windows on a VM in ubuntu** - I haven't found open source VM's to be very stable on windows.  Plus I need quite a lot of processing power for CS4, which VMs will do nothing but slow my system down.  plus, I don't have the windows install disk, so I would have to buy a new copy of windows, which I don't want to do.
[*]**Run ubuntu on a VM in windows** - I've done this, and it works nicely, but I'll need to shell out a couple hundred bucks in upgrades - More RAM, another monitor, etc. - For it to run nicely.  Plus, as with all VMs, its slower then running on a dedicated machine, and with Ubuntu as my primary OS, thats not the ideal situation.
[*]**Two computers networked together** - This isn't a bad idea, but it seems sorta wasteful to me, plus I'll need a seperate keyboard and mouse for the second computer... As well as the cost of buying a new computer + monitor.  I'm not too worried about the extra power usage, I'll only be using the windows comp occasionally.
[*]**Using WINE** - Running CS4 quickly and without bugs?  I don't think so.
[/LIST]

Any options I've overlooked?  Which option would you do?

---

### Post by PythonPower on 2009-02-08
I have been in that situation and just left it "as is". I know the pain it causes but I can manage.

I would consider one of the VM options or waiting for WINE to fix the bugs. WINE is making progress although it does seem quite slow to me.

It's hard to say; just my opinion. ;)

---

### Post by geirha on 2009-02-08
Have you considered using Gimp instead of Photoshop? It'll probably take a while to get used to, but I think Gimp should be able to do most things you can do in Photoshop.

Of the choices you gave I'd probably have chosen running Windows in virtualbox from Ubuntu, since Ubuntu is your main OS. 

On the last choice though. You don't necessarily need a new monitor and keyboard etc. There are switching boxes for that. You connect both computers to the switching box, with one keyboard, mouse and monitor attached, then you push a button to switch between which computer the monitor and peripherals are connected to.

---

### Post by cguy on 2009-02-08
Since you don't have a windows install disk and buying one would be expensive, go with "Run ubuntu on a VM in windows". Shutting it down would empower the base OS (Windows) and give processing power to PS.

All you'll need to buy is more RAM which is feasible if you save your lunch money for a few days. Check out the prices of the RAM! Dirt cheap!

All except the first option include buying a new monitor if you really want / need one. Since you can use seamless integration I don't see any reason why you MUST buy a monitor.

---

### Post by HotCupOfJava on 2009-02-08
> **geirha said:**
> 
On the last choice though. You don't necessarily need a new monitor and keyboard etc. There are switching boxes for that. You connect both computers to the switching box, with one keyboard, mouse and monitor attached, then you push a button to switch between which computer the monitor and peripherals are connected to.

Yeah, I use a little device by IOGear that lets me use two machines with one Keyboard, mouse and monitor. You just hit scroll lock twice and presto, you're looking at the desktop on the other machine. Network them together, and this may be the most pain-free solution (although using GIMP in Linux might be good, too).

---

### Post by codeking on 2009-02-08
I've tried GIMP, and although it is very feature-rich, it just doesn't have what I need.  Same thing with inkscape, it works, but doesn't do quite as well as illustrator.

I'll look into the switcher boxes, that looks like a good option.

**Edit:** I've checked out the KVM switchers.  They're cheap ($10-$20) and don't seem to have any drawbacks.  I think I'll look more into that option.  I'll see if the local computer store has any used/refurbed computers I can buy :D

---

### Post by Hobgoblin on 2009-02-08
> **HotCupOfJava said:**
> Yeah, I use a little device by IOGear that lets me use two machines with one Keyboard, mouse and monitor. 

It's called a KVM switch. ;)

---

### Post by ugm6hr on 2009-02-08
> **Hobgoblin said:**
> It's called a KVM switch. ;)

Software KVM's exist too: [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

---

### Post by slavik on 2009-02-08
synergy does not do monitor switching ... besides: vnc/nx

---

### Post by HotCupOfJava on 2009-02-08
> **Hobgoblin said:**
> It's called a KVM switch. ;)

I just learned something new......

---

