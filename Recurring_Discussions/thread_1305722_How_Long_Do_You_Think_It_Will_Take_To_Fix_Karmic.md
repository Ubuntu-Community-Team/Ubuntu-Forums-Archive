---
title: "How Long Do You Think It Will Take To Fix Karmic?"
date: 2009-10-30
forum: Recurring Discussions
---

### Post by bds28338 on 2009-10-30
Well, I've just installed Karmic as I'm sure many of you have, and I'm having a few small issues myself.

- fake hard drive fail message
- crackling speakers
- serious kernel problem message
- npviewer.bin ended unexpectedly message

How is everyone else doing? How long do you think before the initial "my Karmic install is giving me problems!" fades and the good people at Ubuntu generally patch up the most common problems and errors?

---

### Post by dj-toonz on 2009-10-30
I've had no problems with 9.10 yet bar 1 little bug with Symantic package manager crashing every now & then but updates are rolling in right now as I've just had a few when I did a sudo apt-get update in Karmic, so the little fixes are coming in like a grub 1 & a few others

---

### Post by ikt on 2009-10-30
> **bds28338 said:**
> Well, I've just installed Karmic as I'm sure many of you have, and I'm having a few small issues myself.

- fake hard drive fail message
- crackling speakers
- serious kernel problem message
- npviewer.bin ended unexpectedly message

How is everyone else doing? How long do you think before the initial "my Karmic install is giving me problems!" fades and the good people at Ubuntu generally patch up the most common problems and errors?

Generally there isn't a 'major milestone/service pack' where a whole bunch of bugs get their fixes released, working on launchpad you see that thousands of bugs are at all different stages (from not enough info, to being investigated, to be fixed etc)

Therefore the best thing to do in order to get your issues fixed is to report them to launchpad and try your best to help bug fixers get the info they need to fix the issues you have. :)

---

### Post by diesch on 2009-10-30
Uusually there are lot's of new bugs found and lot's of bug fixes in the first few weeks after a Ubuntu release because there are so many more people using it. To get things fixed it is important that you report the bugs you find, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by bds28338 on 2009-10-30
that's exactly what I did when I had small amount of problems... just reported them and went on my merry way. As of the moment I'm just messing around in Wine as I didn't have a chance to try it before I updated from 9.04. I actually just finished installing 9.04 fully and getting all my settings in place yesterday. Then of course 9.10 comes! Time for a cigarette break though.

---

### Post by JBAlaska on 2009-10-30
I really haven't had any actual "Bugs" in the three systems in my sig. just some minor config stuff and the usual "It's working fine..so let's see if I can screw it up" type errors.

---

### Post by lisati on 2009-10-30
As with other releases I've looked at, the transition to Karmic has gone well for some people, and not so good for others. 

What I've done so far is to download the 64-bit ISO & loaded onto a USB memory stick prior to committing it to CD. Running it in "Live CD" mode on my laptop shows promise of being problematical (not getting to a Gnome desktop, once or twice getting a command prompt). Doing the same on my main desktop machine shows a bit more promise: at least I get a GUI, but the software center and error reporting "stopped working unexpectedly". This is pretty much the sum total of my tinkering so far.

I'm confident that once more of us have had a chance to check things out and reflect upon problems experienced by some of us, any remaining wrinkles that weren't discovered during testing will be ironed out. It could take anything from days to weeks.

---

### Post by spoon_ on 2009-10-30
I had the crackling speakers too but I found a way to fix it. Right click the sound tray icon, go to hardware tab, and change profile from 4.0 to 5.1. At least, that's what fixed it for me.

---

### Post by bds28338 on 2009-10-30
bump

---

### Post by HardcoreSSG on 2009-10-30
Karmic is running pretty good for me! :D

My only two problems are slow graphics and no sound.
I can live without sound and the graphics are really just games - firefox runs the same as it used to.

---

### Post by realzippy on 2009-10-30
It runs perfectly.Only my mousebutton2 (mousewheelclick)
has gone....

---

### Post by bezolaam on 2009-10-30
I have a problem with my audigy sound card and with few small softs (avant window manager, sreenlets etc.) after upgrading

---

### Post by Mzwo on 2009-10-30
i've had the npviewer.bin crash but without any noticable consequences. bizarely, flash would still work.

AND

mousewheelclick doesn't seem to work anymore. also, cube flipping using wheel or right edge of mousepad stopped working.

other than that: it works. however, i think it's running a little slower that 9.04...

Mzwo

---

### Post by rockstarrem on 2009-10-30
I got everything fixed within an hour or so. I think this is a great release and I can't wait 'til April :D.

---

### Post by Mzwo on 2009-10-30
what did you fix and how did you do it? 

