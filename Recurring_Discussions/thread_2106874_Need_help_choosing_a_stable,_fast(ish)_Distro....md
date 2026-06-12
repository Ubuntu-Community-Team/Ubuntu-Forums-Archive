---
title: "Need help choosing a stable, fast(ish) Distro..."
date: 2013-01-20
forum: Recurring Discussions
---

### Post by BigTobster on 2013-01-20
Hi!

Currently using Ubuntu 12.04 but finding it a bit bloated and sluggish on older Hardware (Dual Core 2, 3GB RAM, int graphics). 

Errors drive me mad. As long the software works as it should I really don't care if its not the total latest version. Also, I'm not the world's biggest fan of the command line but I realise that there is no distro you can get away from it completely. I am an intermediate Linuxer.  

I don't mind fiddling with OS during installation but once its done I want to just it without having to spend a few hours configuring every package that I download. 

So... I have identified a few different distros. Some I have used and some I haven't. 

Xubuntu - Possibly with IceWM as an alternative to XFCE. Hear that it is slightly bloated and the Ubuntu packages aren't as stable as would be ideal. Good speed.

FreeBSD - Very different from what I am used to. Some of the ports can be very old. The installation process takes forever! (Personal experience!) Speed is apparently "OK"

Arch - Command line centred so not ideal. I hear some people say its the most stable thing since God and others say that it constantly falls over and its useless. Very fast though. Possibly too much like hard work. 

Debian - Probably as Stable as BSD but also suffers with older packages. I would be more familiar with it though. Speed also found to be "OK"

I'm not really leaning towards anything at the moment. What do you guys think? Any preferences? What do you use and why?

---

### Post by Bucky Ball on 2013-01-20
*Thread moved to **Recurring Discussions***

Try 'em all out. See what suits. That simple. 

Lightweight for old hardware? Lubuntu or Xubuntu. But your hardware is not that old and should be running the current Ubuntu just fine ...

I would advise running them off the disk and trying them out or making a bunch of partitions (possibly logical drives inside and extended partition) and installing then attempting all the variations you suggest. 

Good luck ...

---

### Post by sanderj on 2013-01-20
"Dual Core 2, 3GB RAM, int graphics" doesn't sound bad. It should run Ubuntu 12.04 / 12.10 quite well.

---

### Post by BigTobster on 2013-01-20
In fairness, it doesn't do too badly. However, there are a few (5 or 6) seconds delay when clicking on the launcher button. I'm just looking to trim things like that down to a few seconds.

---

### Post by Version Dependency on 2013-01-20
I would not suggest any rolling release distros (like Arch or Gentoo) if stable is what you want.  There will be breakages with a rolling release model.  Avoid the BSD's too.  Think of them more as server OS's than something you want to live in as a desktop user.

Debian is stable but you are stuck on alot of ancient packages.  Maybe try out Crunchbang if you want a Debian-based lightweight distro...it uses Openbox.   For  something with fresher packages, I'd suggest Lubuntu.  LXDE/openbox is very, very lightweight.  And you have access to all of the (reasonably) fresh packages in the Ubuntu repos.    Stability shouldn't be much of problem with LXDE/openbox.

---

### Post by deadflowr on 2013-01-20
You can try light distros like [bodhi linux ]("http://www.bodhilinux.com/")or [crunchbang]("http://crunchbang.org/").
[Lubuntu]("http://lubuntu.net/") is pretty light, IMHO.

---

### Post by snowpine on 2013-01-20
For absolute stability above all else, you can't go wrong with: Debian, CentOS, Slackware.

For speed, you can't go wrong with any distro, really, so long as you use a lightweight DE such as Xfce or LXDE.

> **BigTobster said:**
> In fairness, it doesn't do too badly. However, there are a few (5 or 6) seconds delay when clicking on the launcher button. I'm just looking to trim things like that down to a few seconds.

For an "apps take too long to load when I launch them issue" I would suspect the bottleneck is loading them from the hard drive, right? One solution would be to put your / ("root") partition on a fast SSD drive, another might be to use "[preload]("http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html")" (which loads your frequently-used apps during system boot, giving the illusion that apps are faster to load).

Also you mention you have (presumably integrated?) Intel graphics. You might have a better experience with Ubuntu's Unity interface if you upgrade to a dedicated graphics card. This will not help specifically with app loading time, but may help with the overall experience of "sluggishness."

---

### Post by sanderj on 2013-01-20
> **BigTobster said:**
> In fairness, it doesn't do too badly. However, there are a few (5 or 6) seconds delay when clicking on the launcher button. I'm just looking to trim things like that down to a few seconds.

I had that with 12.04 too. Using 12.10 solved that irritating delay.

---

### Post by VinDSL on 2013-01-20
> **BigTobster said:**
> What do you guys think? Any preferences? What do you use and why?
I've been using Peppermint OS, for a year or so, on my netbook, on USB-stick installs, et cetera.

It's a Lubuntu fork...

> **BigTobster said:**
> Currently using Ubuntu 12.04 but finding it a bit bloated and sluggish on older Hardware (Dual Core 2, 3GB RAM, int graphics) [...]
You shouldn't have to tap your fingers on the desk, waiting for something to happen!

