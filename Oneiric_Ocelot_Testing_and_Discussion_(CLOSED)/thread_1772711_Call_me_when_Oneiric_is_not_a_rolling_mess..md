---
title: "Call me when Oneiric is not a rolling mess."
date: 2011-06-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-06-01
I've been in every dev cycle since Feisty.

In that time, despite all the breakages I've encountered, not until now have I found that the dev release was bootable yet continually broken beyond usability for long stretches of time.

What gives? This isn't fun or productive to bug squashing.

---

### Post by MacUntu on 2011-06-01
[http://www.youtube.com/watch?v=IyoDpIR1wLI](http://www.youtube.com/watch?v=IyoDpIR1wLI)

---

### Post by ikt on 2011-06-01
> **Starks said:**
> I've been in every dev cycle since Feisty.

In that time, despite all the breakages I've encountered, not until now have I found that the dev release was bootable yet continually broken beyond usability for long stretches of time.

What gives? This isn't fun or productive to bug squashing.

Really? I found 10.04 and 10.10 were quite boringly stable.

---

### Post by tghe-retford on 2011-06-01
Oneiric has been pretty stable for me up until now, and still is as I type. The biggest problem I have had is the udev folder bug but it doesn't impact on anything from what I see.

Should mention at this point that I test Kubuntu as opposed to Ubuntu.

---

### Post by xeizo on 2011-06-01
Kubuntu runs very well so far, it has not been as smooth with Gnome and Unity.
 
In fact, that's why I run Kubuntu now.

---

### Post by caryb on 2011-06-01
I too am on Kubuntu, well I would be but I cant find a catV cable & my wireless is pooched so for the 1st time on my laptop I have booted to Windows 7. I feel so cheap:( Oh well maybe tomorrow there might be a fix to network mangler.

Cary

---

### Post by kansasnoob on 2011-06-01
I rather enjoy all of the borkage, but I may be a really twisted individual ;)

No Lubuntu or Kubuntu iso-testing yet:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I can't help but think gnome3 is just not nearly ready for prime time, I say that even having tested it on Fedora.

---

### Post by xeizo on 2011-06-01
I didn't start to appreciate KDE4.* until 4.6 arrived so Gnome 3 may have to have many iterations before "prime time" ...

---

### Post by jerrylamos on 2011-06-01
> **Starks said:**
> I've been in every dev cycle since Feisty.

In that time, despite all the breakages I've encountered, not until now have I found that the dev release was bootable yet continually broken beyond usability for long stretches of time.

What gives? This isn't fun or productive to bug squashing.

?  As a user/outsider, my myopic view is a bunch of developers around the world throw a bunch of stuff into the stew so of course some of the stuff conflicts and incompatibilities result.  For all I know each developer is pretty well ignorant of what will happen when it's all thrown together.

Early in a new release not very much new stuff is in so it is not very badly broken.  In a few weeks as more and more stuff go in more and more breakages occur, and you and I and many many others try to get someone to listen to the bugs.  

Natty Narwhal for me was a real disfunctional mess for a couple months, would not install at all, just in the nick of time for release being quite stable for me now.

Last Oneiric Ocelot install I did worked however it updated grub menu on a different hard drive than the one it was installed on.  I haven't felt motivated to go look at that since I'm having fun booting the .iso files direct from either a hard drive folder, no partitioning required, or a from a USB stick, or from a USB hard drive.

I don't try to get any usable work done with the new release until very very late in the cycle.

Anyway, Starks, I've gotten a lot of useful info from your posts.  Keep it up!

Jerry

---

### Post by arpanaut on 2011-06-01
What do you want me to call you?

):P

Seriously though, I quite expected things to be a mess early on, what with the transitions taking place.
Patience, Grasshopper.

---

### Post by kansasnoob on 2011-06-01
> **ikt said:**
> Really? I found 10.04 and 10.10 were quite boringly stable.

Actually even Oneiric has been almost boring until the gnome3 packages started pouring in the past week.

I'm just doing some iso and upgrade testing and I'd be shocked if we don't see a rebuild sometime today. It's really rough, particularly unity-2d.

---

### Post by MacUntu on 2011-06-01
20% boot success for weeks - not boring. :D

---

### Post by inportb on 2011-06-01
I'm also using Kubuntu and agree that it's pretty good so far. I'm installing a bunch of updates (including the dreaded udev, but hey, that's what testing is all about) and that would be fun. I think the KDE 4.x series also had its share of unfair criticism when it was in its infancy.

