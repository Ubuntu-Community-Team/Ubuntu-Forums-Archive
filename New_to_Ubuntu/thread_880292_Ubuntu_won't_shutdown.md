---
title: "Ubuntu won't shutdown"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Seaniesean on 2008-08-04
Hello, I know this problem is addressed elsewhere, but none of the solutions posted work for me.  I am actually having serious problems with my computer unrelated to ubuntu, and i think this may be another consequence of this.  Basically, ubuntu won't shutdown properly, though it will restart etc.  Anyway, is there any way of finding any logs of what exactly ubuntu tries to do when it shuts down, or anything like that?  I'm not really interested in solving the shutdown problem, because i know its hardware related, but i don't know exactly what, and i thought this might help me diagnose if i could find some error logs.  Any suggestions?

By the way, sorry if i don't reply to any suggestions, it probably means my computer has bitten the dust.

---

### Post by phidia on 2008-08-04
Most all system logs are in /var/log You could try /var/log/messages; dmesg; syslog and there are plenty of other logfiles there too.

---

### Post by jamesrfla on 2008-08-04
I might be having the same problem that you are having. Take a look at the first post of this thread and look at the attached pictures. If you have the same errors let me know. [http://ubuntuforums.org/showthread.php?t=878805](http://ubuntuforums.org/showthread.php?t=878805)

---

### Post by Seaniesean on 2008-08-05
Cheers phidia, i'll take a look.  I think i would not be having the same problems as jamesrfla, because it's more of a graphics card/bios/cmos/motherboard/stupid computer/not got a clue what's wrong type issue.  My computer starts like, once out of every 700 tries.  It is not an ubuntu problem, though that is the only os i have at the moment after a zero fill of my hard drives.  My bios rarely detects all my devices (that is, rarely after the even rarer circumstance of it actually making it past POST.)  I don't think its a power supply issue, or a graphics card issue, or a hard drive issue, and it's probably not a RAM issue, but it might be.  

While I'm here in a forum with people who are both friendly and good with computers, what would make a computer rarely boot, and when it does, fail to detect devices properly?  It actually runs fine when it does boot, but without detecting all devices.  It is in no way unstable (on the surface, anyway).  I tried replacing the power supply, which didn't help, and also removing all devices apart from those necessary for boot, which also didn't work.  My computer's kind of old (about 4 years).  Would a new CMOS battery help?  Could a failing battery be responsible for this sort of problem?

Any ideas at all are welcome, even rubbish ones!

edit- actually jamesrfla, i do remember something about dbus and dhcp failure errors when i try to shutdown from terminal.  But like i say, it's more of an issue with the hardware than with ubuntu i think.

edit 2-"spilled the beans"?!  have i been promoted?

---

### Post by sayakb on 2008-08-05
At a terminal, try:
```
sudo init 0
```
and see if it shuts down or not..

---

### Post by Seaniesean on 2008-08-05
No no no, I don't want it to shutdown, i just been sat here for 8 hours trying to get it to start up!!!  I want to try and diagnose hardware problems that are unrelated to ubuntu!  I just noticed late last night that ubuntu didn't shutdown when i told it to, and i thought that if there were some logs or something this would help me find out what's up with my computer.

I'll try it later on though, cheers anyway.

---

### Post by billgoldberg on 2008-08-05
I know you don't want to shut it down, but does the command

```
sudo shutdown
```

work?

It should.

---

### Post by Seaniesean on 2008-08-05
sudo shutdown now is what i tried last night.  Didn't work.  Ubuntu shutdown progress bar remains on screen.  And i most certainly am not going to try it now because it is a miracle that my comp is working and if i shut it down now it'll be, like 2 days before it starts again.

What are the symptoms of a failing CMOS battery?

Failure to boot?  Failure to detect devices?

Please Help!

---

### Post by billgoldberg on 2008-08-05
> **Seaniesean said:**
> sudo shutdown now is what i tried last night.  Didn't work.  Ubuntu shutdown progress bar remains on screen.  And i most certainly am not going to try it now because it is a miracle that my comp is working and if i shut it down now it'll be, like 2 days before it starts again.

What are the symptoms of a failing CMOS battery?

Failure to boot?  Failure to detect devices?

Please Help!

I can't help you with hardware stuff, not by best thing.

--

Can you still run a live cd?

--

Also, I removed the login-manager so I can see what goes wrong during start up and shutdown. 

You might want to try doing that.

---

### Post by Seaniesean on 2008-08-05
I'm running ubuntu off my first hard drive right now.  Going great actually.  Like i say, it's only on start up or shut down i have problems.

How do i remove the login manager please?

---

### Post by fiddledd on 2008-08-05
Have you removed the hard drive and tried a Live CD? At least that would eliminate the Hard Drive as a cause. Also try the same with Floppy Drive disconnected.

---

### Post by billgoldberg on 2008-08-05
> **Seaniesean said:**
> I'm running ubuntu off my first hard drive right now.  Going great actually.  Like i say, it's only on start up or shut down i have problems.

How do i remove the login manager please?

Removing the package gdm would do it.

sudo apt-get remove gdm

You'll have a command line login when you boot the pc.

Just type your username and password and start gnome by using the command

```
startx
```

--

Should you want the graphical login manager back, I guess


```
sudo apt-get install gdm 
```

should do.

I don't know if it will be used by default.

If it isn't, try the command:

```
sudo dpkg-reconfigure gdm
```

should do it.

---

### Post by Seaniesean on 2008-08-05
Fiddledd-I removed everything except the graphics card, one stick of RAM, power supply, and motherboard if memory serves me correctly and still no satori, so its not the hard drive.  Plus, i checked both hard drives and they're ok.

cheers billgoldberg, I'll try it later.

Anyone know anything about CMOS?

---

### Post by jamesrfla on 2008-08-05
CMOS is where the BOIS settings are stored at. If you want to set the BOIS back to the defaults take the CMOS battery out for about a min then put it back in the way you took it out. The CMOS looks like a watch battery and may need to be replaced.

---

### Post by jerome1232 on 2008-08-05
Have you ran memtest just to see if memory spits out errors? That's the first thing I would've done, takes like 30 minutes. A failing cmos battery will just make it forget settings after the computer has been disconected from the wall. Usually power supplies keep enough current running through the mobo so that cmos will remember it's config without the use of the battery. now:

#############################
# THIS COULD KILL YOUR BIOS #
#############################

######################
# Second warning lol #
######################

So be warned, although I have done it successfully before if it fails, it wipes all info from bios which is very bad, sometimes (usually?) you can't even re-flash it.
You might want to check your mobo's website to see if they have a firmware update for you bios and flash it, **this carries risk**
This would be the absolute LAST thing I would try.

edit:Is this not monospaced? my warning doesn't look right

---

### Post by Seaniesean on 2008-08-05
yeah, i ran memtest, no errors came up.  Now you mention it, though, my friend ran some program on it and it got IRQ failed or COM1 failed or something.  I don't really know what this means though.

There hasn't been an update for my bios for about 3 years i don't think (ASUS motherboard, p5gd1).  And i flashed it recently anyway.  Nice try though!

Are you sure CMOS only remembers bios settings etc?  Doesn't it have quite a complex relationship with the ram and stuff on boot?  Also i just read some kid had the same problems i had, and some possible greybeards said it might be the battery failing.

---

### Post by jerome1232 on 2008-08-05
That is my understanding of things, cmos is just the setup/config utility for the bios, I am no expert though so I could be wrong.

> **jamesrfla said:**
> CMOS is where the BOIS settings are stored at. If you want to set the BOIS back to the defaults take the CMOS battery out for about a min then put it back in the way you took it out. The CMOS looks like a watch battery and may need to be replaced.

Did you try reseting cmos as jamesrfla suggested? Usually there's also a jumper on the mobo you can use to reset the cmos. If you are getting IRQ problems I know there is a spot where you can configure IRQ's for devices in the bios and if that is screwed up, well there ya go. If you can find the section to configure IRQ's maybe you could manually assign them to make sure nothing is conflicting.

IRQ's are a special numbers devices use to get the cpu's attention basically.

---

### Post by Seaniesean on 2008-08-05
Hmm.  I reset cmos jumper thing yesterday, to no avail.  However, i just replaced CMOS battery with brand new indonesian battery, went to sleep for 15 minutes (me, and the computer) and whadyaknow, it actually detected all my devices for the first time in two days and started first time.

I am no optimist, and certainly no technician, but i bet this isn't a coincidence.  

I have no idea how to manually configure IRQs, but i reckon wikipedia is my next stop, eh?  Unless anyone here is still awake and wants to give me a head start...

I am very reluctant to turn my computer off.  How long do you think i can leave it on?  Hey, it's got to be better than holding down the power button for 8 hours until it starts, right?

---

### Post by Jordanwb on 2008-08-05
> **Seaniesean said:**
> My bios rarely detects all my devices (that is, rarely after the even rarer circumstance of it actually making it past POST.)  I don't think its a power supply issue, or a graphics card issue, or a hard drive issue, and it's probably not a RAM issue, but it might be.

Me thinks your motherboard is toast. Considering that POST (Power On Self Test) fails, something is really wrong (Captain Obvious away!). 

> **Seaniesean said:**
> edit- actually jamesrfla, i do remember something about dbus and dhcp failure errors when i try to shutdown from terminal.  But like i say, it's more of an issue with the hardware than with ubuntu i think.

Dhcp is related to hardware but what it does is get an IP from your Router or ISP. Dhcp is more or less software.

> **Seaniesean said:**
> edit 2-"spilled the beans"?!  have i been promoted?

Not exactly. When you make X number of posts, your title changes.

> **jerome1232 said:**
> A failing cmos battery will just make it forget settings after the computer has been disconected from the wall. Usually power supplies keep enough current running through the mobo so that cmos will remember it's config without the use of the battery. now:

#############################
# THIS COULD KILL YOUR BIOS #
#############################

######################
# Second warning lol #
######################

So be warned, although I have done it successfully before if it fails, it wipes all info from bios which is very bad, sometimes (usually?) you can't even re-flash it.
You might want to check your mobo's website to see if they have a firmware update for you bios and flash it, **this carries risk**
This would be the absolute LAST thing I would try.

edit:Is this not monospaced? my warning doesn't look right

What?! The bios is stored in EEPROM: Electrically Erasable Programable Read Only Memory. It's a form of NVRAM(flash drives are another example), power outages won't affect it.

---

### Post by Seaniesean on 2008-08-06
Umm...if my motherboard is screwed, how come on the rare occasions it does make it past post (this being one of them) and detect all devices (ditto) it can be left on for days, with no errors at all, and i can play games, etc?  Also, my motherboard passes all tests i can throw at it when i am able to boot properly.  

I mean, how many ways are there for a motherboard to be messed up?  A loose wire somewhere?  A wobbly ram socket? A dubious battery connection?  I think (i don't know)  that there are many reasons why a computer might fail POST, no?  

It just seems funny to me that the only time stuff goes wrong is bootup or shutdown.  Surely if my motherboard was that bad, it would fail at least once when an OS is loaded?  And yet, it does not.

---

### Post by jerome1232 on 2008-08-06
> **Jordanwb said:**
> What?! The bios is stored in EEPROM: Electrically Erasable Programable Read Only Memory. It's a form of NVRAM(flash drives are another example), power outages won't affect it.

...when did I say a power outage would affect bios?

In every computer there is a cmos battery, take that bad boy out, unplug your computer from the wall, and just to make sure disconnect all power connectors from your power supply (some will keep a trickle of power for days), now go have lunch.

When you come back hook everything back up and boot the machine, your bios will have all of it's settings reverted back to factory default settings. This is what I am talking about.

Your motherboard requires a constant supply of power to keep the clock at the correct time, and for the bios to retain setting changes (the ones you make by pressing f2 or del or whatever button at startup)

@OP, I have a spare motherboard that does weird things too, every other boot or so it won't post, other than that it's perfectly stable. I've swaped everything out, I've even exchanged it's bios chip with another mobo of the exact same type (that didn't have the problem) and the problem persisted so I would say yes it could be the motherboard and it won't necessarily cause the computer to be unstable.

---

### Post by Seaniesean on 2008-08-06
How unusual for a linux forum to degenerate into a discussion of technical definitions....... :-\" 

Cheers for the help!

---

### Post by jerome1232 on 2008-08-06
I hope that fixed it for you, if that battery was the cause I'm going to have to hit the internet and do some reading up on bios/cmos stuff so I know better :) Let us know if that did fix it though I really want to know if a bad battery can 'cause that kind of thing.

---

### Post by Seaniesean on 2008-08-06
I don't know if it fixed it yet, i'm scared to switch it off!

To be honest, i doubt it, for the simple reason that a battery costs £2, and nothing is ever that simple for me.  Sorry if this sounds pitiful, but it is also sadly accurate.

I did see someone with the same problem though, and some guy said it might be battery related.  I'll see if i can get you one of them hyperlink things...

Look, here's one: [http://forums.pcper.com/showthread.php?t=453090](http://forums.pcper.com/showthread.php?t=453090)

You can find all sorts of problems like mine if you google "cmos failure symptoms" or similar.

---

### Post by Jordanwb on 2008-08-06
Replacing the battery is incredibly easy. only beaten by installing RAM. Just make sure you put the battery right side up.

---

### Post by jerome1232 on 2008-08-06
You might be interested in this link here [http://www.computerhope.com/issues/ch000037.htm]("http://www.computerhope.com/issues/ch000037.htm") it seems to be your problem and the troubleshooting steps for it; has a bit of info regarding irq's as well. (The cmos battery can cause cmos to throw out errors, now I know :))

---

### Post by Seaniesean on 2008-08-10
Boohoo!  Didn't work!

Worse, the other day I turned it on, the fans started, then i went for a pee, came back, and now nothing happens at all!  Only the light on the mobo comes on now.  Maybe i'll try computerhope, sounds like a nice place, but i am doubtful that there is any hope left for my computer.

RIP my computer...my best friend and worst enemy for the last four years. 

:sad:

---

### Post by Jordanwb on 2008-08-10
What would happen if the oscillator on the mobo was screwed up? The processor and other equipment couldn't keep time.

---

### Post by grungedoobie on 2008-08-10
Over the years, I've picked up a number of tricks that have helped me with computers that have "sticky boot" problems.  Of course, you are correct is saying that there are a million and one different reasons why a boot sequence can fail.  On to the tricks though.  

#1 Pull all the hardware connections that you can find, check the connectors, then reinstall.  Sometimes a tiny film of oxide can build up in just the right place, and the operator will lose all of his hair trying to fix it.  

#2 Of course the cmos battery will affect the boot sequence, however, once the power is turned on, your larger power source now supplies the power for cmos.  This means that once the computer is turned on and the settings redone, the cmos will hold the settings until next boot.  This being said, there is also the chance that the battery may be slightly shorted internally causing the cmos to reset while powered up.  I've not yet seen this as I have always changed the battery before they got that bad.  

#3 Since were talking about cmos, although linux is not dictated by cmos, the boot proceedure cannot perform if cmos doesn't do it's thing.  Make sure the bios settings are correctly configured to your hadware.  On another note, turn OFF all hardware acceleration as these setting do nothing more than confuse issues.  I've had several computers fail boot because the "Super Fast Bootup" option was turned on in bios ( I've seen this problem with both the linux and ms platforms, so there. )  Once linux has made it past the grub-loader, linux will make the best choices for the harware on your computer as far as speed and the like regardless of what entries are made to bios (well, most of the time).

#4 And then there is always the possibility that a power conduit on the motherboard has sprung a leak causing an intermittent sputtering at one of your clocks causing the rest of the system to get indigestion.  (Sorry 'bout that one, I had mexican food last night.)  But if this was the case, I don't know that even linux would recover without giving you tons of error reports.

#5 (Actually, this one should be further up on the list, but here it goes) Try a different install.  I've come across this only a couple of times, but I have had an ISO go bad somewhere between the internet and putting it on the computer.  A driver somewhere would hang, the grub would be sticky and a bunch of other weird stuff will happen if this is the problem.

If you have already tried these things, then please accept my sincerest apologies for having wasted time.  My only intentions are that you be able to live with your computer in harmony.  (wow, does that sound disgusting or what..  blech)

The Grunge

P.S.  Another thing I like to have on hand is a boot disk with some general utilities such as disk and hardware detection that I know will work with the system.  They are not always needed but are very handy to have when issues arise.  **WARNING**  If you use a ms boot disk, do not force a hard drive check to a linux installed drive.  Ms loves any excuse it can get to scramble any other platform that is not of its own.

---

### Post by Seaniesean on 2008-08-11
Thanks everyone.  Sniffle.  (wipes tears out of eyes)

From the last bit of advice, it seems my only options involve soldering irons and replacing parts of the motherboard (i just got a mental picture of the results of me trying anything like that, looks a bit like a metal cube with some wires sticking out of it).

The other non hardware options won't work at all because all my computer does now is the mobo light turns on and when i press the power button i get a little click.  Like a death watch beetle.  A very old one.

This has been interesting though, because i never really looked inside my computer before now.  At least i know a bit more about hardware and wires and stuff now.

---

### Post by Jordanwb on 2008-08-11
> **Seaniesean said:**
> From the last bit of advice, it seems my only options involve soldering irons and replacing parts of the motherboard (i just got a mental picture of the results of me trying anything like that, looks a bit like a metal cube with some wires sticking out of it).

Um I would recommend against that. Mobos are what's called Printed Circuit Boards. There's not a whole lot of stuff that you can resolder on and even then you risk screwing it up even more.

---

### Post by grungedoobie on 2008-08-11
It can be hard to watch one go.  I've had three of them and worked on a number of others.  Sometimes the problems are easy to find and make horrible smells.  Sometimes pieces of components bounce around inside the box.  Others, it's slow and you stay awake for days trying to nurse the thing back.

Ugh, I'm not helping am I.

Sorry to hear about your computer.  Check out Ebay, they got lots of stuff there.  Then, Tiger Direct.  A visit to Either is a geeks idea of a dream vacation.  YEah BAby!!

Luck to you.

---

