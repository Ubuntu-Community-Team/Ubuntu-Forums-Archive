---
title: "Help - Wife demanding Windows back!"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Sidney232 on 2008-11-19
My wife is shouting about going back to Windows if I can't fix the FUSA in Ubuntu. I really don't want to do that as it's been a really good experience so far.

I recently upgraded from Hardy to Intrepid and everything appears to work just fine… all except the fast user switcher. It sometimes fails to work altogether. It sometimes throws up error messages such as:

Cannot start new display - there were errors trying to start the X server.

Or...

Graphical System Error - The graphical interface did not properly start, which is needed for graphical logins. It is likely that the X windows system or GDM is not properly configured.
Details - X server failed to finish starting. 3X failed.

From reading about on here I get the idea that the problem is related to my graphics card or its driver or is that just a red herring?

I’m running a Dell Dimension 4400 1.7GHz with 765MB Ram. Display is an old Scott LW851 LCD, video card is ATI Rage 128 Pro. There’s nothing else on the PC – no dual boot etc. I installed originally last year from 7.10 and upgraded to 8.04 with no problems. I have two HDD; a 13GB one on which Ubuntu is installed and a 40GB one set up just for data. Both work just fine.

Someone's gotta have an idea?

---

### Post by MasterSander on 2008-11-19
Get a divorce :D

---

### Post by NullHead on 2008-11-19
I don't know much about that graphics device, but does it require a restricted driver from the restricted driver manager?

Give her windows then and you can dual boot into ubuntu when you use the machine.

---

### Post by wolfen69 on 2008-11-19
why not dual boot? then both of you can be happy. just remember to install xp first.

---

### Post by Sidney232 on 2008-11-19
OK, assuming divorce is not an option...
We have one PC and we switch users multiple times per day - dual booting just isn't an option. All she uses in internet access for facebook etc and sorts photos etc.

---

### Post by ARhere on 2008-11-19
Use the same account, get a new video card (*they are cheap now anyways*) or get her own PC.

-Andrew

---

### Post by Sacrifice on 2008-11-19
> **ARhere said:**
> Use the same account, get a new video card (*they are cheap now anyways*) or get her own PC.

-Andrew

Use the same account. :I You are married and whatnot.

---

### Post by skintythe1andonly on 2008-11-19
Go back to hardy when things worked id say. It is LTS so prob for the best to save yourself headaches like this. I gave up on getting my printer to work for my mum on Intrepid and its now back on hardy. Just because Intrepid is newer doesnt mean its better

---

### Post by kneewax on 2008-11-19
> **Sidney232 said:**
> OK, assuming divorce is not an option...
We have one PC and we switch users multiple times per day - dual booting just isn't an option. All she uses in internet access for facebook etc and sorts photos etc.

IF the machine is beefy (1GB+ RAM) Run Windoze in a Virtual Box, so she can just open a minimised window or (stick it to DESK4) when she wants to dance with Uncle Bill

---

### Post by porchrat on 2008-11-19
> **kneewax said:**
> dance with Uncle Bill

I like that

---

### Post by detroit/zero on 2008-11-19
> **Sidney232 said:**
> I recently upgraded from Hardy to Intrepid and everything appears to work just fine… 

[...]

I installed originally last year from 7.10 and upgraded to 8.04 with no problems.
That's two upgrades. Upgrades aren't as reliable as fresh installs. I'd say back up all important data and do a fresh install of 8.1, assuming that's the version you want to run.

You might be well off to re-install XP as well, and dual-boot your system as others have suggested.

---

### Post by starcannon on 2008-11-19
Get rid of the FUSA applet and just do a regular log out to the log in screen. It only takes moments more than fusa, and has none of the problems.

---

### Post by fooman on 2008-11-19
i agree with starcannon....ctrl-alt-backspace works pretty darn fast on my machine.

---

### Post by LowSky on 2008-11-19
Why can't you use the same account? sounds like someone is hiding something!

hope all is well..

oh and if you do go the new install route, don't forget to make a backup of your firefox bookmarks and your /home folders.

---

### Post by Keen101 on 2008-11-19
Yeah get another graphics card, or get another machine for you that works good with linux.

---

### Post by Paqman on 2008-11-19
> **LowSky said:**
> Why can't you use the same account? sounds like someone is hiding something!


The way my missus leaves junk all over the desktop, she's not going near my login.

Besides: themes, bookmarks, IM contacts, etc, etc. It's not about hiding anything, it's about personalising the machine.

---

### Post by perlluver on 2008-11-19
I had some troubles after upgrading, like no splash screen, and my second hard drive wouldn't mount.  Did a fresh install and everything seemed to work ok.  If that is an option, do a backup and do a fresh install.

---

### Post by dracayr on 2008-11-19
have you tried reinstalling the fast userswitch applet?```
sudo apt-get install --reinstall fast-userswitch-applet
```

dracayr

---