---

### Post by PaulW2U on 2011-06-01
> **xeizo said:**
> Kubuntu runs very well so far,
With over 150 updates over the last three days, quite a few packages held back and the possibility of getting KDE 4.7 soon, that may well change. But Kubuntu 11.10 is running so well for me that I forget I'm running a pre-alpha build. I **do** remember to copy my personal files across to my 11.04 installation as a backup though, just in case  :D

---

### Post by xeizo on 2011-06-01
> **PaulW2U said:**
> With over 150 updates over the last three days, quite a few packages held back and the possibility of getting KDE 4.7 soon, that may well change. But Kubuntu 11.10 is running so well for me that I forget I'm running a pre-alpha build. I **do** remember to copy my personal files across to my 11.04 installation as a backup though, just in case  :D

Yes, there are some dependencies unmet. But as long as one doesn't mess with installing stuff that threatens to remove half the distro just to be installed, things have been smooth.

4.7 may change that, granted, we'll see.

The only obvoius problem I've had with Oneiric Kubuntu is Kwin eating away lots of cpu-cycles in it's default config for a powerful graphics card, when running Nvidias proprietary driver. If I don't remember it wrong ,so was turning off shadows the springing point, total cpu-usage when just browsing the desktop went down to ~2% after that.

Another problem was there, but it wasn't Kubuntus own fault, because I have Gnome 3 installed as well. It was Gnome-shell running a shadow desktop behind the KDE-desktop. Turning off Nautilus in autostart and removing "let nautilus take care of the desktop" in gnome-tweak-tool removed that issue.

And then I have some mysterious scripts during the boot sequence that seem to cause errors, but those errors doesn't affect any functionality, I guess there are stuff needing to be cleaned out in the boot config, probably caused by myself running this same install since Natty pre-alpha  ;) 
I've removed as much as I can find, but some remain, even though seemingly harmless.

I think it's respectable to be able to continously upgrade from Natty pre-alpha to current Oneiric and things still running stable.

---

### Post by screaminj3sus on 2011-06-01
You realize you are using pre-alpha software right?
And there is huge changes going on in onerick, like the move from gnome 2 to gnome 3. You should expect many, many bugs.

---

### Post by jerrylamos on 2011-06-01
29 May Oneiric Live works on a couple of my test pc's.

31 May Oneiric Live boots but can't do anything with launchers or much of anything else.  Crash....Crash,...Crash....

Oh, yes, 31 May claims it is reporting bugs to launchpad.  Strange, launchpad never says the bugs are duplicates and I know I've gotten the same bug on three different test pc's.

Looks like the closer Oneiric gets to Alpha the deader it is.

Oh, well, I saved a .iso that works.

Jerry

p.s. Starks is one of the most capable testers on this forum....

---

### Post by arpanaut on 2011-06-01
> p.s. Starks is one of the most capable testers on this forum....I Know, that is why I was giving him a hard time.    :biggrin:

---

### Post by 3vi1 on 2011-06-01
> **Starks said:**
> I've been in every dev cycle since Feisty.

In that time, despite all the breakages I've encountered, not until now have I found that the dev release was bootable yet continually broken beyond usability for long stretches of time.

**What gives?** This isn't fun or productive to bug squashing.

The first really major Gnome update in a long time gives.  It's not *supposed* to be in a usable state right in the middle of a DE upgrade.

I've found days/weeks in all the previous alphas where things were broken - especially when testing the major KDE updates for the Kubuntu flavor.  It's pretty much the same with Gnome:  Don't update until you know that all the related packages for the DE have hit, because DE's hate partial upgrades even if their dependencies wouldn't lead you to that conclusion.

---

### Post by jerrylamos on 2011-06-01
> **arpanaut said:**
> I Know, that is why I was giving him a hard time.    :biggrin:

I thought Starks was a her.

Jerry

---

### Post by Starks on 2011-06-01
Nope. Just some regular guy going through a compsci grad program. Too lazy to change my avatar to eliminate confusion.

