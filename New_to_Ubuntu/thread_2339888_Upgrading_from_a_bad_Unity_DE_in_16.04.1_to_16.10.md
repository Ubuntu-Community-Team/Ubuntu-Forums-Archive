---
title: "Upgrading from a bad Unity DE in 16.04.1 to 16.10"
date: 2016-10-13
forum: New to Ubuntu
---

### Post by reykevster on 2016-10-13
So I got the email, 16.10 is out, but I have a question:


Upgrading from 14.04 to 16.04, for me, was a disaster insofar as I still have no working Unity DE.  Actually I had to upgrade to 15.10 before I was allowed to upgrade to 16.04.1.  Yes, I waited for the .1 to come out as I thought it was safer.  Anyway, thank goodness I had other DE's and Cinnamon has saved me.  Admittedly, I haven't had the time to pursue every possible fix for that but, there it is.


My question is:


Do you think upgrading to 16.10 might fix that or, make it worse?  Do you think that if I upgrade now, with a messed up Unity DE, my problem might be solved?  Or, must I get Unity fixed before upgrading to 16.10?


Any advice appreciated.


Thank you,


Kevin

---

### Post by Frogs Hair on 2016-10-13
16.10 is only supported for 9 months so 16.04 is a better option for the long term. I don't think another upgrade would help though you haven't described what the problem with Unity is.

---

### Post by Bucky Ball on 2016-10-13
Upgrading a broken install in the expectation it will fix it generally leads to disappointment.

