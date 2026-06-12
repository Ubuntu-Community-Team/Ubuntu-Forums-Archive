---
title: "This ocelot is on my last nerve!"
date: 2011-10-15
forum: Recurring Discussions
---

### Post by KnightLord on 2011-10-15
Let me be clear.  I don't really like Unity to begin with.  It is cumbersome, requires too many actions to initiate the simplest actions, hides essential applications and operations, and has other obvious problems that are unintended.  I found a way to live with 11.04, but 11.10 took that option and flushed it.

My external hard drive, that mounted just fine day before yesterday, is now unmountable.
Certain apps I need for my work no longer load and function {at least not under Unity}.
No matter what I open, it opens maximized, requiring extra fidgeting.
Skype no longer gives me the stand alone indication that it is functioning.
Minimized windows reopen maximized.

These are just a few of my least favorite things about this stupid cat.  Now don't get me wrong, sometimes change is good, but I am sitting at a Personal Computer, NOT a smart phone.  

I tried to go back to the gnome interface, that works so well for me, and what I got was the most wretched version possible.  It didn't even have the system icon so I could reboot the computer properly.  

Did I mention I use my computer for my business?  I can't afford to sit here for hours to try to find a way to work around this system so I can do what I need to do.  If, however, you'd like to pay me $100/hour, I might consider it, but otherwise ... well, there we are.

There is one solution I can think of, and if you'd please be so kind as to tell me how to return to version 10, or even 11.04 with the gnome interface, I would be ever so grateful.

Oh, and I need to know how to stop these infernal upgrades so that my graphic human interface remains constant from this day forward, even forevermore.  

Thank you.

---

### Post by mörgæs on 2011-10-15
Xubuntu 11.10 might be worth a try. More and more people are leaving to this one.

Returning to an older release (say, 10.04) is another option. It can only be done with a fresh install.

---

### Post by KnightLord on 2011-10-15
I've thought about a fresh install.  

As I mentioned, this "upgrade" won't mount my external HDD, so I have no place to back up to, so all my files would get wiped out in the Fresh Install.  Reconstructing this past year would only take ... the rest of this year if I did nothing else.  

Like I said, I've thought about it.

Xubuntu?  We shall see.

---

### Post by varunendra on 2011-10-15
> **KnightLord said:**
> Oh, and I need to know how to stop these infernal upgrades so that my graphic human interface remains constant from this day forward, even forevermore.
To prevent newer releases from appearing in the update manager (with the 'Upgrade' button beside it), open Software Sources (either directly or via Update-Manager > Settings) > goto 'Updates' tab, and under 'Release Upgrade' set the value of 'Show new...' to "Never". Close Update Manager and reopen to confirm that the upgrade offer is gone.

By the way, you are never forced to upgrade, it's always optional. And it is always recommended to try out a newer release using a LiveCD or USB first, before installing it natively. This way you can test safely how good it is for your hardware and your preferences. Even if you decide to install afterwards, a clean install is recommended over an 'Upgrade' from within update manager.



**EDIT:**
Saw your above post after posting mine. You can always use 'any' live cd or live usb to boot and backup your files on an external drive. Just try an older one if 'this' one is unable to mount it, although that can be troubleshooted too, but using a working live cd would be easier option.

---

### Post by KnightLord on 2011-10-15
> **varunendra said:**
> By the way, you are never forced to upgrade, it's always optional. And it is always recommended to try out a newer release using a LiveCD or USB first, before installing it natively. This way you can test safely how good it is for your hardware and your preferences. Even if you decide to install afterwards, a clean install is recommended over an 'Upgrade' from within update manager.

Unable to mount:
Ubuntu 10.04 => Not Authorized
HDD              => Not Authorized
Flash Drive    => Not Authorized

Golly Gosh, this just keeps on getting better and better.

Should I remove all flammable objects anytime soon?  
I'm just sayin'.

---