Anyway, the GNOME3 transition is creating a very unique situation. Packages are getting updated, but Ubuntu as whole isn't benefiting unless you run it with the Shell or Fallback. I fully expect Unity to receive considerable updates in the next few months, but they are needed now during the transition for the sake of prioritizing and making the rest of the dev cycle as painless as possible. Forcing Unity or Unity 2D as they exist right now is not helpful. Most of Natty's problems stemmed from the fact that Unity didn't come together until the final month of development. This should not be repeated as Unity bugs are fixed and the interface is moved to GTK3. I know that Didier and the rest of the Ayatana team are working hard, but it's very upsetting that no-brainer bug filings of established Unity problems are still unconfirmed or barely past the triage stage. I've filed quite a few bugs in which Mark Shuttleworth has weighed in on, but then there's nothing but inaction. I sincerely wish that the Unity bzr gets more attention at or before the first Alpha.

Problems related to booting (like the udev issue) or X will pop up every now and then, but are manageable because they usually stem from a quickly correctable packaging error or somebody dist-upgrading when they shouldn't have. And then there are planned breakages which the testing community readies itself for. Oneiric thus far has only fallen into the former. The result has been an overly Wild West style of pre-alpha testing. I make no expectation of quality at this point, but meaningful testing has to be possible.

---

### Post by nm_geo on 2011-06-01
Well I finally got the old Oneiric running had to install from the alternate iso.. I really got tired of that migration assistant messing with me during the normal install from live usb. Joined that bug way back in Natty installs.   I err heh.. have been also messin with Fedora 15 and Gnome 3. Perhaps all the hacks and tweak will payoff in Oneiric.  We will see what we will see.  I find Gnome 3 to be pretty okay for me.  I just don't really like yum yum and all that other Rehat stuff.

---

### Post by castrojo on 2011-06-01
> **Starks said:**
> The result has been an overly Wild West style of pre-alpha testing. I make no expectation of quality at this point, but meaningful testing has to be possible.

Ubuntu didn't exist when the GTK1->GTK2 transition happened, so this is really a first cut at a major desktop transition like this.

In the platform team at Canonical most people transition to +1 at about Alpha 2, so really no one is really dogfooding Oneiric yet, most of DX is still doing SRUs on Natty and the desktop guys are doing GNOME/GTK3, which after only about a month in is mostly working (yeah, it's still ugly, but it's mostly working).

IMO it doesn't make sense to bug report until about alpha 3 or so, until then it's all automated importing from Debian.

There's a platform sprint in Dublin in about 3 weeks, right around that point and after is when things will start to gel for 11.10.

---

### Post by mc4man on 2011-06-01
> I sincerely wish that the Unity bzr gets more attention at or before the first Alpha.
Attention, yes - significant   progress probably not. There have been a dozen or so bug fixes recently, (O & natty-proposed), some more likely soon

I wouldn't expect much of interest from unity for a couple of weeks at the very least.

---

### Post by Starks on 2011-06-01
While I agree that bug reporting isn't the most useful method of communication at this point for anything beyond system-breaking bugs, I disagree that pre-Alpha is not a useful period as a whole.

A lot of stuff gets done or put on the radar if you're an mailing list or IRC monkey.

* Universe testing
* Graphic stack and general driver testing (for getting things upstream and packaging fixes ASAP)
* Team organizing

---

### Post by jerrylamos on 2011-06-02
"Rolling mess" for me is the 31 May daily build.  Cannot select any launcher or the applet in the top left corner.  apt-get update apt-get upgrade was no help,

30 May daily build works for me, launchers work, applet in the top left corner works, ... a crash or two but keeps on running.

Here it is 2 June and the dead 31 May is still what is in daily build.  ??

The Alpha 1 is scheduled for 2 June.  Anyone any info on that?

Jerry

---

### Post by PaulW2U on 2011-06-02
> **jerrylamos said:**
> The Alpha 1 is scheduled for 2 June.  Anyone any info on that?

The Kubuntu page is there - [http://cdimage.ubuntu.com/kubuntu/releases/oneiric/alpha-1/](http://cdimage.ubuntu.com/kubuntu/releases/oneiric/alpha-1/) - but not the ISO images...yet.

---

### Post by cariboo on 2011-06-02
If you are subscribed to the ubuntu-announce mailing list, you'll get notification when the alpha is released.

---

### Post by kansasnoob on 2011-06-02
> **jerrylamos said:**
> "Rolling mess" for me is the 31 May daily build.  Cannot select any launcher or the applet in the top left corner.  apt-get update apt-get upgrade was no help,

30 May daily build works for me, launchers work, applet in the top left corner works, ... a crash or two but keeps on running.

Here it is 2 June and the dead 31 May is still what is in daily build.  ??

The Alpha 1 is scheduled for 2 June.  Anyone any info on that?

Jerry

It's all part of the dev cycle. Alpha2 will be released later today, but iso-testing revealed many bugs:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I'm a bit surprised that they decided to release with so many unity-2d bugs but they did what they thought best.

---

### Post by Harry33 on 2011-06-02
> **kansasnoob said:**
> It's all part of the dev cycle. Alpha2 will be released later today ...

Hmm, alfa2 ?

---

### Post by kansasnoob on 2011-06-02
> **Harry33 said:**
> Hmm, alfa2 ?

Oops. Meant Alpha1 :D

Silly typos anyway.

Edit: Actually to make that post totally mind blowing I should also have referred to unity-1d.

---

### Post by jerrylamos on 2011-06-02
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1)