### Post by loboc on 2008-11-19
Intrepid dropped support for older video cards in both ati and nvidia varities.   You could get on new egg and get a new card or figure out how to get the ati driver from hardy in ibex 

Reading Release Notes is good:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Upgrading

Users of Ubuntu 8.04 LTS can upgrade to Ubuntu 8.10 by a convenient automated process. Users of older Ubuntu releases need to upgrade to Ubuntu 8.04 LTS first, and then to 8.10. Complete instructions may be found at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).
nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.
ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information

---

### Post by newbuntuxx on 2008-11-19
I had issues with the upgrade as well. But after an reinstall, everything worked fine.

Solutions to your problem:
1. Download 8.10 image and burn it to CD
2. if you dont already have a separate /home partition, then back up all data that you need
3. reboot with cd in and reinstall the system (if you haven't done so alreayd, you should always create a partition for your root "/" and a separate partition for your "/home". It makes a reinstall very easy)

Second solution:
install virtual box and install windows on it. and if you install the extra tools that come with it, you can even fool your wife into thinking that she is actually using windows.

hope this helps

---

### Post by bodhi.zazen on 2008-11-19
Actually, a very simple solution is to run multiple X windows. Your wife can have a session on Ctrl-Alt-F7 and you can take Ctrl-alt-F8 (for example).

It is quite simple and does not take up as much in terms of resources as you might think.

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674")

---

### Post by Therion on 2008-11-19
[COLOR="White"].[/COLOR]

---

### Post by medic2000 on 2008-11-19
These types of jokes are not funny i think and does not help OP too. So we can take our jokes to somewhere else.

---

### Post by Therion on 2008-11-19
> **medic2000 said:**
> These types of jokes are not funny i think and does not help OP too. So we can take our jokes to somewhere else. :roll:

Happy now?

---

### Post by Sidney232 on 2008-11-19
Thanks. I kind of get the idea that there's some consensus that it is the old ATI card and/or (lack of) driver that's the root cause here. I guess there's not much point trying a fresh install if I'll run into the same problems again afterwards?

---

### Post by rustic on 2008-11-19
> **medic2000 said:**
> These types of jokes are not funny i think and does not help OP too. So we can take our jokes to somewhere else.

not be be contrary (ok, to be contrary), I think the OP has been given an abundance of tips (Top of page 3 is full of win), and now, in our time of need, nothing helps more than levity.

Levity, for the grammatically deficient, is simply a sense of humor.

I, for one, and I bet I speak for many, found both the tips AND the humor fitting.

Oh yes, as part of my obligation from my employer, "Would you like fries with that?".

---

### Post by sigurnjak on 2008-11-19
My wife and me share same user . She does lots of internet related stuff such as facebook , photo galleries and such .We figured having 2 users is trouble .

---

### Post by medic2000 on 2008-11-19
> **Therion said:**
> :roll:

Happy now?


It is not happiness :D But thank you ;)

---

### Post by Kellemora on 2008-11-19
Hi Sidney

I'm in the same boat!

My wife loves to play these Adventure Games, not the really hard ones, but usually hunt n find types.  She like Nancy Drew games, and all those downloadable hunt n finds from an on-line source.

Since they ALL either require the CD to be in the slot, OR the on-line downloads use numerous API calls to function.

They will not work even in a Virtual Machine on Linux.........

So, I swung by the pawn shop and picked her up a 1 year old computer for 150 bucks.  After looking it over, decided I would keep it for myself and went and bought her a brand new machine with the XP-Pro UPGRADE from that Spyware OS Vista, hi hi.........

All of her personal data resides on one of my Ubuntu boxes in a shared folder that emulates her original C drive, so she's happy as a bug in a rug!

Matter of fact, I'm on that 150 buck pawn shop find right now!

So it is something to consider!

TTUL
Gary

---

### Post by crjackson on 2008-11-19
> **skintythe1andonly said:**
> go back to hardy when things worked id say. It is lts so prob for the best to save yourself headaches like this. I gave up on getting my printer to work for my mum on intrepid and its now back on hardy. Just because intrepid is newer doesnt mean its better
+1

---

### Post by dowell22 on 2008-11-19
i don't know all the details, but i would suggest a new graphics card.

i know that graphics cards can cause alot of unusual problems with ubuntu.

---

### Post by yogo on 2008-11-19
Having gone thru the same thing a year or so ago with my wife I feel your pain. I just put her on Windows it simplified things.

If I were you though, I would go back to 8.04 as you are not alone with troubles with 8.10.
and like others have said, just log in and out with different sessions.

Trying to fix Ibex may be more of a battle than you are willing to undertake.

---

### Post by POWMS on 2008-11-20
I dual boot my laptop with Xubuntu8.04 as of a month ago. My wife and I have not had any reason to use Windows since. My kids use it like they were born with Linux.......no pain here.

---

