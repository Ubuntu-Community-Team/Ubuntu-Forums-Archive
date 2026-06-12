---
title: "What is this symbol and how do I get past it?"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-11-30
Booting straight from the 12.04 CD that I burned, I get a solid black screen with this at the bottom:

[IMG]http://img829.imageshack.us/img829/4149/ubuntuf.jpg[/IMG]

Then nothing happens. Ever.

Ummm..... help?

---

### Post by arpanaut on 2012-11-30
That is a screen that usually appears for just a few seconds and allows you to tap any key to get to an interface that allows you to set boot parameters, check iso integrity, and a few other options.
Unusual that it hangs there. Did you check MD5Sum?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) Did you burn the CD at slow speed?  Good quality CD's 

Sounds like a bad iso or bad burn, do you have another system to boot the CD on to see if it works there.

---

### Post by Elect GMax on 2012-11-30
> **arpanaut said:**
> Did you check MD5Sum?

I have no idea what that is.

> **arpanaut said:**
> Did you burn the CD at slow speed?

I wasn't given a choice of burn speeds

> **arpanaut said:**
> do you have another system to boot the CD on to see if it works there.

No

---

### Post by arpanaut on 2012-11-30
1. check link in my post
2. check this out: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3, that's too bad.

Read those links then try a fresh burn, see if you have better luck.
Did you possibly try hitting some keys while you were stuck at that screen?
Still think it's a bad iso or bad burn try again.

Good Luck, and Welcome to the Forum!

---

### Post by Elect GMax on 2012-11-30
Probably a bad burn. I got some kind of error message during the post-burn disk-check. Fortunately, I have plenty of blank discs, so I can keep trying.

What the heck IS that symbol, anyway? What does it mean? Who drew it?

---

### Post by arpanaut on 2012-12-01
I've got no clue as to the symbolism, I just know that I wait to hit the spacebar as I hate to wait for the next  Try or Install screen and then wait for those to begin.
I just hit a key choose lang. and then choose Try... takes much less time.

You might want to try to create a Live USB instead of a CD if your burner in whacko.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Later...

P.S. if that is the actual icon you are getting then your iso is really messed.

---

### Post by Elect GMax on 2012-12-01
Yup, it was a bad burn. The second disc went without any hitches, one of my hard drives now has 12.04 installed on it, and I've moved on to trying to pull Unity's head out of its ***.

> **arpanaut said:**
> P.S. if that is the actual icon you are getting then your iso is really messed.

:lol:

No, it's just something that I hastily drew in MS Paint. We should make an art gallery of people's attempts at drawing it!

---

### Post by Cheesemill on 2012-12-02
> **Elect GMax said:**
> What the heck IS that symbol, anyway? What does it mean? Who drew it?
It means press any key to access the accessibility options, represented by a keyboard icon, an equals sign, and then the default gnome icon for accessibility options (take a look at Settings > Universal Access).

---

### Post by grahammechanical on 2012-12-02
That screen should be purple in colour.

At that screen press Enter, Then select your language at the next screen or press Enter to accept English as the default. Then press F6.

At the menu select nomodeset and press Enter. Then Press Esc and use the arrow key to select Try Ubuntu and press Enter.

The live session may be having difficulty accessing the video modes for your machine. So, we tell it to not set a video mode. That sometimes gets us to a Ubuntu Live Session which we can use to try Ubuntu or install Ubuntu. Then after installing we will get the opportunity to install a proprietary video driver using Additional Drivers.

Regards.

---