is less of a rolling mess.  I'm running it Live here as booted directly from the .iso file in a directory /dev/sda1.

There are known bugs listed in the Overview.

Jerry

---

### Post by VinDSL on 2011-06-03
> **Starks said:**
> In that time, despite all the breakages I've encountered, not until now have I found that the dev release was bootable yet continually broken beyond usability for long stretches of time.[...]
Thanks, for starting this thread!  ;)

Reading through the posts, I'll wait awhile before downloading the Alpha/Beta ISOs.

My patched & mod'ed Alpha 1 NN -> Oneiric install is working good enough, for my purposes.

---

### Post by ronacc on 2011-06-04
the reason for using an alpha or beta is testing ,so it is rather pointless not to be using the most up to date since old bugs are constantly being squashed and new ones born .

---

### Post by jerrylamos on 2011-06-04
> **ronacc said:**
> the reason for using an alpha or beta is testing ,so it is rather pointless not to be using the most up to date since old bugs are constantly being squashed and new ones born .
"Most up to date" Alpha 1 was so broken for me I couldn't "use" it.  Applications launcher just crashed, no function, BFB just crashed, ...  I could get Firefox up.

My view the "Alpha 1 date" came up so they swept up whatever was on the floor and put it out usable or not.  The 30 May was more usable than what they used for Alpha.

The Release Notes were useful.

Now 4 June daily build Live I'm using here is crippling along.  The Application launcher did, the BFB applet at top left did. Strange, the applet is not visible but it did work. 

There was the usual crash about Gnome user share.

The usual close - minimize - maximize buttons are missing on Terminal but are present on Firefox.  Alt-F4 usually works on the Terminal session.

The Home Folder launcher did come up 

Workspace Switcher did launch and sort of works.

Anyway there's a chance 4 June is working enough to find some bugs.

So what I do is save a .iso that sort of works in case the next build is DOA (Dead On Arrival).

Jerry

---

### Post by jerrylamos on 2011-06-04
On 4 June daily build booting .iso  directly from hard drive folder "persistent" worked.  I have a 1 GB partition labelled casper-rw.  

Persistent was able to remember I had a terminal session launcher added, screen lock set to off, and also remembered flashplugin for Firefox.

It's got some problems with left-over windows on the screen but I can cope with that.

Why am I bothering with .iso and persistent?  
1. lets me check out the latest daily build.  
2. Much faster than install.  
3. Install on Natty Narwhal was all screwed up for weeks and either didn't work at all or else clobbered the Grub2 boot menu.
4. For the last several releases sooner or later the "dread update" would screw up the install.

Enjoy.

Jerry

---

### Post by ronacc on 2011-06-04
I have an install ( currently NN release updated at rpeo open to OO ) that I update atleast daily with synaptic NOT UM or aptitude . and I test the daily's live from a usb sitck or sometimes burn a cd if the usb method won't work , or a dvd if the image is too big . I get the cd/dvd's at Sams club for 13 or 17 $/100 respectively so thats not too costly .

---

### Post by Starks on 2011-06-04
Until Ambiance GTK3 and Unico are ready, there's no point in trying to coax Unity into working properly.

---

### Post by ronacc on 2011-06-04
I'm using Gnome-shell and classic .

---

### Post by Starks on 2011-06-04
As am I.

Oneiric is not usable otherwise.

---

### Post by seeker5528 on 2011-06-04
> **Starks said:**
> Until Ambiance GTK3 and Unico are ready, there's no point in trying to coax Unity into working properly.

The theme may be a contributing factor, but Unity works fine for me on my home and work systems, the work system using....

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150] (prog-if 00 [VGA controller])
	Subsystem: Connect Components Ltd Radeon 9600 256Mb Primary [17ee:2002]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at d800 [size=256]
	Region 2: Memory at be000000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at dffe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