### Post by KnightLord on 2011-10-15
Well, I guess I was wrong about the "last nerve" thing.  This frisky {not the first "F" word I thought of, but it'll suffice} feline has found another one to pounce upon.

Shut Down only logs me out of my account and back to the log-in screen.  

I found this out when I tried to boot from my original Ubuntu installation disk.  I'm like "WTF???"

BTW my cats are now terrified in my presence, and my dogs are looking pretty nervous.  I'm not saying I'm gonna kill something, but they're thinking it pretty loud.

Just a thought here, but did Billy Gates buy Linux or something?
I'm just asking.

---

### Post by effenberg0x0 on 2011-10-15
@knightlord
Are you a member of the **plugdev** group? You can check that by running the following command in a terminal:

```
groups yourloginhere

```The above command will show the groups your login is part of: admin, adm, lp, etc.

If plugdev is not in the list, run:
```
sudo usermod -aG plugdev yourloginhere
```Then you'll have to reboot.

Effenberg

[B][U] EDIT 1: 
a) Automount may be disabled in Nautilus. Run this to make sure its enabled.[/U][/B]
```

gconftool-2 --set /apps/nautilus/preferences/media_automount --type bool true
gconftool-2 --set /apps/nautilus/preferences/media_automount_open --type bool true

```

**b)** You may also use Ubuntu Software Center to install **mountmanager**[B][U]

c) I made you a little script to mount and open the unit on Nautilus "the hard way".

[/U][/B]```
sudo mkdir /media/myusb
```
Plug the USB unit (only one per time)
Paste this on terminal:
```

if [ `sudo fdisk -l  | grep sdb | grep FAT | wc -l` -eq 1 ]; then echo "FAT"; else if [ `sudo fdisk -l  | grep sdb | grep NTFS | wc -l` -eq 1 ]; then echo "NTFS"; else echo "FS Unknown, check manually"; fi; fi;
```
Paste this on terminal:
```

if [ $MYDRIVEFS == "FAT" ]; then sudo mount -t vfat /dev/sdb1 /media/mydrive -o uid=1000,gid=1000,utf8,dmask=027,fmask=137; xdg-open /media/mydrive; else if [ $MYDRIVEFS == "FAT" ]; then sudo mount -t ntfs-3g /dev/sdb1 /media/mydrive; xdg-open /media/mydrive; fi; fi****_
```_[B][U]

EDIT 2: Additional help with Unity[/U]

1. "No matter what I open, it opens maximized, requiring extra fidgeting."[/B]

See if you have CompizConfig-Settings-Manager (ccsm) installed. If not, use the Ubuntu SOftware Center to install it.
Inside of ccsm, go for the Ubuntu Unity Plugin. 
Go for the "experimental" tab.
Change the "automaximize" value to 85.

[B]2. "Skype no longer gives me the stand alone indication that it is functioning."
[/B]
Skype looks for a Notification area, which doesn't exist anymore.
But you can have SKype inside the Messaging (envelope) icon now.
See screenshots and instructions here. Really easy to do.
[http://www.omgubuntu.co.uk/2011/04/how-to-add-and-control-skype-via-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2011/04/how-to-add-and-control-skype-via-the-ubuntu-messaging-menu/)

---

### Post by mikewhatever on 2011-10-15
Ah, rants! They are always so much fun. :p

---

### Post by hylogibbon on 2011-10-15
> **KnightLord said:**
> Just a thought here, but did Billy Gates buy Linux or something?
I'm just asking.
It would appear as if Ubuntu is becoming more and more like Windows with each release. Less stability, aesthetics over function, and inability to customize (while at the same time, Windows is becoming more stable with each release).

If things continue down this road, I may switch to a real linux flavor, or worse, Windows. I was forced to do a hard reset today in 11.10. The first time I've had to do that from linux in the 10 or so years I've been using it. To me, that is a sign to jump ship before it is completely sunk.

---

### Post by SushiR on 2011-10-15
Dear KnightLord,

I really wonder why you replace a running system on a production machine (you said you need the computer for your business) WITHOUT backing up important files first. Or why you didn't try 11.10 on an USB stick (even as persistant install) to see if the Ocelot can fit your needs?

It's not very pro to ignore every possible warning (backup etc.) before upgrading. And it's not very pro either to just start  ranting instead of politely asking for a little help...

---

### Post by KnightLord on 2011-10-15
> **hylogibbon said:**
> It would appear as if Ubuntu is becoming more and more like Windows with each release. Less stability, aesthetics over function, and inability to customize (while at the same time, Windows is becoming more stable with each release).

If things continue down this road, I may switch to a real linux flavor, or worse, Windows. I was forced to do a hard reset today in 11.10. The first time I've had to do that from linux in the 10 or so years I've been using it. To me, that is a sign to jump ship before it is completely sunk.

What really kills me is that I've been bragging on Ubuntu and encouraging every Windoze user I know to check it out.  Honestly, I can't recommend this O/S with all these bugs to anyone, not even Vista users {A decidedly frightening thought in and of itself}.

---

### Post by varunendra on 2011-10-15
> **KnightLord said:**
> Unable to mount:
Ubuntu 10.04 => Not Authorized
HDD              => Not Authorized
Flash Drive    => Not Authorized

Golly Gosh, this just keeps on getting better and better.

Should I remove all flammable objects anytime soon?  
I'm just sayin'.
First off, please be calm and show some patience as we are trying to help. Secondly, sorry but I don't get you. Please explain in detail what you mean by "Not authorized". Is it that you can boot into a live session but can't access the files or the external drive? If so, it is not a common behaviour, and is instead a problem specific to you which can be easily solved if you are willing to cooperate. First approach can be what effenberg0x0 suggested.

Another one can be to just try another live cd that 'can' mount the drive as I suggested earlier. Why are you sticking with 'this' one (11.10??) if it is refusing to work?

If I am misunderstanding something, then maybe you can help us understand everything better by just providing details of the problem(s). With a little bit of patience and cooperation, you can make all your cats and dogs much more comfortable and happy. But if you wish to rather keep the current rate of increasing temperature, then yeah, you should move 'yourself' away from all the inflammable objects! ;)


