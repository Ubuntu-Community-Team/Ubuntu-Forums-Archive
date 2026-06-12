---
title: "Ubuntu boot disc woes"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by mquest724 on 2008-07-25
So I downloaded the Ubuntu iso file and burnt it to a disc.  This failed to load properly.  So I downloaded it to another computer and thought that maybe it was just the burn program I had messing it up. This disc also did no load.  So I downloaded an alternate version and this too gave me the blues.  I've done a lot of the things I have seen in the forums like changing the bios to read the cd drive upon booting and whatnot and my mean machine keeps bringing me down.  What is a little boy to do who just wants his Ubuntu?  The computer I'm using isn't horrifically old, I mean it came with XP on it (one of the main reasons why I want Ubuntu because I'm so sick of the hassle XP has been).  Any eggs of knowledge that can be cracked on me would be greatly appreciated.  Thank you Linux-iacs.[LIST=1]
[/LIST]

---

### Post by adult swim on 2008-07-25
are you burning the iso as a data disc or burning it as an image?
you must burn it as an image for it to be bootable

---

### Post by Dylock on 2008-07-25
I had this problem before, try burning at a really slow speed (4x) maybe. I really don't know why this matters but it seems to work. 

It would be nice if there was a md5 of the iso so we could check if we have everything when we download it. *shrug*

---

### Post by mquest724 on 2008-07-25
Alright, so I've done just about everything I can think of.  I'm redownloading the .iso file and if this one doesn't work, I have the feeling that maybe Ubuntu isn't for me (even though I really want to try it out).  Being horribly impatient, I don't know if I'd be able to wait for a cd to come in the mail.  I am burning it as an image file and it's booting to a point and then giving me error messages or just a prompt where it stops loading and reading the disc all together.  Maybe that's what it's supposed to do and I just can't figure it out.  Who knows...

---

### Post by dstew on 2008-07-25
Do you get a menu when you boot the CD? What is the error message?

If you get a menu, try the option to check the CD for defects (integrity check).

---

### Post by candtalan on 2008-07-25
> **mquest724 said:**
> I am burning it as an image file and it's booting to a point and then giving me error messages or just a prompt where it stops loading and reading the disc all together. 

Burning an iso image has to be byte exact. I believe there are not the same error corrections which are in place as when you make your own CD of say data or audo or etc etc. If your media or yuor burner are not well good, you may get burn errors, but not know it. The slower you speed chosen fo rburning then the better your chances, but no guarantees I am sorry to say. Usually my media and system are good at half speed (x24) but I recently had a box of 100 blank CDs which gave a *lot* of trouble. Nearly half of them were no good. A bad batch I am told.

If you wish you can check the accuracy of the image download using the md5sum published in the download mirrors. After this, after burning the CD, you can check for the same md5sum as read from the burned CD image. Or easier, you can boot the CD and choose the boot option 'check this CD for errors'. There should be zero errors.

> 
 Maybe that's what it's supposed to do

No it is not!

> 
 and I just can't figure it out.  Who knows...

It is not you. You may not be used to using iso images - in windows world they are just not given away! There are a number of simple things which may be giving trouble which you can soon find out about.

Once you start using ubuntu you will not look back.


Ther is an unusual situation I have on one of my older machines: As purchased, it works ok with live CDs, check etc all ok. However, with a second CD drive and a second hard drive in place also, I found I get check sum errors - sometimes. I conclude that in this particular machine, the power supply is marginally (cheap)  weak and the CD read is not good enough for this purpose. The problem is repeatable, but I have not yet bothered to change to a bigger PSU, probably not worth it now I know the problem.

Good luck.

---

### Post by mquest724 on 2008-07-25
I am out of options. I've tried several programs to butn the iso file with and every time the same thing happens upon booting.  I am officially hopeless. I have requested the cd and I am praying that this will work.  I've tried burning the iso file from my mac, from windows with a slew of programs, all different speeds and there is nothing left for me to do.  I checked the file with the md5sum and it was fine. I am defeated.  Ubuntu 1, mquest724 0.  Maybe in a different life Ubuntu and I can co-exist, but not today. It is a dark day for me. All I want to do is just try it out and grow to love it...

---

### Post by mquest724 on 2008-07-25
To shed a little more light on my hopelessness with the prayer that someone will recognize this problem and help me out. When I try to boot in Ubuntu, it goes through the process a little bit, then a fully black screen shows up and says to me, it says "To run a command as administrator (user "root) use "sudo <command>". See "man sudo_root" for details."
It says this when I try running the program without installing, when I try installing and I even installed it through windows and then took the cd out and was presented with the option upon turning my computer on to boot in ubuntu or windows, chose ubuntu and the same thing showed up.  Maybe I'm just slow and I have to type in some sort of code or something to make Ubuntu run, but I thought it should just kind of come up.  Let me know what you guys think

---

### Post by candtalan on 2008-07-26
sorry to hear you are having so much trouble with this.

I am guessing: a possible problem could be the recognition of the video card chip, and the incorrect driver is being automatically chosen.

this is a killer because you get nothing on the screen, and as a beginner - well - I dont have to tell you.

