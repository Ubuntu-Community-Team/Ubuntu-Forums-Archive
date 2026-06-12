---
title: "Daily ISO Updates vs Running Update Manager Daily"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Ub11 on 2011-06-24
I want to run/test the latest version of Oneiric everyday.

Do I need to download the new ISO image everyday (With zsync to speed things up a bit) and run a new Live Session test with the updated ISO image

OR

can I use an ISO image for a specific day and create a USB image with a persistence folder and just run Update Manager everyday during a Live Session test to get the latest updates for the day from the repositories?

Please explain the difference, if any, between the two approaches.

Thanks.

---

### Post by jerrylamos on 2011-06-24
Update might work for a few days.  Alpha 2 is to come out June 30.  My experience, maybe 2 to 4 days later zsync the daily build and do another install, in another partition.

There are those who claim updates will do it, but I've run updates vs. a new install "side by side" and when there is something like Alpha 1 or Alpha 2 or Alpha 3 or Beta available, it pays me to try an install in a different partition and compare the two.

Also early in the development cycle the "dread update" will unexpectedly appear and kill the ubuntu.  This was very rough in Natty where for nearly two months "install" was busted.  Oneiric has been better behaved likely because Unity is more developed.

Anyway, with development code, back up often and expect to do installs.

Jerry

---

### Post by VinDSL on 2011-06-25
I run the Daily Builds, during the Alpha(s) stage.  And, I do a fresh install every 24 hours.

Things generally stabilize around Alpha-2 / Beta-1.  After that, I just do updates - several times a day.

Personally, I NEVER use the Update Manager. Ranch Hand calls it "Update Mangler".  Enough said?!?!?

IMO, Synaptic (gui) and apt-get (cli) are the way(s) to go.

I use to download entire ISOs and burn them coasters - been doing it that way for years.  However...

Last week, they made it possible to burn ISOs directly to Flash devices, soooo that's what I'm doing now - zsync the Daily Build ISO and burn it to a thumb drive using DD.

Bada bing, bada boom.  Best invention since water!  ;)

---

### Post by Ub11 on 2011-06-25
> **jerrylamos said:**
> Update might work for a few days.  Alpha 2 is to come out June 30.  My experience, maybe 2 to 4 days later zsync the daily build and do another install, in another partition.

Jerry

Thanks for your advice.

The MAJOR problem for me was downloading the complete ISO image every day. With a rather slow Internet link, this is impractical.

Both Update Manager and zsync now allows me to only download the updated code, which seems to be around 120MB a day on average, rather than the full 700MB ISO image.

Based on your advice, I shall follow the zsync method to update the ISO image and re-install, rather than just running Update Manager.

---

### Post by JRV on 2011-06-25
I broke it.

Time for a zsync, reinstall.

---

### Post by VinDSL on 2011-06-25
> **jarryslink said:**
> So, back-up your data in any event.
Good point!

A should have mentioned...

I run a separate /home partition, and I NEVER format it.  IMO, this is paramount!  Basically, it's a Lazy Man's Backup.  :D

For the most part, I could care less about anything in root (except /home).

When I do a fresh install of a Daily Build, I have the installer format the / partition (root). NOT formatting it is asking for trouble.

Then, I direct the installer to use my existing /home partition, but DO NOT format it.  This will generate a warning dialogue, but you can ignore it (e.g. "Continue" the install).

When everything is said n' done, all of my important data is still there - local config files, pics, docs, notes, downloads, blah, blah, blah.

If I couldn't easily "backup" my /home partition, I'd find another hobby.  Installing Daily Builds would be too exasperating.  And, maintaing a separate /home partition is the easiest and fastest method that I'm aware of...  ;)

---

### Post by el_koraco on 2011-06-25
> **VinDSL said:**
> And, maintaing a separate /home partition is the easiest and fastest method that I'm aware of...  ;)

Until Ubiquity formats it. Like on my last **stable** release install of Natty. 

OP, although it's not exactly Ubuntu policy, you might prefer the apt-get (not aptitude, it's too "smart" for dev releases) method for updating. And check to see if apt is offering to remove half of your install while it's upgrading. 