**PS:**
Bugs ARE parts of newer releases. They always were and will always be. This is the way how Open Source works. If you want stability, stick with older, tested versions - preferably - the latest LTS, which currently is 10.04.

---

### Post by nothingspecial on 2011-10-15
Moved to Recurring

@ KnightLord

You'll get better help if you just simply ask your question in General Help.

---

### Post by KnightLord on 2011-10-15
> **SushiR said:**
> Dear KnightLord,

I really wonder why you replace a running system on a production machine (you said you need the computer for your business) WITHOUT backing up important files first. Or why you didn't try 11.10 on an USB stick (even as persistant install) to see if the Ocelot can fit your needs?

It's not very pro to ignore every possible warning (backup etc.) before upgrading. And it's not very pro either to just start  ranting instead of politely asking for a little help...

Would you like the answer in alphabetic, or numeric order?

I really wonder why an operating system would be released with as many bugs as this one obviously has.  Have you seen how quickly these messages are turning over?  

I am spending these hours trying to fix this problem, hours I really can't afford to spend, and you're criticizing me because I inadvertently clicked a button by accident.  BTW what level of concentration does your job demand, what criticality if you screw it up, and do you always assume yourself to be superior to others?  

Well, the answers here are pretty obvious to the casual observer, so why don't you and Mike Whatever choose to be part of the solution, or continue to be part of the problem elsewhere, please.  Thanks.

---

### Post by madjr on 2011-10-15
@OP / knightlord

i hear you, but i think most of the things you mention are bugs from a **bad upgrade...**

I even had a thread going advising that **upgrades will be pretty bad this cycle**:
[http://ubuntuforums.org/showthread.php?t=1852654](http://ubuntuforums.org/showthread.php?t=1852654)

now, can you try on a usb stick and see if you have all the same issues?

thanks

---

### Post by nothingspecial on 2011-10-15
Let's keep this thread civil please.

---

### Post by KnightLord on 2011-10-15
> **varunendra said:**
> First off, please be calm and show some patience as we are trying to help.

I do appreciate your attempt to help, however others seem intent on doing the opposite.

> **varunendra said:**
>  Secondly, sorry but I don't get you. Please explain in detail what you mean by "Not authorized". Is it that you can boot into a live session but can't access the files or the external drive? If so, it is not a common behaviour, and is instead a problem specific to you which can be easily solved if you are willing to cooperate. First approach can be what effenberg0x0 suggested.

All it says is, "Unable to Mount" whatever device
                                  Not Authorized

So it isn't me you're not getting, it is Ubuntu that neither one of us is getting.

Also this thing won't shut down, short of a simulated power failure.  I'm kinda saving that for a last resort, as this thing is buggy enough without doing something radical.


> **varunendra said:**
> Another one can be to just try another live cd that 'can' mount the drive as I suggested earlier. Why are you sticking with 'this' one (11.10??) if it is refusing to work?

I guess you're really not getting me after all.  Is it really necessary for me to go into more detail than I already have, and what information would that provide toward the resolution of this problem?

> **varunendra said:**
> If I am misunderstanding something, then maybe you can help us understand everything better by just providing details of the problem(s). With a little bit of patience and cooperation, you can make all your cats and dogs much more comfortable and happy. But if you wish to rather keep the current rate of increasing temperature, then yeah, you should move 'yourself' away from all the inflammable objects! ;)