In the initial boot menu from the CD, there are a number of options, some obvious, and some not so obvious. Any option for graphics will be useful to try. Using versiion 8.04.1 desktop (live cd), you will see
'Press F4 to select alternative start-up and installation modes'

Use F4 to select
'safe graphics mode'

and then continue.

If that is not any good, then, again from the initial boot menu. use F1 then F6 (within the F1 menu).

From the intial boot menu, again, the use of F6 by itself may be useful for options, but my guess is that it is a video card recognition problem.

Advanced:
It is possible to examine, and even change, the recognised information, using the black screen and root sign on, by use of an in built text editor, and looking at the file /etc/X11/xorg.conf

(Do you have any Linux user groups in your area I wonder?)

best wishes

---

### Post by mquest724 on 2008-07-28
In the third installment of Ubuntu vs. My Computer, we have an update in exactly what in the world of all that is holy is going on.  Still at a stalled point in the process of getting Ubuntu to work on this blasted machine, I have now tried getting my computer into safe mode, and I can do that, but it still fails to boot Ubuntu all the way.  I am going to type word for word what I get at that dangerous and deadly black screen that I can see when I get the prompt at the bottom and maybe, just maybe, we can get something to work:

File "/usr/bin/ubiquity-dm", line 237 in <module>
    ret=dm.run (*sys.argv[3:1]
File "/usr/bin/ubiquity-dm", line 146 in run
    (root_width, root_height)=root.get_size()
AttributeError: 'NoneType' object has no attribute 'get_size'

*Side note:Under this message there is something all the way over to the right that says [fail] in red lettering which is pretty ominous...
This is where the action picks back up underneath this

*Started Deferred execution scheduler atd
*Stating Periodic command scheduler crond
*Checking battery state
*Running local boot scripts (etc/rc.local)

*Side Note: Next to all of these is a [pass] or [ok] or something that makes me feel good inside, I don't remember exactly what it is, but it feels like Christmas morning...

Then it has some general Linux info like the whole warranty thing and what have you then gives me the prompt down at the bottom again.

If you have anything for this set of circumstances, feel free to let me know.  If it would help to know what my graphics card is, I think it is a VIA/SG3 UniChrome Graphics.
I THINK that's what it is, I went into the device manager and I'm pretty sure that's the graphics card.

Thanks again for everyone helping out and pitching in, let's hope we can get through this together.

Also I live in Los Angeles, but I don't know how I would find these user groups.  If you could help me out with that, it would also be appreciated.

---

### Post by candtalan on 2008-07-29
When you use a ubuntu Live CD version 8.04.1 and boot from it, and you will see at the lower part of the screen
'Press F4 to select alternative start-up and installation modes'
Use F4 to select
'safe graphics mode'
and then continue. 

This live CD experiment should help to indicate if your video or display information can be used easily some way.

---

### Post by mquest724 on 2008-07-29
I am refusing to give up, but I just wish I could see the river over the horizon, for my horses are thirsty...

I have tried the booting in safe graphics mode, and I have gotten nothing more than the Ubuntu prompt again with the money symbol and whatnot, basically the same screen as before.  
I then tried booting after going into F1 and hitting F6 and seeing what I could do differently, then after hitting F6 on the main screen I typed in "vga=771" assuming that that's the way the help menu wanted me to do it.  I got a very disturbing error that read:
bogl_init failed: EXPLODE
Screen init failed

And I am not joking, "EXPLODE" was really in all caps making me very nervous and also ducking under my desk in a fetal position.

I then tried booting in safe graphics mode with the parameter of "vga=771" and wouldn't you know I received that pesky "EXPLODE" message again...

It's official, Ubuntu is making me want to set myself on fire.  I am going to try some of the other alternate boot options with the F6 command at the bottom, but who knows if it will work... who knows...

If it does, I shall post immediately.
If you don't hear from me within 6 hours, send for help.
Godspeed.

---

### Post by adobrakic on 2008-07-29
I don't know if this has been pointed out already, but download the .iso (which sounds like already have), download PowerISO and burn the .iso to a CD at the slowest speed possible.

---

### Post by mquest724 on 2008-07-29
The disk I burned worked fine. Thank you for trying though.  I did the disk check thing before booting and it found no errors and I did the whole dm5sum or whatever and it checked out alright too.  My new fun thing is trying all the possible boot parameters and all of those are bringing me right back to the Ubuntu prompt with the $ thing.  When the screen flashes and everything and I can catch a couple words I keep seeing "Screen Failed" but it goes away so quick.  I don't know what to do at this point. Once again, not giving up, but it's bumming me out more and more.  This once bright eyed and bushy tailed prospective Ubuntu-er is now feeling more and more disenfranchised and jaded.  
Ubuntu gods, why are you frowning upon me so?

---

### Post by JoneYee on 2008-07-29
> **mquest724 said:**
>   My new fun thing is trying all the possible boot parameters and all of those are bringing me right back to the Ubuntu prompt with the $ thing.  When the screen flashes and everything and I can catch a couple words I keep seeing "Screen Failed" but it goes away so quick.

I don't think it's the disk.  If that message is accurate, it would seem to be a video hw/driver problem.

---

