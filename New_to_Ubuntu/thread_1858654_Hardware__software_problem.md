---
title: "Hardware / software problem?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by JayzeeT on 2011-10-12
I've been using Ubuntu on and off for a while, but still consider myself a newbie, that's for sure. 

My Dell Inspiron 6400 laptop seems to be struggling, I think the problem started at the same time I upgraded to 11.04, but can't say that for sure. 

Basically it seems that the machine can't keep up with my typing, I have to force myself to type slow otherwise letters get missed out and so on. The mouse (trackpad) also seems a bit sluggish and 'jumpy' too, but it's been like this for so long now, I've kinda got used to it. 

Thought that maybe updating my BIOS might help (current version A04), but got totally confused by various tutorials on how to do it and got scared off in the end...

Computer feels quite hot at times, but don't think it's an overheating thing, the typing is slow right from boot up. 

Other than the typing and the trackpad, everything else seems to be working ok, I can watch movies and the like. 

'Slow keys' in prefs > keyboard is unchecked!

Really not sure what to do next? Bit annoying, as I'm a writer and can't go at my normal pace! 

Any help much appreciated.

---

### Post by sanderd17 on 2011-10-12
Could you open the system monitor (or use the command "top" in your terminal) to see if there is any process using a lot of CPU.

If there is nothing wrong with your CPU usage, it looks like the governor of your threads has some wrong options set. Correcting this would require to compile a custom kernel, or at least install a new one.

---

### Post by JayzeeT on 2011-10-12
The CPU doesn't seem that hard pressed, the typing is slow if I just boot up and open up gedit and nothing else.

--
top - 23:30:22 up  1:48,  2 users,  load average: 0.75, 1.08, 0.80
Tasks: 137 total,   1 running, 135 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.3%us,  7.2%sy,  0.0%ni, 83.8%id,  0.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2051172k total,  1663340k used,   387832k free,   118804k buffers
Swap:  2377724k total,        0k used,  2377724k free,   981572k cached
--

'governor of your threads'??? You've lost me there!

---

### Post by Lisiano on 2011-10-12
A governor is something that tells threads (Processes/applications) when they can run and when they must wait and let other applications run.

Just to rule out hardware, do you have any USB Keyboard you could connect to the laptop? For some reason I'm thinking it's more like faulty hardware than software. Also do you have a LiveCD (The disk you installed Ubuntu with) lying around? If yes, try putting it into the laptop and boot of it ("Try Ubuntu") and see if the problem is there too.

---

### Post by The Sorrow on 2011-10-12
Could be a lack or RAM or a hardware issue... Was it slow when you first installed Ubuntu? If not when did this start and did anything else happen to the system during that timeframe?

---

### Post by wolfen69 on 2011-10-12
> **JayzeeT said:**
> I think the problem started at the same time I upgraded to 11.04


Upgrades have been known to go bad and bork things. Try a live cd and see if the problem persists.

---

### Post by JayzeeT on 2011-10-13
Nice idea about trying a USB keyboard, don't have one but will try and borrow one. 

Don't think it's 'not enough RAM' or anything like that, as I was running ubuntu fine on this laptop before and nothing has changed, hardware wise. 

Like I said, I think it started to go wrong during the update to 11.04, the only reason I'm not totally sure is that I had some problems with the update. 

Will try the Live CD idea, haven't got the original that I used to install the system, but guessing I could just burn a new one?

Thanks for the help!

---

### Post by JayzeeT on 2011-10-13
Ok, just booted from LiveCD and still got the same problem, so I'm guessing that points to hardware issues?!

My new test is to use a single finger and type 1 2 3 4 5 6 7 8 9 0 and often it misses a number or two. Also I've got a delete test, bang delete 3 times quite fast, but often just deletes 2 characters. 

123567890

Where's the 4!

Er... Any other ideas? Guess I'll try the USB keyboard idea, if I can get my hands on one.

---

### Post by mastablasta on 2011-10-13
if oyu had some PPA and upgraded something could have gone wrong.

---

### Post by sanderd17 on 2011-10-13
> **JayzeeT said:**
> Ok, just booted from LiveCD and still got the same problem, so I'm guessing that points to hardware issues?!

My new test is to use a single finger and type 1 2 3 4 5 6 7 8 9 0 and often it misses a number or two. Also I've got a delete test, bang delete 3 times quite fast, but often just deletes 2 characters. 

123567890

Where's the 4!

Er... Any other ideas? Guess I'll try the USB keyboard idea, if I can get my hands on one.

My guess about a governor setting can't be right. With a very wrong setting, you would still get all the characters, they would just appear slower.

So yes, try another keyboard if you can.

---

### Post by JayzeeT on 2011-10-13
Er... What's PPA?

---

