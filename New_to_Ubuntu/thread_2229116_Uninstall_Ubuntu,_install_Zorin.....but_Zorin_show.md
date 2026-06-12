---
title: "Uninstall Ubuntu, install Zorin.....but Zorin shows Ubuntu; why?"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Mike_Walsh on 2014-06-11
Afternoon, all.

I'm trying to install Zorin O/S Ultimate 64-bit, in place of Ubuntu 14.04.

I'm trying to get the Zorin Live Session up and running, so I can install it from there.

I installed Ubuntu about a month ago; prior to this, I was running Win XP. While running under XP, I created a number of Live Session CDs, every one of which, including the Zorin Ultimate 64-bit, functioned perfectly.

Now, I understand that running a Linux LiveCD from WITHIN another Linux O/S is rather more complicated. I've tried Zorin THREE different ways, now; as a LiveCD, as a LiveUSB stick, AND from a partition on my external hard drive, which I've formatted to behave as a USB stick. 

EVERY single time, the Zorin splash screen will come up, as it should. But after this, it opens into the Ubuntu desktop...EVERY time.

What am I doing wrong?

Remember, I'm an XP refugee! Can anybody explain to me, in plain single English, how to get round this? (Not command-line terminology, please, because I DON'T understand it...) 

I appreciate that to you Linux experts, using the terminal is second nature, like breathing. But I'm afraid I came to Linux, as an easy-to-get-on-with alternative to paying out BIG bucks to one of the world's biggest and most self-centred organisations, for bloated and horrendously over-priced software.....I REFUSE to go down that road again!!!

On top of which, I just don't have the time to learn a completely new programming language...sorry! (lol)

Can anybody help.....please?

Mike Walsh.

---

### Post by 3rdalbum on 2014-06-11
Can you please describe exactly what is happening? For instance, is it this:

The Zorin splash screen comes up with the options "Try Zorin OS", " Install Zorin OS", "Boot from first hard disk". I choose Try Zorin OS and this screen immediately disappears and the purple Ubuntu loading screen with the dots appears. Then the purple login screen comes up where I can log in with my normal username and password and access my normal files.

^That is a good level of detail to give when asking for help. If we know what you are seeing on the screen and what you are doing we will be able to help.

---

### Post by buzzingrobot on 2014-06-11
Just to be sure, a LiveCD cannot be run "within" another Linux. If the Zorin images booted successfully before, they should boot now.

---

### Post by LastDino on 2014-06-11
Not the solution, but food for thought from one windows refugee to another;
I don't know about Zorian but when Linux distro shares its /home with another, desktop settings and all gets shared too and after booting you will see the desktop which you were booting into originally or was/is the original owner of that /home. 
Don't think that applies to live seasons though, so I'm bit interested as well.

---

### Post by Mike_Walsh on 2014-06-11
Hi, 3rdAlbum (& others...)

Okay. What happens is quite simply, this:-

What I describe as the 'splash screen' is the initial Zorin screen, with the white "Z" logo on the pale blue background. The 'Z' logo 'flashes' about 9 or 10 times. The screen then goes blank for about 20-25 seconds; sometimes, the next occurrence is the appearance of a window on this blank screen, top left corner, saying "System Error detected; do you want to send a report? Send/Cancel"

The buttons on this window don't respond, and about 30 seconds later it will open into the Ubuntu Unity desktop. It then asks for a password to send this error report, which I can't enter, because you don't set up a password on the Live Session.!This keeps repeating until I reboot back into the normal O/S.

On other occasions, this window doesn't appear, and the next thing I see IS the Unity desktop, with the 'Install Ubuntu 14.04' icon on the desktop.

Yet when I tried the Live Session under XP, the 'Z' logo appeared on the blue screen, did its thing, then the next screen was, "Do you want to try Zorin O/S first, or install it straight away?", as you would expect! I selected "Try Zorin", and then the Zorin desktop appeared, complete with the install icon on the desktop...

Now that I am running Ubuntu, I cannot make this happen..!

Any ideas?

(Incidentally, on power up, after setting the boot to whatever I am attempting to boot from...you remember, I've tried to do this THREE different ways (!); the initial Unetbootin screen ALSO won't respond to arrow keys and selection. It sits on the initial 'Default' setting, and all I can do is wait for it to start by itself...)

Does that tell you anything?

Any suggestions will be gratefully received! I've been going round in circles on this for the last 4 or 5 days now.....


Mike Walsh.

ps Just so that you all know, although I've been using these things for over 30 years, the Ubuntu install the other week, when I replaced XP, was the first time I've ever done an install...so I'm quite a novice in that respect too!