Peppermint OS is fast, lightweight, no lagginess, stable, and looks great (with some tweaking).

If you go to the Peppermint OS site, don't let the "cloud" talk scare you off.  While it sounds intimidating (like you will need to learn something new) it actually runs like any other Ubu distro -- uses the same PPAs, and so forth, and so on.

Here's a recent screenie of my humble 10-inch netbook install (still tweaking)...


[INDENT]**[COLOR="Sienna"]ASUS Eee PC 1000HD (circa 2009) / Peppermint Two OS (Lubuntu Fork) / Conky 1.8.0 / ConkyWX 0.7.9[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-eeepc-30-dec-2012-1(650x381).png[/IMG]]("http://vindsl.com/images/vindsl-eeepc-30-dec-2012-1.png")[/INDENT]


Check out the RAM usage.

Guayadeque (music player) is using a few CPU cycles, but that's okay...  gotta have tunes.  ;)


Here's a 16 GiB USB-stick install, mounted on a desktop box (still tweaking)...


[INDENT]**[COLOR="Sienna"]Intel P4 Extreme Edition (circa 2005) / Peppermint Two OS (Lubuntu Fork) / Conky 1.9.0 / ConkyWX 0.7.9[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-26-nov-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-nov-2012-2.png")[/INDENT]


Anyway, that's my choice, and my reasoning...  :)

---

### Post by greg_ory on 2013-01-20
Your specification are absolutly fine even for 12.04, what has boosted my laptop with near the same specification was the fact that I exchanged my old HDD with a SSD. You get currently quite good bargins such as:

CRUCIAL M4 SATA III 2.5" SSD - 512 GB for £279.99

There are of course many other tips and tricks you can enhance your performance but I found the new SSD the best solution for me.

-Greg

---

### Post by sidzen on 2013-01-20
All above are sound suggestions and observations. 

It sounds  like performance is a priority.  Same with me.  If so, 64-bit is not necessary.  Neither is a DE any 'heavier' than LXDE.  This narrows it down  a bit (looking for a distro with just a WM or lxde . . . hmmm).

You may also want to look into antiX

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

However,  like CrunchBang 'Statler,' it is a Debian distro and Debian is in transition, waiting for Wheezy to go 'stable,' and sid-based distros are for adventuresome hoppers, so . . .

Slackware-based distros come to mind.  But Salix-lxde is still at 13.37, leaving but ones like [*Slackel-openbox*]("http://www.slackel.gr/")

which is pretty impressive, using Slackware, Salix and its own repos.  Openbox WM is very responsive.  A little Greek pops up in the menu at right-click occassionally, but international symbols and its place on the menu window makes selection of no real concern, if a bit disconcerting at first.  It is available at Sourceforge [**here.**]("http://sourceforge.net/projects/slackel/")

Once again, snowpine and I are of like mind.  12.04.1 fom Italy with e17 is unofficial but very well done is [Salent OS]("http://www.salentos.it/").

---

### Post by BigTobster on 2013-01-20
Thanks for responses. 

Loving CrunchBang although this is perhaps unnecessarily scary? It's based on the super-stable Debian so not sure how far CrunchBang can go wrong???

> CrunchBang Linux is not recommended for anyone needing a stable system or anyone who is not comfortable running into occasional, even frequent breakage. CrunchBang Linux could possibly make your computer go CRUNCH! BANG! Therefore CrunchBang Linux comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
This is from the CrunchBang Wiki

Bodhi looks great. So does PepperMint. I think Lubuntu looks unnecessarily ugly but nothing that tweaking can't solve I'm sure. 

Slack-stuff is very different and quite the learning curve. That's not so bad but non mainstream OS's are a little scary to the relatively uninitiated. 

I already have pre-load but I am currently installing 12.10 so hopefully that will fix the lag issue. 

VinDSL, your set up looks fantastic. Good work :)

I am getting a new machine entirely in a year or so. Changing the drive might be a bit wasteful :)

Lubuntu, Peppermint, Bodhi and CrunchBang all hit the spot. Now to try them...

---

### Post by pissedoffdude on 2013-01-20
Why not give Fuduntu a try?  It still uses Gnome 2, which runs like a dream on older computers.  Plus you get basically all you need to be up and running pre-installed.

---

### Post by BigTobster on 2013-01-21
Liking Fubuntu too. Looks a touch bloated though? (Just from what I have seen on the website)

Update on the Launcher Lag issue: 

Upgrade to Ubuntu 12.10 does indeed solve the problem. Boot is a bit slower but that is preferable.

---

### Post by snowpine on 2013-01-21
> **BigTobster said:**
> Looks a touch bloated though? (Just from what I have seen on the website)

What do you mean?

---

### Post by Cheesemill on 2013-01-21
> **BigTobster said:**
> Loving CrunchBang although this is perhaps unnecessarily scary? It's based on the super-stable Debian so not sure how far CrunchBang can go wrong???