### Post by Lisiano on 2011-10-13
PPA - Personal Package Archive, basically a link in your /etc/apt/sources.list or /etc/apt/sources.list.d/*.list
You might have added a ppa using this command
```
sudo add-apt-repository ppa://someone/something
```
Manually editing the files I said above, or using the Sources List program and adding new Sources. Just type this in a terminal (Ctrl+Alt+T) or in the Run dialog (Alt+F2) and put this line in
```
gksudo software-properties-gtk
```
A box will popup and ask for your user password, give it.
Another window will appear, open the Other Software tab. If it has only "Cdrom with Ubuntu xx.xx xxxx xxxx" (Xs replace a version number and the name), "Canonical Partners" and "Independent" then you have no PPA's and no other Software installed. If there is something else, look at the line in the brackets and if it looks like this ([http://ppa.launchpad.net/someone/something/ubuntu](http://ppa.launchpad.net/someone/something/ubuntu) xxxx) (Someone replaces the owner, something the ppa name and xxxx replaces the Ubuntu codename) then you have a PPA, if not, then it's some software from a unknown source (For example Google, Opera or Skype).
If what I said is over your head, just type this commands in a terminal (Ctrl+Alt+T) and post what they say
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by JayzeeT on 2011-10-13
I tried your first suggestion but my 'other software' tab seems to have a lot of stuff in it, although most unchecked. Lots of references to 10.10, which is odd as I'm running 11.04?

The following options are checked:
 - Independent
 - Independent (Source Code)
 - Canonical Partners (added by U1MusicStoreWidget)

And that's it, so maybe quite different from what you suggested below?

So here's my 'cat /etc/apt/sources.list':

--
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free # disabled on upgrade to natty
# deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) natty main ## Cairo-Dock-PPA-Stable disabled on upgrade to natty

--
And here's 'ls /etc/apt/sources.list.d/':
--

canonical-partner-maverick.list  canonical-partner-maverick.list.distUpgrade  canonical-partner-maverick.list.save  medibuntu.list  medibuntu.list.distUpgrade  medibuntu.list.save


Anything odd going on there?

---

### Post by JayzeeT on 2011-10-13
Just borrowed a USB keyboard and it works fine! No jumpy weird delays at all. 

So I'm guessing it's either a software problem with something that's dealing with my laptop keyboard, or a hardware problem with the keyboard itself? 

Think it's probably a software thing, as it's not always the same key that has problems, so don't think it's chewing gum or *** ash under the keys or anything. 

Any ideas? Obviously I can use the USB keyboard, but would like to get the normal keyboard working as well. 

Cheers!

---

### Post by Lisiano on 2011-10-14
It means that currently you don't have any PPA installed but you did before the upgrade (That's why you see a lot of unticked stuff).


You said you booted from a LiveCD, which exactly? The one you originally installed Ubuntu with or the natty/oneiric one?
If the 1st, you have a hardware problem. If the later, it might be some sort of regression, try the LiveCD for the Ubuntu you originally installed.
The ideal thing to do would be to open up the laptop but I wouldn't recommend that since laptops are harder to open than desktops and keyboards, it also varies from manufacturer to manufacturer.
If you can, try to get a local hardware specialist to take a look.

---

### Post by JayzeeT on 2011-10-15
Ah... I haven't got the original CD I installed from, so I just burnt a new CD from the Ubuntu website, so maybe this 'regression' thing?!?

I'm pretty good with opening up electronics, so happy to have a shufty inside, in fact that was next on my list, what should I be looking for, dirt / dust / fluff balls and loose wires?

Thanks again for the help, was close to buying a new(er) laptop, but now I've seen a USB keyboard working well, think I'll crack this problem in the end!

---

### Post by Lisiano on 2011-10-15
You can always download a older version and burn it to a USB or CD, USB is better since you can test multiple times if the CDs you have are not rewritable.
Pick the one you installed originally (Or the one without a problem) and use it to test.
[LIST]
[*]Oneiric - [http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)
[*]Natty - [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)
[*]Maverick - [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
[*]Lucid - [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)
[*]Karmic - [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)
[/LIST]If you used an even older release, substitute the number on the end of the line with the one you installed. If the problem persists, 100% hardware related.

If you are not afraid to open up your laptop, I recommend first googling a guide to opening your laptop as they get tricky and some manufacturers don't want you to get in. Note that unlike desktops, opening a laptop (Excluding the panels on the bottom) voids the warranty immediately while opening a desktop (In most cases) does not (They allow adding more RAM by hand).
The thing you should be looking for is exactly what you said, dust, dirt, food, etc. Mostly concentrate on the area where your keyboard is and it's connector with the cable, try to see if the cable is 1) Torn 2) Loose or if the connector is 1) Not fully closed 2) Broken. Note that you should be careful with the cable, while the ribbon cables themselves are quite sturdy and won't break that easy, the connector on the other hand, will break with ease.
Also a warning if you never dealt with flexible ribbon cables [(Link)]("http://en.wikipedia.org/wiki/Flexible_flat_cable"), ***_[COLOR="Red"]DO NOT TRY TO REMOVE IT BY ANY AMOUNT OF FORCE.[/COLOR]_*** There is a lock(?) on the upper part of the connector which you need to _**gently**_ pull back.

---

### Post by JayzeeT on 2011-10-17
YAAAAAAAAAAAAAY!

So I tried a 10.10 live CD (which I'm pretty sure was the original install) and still had the problem. So I went for it opened up the machine, everything apart and cleaned and what not. 

Couldn't see any particular issues, nothing looking damaged or whatever, so just put it all back together not really expecting much and BINGO! Keyboard is working fine and the track pad (mouse on screen) is less jumpy. So obviously something going on in there which a bit of a clean sorted out. 

Pretty nuts, it's like a new machine again. 

I followed this tutorial, which is nice a clear...
[http://ahwee.com/how-to-disassemble-laptop-insp6400](http://ahwee.com/how-to-disassemble-laptop-insp6400)

Thanks for the help with this, don't think I would have bothered to take it this far without the words of encouragement. 

Cheers!

---

### Post by egalvan on 2011-10-17
> **JayzeeT said:**
> YAAAAAAAAAAAAAY!. So I went for it opened up the machine, everything apart and cleaned and what not. 

Couldn't see any particular issues, nothing looking damaged or whatever, so just put it all back together not really expecting much and BINGO! Keyboard is working fine and the track pad (mouse on screen) is less jumpy. So obviously something going on in there which a bit of a clean sorted out. 

Pretty nuts, it's like a new machine again. 



Many times electronic components will develop "rust" or "corrosion" at contact points, such as pins/cables/etc...
many times removing and reinstalling these will clean the contacts,
and at times just moving them a bit will do the trick.

When I service computers, I always disconnect/reconnect anything I can...

---

