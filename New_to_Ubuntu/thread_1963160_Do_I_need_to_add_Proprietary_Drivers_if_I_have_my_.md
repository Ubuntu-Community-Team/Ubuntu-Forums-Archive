---
title: "Do I need to add Proprietary Drivers if I have my BIOS set up to accept Linux?"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Doxa on 2012-04-22
Prior to deleting Windows (totally premeditated), I installed the BIOS driver for my Gateway NV53A24U that is meant for Non-Windows use.  Should I install the proprietary drivers?  And if not, how do I dismantle that function from continually popping up on my desktop?

Thanks :)

Doxa 
:-({|=

---

### Post by 3rdalbum on 2012-04-22
No driver for Windows will be working when you're not running Windows, if that's what you're asking.

Exactly what driver are you being offered? If it's being offered, then you might as well install it. Nothing you've installed before on Windows will be relevent on Ubuntu, remember.

---

### Post by Doxa on 2012-04-22
I'm scared to.  That's why the last time my OS crashed, I installed windows and went to gateway.com and downloaded the BIOS that said it was for non-windows installations.  
It's for the proprietary drivers, however when I go to my BIOS screen, its says that the exact driver that is to be installed is already installed.  So, should I do it?  I just put everything back on the computer and deleted it from the hard drive.  If it crashes this time, I will lose everything.

Oh and I'm on Ubuntu 10.04 GNOME.  I've got a Gateway NV53A24U standard.

---

### Post by 3rdalbum on 2012-04-22
> **Doxa said:**
> I'm scared to.  That's why the last time my OS crashed, I installed windows and went to gateway.com and downloaded the BIOS that said it was for non-windows installations.  
It's for the proprietary drivers, however when I go to my BIOS screen, its says that the exact driver that is to be installed is already installed.  So, should I do it?  I just put everything back on the computer and deleted it from the hard drive.  If it crashes this time, I will lose everything.

Oh and I'm on Ubuntu 10.04 GNOME.  I've got a Gateway NV53A24U standard.

The BIOS doesn't deal with drivers. What I think you attempted to install was a BIOS update - but you already had the updated version.

Ubuntu needs to be able to know the language to use to talk to the hardware. Currently Ubuntu has a limited vocabulary when talking to your hardware, because it's using its own driver. The proprietary driver you've been offered will give Ubuntu the full vocabulary so it can use more of your hardware's features.

There's a small possibility that the driver might make things worse, but it's rare. You won't lose your data in any case. It would still be on the hard disk, ready for you to pluck it off using an Ubuntu CD. Or you'd just have to remove the driver and then you'll be back to normal.

If everything on your computer is working just fine for you, then there's of course no need for any additional driver. But generally you'll get better performance, lower temperatures or additional features by installing a proprietary driver when one is available.

What you've got in the BIOS is nothing to do with drivers. I can say that definitely. Nothing in the BIOS gives Ubuntu a way of talking to the hardware.

---

### Post by Doxa on 2012-04-22
Doing it, and will inform you of the outcome. :KS

---

### Post by Doxa on 2012-04-22
Upon restart, it works.  Just like it did before.  I'm hoping that it stays like this.  The problem might have been that I had a distro that was too overwhelming for my computer. Thank you for answering my question.  I've been loathe to register on the forum and have led myself some wrong turns.  I like asking before doing now.  Thanks, again!  :KS

---

### Post by Bartender on 2012-04-23
I've never heard of a "Non-Windows" BIOS before.  The BIOS (Basic Input Output System) doesn't really have anything to do with the OS, which boots up later.  
 
Does it?

---

### Post by Mark Phelps on 2012-04-23
> **Bartender said:**
> I've never heard of a "Non-Windows" BIOS before.  The BIOS (Basic Input Output System) doesn't really have anything to do with the OS, which boots up later.  
 
Does it?

As far as I know, you are correct -- BIOS is OS-independent as it takes over the PC long before any operating system is loaded and actually hands off control to a boot loader when it is finished initializing.

---

### Post by Fraoch on 2012-04-23
> **Doxa said:**
> Upon restart, it works.  Just like it did before.  I'm hoping that it stays like this.  The problem might have been that I had a distro that was too overwhelming for my computer. Thank you for answering my question.  I've been loathe to register on the forum and have led myself some wrong turns.  I like asking before doing now.  Thanks, again!  :KS

This driver was probably for your video.  Ubuntu detected that a proprietary driver was available for it and offered to install it for you.

---

### Post by Doxa on 2012-04-24
well now it's not showing up at all.  crashed...
so i'm going to change to meercat...maybe an apt install will get all that working again...

---

### Post by PaulW2U on 2012-04-24
> **Doxa said:**
> well now it's not showing up at all.  crashed...
so i'm going to change to meercat...maybe an apt install will get all that working again...

Maverick Meerkat 10.10 is no longer supported, you won't get any updates for it.

---

### Post by Fraoch on 2012-04-24
> **Doxa said:**
> well now it's not showing up at all.  crashed...

What do you mean?  Can you be more specific?  What's not showing up and how is it crashing?  Do you get any error messages?

---

### Post by Bartender on 2012-04-24
Doxa -

It might be helpful if you could provide a link to this Gateway site with the "Non-Windows" BIOS.  I'm curious to see what that's about.

You know the basics, right?  That the BIOS is a small package of data stored on a chip that's typically soldered to the motherboard?  And that little coin battery on the motherboard provides the power needed for the chip to store & access the BIOS data?  When you first push the "On" button your PC is dumber than a bag of hammers.  It doesn't know the first thing about itself.  The data stored on the BIOS chip tells the PC about itself, then which devices it has attached to itself, then which of those devices to spin up to find an operating system.

I'm very leery of replacing or updating the BIOS unless there's a clear reason to do so.  If anything goes wrong while flashing the BIOS you could easily end up with a junk motherboard.  So the first concern I have in your case is that you could brick your motherboard by mucking with BIOS.

The second concern I have has been mentioned earlier: I've never heard of replacing the existing BIOS with another in order to install a non-Windows operating system.  So I'm thinking that there's no need to be messing with BIOS in the first place.

My third concern?  "Drivers" are packages of data that allow the operating system to talk with the hardware.  *As far as I know*, drivers are not part of BIOS.  Drivers come into play as the operating system is loaded and tries to take charge of the devices such as video, audio, network, etc.  But you've been talking about BIOS and drivers interchangeably.  So I'd want some clarification on that.

EDIT: We can check your BIOS easily enough.  When you first push the "On" button, you can interrupt the boot sequence and get into BIOS by pushing a key repeatedly.  It's often F2, or Delete key.  See if you can get into BIOS and go thru the basic menus.

---

### Post by Fraoch on 2012-04-24
> **Doxa said:**
> I installed the BIOS driver for my Gateway NV53A24U that is meant for Non-Windows use.

I believe what the site means by this is...a lot of motherboards these days come with Windows utilities to update the BIOS directly from within Windows.  Obviously you can't do this from within Linux - therefore you need something to be able to install from a command-line as the PC is booting.  That's what this "non-Windows" BIOS was about - it's not that it's not for Windows as the BIOS doesn't care, it's for *installing* outside of Windows.

Looks like Doxa has other problems at the moment but I'm pretty sure that's what it means.

I'll second what Bartender says - updating a BIOS is a very risky thing.  If anything goes wrong while it's updating, including a power failure, you now have a useless motherboard.  Only update a BIOS if the new one specifically addresses a problem you're having.  Or if you're feeling adventurous.;)

---

### Post by Mark Phelps on 2012-04-24
> **Fraoch said:**
> .. it's not that it's not for Windows as the BIOS doesn't care, it's for *installing* outside of Windows 

OK ... understand now ... My old ASUS motherboard had something called EZ-flash -- which did the same thing.  You booted using a special key combination and you could then flash the BIOS from diskette or USB stick.

---

### Post by jerome1232 on 2012-04-24
> **Fraoch said:**
>  including a power failure, you now have a useless motherboard.

not to roam further offtopic...

Perhaps because I haven't purchase a pre-built pc, but every motherboard I have ever owned the Bios used a socket type connector. I actually just recently flashed the incorrect bios image to this computers bios, $7.50 US dollars and 3 days later a new bios from an online bios vendor saved my life. Even came with a new cmos battery.

---

### Post by Bartender on 2012-04-24
Hey, jerome -
Thanks for the update, and I'm glad to hear it worked out for you.  It worries me that sometimes I make statements that I believe to be correct but they're not true any longer, or are only partially true.

Fraoch's comment about the "non-Windows BIOS" being a method to _flash_ the BIOS, not the BIOS itself, makes sense to me.  

I recently updated the BIOS on an old (2004) HP nc6000 laptop that was given to me by the IT dept. at work.  Windows had been blown away.  There was a "flash BIOS from within Windows" option, and there was a "flash from floppy" option.  I lucked out - the IT dept. threw in a genuine HP external floppy drive on a USB interface.  I didn't know such a thing existed!

---

### Post by Fraoch on 2012-04-25
Since the OP seems to have vanished...?

> **jerome1232 said:**
> Perhaps because I haven't purchase a pre-built pc, but every motherboard I have ever owned the Bios used a socket type connector. I actually just recently flashed the incorrect bios image to this computers bios, $7.50 US dollars and 3 days later a new bios from an online bios vendor saved my life. Even came with a new cmos battery.

Oh yes I forgot about socketed BIOSes!  Doesn't one vendor also have dual BIOSes (Gigabyte?)

Actually the board I have by MSI has a neat feature - from within the BIOS you can not only write all BIOS settings to a flash drive, it actually copies the entire BIOS ROM to a flash drive.  In the event of a failure the flash drive can either write the BIOS back to the chip with settings or even function as a BIOS chip.  Of course with a non-functioning BIOS I can't see how a board can even read a USB stick but neat idea all the same.

I still think flashing a BIOS always carries a risk though.

---