My jest indicated a concern as to whether my computer would soon explode due to the ongoing discovery of new and different bugs in this version.  As for my patience level {all kidding aside} if you were to need the services I provide, you would find yourself astonished at just how patient I actually am.  I stay that way by making light of the situation {that is I poke fun at it}.  If this is confusing for you, as it seems to be for others, then I apologize for assuming a sense of humor, and shall refrain in the future.  Normally I don't have a problem with people "getting me" on this, but I can adapt.

> **varunendra said:**
> **PS:**
Bugs ARE parts of newer releases. They always were and will always be. This is the way how Open Source works. If you want stability, stick with older, tested versions - preferably - the latest LTS, which currently is 10.04.

Yes, the very CD I have in the drive that can't be mounted because it isn't authorized.  BTW Yes, I am a member of the plugdev group, so that must not be the problem.

---

### Post by kurt18947 on 2011-10-15
> **madjr said:**
> @OP / knightlord

i hear you, but i think most of the things you mention are bugs from a **bad upgrade...**

I even had a thread going advising that **upgrades will be pretty bad this cycle**:
[http://ubuntuforums.org/showthread.php?t=1852654](http://ubuntuforums.org/showthread.php?t=1852654)

now, can you try on a usb stick and see if you have all the same issues?

thanks

I think you're right.  There have been a LOT of changes since 10.xx.  I would be more surprised if there weren't problems with upgrades than if there were problems. A clean install after backing up important files is certainly the way to go - or install alongside your existing setup so you can go back if necessary.

  Except for problems with a Brother scanner documented elsewhere,  fresh installs of 11.10 have gone very well for me. I agree that gnome 3 (shell) and unity don't yet have the tweakability of gnome 2. I expect that will change in short order.

---

### Post by KnightLord on 2011-10-15
> **madjr said:**
> @OP / knightlord

i hear you, but i think most of the things you mention are bugs from a **bad upgrade...**

I even had a thread going advising that **upgrades will be pretty bad this cycle**:
[http://ubuntuforums.org/showthread.php?t=1852654](http://ubuntuforums.org/showthread.php?t=1852654)

now, can you try on a usb stick and see if you have all the same issues?

thanks

CD, Flash drive, External HDD, all unmountable, all "Not Authorized".

Sadly, I have no time to keep read up on Ubuntu upgrades.  I run the office part of my business from this computer, and what time field operations allow me is limited at best.  

Hope this helps you to help me with this problem.  I can try to redo the upgrade, and hopefully it'll work, but if not I'm going to have to do something a bit more tech-drastic.

Thank you

---

### Post by kaldor on 2011-10-15
You're using a 6-month release in a production environment. I wouldn't do that. 

I recommend that you go from LTS to LTS when you're in these situations. Unity is still in its "growth phase" and is not quite ready yet. Use Ubuntu 10.04 LTS and wait for Ubuntu 12.04 LTS before upgrading again. 

The normal releases introduce new ideas, features, and other unstable stuff. These are the releases where problems are understandable. If you have these issues on an LTS, *then* you should complain since it's supposed to be stable.

---

### Post by Ric_NYC on 2011-10-15
> **KnightLord said:**
> Let me be clear.  I don't really like Unity to begin with.  It is cumbersome, **requires too many actions to initiate the simplest actions, hides essential applications and operations**, and has other obvious problems that are unintended.  I found a way to live with 11.04, but 11.10 took that option and flushed it.




Perfect! Case closed!

---

### Post by KnightLord on 2011-10-15
> **kurt18947 said:**
> I think you're right.  There have been a LOT of changes since 10.xx.  I would be more surprised if there weren't problems with upgrades than if there were problems. A clean install after backing up important files is certainly the way to go - or install alongside your existing setup so you can go back if necessary.

  Except for problems with a Brother scanner documented elsewhere,  fresh installs of 11.10 have gone very well for me. I agree that gnome 3 (shell) and unity don't yet have the tweakability of gnome 2. I expect that will change in short order.

You are indeed fortunate.  I think I've gotten a few of the bugs that were intended for you.  You can have them back now, if you want.  :-)  No, seriously, I've got 'em to spare, and I promise I won't miss them at all.  LOL

Seriously, I'm glad you've come through relatively unscathed.  Hope it stays that way for you.  :-)

---

### Post by nothingspecial on 2011-10-15
Closed for cool down.

---