---

### Post by LastDino on 2014-06-11
Hmm did you install Ubuntu using the same LiveUSB? Did you try with different Zorian ISO? What are the options that you see on that Unetbootin screen? I would really love to see some screen pics if possible.

---

### Post by Mike_Walsh on 2014-06-11
Hi, Last Dino.

No. The Ubuntu install was implemented from a partition on my external hard drive, which had been formatted to FAT32, so that it would behave as a USB thumbdrive.

The Zorin Live Session has been installed on a completely different 32 Gb SanDisk CruzerBlade thumb drive, which was re-formatted prior to use, so that it was totally blank.

Shouldn't have been ANY chance of old data corrupting the install..!

Mike.

---

### Post by oldfred on 2014-06-11
Sometimes things are not were we think they are.
Best to see details. 
From live installer or any working Linux (most work).
Post link to BootInfo report that it gives you.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by buzzingrobot on 2014-06-11
> **Mike_Walsh said:**
> 
What I describe as the 'splash screen' is the initial Zorin screen, with the white "Z" logo on the pale blue background. The 'Z' logo 'flashes' about 9 or 10 times. The screen then goes blank for about 20-25 seconds; sometimes, the next occurrence is the appearance of a window on this blank screen, top left corner, saying "System Error detected; do you want to send a report? Send/Cancel"

The buttons on this window don't respond, and about 30 seconds later it will open into the Ubuntu Unity desktop. It then asks for a password to send this error report, which I can't enter, because you don't set up a password on the Live Session.!This keeps repeating until I reboot back into the normal O/S.



I don't have the foggiest, but can you tell if the Unity desktop you see is *your* desktop?  

I'd guess you've tried entering your Ubuntu password at that prompt.  It would be very strange indeed if it was accepted because that would indicate it was your Ubuntu install displaying the message, not Zorin.

Have you tried burning a new image on Ubuntu? USB images can sometimes be damaged when they're removed before they're unmounted.  I'd avoid booting off the USB-like image you created on the drive since, perhaps, that confuses the installer about which drive it should look to to find its tools. 

> On other occasions, this window doesn't appear, and the next thing I see IS the Unity desktop, with the 'Install Ubuntu 14.04' icon on the desktop.

That seems to suggest a problem with the Zorin installer.  I've seen occasional similar reports from users of other Ubuntu derivatives. 

I have no idea why these things didn't happen on XP.

---

### Post by Mike_Walsh on 2014-06-23
Hiya, buzzingrobot!

Actually, the whole thing has turned out to be a 'storm in a teacup'...and probably my own fault, to boot (!) [Sorry, couldn't resist that...*Hee,hee...]

When I first installed Ubuntu, I'd just started playing around with the disk admin tools in Windows XP. I have a 500 Gb Seagate external hard drive; just for the hell of it, I created a small partition on it & formatted it to FAT32, so it would behave like a thumbdrive. I installed the Ubuntu .iso onto this with UNetbootin, and ran the Ubuntu Live Session from there, before installing it, also from this partition.

Every time I tried installing Zorin, I ended up getting the Ubuntu Live Session, instead of the Zorin one. I left it alone for a week or so, 'cos I was getting fed up with it. I came back to it the other night, and decided to give it another go! Same thing happened again; Zorin splash screen, then at the point when it should have gone to the Zorin desktop environment, up came Unity again. But as this was happening, out of the corner of my eye, I caught sight of the Seagate's LED merrily flashing away (remember, I was trying to run Zorin off a totally separate thumbdrive, and to be honest, the Seagate shouldn't have 'kicked-in' at ALL); the Seagate is 'Blutack-ed' to the top of my tower, and tucked away under my desk.

I thought to myself, 'That shouldn't be happening', and shut the Live Session down. Incidentally, to answer your question at this point, the Unity desktop that appeared was NOT 'my' desktop; it was the basic install, from the Live Session.

So; I unplugged the Seagate, and tried booting up again from the thumbdrive Zorin was installed on. Guess what? Zorin booted up successfully and ran, like it ought to have done, all along! Somehow, the boot command for the Zorin thumbdrive was activating the partition on the Seagate, and it was overriding the thumbdrive, EVERY time. I don't even PRETEND to understand WHY this was happening, but I now have a dual-boot setup, with Ubuntu AND Zorin.....which is what I was aiming for, all along.

It just goes to show, even after 30-odd years of playing around on these things, you can STILL be surprised when the box of electronic trickery throws you a curveball like that!!!

I'm gonna mark this as SOLVED, because I've sorted my own problem; but it was a pure fluke, at that..!

Mike.

---