### Post by NullHead on 2008-11-20
> **bodhi.zazen said:**
> Actually, a very simple solution is to run multiple X windows. Your wife can have a session on Ctrl-Alt-F7 and you can take Ctrl-alt-F8 (for example).

It is quite simple and does not take up as much in terms of resources as you might think.

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674")

I think you should do bodhi.zazen suggested.

---

### Post by Sidney232 on 2008-12-05
OK, so I'm looking at a new video card, but one that will work with my PC. In the 8.10 release notes it says that support is being dropped for cards that use the r300 based chips. Does that imply that support for the r100 and r200 based chips has also, previously, been dropped?

---

### Post by mcloser on 2008-12-05
Stick with well known vid cards, avoid no-name grey market crap, you'll only save 10-15 bucks anyway.

my first thought is that you may want to boost your ram, what u have should be enough to run Ubuntu but it can't hurt.  i'm amazed that you can run whine-doze with that little ram !  i've got an old amd box 1.5mhz and i threw 1.5 G ram and it works ok.

I will be checking out the multi session idea too. fortunately my wife has her own laptop, there is no way in hell that she would put up with learning a new OS, as good as Ubuntu is.

live long and perspire         -  or is it -    nanoo nanoo    ?

---

### Post by RgnKjnVA on 2009-02-01
Sidney, it's been a while but I found this thread because I have the same problem on an old Dell laptop I bought and installed Intrepid on. I've set my wife up with a login mostly for when we're on vacation which is about the only time she'll use it so my need to switch is much less urgent. Still, I get the exact same error when I try to use FUSA to switch to her login. However, I've noticed that I can switch to Guest then, before the Guest is completely finished loading, I can switch to my wife's login. Kinda takes the 'F' out of 'FUSA' but for those, like me, who don't read all the warnings before loading software, it works and is cheaper and easier than a new video card (unless it's too late). Oddly, I can switch from her login to mine without a problem. *shrug*

---

### Post by 5nak3 on 2009-02-03
This might be a bit late, and may not help you too much however here is an idea:

On my laptop i dual boot, now while you said dual booting wasn't an option (as is also the case in my household) there is a solution. My linux install can read the other partition (the vista partition) so that means, if someone else wants to see a file in the vista partition for instance they simply mount the vista partition by selecting it from the places drop down list at the top of the screen.

All files are completely accessible (music, docs, pics) programs will not run, but this shouldn't be a problem if all your wife needs to do is view a few pics and what not.

The benefit of this is, you can have windows and linux running (good for programs that do not run nicely in linux), FUSA is not necessary as the other user (the windows user) can still access their files and what not without having to boot into windows. And when you are not at home assuming the other person (in this case your wife) is not comfortable with linux, they can use windows and avoid any scary situations.

So essentially, create a dual boot if you must, but you should be able to read the files without a problem meaning no need to reboot when wanting to access a windows file.

Hope that helps :)

---

### Post by Sidney232 on 2009-02-22
Thanks for all the ideas. The problem has temporarily solved itself; the missus now has a laptop PC given to her for her work at home. It's Windows so she can do all she wants on that. Still, it would be nice to have a bug free Ubuntu...

---

### Post by Virtualboxbuntu on 2009-02-22
Windows is not without its own bugs...

---

### Post by steveneddy on 2009-02-22
Go back to Hardy or dual boot/VM.

VM would be my choice.

Maybe you should just buy her another laptop?

Just go to [www.system76.com](www.system76.com) and spend your income tax return there.

Give her the old machine and you go to the coffee shop with your new, shiny lappie.

---

### Post by msimon1960 on 2009-10-12
Go back to Windows...the wife is always right.  Even when they are dead wrong...the wife is always right.

---

### Post by brookie on 2009-10-12
Ha! 

My wife was the same way. She wanted WinXP and only WinXP so she could surf the NET and occasionally use Office 2003. 

I installed Intrepid on an external USB HDD and after a couple of months she was not even booting up WinXP anymore. 

I eventually swapped out the external HDD with the internal one and edited grub so there is no WinXP option. I also installed Virtualbox and XP on that with Office 2003 for her. She never uses it though. 

This is her machine though so no user switching needed. The main reason I switched her to Ubuntu is that she did not like doing any WinXP maintenance like regularly defraging, scanning with anti-virus scanners and anti-spyware. 

She also did not want to maintain these sw programs as some of them are freeware and expire after a time and need re-installing and re-configuring. 

So now we are an Ubuntu Family, however I am uneasy about updating all three of our machines to Karmic, or maybe wait till 10.04 LTS. 

Good luck, and try and get individual computers set up if you can afford it somehow. Maybe buying used or something. 

Hang in there! ](*,)
Brook

---

### Post by Sir Jasper on 2009-10-12
Hi,

I make all the important decisions in our house. It&#347; just that my wife decides what&#347; important.

You could try to part exchange your computer and/or your wife.

My regards

PS my machine is ancient and I&#7743; delighted with Xubuntu.

---