You can also run upgrades with the simulate switch. 

```
sudo apt-get update
sudo apt-get dist-upgrade --simulate

```

This will just show you what it's doing and won't actually do it.

---

### Post by sparker256 on 2011-06-25
Have been using my routine for three of four cycles and seems to work for me.

 A separate /root and /home partition is a must when doing this kind of testing.

I also use zsync to keep a couple of different days of daily builds encase the current daily build has a problem.

I use startup disk creator to make live usb from the daily builds and give myself 2G of persistence on my 8G thumb drives. This allows me to install a driver or updates,

I only reinstall if I have no other choice. I use aptitude to update as often as needed. The command I use to update is.
```

sudo aptitude update && sudo aptitude safe-upgrade

```  
 This has forced me to fix a problem instead of just reinstalling. My thanks to all on the forum who have helped in the process.

Bill

---

### Post by VinDSL on 2011-06-25
> **el_koraco said:**
> [...] you might prefer the apt-get (not aptitude, it's too "smart" for dev releases) [...]
Man, isn't that the truth!?!?!?!  :D

I converse with some movers n' shakers in other forums - died in the wool, hardcore, Debian users, e.g. industry professionals.  You know the type, right?

If you mention anything other than Debian and Aptitude, it's like you're spitting in their virtual faces... but, I tried Aptitude on Ubu for awhile.

OMG!!!  Aptitude is like a Pitbull on a bone.  It just won't let you get away with any non-sense.  It'll rip the arms off your dev release, if you aren't careful.

Anyway, I agree with you.  Aptitude is too fastidious for dev duties.   ;)

---

### Post by julianb on 2011-06-25
re: using zsync and then re-installing...

yes you can do that... there's another option too:

put the ISO on your hard drive, zsync it every day, and run Ubuntu directly from the ISO rather than installing. (of course, if you want to install packages to your hard drive, that method won't work).

---

### Post by VinDSL on 2011-06-25
> **sparker256 said:**
> I use aptitude to update as often as needed. [...]
Oh, swell... stuck my foot in my mouth again.  :D

We must have typing at the same time.

No offense intended, Bill, with what I said above.  It wasn't directed at anyone in particular.

I just haven't had a good experience with Aptitude, that's all...  ;)

---

### Post by sparker256 on 2011-06-25
> **VinDSL said:**
> Oh, swell... stuck my foot in my mouth again.  :D

We must have typing at the same time.

No offense intended, Bill, with what I said above.  It wasn't directed at anyone in particular.

I just haven't had a good experience with Aptitude, that's all...  ;)
No offense taken I was just stating what worked for me and I have learned that we all have different way of getting to the same place. 

Bill

---

### Post by el_koraco on 2011-06-25
> **VinDSL said:**
> Man, isn't that the truth!?!?!?!  :D


Aptitude is ok for Debian stable releases, or Debian Testing. But even the Debian Way points to something like - when in doubt, use apt. Even in the early days of stable Ubuntu releases, with regular changes to the repos, the poor thing can get confused. Kinda like Update Mangler with its partial upgrades. Mind you, apt had a tendency to remove half of KDE in the final days of the last Kubuntu dev cycle.

---

### Post by el_koraco on 2011-06-25
> **sparker256 said:**
> No offense taken I was just stating what worked for me and I have learned that we all have different way of getting to the same place. 

Bill

You're walking a fine line :D

---

### Post by seeker5528 on 2011-06-27
> **el_koraco said:**
> Aptitude is ok for Debian stable releases, or Debian Testing.

Aptitude is good if you only ever use aptitude. If you use other stuff to install packages, then aptitude becomes a PITA.

Even if you only ever use aptitude, you may have to force it to see things your way relative to it's brain dam ...er... removal of "no longer needed" packages. :P

Later, Seeker

---

### Post by jerrylamos on 2011-06-28
> **seeker5528 said:**
> Aptitude is good if you only ever use aptitude. If you use other stuff to install packages, then aptitude becomes a PITA.

Even if you only ever use aptitude, you may have to force it to see things your way relative to it's brain dam ...er... removal of "no longer needed" packages. :P

