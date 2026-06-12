---
title: "Downgrade Hardy xorg ATI drivers?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2008-05-27
Hi,

I have an ATI Radeon 7000 video card that works great in Gutsy but seems to really fall down in Hardy, could someone please walk me through the steps I need to take in order to downgrade the ATI video modules to the ones used in Gutsy?

--bornagainpenguin

---

### Post by tramir on 2008-05-27
Or you could use the latest ATI drivers via EnvyNG (it's available in the repos)

---

### Post by bornagainpenguin on 2008-05-27
> **tramir said:**
> Or you could use the latest ATI drivers via EnvyNG (it's available in the repos)

Not really...the Radeon 7000 has been abandoned by ATI.  If it weren't for the fact this is a friend's computer I'm working on here (and being stuck with a RAdeon 7500 in my Inspiron) I'd never use another ATI card again, given how eager they've been to abandon their customers....

No I'm afraid downgrading seems to be my only hope right now.  :(

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
/LE BUMP

From the [Community Documentation](https://help.ubuntu.com/community/RestrictedDrivers/ATI):
[quote=RestrictedDrivers/ATI]Radeon R100 to R200 - Cards in this range (Radeon 7000 to Radeon 9250) should use the open source ati driver which is the default on Ubuntu. This driver provides full 3d acceleration and is fully capable of running a composite manager. Older versions of fglrx (in 6.10 and older) supported the r200 series (Radeon 8500+), but it is practically impossible to use this driver on 7.04 (Feisty), and there is very little reason to do so.[/quote]

See?  Envy will do nothing for me...can anyone give me directions on how to downgrade?

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
/bumping this back up from the end of page three...

Anyone?  I really need to get this to work in Hardy because otherwise my friend will be stuck with Gutsy and Gutsy is EOLing pretty soon..  Not to mention the button in Update Manager advising him to update all the time...

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
Am I to conclude by the silence that the behavior indicated in the screen shot is to be considered "normal" on Hardy?

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
> **tramir said:**
> Or you could use the latest ATI drivers via EnvyNG (it's available in the repos)

Trying this resulted in:

> EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

--bornagainpenguin (doing this so no one can say I'm ignoring advice given)

---

### Post by overdrank on 2008-05-27
Hi and you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by bornagainpenguin on 2008-05-27
> **overdrank said:**
> Hi and you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Thank you for the link, unfortunately it does not seem to apply to my situation.  Compiz is *already **working*** at install.  That is not the issue I am having.

The issue I am having has to do with poor video performance and redrawing issues along with black boxes (from shadows?) being left behind when things don't refresh properly.  Also after entering my password I see white streaks and blocks of grey flashing horizontally accross the screen.  This does **not** happen in Gutsy, with or without Compiz installed, so the only thing I can point to is Hardy itself or changes in xorg...

Thus I am asking for a way to "downgrade" back to the Gutsy version of xorg--what I know works; can anyone help me with that? 

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
Rebumping this from the bottom of the third page...

As previously stated, EnvyNG is not a solution (card not supported), Compiz already works so that is not my issue, what **is** my issue is the video drivers in Gutsy Gibbon better supported my card and I need help somehow keeping those drivers while upgrading\installing Hardy heron.

I have just wiped the Hardy install and installed a command line only system from my Gutsy alt-installer cd.  Am now waiting (currently at 59m54s) for that command line install to be updated with:

```
sudo aptitude install ubuntu-desktop
```

Can someone please explain to me how to pin the Gutsy xorg drivers from here and how to update to Hardy after doing so?  From the command line if at all possible?

Thanks!  And I'm sorry to be constantly bumping like this, but I really do need the help....  

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-05-27
/BUMP

Rescuing this from page three again...

--bornagainpenguin

---

### Post by krash182 on 2008-05-28
Mine won't work either, same card same problem, same runaround for help. the default drivers are usless with the 7000 and I am ready to reinstall windows and abandon this joke of a operating system.

---

### Post by krash182 on 2008-05-28
> **tramir said:**
> Or you could use the latest ATI drivers via EnvyNG (it's available in the repos)

EnvyNG driver does not recognize the 7000, not an option.

---

### Post by bornagainpenguin on 2008-06-01
[QUOTE=jacobmp92]Dear bornagainpenguin,

You have received a warning at Ubuntu Forums.

Reason:
-------
Excessive Bumping

Please, don't bump your threads so often. The third page does not mean your topic will never be seen again. We have forum teams that deal specifically with unanswered posts and the ABT forum. If you must bump a post, wait at least a day before doing so. You may not notice it, but frequent bumping only has a negative impact on the chance of your thread being answered, as people become less interested and more annoyed.

Thanks!
-------

Original Post:
[post]5059139[/post]
> /BUMP

Rescuing this from page three again...

--bornagainpenguin

Warnings serve as a reminder to you of the forum's rules, which you are expected to understand and follow.

All the best,
Ubuntu Forums[/QUOTE]

It's now been five days since I originally posted this thread asking for help with this video card and about Hardy's abysmal support for it even though Gutsy had no such issues.

Five days.  And the only responses have been from those offering bad advice, or recommending I move back to Windows.  Oh and a PM from an annoyed mod who decided to issue a warning instead of noticing the distinct lack of help.  Where are these forum teams you mention?  Wow look at how the views just seem to taper off once the thread makes it past page three...

I've already removed Hardy from this machine and installed Gutsy, disabling the distro upgrade notice.  Hopefully this won't cause any issues down the road and the people who will be using the machine won't be zombified due to not running the most up to date releases.

Look, even a cursory scan of the forums should indicate that people are having major issues with the new xorg and or video drivers.  I can't understand how Ubuntu can have a release that works perfectly and then come out with something that drops the ball as badly as this...

--bornagainpenguin

---

### Post by xfceuser on 2008-06-01
i have sort of similar problem, that it seems the best way might be downgrading the driver. i have ati radeon 7500. before Ubuntu 7.10 there was a prop. driver in the restricted driver section that was removed later, now i have no 3D and trying 3 month to solve this problem. the new ati prop. driver dont support 7500 and older.
more details of my problem here :
[http://ubuntuforums.org/showthread.php?t=814518](http://ubuntuforums.org/showthread.php?t=814518)
:confused:

---

### Post by bornagainpenguin on 2008-06-14
/Unresolved BUMP

(mostly bumping for others-I've since installed Gutsy due to these issues)

PS: Love those forum teams...

---

### Post by bornagainpenguin on 2008-07-07
Wow...those forum teams must be *really* busy....

--bornagainpenguin 

PS: /BUMP for answers for use in future installs...

---

### Post by ABPenguin on 2008-07-10
I'm having the same issue on Hardy.  Since upgrading I have yet to get 3D working properly on my Xpress R200 card which in on the mother board.  3d did work on prior versions without major issues.  I was looking for a solution and am apparently dead-ended with the new driver versions, so down grading or replacing my video card is the only solutions left.

2D works fine with FGLRX driver and compiz has no problems.  But no matter what I try direct rendering(DRI) won't load with the new drivers and cannot run anything that needs openGL.   

So I guess the question posted earlier was how does one go about installing the old drivers.  I had full 3D before upgrading and never contemplated loosing existing capabilities.

One can easily remove the existing drivers,  how do I install the old drivers and where should I be getting these from.  I guess the other question is are there any dependencies that halt Hardy from loading the old drivers? 

I guess the other question is, is downgrading the correct solution?  Is there something else possible.  I'm thinking purchasing an Nvidia card but have no idea which of there cards are good or bad especially when used under Linux.   Am I wasting my time trying to get 3D working for this card under Hardy?

---

### Post by cariboo on 2008-07-10
I've got an HP ze5475ca, I'm using the latest Linux Mint light version. It's got an ATI graphics card M300 if I remember correctly. It works quite well, compiz doesn't work, but I really don't care, it uses the open sources radeon module. I'm quite satisfied with the way it runs. I gave up on Hardy on the laptop after trying for several weeks to get it to work properly. I really do not like ATI as over the years I've never had good luck with the video cards, especially in Windows.

Jim

---

### Post by soxs on 2008-07-10
Simply remove any restricted ati drivers and afterwards go to /etc/X11/xorg.conf and open it with su rights. Goto the device section and replace "fglrx" with "ati". Finish (in theory).

---

### Post by Rocket2DMn on 2008-07-10
OK, so what exactly is the problem you are having?  First, you should make sure there are no restricted drivers.  Try uninstalling from EnvyNG (even though your initial installs failed, hopefully this can clean up remnants).  Otherwise try
```
sudo apt-get remove --purge xorg-driver-fglrx
```
overdrank posted a link to my compiz workaround already for Hardy Heron.

Some people have issues with xserver-xgl if it was installed and for other people, resetting xorg.conf to match the new version of X cleared up some problems:
```
sudo apt-get remove xserver-xgl
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.

---

### Post by skrribble on 2008-07-10
the best solution i have come up with for an ATI card is to use the open source "ati" driver rather than the "fglrx" driver in the xorg.conf.  My problem with compiz is that i use dual monitors and my card (an ati mobility radeon x600) only supports 2400 pixels wide, so i can't enable compiz.  I am almost positive tho that the open source drivers will support most cards for 3D and compiz.  In my experiences with the fglrx driver, it is ****.  I try it every 3 months or so, and it never works how I want it to.  So, again, my suggestion is to try the 'ati' open source driver.

---

