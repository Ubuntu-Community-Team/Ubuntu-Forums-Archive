---
title: "Unable to install with Radeon HD 7340."
date: 2013-04-17
forum: New to Ubuntu
---

### Post by petr0lb0mb on 2013-04-17
Hi, wisecat.

Can I ask how you were able to get Ubuntu installed in the first place with the Radeon HD 7340?  I have a Toshiba Satellite C855D-S5320 which has the Radeon HD 7340.  When I try to install or even live boot Ubuntu Desktop (64bit AMD), I only end up with a black screen.  I'm not asking you to write me a tutorial but just some helpful pointers would be great.  I'm specifically wondering if there's a way for me to create a custom install DVD that will include the beta drivers you speak of so that I may get the install off the ground.

P.S., This is my first post here.  I'm a Linux newbie.

---

### Post by coffeecat on 2013-04-17
@petr0lb0mb, I've moved your post into its own thread where you are more likely to get answers to your question. The person you are addressing has not logged in since they last posted over three weeks ago, and the way to get optimal help is to start your own thread where the wider forum membership will see it and be able to help you.

Creating a custom DVD is not the best way to go - I am sure that someone will help you find a way of booting up the live CD to a usable desktop so that you can perform an installation.

---

### Post by ajgreeny on 2013-04-17
When you boot to the normal live DVD you can hit any key at the first screen, choose language, then hit F6 and use the nomodeset boot option as a first attempt.  That may get you to a GUI and you can install from there.

We can then help you use nomodeset as default if needed after installation, though a full update may allow you to boot without that option being needed.

---

### Post by petr0lb0mb on 2013-04-17
Thank you coffeecat and thank you ajgreeny.

Ajgreeny, I will give it a go pressing F6 and choosing nomodeset.  Will report back.

Thanks!

---

### Post by petr0lb0mb on 2013-04-17
Update: Well, the install doesn't get much further than it did before.  After selecting "Try Ubuntu without installing" I begin pressing F6 key.  The install still stops at the same place except that that it reads "^[[17" from the key press.  If I spam the key a bunch of times then it looks like ^[[17^[[17^[[17^[[17^[[17 at the top of the screen.

Am I doing something wrong?  Sorry if this is a stupid question.  Any pointers?

---

### Post by ajgreeny on 2013-04-17
There are several other boot options on the F6 key, if I remember correctly, so try them one by one; hopefully you will find one that allows you to boot properly.

---

### Post by coffeecat on 2013-04-17
> **petr0lb0mb said:**
> After selecting "Try Ubuntu without installing" I begin pressing F6 key.

I think you're pressing F6 far too late. The "Try Ubuntu without installing" is a couple of minutes after you start booting the live DVD, is it not? ajgreeny said to tap any key at the first screen. I think you may have missed that.

As soon as the live DVD starts booting, you'll see a purple screen with two small icons at the bottom. Tap any key, select your language from the list and then you'll see an old-style text menu. At the bottom of the screen you'll see the prompts for the various F keys. Press F6 and then select nomodeset.

---

### Post by petr0lb0mb on 2013-04-18
I see.  Perhaps this is a clue.  The "Try Ubuntu without installing" screen is the first thing I see after the Toshiba splash screen.
I've searched exhaustively for a way to disable the Toshiba splash screen to no avail.

I will try the option to press 'e' to edit the commands before booting.

I feel like I'm on the right track.  Thanks for your input coffeecat.  I'll report back when there is some news.

---

### Post by petr0lb0mb on 2013-04-18
Okay... Making progress but now I'm stuck further down the line.

So, I pressed 'e' to edit the commands.  Added nomodeset to the GRUB CMDLINE after quiet splash and enclosed in quotes "casper quiet splash nomodeset"
Well, that got me to the next stage (which I never got to previously) where it appears to be discovering hardware.
It was cranking along and then suddenly stopped at the following line:
7.754860] usb 2-4: >Manufacturer: Importek

Any thoughts?

---

### Post by coffeecat on 2013-04-18
@petr0lb0mb, apologies - I missed an important detail. Googling your "Toshiba Satellite C855D-S5320" came up with this forum thread:

[http://ubuntuforums.org/showthread.php?t=2102331](http://ubuntuforums.org/showthread.php?t=2102331)

You have a Windows 8 machine with secure boot and UEFI which all add a degree of complexity. Added to which, the last post there does not give one optimism that your particular laptop is going to be Ubuntu friendly. First thing, don't do as the OP did and disable secure boot. Before you proceed further you need to know a little more about the issues confronting you. See here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

One point to pick up: when you mention the "Try Ubuntu without installing" screen, is it white on black as in the EFI mode screen in that link? If so, you are booting the DVD correctly for your model of laptop, and you can ignore my "purple screen with two small icons" suggestion. I made the unthinking assumption that you were booting in legacy mode.

At this point it's not clear whether your problem is really down to the Radeon GPU - it might be an issue with the laptop firmware. One other question so that others might be able to help. Which Ubuntu version are you trying, 12.04 or 12.10?

---