You are much better posting about what issues you are having with Unity in 16.04 and trying to fix them. An upgrade is not a solution (unless you want to end up with the same broken Unity in a release that came out yesterday and will no doubt have teething problems quite apart from the one you're having).

---

### Post by reykevster on 2016-10-13
Thank you Frogs Hair.  Sounds good, I'll stick with 16.04.  I thought the Unity problems deserved a question all their own.  I didn't want to mix things up.  Thanks again!

---

### Post by reykevster on 2016-10-13
Thank you Bucky Ball.  Yeah, sounds like good advice.  I thought the Unity problems deserved a question all by itself.  I didn't want to mix things up.  Thanks again!

---

### Post by Geoffrey_Arndt on 2016-10-13
Frankly . . . . IF this is the System76 machine you're running (_which is 100% compatible with Ubuntu)_,   I'd opt for a full clean "re-install" of 16.04.1 LTS.   In my experience with Linux/Ubuntu/System76 , , a full-install should provide a flawless Unity and can be done in 30 to 45 minutes or so.

If you need info on how to do a clean install . . just let us know.

---

### Post by monkeybrain20122 on 2016-10-14
Firstly upgrading takes long time and problem prone, you should do a fresh install especially that your system is already broken (very possible from your previous "upgrade") Secondly you are asking for troubles to install a new OS days after it is released. I would wait for a month at least until the post release bugs are ironed out. Thirdly, as others said 16.10 is supported for only 9 months. I don't always stick to LTS, but this is a valid consideration. Unless you have compelling reasons (like hardware not working and there is no other workarounds ) I don't recommend trading in a working system after only 6 months. I tested 16.10 briefly and it is not that different from 16.04, except the wall paper hurts my eyes (too red)

I suggest you backup your data and do a fresh install of 16.04 instead. I have a feeling that your problem is caused by 'upgrading' from 14.04 to 16.04. Test with a 16.04 live usb first.

---

### Post by reykevster on 2016-10-17
Thank you [[COLOR=#000000]Geoffrey_Arndt[/COLOR]]("https://ubuntuforums.org/member.php?u=1973436")[COLOR=#000000] !  This sounds like the right thing to do.  Can you tell me please, how do I go about doing that.  Yes, this is a System 76 machine I got in mid May, 2014 with Ubuntu 14.04 installed.  I had just migrated from Windows when they dropped support for "XP".  I would be willing to buy something to make that happen, you know, a CD or thumb drive or whatever.  Thanks again [/COLOR][[COLOR=#000000]Geoffrey_Arndt[/COLOR]]("https://ubuntuforums.org/member.php?u=1973436")[COLOR=#000000] .
Kevin

[/COLOR]

---

### Post by reykevster on 2016-10-17
Thank you monkeybrain20122.  Yes, re-installing 16.04 sounds like the right thing to do.  What's the best way to do that?  I would be willing to put out a few dollars to make that happen.  Thanks again monkeybrain20122.
Kevin

---

### Post by Bucky Ball on 2016-10-17
What do you need money for? Just download Ubuntu 16.04 if you haven't already, create install media and install it. Which bit do you need help with there?

Are you talking about spending money on a modern version of Windows? If that is the case, buy a copy and install that first.

---

### Post by reykevster on 2016-10-17
Hi Bucky Ball.  I hope my lack of tech savvy doesn't upset anyone here.  I thought I might need to buy a DVD or a CD with Ubuntu 16.04.1 on it.  I really don't want to have anything to do with Windows.  That's the decision I made when they dropped support for XP and I'm sticking with it.  :)  Sorry if my evident ignorance is a pain.  Thanks for your help.
Kevin

---

### Post by Bucky Ball on 2016-10-17
All good. Just [download the ISO from here]("https://www.ubuntu.com/download/desktop") then create a USB or DVD to install by burning a disk image using the ISO. You can use something like Rufus or UNetbootin to create a USB on Win or the default disk burner in Win should be able to create a disk image to DVD. [See here for details]("https://www.ubuntu.com/download/desktop/install-ubuntu-desktop").

You then boot from whatever install media you've created (by booting to the BIOS or F12 for boot device options and booting from the USB or DVD) and you're on your way. Just let us know where/when you get stuck.

Just curious: how did you install 16.04 LTS in the first instance? Did you lose that install media?

---

### Post by reykevster on 2016-10-18
Hey Bucky Ball.  Thank you.  I really appreciate it.  When 16.04.1 came out I was able to go through "Software Updater", something I couldn't do when it was just 16.04 and I had thought, heard actually, that it would be safer and more solid to do it that way so I never had any media.  So it was "Software and Updates" > "Updates" tab > "Notify Me of Any New Version" > "For Any New Version".  Then click the "Upgrade" button in "Software Updater".  That's how I did it.  Thanks again Bucky Ball.  Again, appreciated.
Kevin

---

### Post by reykevster on 2016-11-28
Okay!


I finally got a chance to try this.
I got my ".iso" image burned to a DVD.


Disconnect my external hard drive, as the ".iso" tried to install there.


Boot to DVD, click install, and I have 6 choices:


1. Erase 16.04.1 and reinstall
	Note: This will delete all programs and files.
2. Install alongside 16.04.1
	Note: Keep everything but have 2 OS's to choose from on every boot, both of them being 16.04.1
3. Erase disk and install
	Re: Note 1
4. Encrypt
5. Use LVM
6 Something else.


The problem: I don't want to loose all my programs just now.
The question: Can't I just install over the old OS?


It looks like I have 2 choices:
1. Loose everything, or
2. Have a dual boot 16.04.1 system.


Is that really it?


Any help is appreciated.


Thank you,
Kevin

---

### Post by Bucky Ball on 2016-11-28
Yes, you can. Choose 'Something Else' and partition the drive manually. You can select your / partition and install the new install over that. Leave your existing /swap and the new install will use it.

One thing has me a little confused.
> 
The problem: I don't want to loose all my programs just now.
The question: Can't I just install over the old OS?

The answer is yes, you can install a new OS over the old but that will wipe the old OS and everything in it, including whatever programs you've installed (and your personal data if you have it stored in /home directory in that partition also).

So not sure where you go from here.

---

### Post by reykevster on 2016-11-29
Thank you Bucky Ball.  Right now I am too dependent on my programs to wipe them all out.  Come March I may be able to give it a try.
Thanks again Buchy Ball.  I appreciate the help.
Kevin

---

### Post by reykevster on 2016-11-29
Thank you Bucky Ball.  Right now I am too dependent on my programs to wipe them all out.  Come March I may be able to give it a try.
Thanks again Bucky Ball.  I appreciate the help.
Kevin

---