```

Not sure what the card in my home system is, but I'm pretty sure it's in the R400-R500 range of chipset, don't have R600 or newer in any of my systems. 

Later, Seeker

---

### Post by MacUntu on 2011-06-04
> **Starks said:**
> Until Ambiance GTK3 and Unico are ready, there's no point in trying to coax Unity into working properly.

They aren't finished, but definitely ready for use.

---

### Post by VinDSL on 2011-06-04
> **Starks said:**
> Until Ambiance GTK3 and Unico are ready, there's no point in trying to coax Unity into working properly.
> **MacUntu said:**
> They aren't finished, but definitely ready for usage.
Heh!  My opinion falls in the middle.  :)

GTK3 and Unico are working good enough to give me a taste of things to come, but...

There is a dirth of GTK3 themes and icon sets, so the 'whole thing' is rather exasperating right now.

Oh well, they say patience is a virtue.  Time shall pass - things will get better - and we'll be on the trot...

---

### Post by VinDSL on 2011-06-04
> **ronacc said:**
> I'm using Gnome-shell and classic .

> **Starks said:**
> As am I.
As an aside...

I'm starting to see articles referring to Gnome 2.32 as "retro", not "classic".  LoL!

Just saying...  ;)

---

### Post by ronacc on 2011-06-04
> **VinDSL said:**
> As an aside...

I'm starting to see articles referring to Gnome 2.32 as "retro", not "classic".  LoL!

Just saying...  ;)

a rose by any other name .

---

### Post by VinDSL on 2011-06-04
> **ronacc said:**
> a rose by any other name .
True!  Although...

"Classic" has a whole different connotation than "retro", "vintage", and/or "antique."

Gnome 2 is starting to lose a few petals, me thinks...  ;)

---

### Post by ronacc on 2011-06-04
perhaps but unity still smells like something I don't want growing in my garden .

---

### Post by seeker5528 on 2011-06-04
> **ronacc said:**
> perhaps but unity still smells like something I don't want growing in my garden .

I'm assuming it's something that makes good fertilizer.

Later, Seeker

---

### Post by Hedgehog1 on 2011-06-04
I have loaded 11.10 from the June 4th 'desktop' ISO on one of my two testing partitions.

I did these following things to get mostly-operational:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

I run NVidia on all my systems; so I did this for the restricted driver:

```
sudo jockey-text -e xorg:nvidia_current
```

The 'Applications' icon never populates and disappears in 2D (known issue), so I can only run things I know the CLI command for or already had icons in the launcher.

However Unity 3D seems to more more functional, and the 'Applications' icon works there OK.

[SIZE="3"]**EDIT:** Cool! This works for 11.10 also: [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")[/SIZE]

***The Hedge***

:KS

p.s. for those who use other than NVidia, here is how to load your resticted driver without the GUI:

```
sudo jockey-text -l
```

If it lists any drivers then type

```
sudo jockey-text -e <driver>
```

Change <driver> for the name of the driver jockey gives you. (the bit at the beginning of the line).

---

### Post by cariboo on 2011-06-05
I just used:

```
sudo aptitude install nvidia-current
```

to install the restricted drivers when I found that Unity 2D is broken.

---

### Post by Hedgehog1 on 2011-06-05
> **cariboo907 said:**
> I just used:

```
sudo aptitude install nvidia-current
```

to install the restricted drivers when I found that Unity 2D is broken.

Thanks **cariboo907**!  I will add that to my notes...

I can't believe I forgot that... *Again...*


***The Hedge***

:KS

---

### Post by lucazade on 2011-06-05
> **VinDSL said:**
> Heh!  My opinion falls in the middle.  :)

GTK3 and Unico are working good enough to give me a taste of things to come, but...

There is a dirth of GTK3 themes and icon sets, so the 'whole thing' is rather exasperating right now.

Oh well, they say patience is a virtue.  Time shall pass - things will get better - and we'll be on the trot...

This is the real "taste" at the moment..
The widgetfactory is a gtk2 test app. Test-widget, gnome-panel and nautilus are gtk3.

(yes, there are some details to be refined..but, well, 
this is the result of a week of work and we have more or less 6 months to improve it :) )
 
[[IMG]http://dl.dropbox.com/u/1338581/varie/ambiance-s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/ambiance.png")

PS.. If anyone want to help clone my bzr branch and notify me!

---