what i forgot: startup is noticably slower than 9.04. shutdown, on the other hand, is extremely quick. 

Mzwo

---

### Post by ndefontenay on 2009-10-30
Will be installing it with my girls tonight :)

I've seen quite a few bugs reported but as mentioned earlier, using Ubuntu is not just about enjoying it. It's about each of us doing our ant's job of finding and reporting those bugs too.

I'm really looking forward to tonight.

---

### Post by ElSlunko on 2009-10-30
I had that annoying harddrive message too. Wish they had stuck to not using it since it doesn't work well (I think, my hard drives might actually be ready to take a spill!).

I just disabled it from my startup programs.

---

### Post by philinux on 2009-10-30
> **bds28338 said:**
> Well, I've just installed Karmic as I'm sure many of you have, and I'm having a few small issues myself.

- fake hard drive fail message
- crackling speakers
- serious kernel problem message
- npviewer.bin ended unexpectedly message

How is everyone else doing? How long do you think before the initial "my Karmic install is giving me problems!" fades and the good people at Ubuntu generally patch up the most common problems and errors?

This is one bug you are referring to and it has been triaged.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536)

I suspect it will takes weeks to get some of these ironed out.

---

### Post by mrbinitie on 2009-10-30
I cannot change my login screen - I get a panel that asks me to confirm if I want a password login and all that stuff but nowhere I can actually change my GDM.
In addition I cannot seem to install Flash 1o from the Terminal - tells me my glibc is old and I need to update - why is that?
I also cannot use the mouse pad to rotate my Desktop Cube
I get a failed harddrive message on a 3 month old HP 8710 w laptop

---

### Post by bds28338 on 2009-10-30
bump

---

### Post by rosswmcgee on 2009-11-01
So is the 9.10 problem 422536 confined to the upgrade and absent from the clean install?

 422536 seems to be my only problem.

---

### Post by Nightstrike2009 on 2009-11-01
After it has borked my 3G internet connection, until 10.4 as I am downgrading to 9.04 which i was more than happy with. 
Ubuntu 9.10 is like windows vista, I wont be upgrading from 9.04 until next release i don't think i am alone on this one neither problems like this deter new users instead of winning them over, should have been delayed until resolved not rushed out full of holes like MS does (The very reason i am using ubuntu is i think better of it and 9.10 lets the name down). :(

---

### Post by DonaldJ on 2009-11-01
"How Long Do You Think It Will Take To Fix Karmic?"


__________________________


For me, it's good.. There are just a couple irritations that will probably be fixed for the next update.. But for some with troublesome antique motherboards.. Um, ever heard of, "*when hell freezes over*"..?

---

### Post by rosswmcgee on 2009-11-02
I love the term Borked! So how do you down grade?

---

### Post by Nightstrike2009 on 2009-11-03
I tried to at least but can't get 9.04 to accept its own ati driver now that was working before. Also though annoyed with karmic noticed many improvements in with the bugs (Internet prob annoys the hell outta me though).

Fortunately i can dual boot so i can use windows for internet, using Karmic as practice for Lucid. 

PS: Please, please don't let lucid be released with sub-standard bugs in it, I am trying to win people over to ubuntu and this sort of thing just makes us all look stupid. (Well it worked in last version, but look they have borked it in new version, it aint funny and its getting beyond a joke now) :(