Later, Seeker

apt-get update, apt-get upgrade has screwed me royally since it is quite happy to load half baked unfinished packages.

I've had better luck with aptitude update, aptitude safe-upgrade.

Now on this thread topic, I do both.  I have installs on a couple of USB hard drives and boot the .iso from a folder on the hard drive.  If the .iso seems to work O.K. I do an update.  Do note that the Daily Builds are not quite up to date......

The USB hard drives are cheap for me.  I had a couple spare laptop drives, and the two cases cost $10 and $20.  

I have been trashed by development level ubiquity installs over the years.  I do gparted to set up the partitions since it at least shows me partition labels, and try to be careful on the ubiquity install formats.  Now the grub menus do get fouled up royally but I've been able to find at least one existing partition that worked to do a grub-install.

Somebody else can test ubiquity install's inability to handle partitions.

Jerry

---

### Post by fjgaude on 2011-06-28
For the last five days I've been updating twice a day after installing a daily into VMware Player... works great, but only using Unity 2D.

---

### Post by jerrylamos on 2011-06-29
> **fjgaude said:**
> For the last five days I've been updating twice a day after installing a daily into VMware Player... works great, but only using Unity 2D.
Unity 2D is my preferred even though three of my four test pc's will run 3D.  No added function for what I do, and historically "Compiz" has been full of bugs besides soaking up 5%+/- processor cycles even when I'm running full screen apps and there is nothing that Compiz does that's even visible.

So far I've got choices with Unity 3D and Unity 2D.  I would like a choice without all the screen gobbling icons, similar to old classic, with sorted lists of text.  I can read.  The "pictographs" don't do a thing for me functionally.

Jerry

---

### Post by fjgaude on 2011-06-29
My main box is so fast Compiz is a non-issue, but I can see it being otherwise for netbooks and the like.

Touch screens are being pointed to by Ubuntu, coming one of these days, but hopefully we will always have something different for big desktops.

I sorta like the icons, reduced to 32 pixels. <smile>

---

### Post by julianb on 2011-06-29
> Touch screens are being pointed to by Ubuntu, coming one of these days, but hopefully we will always have something different for big desktops.

Presently there are a few choices that serve the "big desktops" need well. Seems like people don't really like Unity and Gnome-shell for big screen desktop machines, but the latest releases of Kubuntu as well as the GNOME2 disros seem to fill that need pretty well. (consider Mint, Ubuntu Lucid, Debian Squeeze).

As time goes on, I suspect KDE and Xfce will very effectively meet the needs of people who liked GNOME2 and don't want to use GNOME3 or Unity. 

I think Unity's cool except that performance-wise it didn't compare well to Lubuntu/Kubuntu/Xubuntu. I currently use Lubuntu Oneiric, but I think I will switch to Xfce or KDE to get some of the functionality I'm looking for.

---

### Post by fjgaude on 2011-06-29
I like Unity, don't get me wrong... it has made my work flow go smoothly, better than gnome shell or other DMs I've tried.

I can't imagine using a touch screen for graphic design work, but the way 11.04, and likely 11.10, is is fine with me.

---

### Post by cariboo on 2011-06-29
Unity was never designed for use with a touch screen. I'm trying to find the post, someone tried it, and said Unity+touch screen was worse than WIndows 7+touch screen.

I've tried Windows 7 on a touch screen, it's a fun toy, but it's pretty well useless for getting things done.

---

### Post by lucazade on 2011-06-29
> **cariboo907 said:**
> Unity was never designed for use with a touch screen. I'm trying to find the post, someone tried it, and said Unity+touch screen was worse than WIndows 7+touch screen.

I've tried Windows 7 on a touch screen, it's a fun toy, but it's pretty well useless for getting things done.

What a pity, it was a good opportunity to make a touch-friendly interface.
Hope there is room for improvements in this area. 
Win7 touch device I tried seemed enough responsive and well supported but haven't tested so long.

---

### Post by seeker5528 on 2011-06-29
> **jerrylamos said:**
> apt-get update, apt-get upgrade has screwed me royally since it is quite happy to load half baked unfinished packages.