This is from the CrunchBang Wiki
> CrunchBang Linux is not recommended for anyone needing a stable system  or anyone who is not comfortable running into occasional, even frequent  breakage. CrunchBang Linux could possibly make your computer go CRUNCH!  BANG! Therefore CrunchBang Linux comes with ABSOLUTELY NO WARRANTY, to  the extent permitted by applicable law.

I would say the warning is unnecessarily scary.

I've been using CrunchBang for years without any issues. I believe that Corenominal is just covering himself as he is the only person developing the distro.

---

### Post by Mikeb85 on 2013-01-21
openSUSE, if you're worried about having a light DE then go with Xfce or openbox.  I personally find SUSE is alot quicker than Ubuntu, it's very customizable, but still has alot of the same conveniences.  It does have a few quirks, but it's also very stable (and fast).

---

### Post by Warren Hill on 2013-01-21
Ubuntu 12.04 and 12.10 are a bit slow when using the default Unity desktop but there are other desktops.

Try the classic desktop

```
sudo apt-get install -y gnome-session-fallback
```
Log out and back in again selecting "Gnome Classic (No Effects)" as the desktop. 

Or take a look at Lubuntu/Xubuntu

---

### Post by BigTobster on 2013-01-21
> Our platform includes a classic desktop experience using GNOME 2, and we provide many software packages important to our users such as Netflix and Steam which are available for installation from our software repository.

SnowPine - Gnome rather than a lighter DE and advertising sexy packages is common with the bigger Distros. Seriously though, I know nothing about this distro :) Just a totally random thought just from the Website page :) I bow to anyone's recommendation. 

In regards to CrunchBang - I think you got the nail on the head there CheeseMill. Fair-play to Corenomial. 

The learning curve with Suse always seems like a lot of fun but a lot of time-consuming confusion! I definitely want to give OpenSuse a go but I really need something that I know quite well (for University). I am going to put OpenSuse on the list of Distros to spend some real time on getting to know and learn. I hear many good things :)

I actually like Unity btw! I think its great as an interface its just a bit sluggish without better hardware. Thanks for the tip Warren but I think I'm going to change OS during the week so not worth the fiddling :)

---

### Post by pissedoffdude on 2013-01-21
> **BigTobster said:**
> Liking Fubuntu too. Looks a touch bloated though? (Just from what I have seen on the website)



Actually it's super quick, even with compiz enabled.  It makes you realize how quick Gnome 2 used to be.

---

### Post by snowpine on 2013-01-21
+1, I remember running Gnome 2 distros on old Pentium 3's and 4's back in its heyday.

---

### Post by Marzata on 2013-01-27
Xubuntu is very stable and very good!

---

### Post by santosh83 on 2013-01-28
> **snowpine said:**
> +1, I remember running Gnome 2 distros on old Pentium 3's and 4's back in its heyday.

My very first Linux experience was with Linux Mandrake from the then company Mandrakesoft, featuring GNOME 1.1.

It was beautiful and had a certain charm you'll never get again!

I might just try it again in VirtualBox just for the Nostalgia. :-)

---

### Post by houseworkshy on 2013-01-31
One doesn't have to stick with the big names have a good browse on distro watch.  
For stable no fuss desktop Mepris which is based on stable debian is really swift on my 1.8g machine. The same team do a lighter version called antix 
For lightweight slitaz is amazingly good, very much lower on system resources and far faster than the usuall xfce or lxde buntu's that usually get recommended.  Seems well supported too, or has been for the last few years.  If you want consistancy over a large number of machines of various ages which can be relied on for years not to upgrade beyond the abilities of the least powerful machine in the pack, as the op does, I'd definately recommend slitaz.

---

### Post by Mikeb85 on 2013-02-01
I'm currently (and most likely permanently) on openSUSE 12.2 Gnome.  I was getting poor wireless performance in Ubuntu (Intel Wireless, I was using 3.7.5 kernel), the bootloader and file system kept messing up, and switching to SUSE solved all those problems, and it's a heck of a lot quicker too.  With the Amazon annoyances, and the general lack of stability and quality of Ubuntu, I think I'll likely stick with openSUSE.  I like Unity, I like Mark Shuttleworth's vision, but I can't deal with everything breaking.  As a bonus, I much prefer Zypper to app-get and dpkg...

---

### Post by cg40k on 2013-02-01
Lubuntu is a great choice for speed.

But a personal favorite of mine is PeppermintOS. A great light distro. Give it a try.

---

### Post by joemartin on 2013-02-02
I highly recommend Xubuntu 12.04 in every way.

I have never been a Ubuntu fanboy and have hopped for several years.  Xubuntu brings all the benefits that go along with Ubuntu  but runs with the stability and speed you love with the XFCE environment.  IMHO, Xubuntu far surpasses LXDE distro's in stability and has greater ability to be customized.   Xubuntu also has LTS support that goes with 12.04. 

If you (like me) grew weary of Unity shortcomings, the bugginess of Cinnamon and did not want the bloat of KDE, Xubuntu may be for you too.

---

### Post by Max Blyss on 2013-02-03
Xubuntu 
Crunchbang
Racy Puppy

---

### Post by NobleYorkshire on 2013-02-04
I use Lubuntu 12.10.  Works nicely, seems lightweight.

---