PPS: I am a linux user since Red hat 3.0 and the amount of daft mistakes made in ubuntu, is getting silly now, come on guys, I believe in ubuntu but none of us needs this kind of daft behaviour (If lucid is borked, I am leaving for a new distro probably Debian or Linux Mint, I don't think i'll be alone either). :(

---

### Post by ChrisInvisible on 2009-11-03
I only used 9.04 for a couple of weeks before upgrading to 9.10, but I'm only having a few small cosmetic issues. Namely the icon for logout has changed and I'm unable to figure out how to change it back (that may be my lack of knowledge, admittedly), and network manager's notification bubbles seem to be popping up about 100px lower on the screen than usual. I'm not sure if that's by design or not, but I'm not fond of it. To me, it seems a little disconnected from the top panel, making it seem like it's an entity all its own, when it's clearly network manager. I'd rather like to see the notifications pop up in sort of a "speech bubble" format, with the indicator pointing to nm's icon on the panel. Just my preference, though.

---

### Post by Zoot7 on 2009-11-04
Living with Karmic now for a week, I have to say it's fairly rock solid for me.

I still have some issues with Pulseaudio; I've always stripped Pulseaudio and just used alsa previously (which was always flawless), but now it's too integrated to simply uninstall it. I hope Pulseaudio isn't the problem it is now in Lucid.
There's been two cases where the network manager hasn't started on a boot, forcing me to reboot to get it to work again.
Not sure what the cause of that is, but it's only 2 isolated times in the last week. That said wireless seems to be now rock solid for me, which is a very welcome change. :)

---

### Post by jwbrase on 2009-11-04
> **Nightstrike2009 said:**
> I tried to at least but can't get 9.04 to accept its own ati driver now that was working before. Also though annoyed with karmic noticed many improvements in with the bugs (Internet prob annoys the hell outta me though).

I'm surprised you got Jaunty to work with ATI at all. As I understand, ATI pulled support for certain of their cards when they put out their proprietary Linux drivers around the time that Jaunty was released, and the old drivers don't support the kernel that Jaunty uses. I don't know exactly what problems you're having, but with our family desktop (which has an ATI card) back home, I could get LXDE to work under Jaunty, but GNOME chokes. I'm using a System 76 Laptop with NVidia and Jaunty here, and it's running very smoothly under GNOME.

---

### Post by dmclennan on 2009-11-04
Several problems/bugs =

[LIST=1]
[*]gedit won't save files on Windows Sever network share using cifs
[*]mpd won't read music library stored on Windows Server network share using cifs.  Returns failed to stat error message.
[*]pulseaudio/alsa now plays through PC speakers.  It appears that blacklist does not work.
[*]volume control lacks options, volume sliders, mixers.
[*]Either screen saver or powersaver don't release keyboard lock (need to minimize/restore windows to regain use of keyboard). This was also a problem with 9.04.
[*]gtkpod crash when drop files onto iPod
[*]Rhythmbox resets its volume to 0 (this might be bugs with replaygain as you can see the volume control slider move up/down).
[/LIST]
Almost enough reasons to downgrade back to 9.04.

On the other hand, pulseaudio seems to work much better than 9.04.

I agree with other posts - this looks a lot like a Windows release (ME or Vista).

---

### Post by togo59 on 2009-11-04
I agree with NightStrike2009, Karmic has borked some of my stuff too. The upgrade to 7.10 borked my wireless, 8.04 borked my sound system (removing pulse audio fixed it) and Karmic has borked the graphics.

Like NightStrike2009 I have been eulogising Ubuntu and it doesn't make it any easier when Canonical cock things up (sorry, bork things up) on this scale. Is Karmic Canonical's Vista?

I have resolved to install 10.04 as soon as the beta is out and to lobby for the problems I get to be fixed in time for the release. I have just got rid of my Vista partition so in future I'll dual boot with the current version of Ubuntu on one partition and the upcoming version on another. The more of us that actually test before the new release comes out the better it will be in the long run.

I guess what I am saying is that I can't really complain about Karmic because I did diddley-squat to help test it in the first place. 

But, honestly, borking the capability of perfectly up-to-date Radeon graphics cards is, IMHO, a bork too far.

---

### Post by Ian Sinclair on 2009-11-04
The ECC error message seems to have disappeared, and I can now print photos with Photoprint (but not with F-spot). I still have problems with Grisbi, but the Grisbi bug team is chasing this one. Once Grisbi is fixed Karmic will be working for me and I can put that Jaunty install diskl away.

---

### Post by Nightstrike2009 on 2009-11-05
> **By togo59:Like NightStrike2009 I have been eulogising Ubuntu and it doesn't make it any easier when Canonical cock things up (sorry, bork things up) on this scale. Is Karmic Canonical's Vista?**

Thanks for the support i was winning another user over to Ubuntu very successfully, but has he had the same 3G wireless modem as me (that Karmic borked up) he has since exercised caution and stuck with windows.

How many times do we have to keep saying this "If it aint broke don't fix it, promoting Linux is hard enough without these constant bugs loosing us potential users who could further the linux cause and add to the ubuntu help forums"

I stand by what i say one more fatal flaw in either the 3D Drivers, Network Connections, or Audio System (OpenAL) and iam off to another distro. 

I started at a time when many knowledgeable forum posters left, and although new promised to share what i learned about solving ubuntu problems with others who needed my help (Which i have, and been involved in testing on alphas/betas reporting bugs as best i could.) 

This is not the way forward to win over MS Domination of the OS Market, get a grip guys many of us left MS because of releasing unfininshed products with many bugs, do you really think new Ubuntu users expect the same treatment from a more stable, relable OS like Ubuntu should be?

Because I don't if you want MS to destroy Linux keep releasing bug ridden OS with major 3D GFX, Sound problems, or network problems and they will.

To those who tell other users to stop complaining and use another distro i suggest you follow your own advice. We are trying to give our feedback to make Ubuntu better so the mistakes of the past can be avoided instead of repeated.

---