Loading 'half baked unfinished packages' is going to have issues no matter what front end you use.

> I've had better luck with aptitude update, aptitude safe-upgrade. 

Aptitude always wants to remove stuff I want to keep, so I never really used it on an ongoing basis. The Debian user mailing list has had lots of posts from people who had issues resulting from the way aptitude works.

Theoretically, anything 'apt-get upgrade' would install, 'aptitude safe-upgrade' should also install, aptitude also has an additional list of "safe" things on top of that, which would probably typically be safe during a stable release cycle, but may not be as safe during a development release. Don't know if the additional list of safe things really makes any difference in the real world.

Later, Seeker

---

### Post by el_koraco on 2011-06-29
> **cariboo907 said:**
> Unity was never designed for use with a touch screen.

There's an article on OMGUbuntu with a video link to Unity on a tablet. Looks pretty nice.

---

### Post by cariboo on 2011-06-30
> **el_koraco said:**
> There's an article on OMGUbuntu with a video link to Unity on a tablet. Looks pretty nice.

That was on the mutter version of Unity, 2 versions ago, as far as I have been able to find out, there really isn't any work going on, on a touch interface.

Just to keep on topic, I'm running what started out as alpha 1 on this system, with updates twice a day, there have been a few problems along the way, but checking here, there has always been a fix available.

---

### Post by mc4man on 2011-06-30
A fresh install is obviously going to be more reflective of the current state than an older one updated.
Just like in natty there can be differences between the 2, for better or worse.
A few Ex. - 
On a just before A1 updated - 
gksudo nautilus works fine
systray icons work and display properly
update manager is dead and buried
vlc works fine
attempts to create a new user fail to create /home/<newuser>

On todays iso
gksudo nautilus is completely broken
systray icons work but display garbage icon
update manager is fine
vlc works but opening tools > preferences locks up everything
A new user can be created and logged into, the new user's terminal is borked

I'm sure there are more...
So what's a bug and what's just an (un)fortunate state is hard to tell, I don't expect much consistency until A2 at the least

---

### Post by VinDSL on 2011-06-30
> **cariboo907 said:**
> Unity was never designed for use with a touch screen.[...]
That surprises me.


I suppose everyone has seen this video by now, but in case not...

[INDENT][http://blip.tv/ubuntu-developers/utouch-on-unity-4264171](http://blip.tv/ubuntu-developers/utouch-on-unity-4264171)  (uTouch on Ubuntu Unity)[/INDENT]


I assumed the devs designed this on purpose...  :)

---

### Post by VinDSL on 2011-06-30
> **cariboo907 said:**
> **[COLOR="Red"]That was on the mutter version of Unity, 2 versions ago[/COLOR]**, as far as I have been able to find out, there really isn't any work going on, on a touch interface.[...]

Oops!

I should have kept reading.

Thanks for the explanation...  :)

> **cariboo907 said:**
> Just to keep on topic, I'm running what started out as alpha 1 on this system, **[COLOR="Red"]with updates twice a day[/COLOR]**, there have been a few problems along the way, but checking here, there has always been a fix available.
Yes, back on topic...


Here's something I *think* we can all agree on:

[INDENT][http://blip.tv/ubuntu-developers/ubuntu-uds-o-budapest-reducing-number-of-patches-in-our-packages-5294090](http://blip.tv/ubuntu-developers/ubuntu-uds-o-budapest-reducing-number-of-patches-in-our-packages-5294090)  (Ubuntu UDS O Budapest - reducing number of patches in our packages)[/INDENT]


I probably update my install 10 times a day.  But, is it necessary and/or even desirable?!?!?

Personally, my attitude is... bring 'em on.  However...

I think these incessant patches and updates are starting to wear on users.

At some point - in some ppl's opinion - Ubuntu needs to switch to a (ahem) Microsoft [Patch Tuesday]("http://en.wikipedia.org/wiki/Patch_Tuesday") Model.

The jury is still out of this idea, but it's interesting to see the devs grapple with the problem, no?!?!?

---

### Post by el_koraco on 2011-06-30
> **cariboo907 said:**
> That was on the mutter version of Unity, 2 versions ago

They say it's Natty - [link]("http://www.omgubuntu.co.uk/2011/06/ekoore-announce-two-new-tablets-running-ubuntu-11-04/")

Mutter doesn't have wobbly windows and the shift switch cover preview. And the thing is looking pretty sweet, maybe a little bulky, but more suited for multitasking than your regular tablet interface. 

I'm guessing a good area to target are gonna be those combo netbook-tablet things, like the Asus Transformer, they seem like they're gonna be the bomb in a couple of years.

---

### Post by fjgaude on 2011-06-30
> **el_koraco said:**
> They say it's Natty - [link]("http://www.omgubuntu.co.uk/2011/06/ekoore-announce-two-new-tablets-running-ubuntu-11-04/")

Mutter doesn't have wobbly windows and the shift switch cover preview. And the thing is looking pretty sweet, maybe a little bulky, but more suited for multitasking than your regular tablet interface. 

I'm guessing a good area to target are gonna be those combo netbook-tablet things, like the Asus Transformer, they seem like they're gonna be the bomb in a couple of years.

From all the articles from Shuttleworth I would say the tablet is his goal, but still retaining server and desktops.

---

### Post by cariboo on 2011-06-30
At this point in time, I think Canonical is more than happy to let third parties, do the work on touch screens.

---

### Post by ranch hand on 2011-07-01
I would like to know what, if not intended for touch screens, it was designed for.

Monster icons that cover the screen have only one use and that is touch screens.  Anywhere else they are nothing but extremely stupid.

---

### Post by cariboo on 2011-07-01
ranch hand you're behind the curve, large icons are no longer a problem, I think it was a design decision that didn't work the way the designers expected. Unity can now be customized a lot more than during the natty testing session using compizconfig-settings-manager.

Unity was developed, because at the end of the Maverick design cycle Canonical wasn't sure if Gnome could deliver gnome-shell on time, as well as political problems between the two. At one point the mockups of Gnome-shell looked quite a bit like Unity. Now though gnome-shell looks quite a bit different

---

### Post by wildmanne39 on 2011-07-01
Hi, I must say running the test version is never boring.

---

### Post by VinDSL on 2011-07-02
> **wildmanne39 said:**
> I must say running the test version is never boring.
Nor, the testers...  :D

---

### Post by el_koraco on 2011-07-02
> **ranch hand said:**
> I would like to know what, if not intended for touch screens, it was designed for.

Monster icons that cover the screen have only one use and that is touch screens.  Anywhere else they are nothing but extremely stupid.

You obviously haven't seen the videos of Gnome Shell on a touch device. You can see that a lot more effort has gone into making Shell touch device ready than it is the case with Unity. Unity has some elements that can be effectively used on a touch device, but the whole "metaphor" is much more suited for netbooks and laptops, meaning the whole uTouch technology is much more geared towards touch - and trackpads than regular touch screen devices.

---

### Post by jerrylamos on 2011-07-02
> **wildmanne39 said:**
> Hi, I must say running the test version is never boring.
I'll say!  Oneiric amd64 grub2 update-grub on a USB hard drive just sudsed the hard drive on this notebook!

I don't know yet whether it just screwed the master boot record or the partition table or both.  This is the first such disaster for me since 2006 running shaky development Ubuntu's.  Guess I'll research the forums since I've seen other people report on such problems.  I do have the massive 5 DVD Windoze7 backup I made originally, however that may be used. 

So, running Oneiric updated from the USB hard drive, the daily updates have NOT fixed the top panel which is missing applets.  A fresh install from daily build on another notebook has correct top panel.

Jerry

---

### Post by fjgaude on 2011-07-02
> So, running Oneiric updated from the USB hard drive, the daily updates have NOT fixed the top panel which is missing applets. A fresh install from daily build on another notebook has correct top panel.

Well, things are good here. With the grub iso the daily has been perfect for two or three days... full system with the panel having what it should.

The VM has been updated many times each day without issue, but of course it is only Unity 2D, the grub iso is 3D. I don't use persistent with the grub iso like you do.

---

