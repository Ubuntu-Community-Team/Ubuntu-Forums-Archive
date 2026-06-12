---
title: "What are the differences between Ubuntu and Debian?"
date: 2011-03-26
forum: Recurring Discussions
---

### Post by Linux_junkie on 2011-03-26
Hi guys,
 
I would like to know what, if any, are the main differences between Ubuntu and Debian distributions.
 
I know that Ubuntu release a new version every six months and that Debian release a new version approx. every five years.  What I would like to know is what are the advantages of using Debian over Ubuntu or vice versa?
 
I'm currently using Lucid Lynx version of Ubuntu but am thinking of changing to Debian 6 (squeeze).

---

### Post by NightwishFan on 2011-03-26
Well Debian release cycles are stabilised to more like two years now instead of "when it is ready".

Well the main difference is philosophy. I actually tend to favour the way Debian does things though generally the amount of great defaults and engineering in Ubuntu does help a lot.

Perhaps try an install in virtualbox before you try it on real hardware.

This page is useful:
[http://www.debian.org/doc/](http://www.debian.org/doc/)

---

### Post by CharlesA on 2011-03-26
There isn't all that much difference between the two.

Just remember that even if you test it in a virtual machine, nothing beats trying it on the hardware you are going to be using.

---

### Post by boydrice on 2011-03-26
Debian is more focused on free software in the FSF view, so no firmware blobs in the kernel etc.  Debian ships software closer to how upstream intended it, more vanilla less customized.  Debian supports more platforms and a whole different kernel.  Debian is more akin to an enterprise class distro like centOS, RHEL, Scientific Linux, as it is a great server OS that is very stable and conservative but can be made into a great desktop/workstation.  Debian doesn't split other desktops into separate distros so there are install CDs for KDE, Xfce, GNOME, and LXDE.  Debian as a distro doesn't hold your hand or do much for you, it leaves a lot up to the user (not as much as Arch, Gentoo, Slackware, but more than Ubuntu).  Debian in my experience runs faster than Ubuntu on comparable hardware.

---

### Post by Sean Moran on 2011-03-26
Debian is like a Chevrolet.  Ubuntu is more like a Pontiac.

---

### Post by Random_Dude on 2011-03-26
I'm also gaining an interest on Debian.
I've got an old computer that I would like to make my test machine (so I can play around with different distros when I'm bored).

Does Debian come with a default environment and window manager installed? Since it's an old computer I was planing on running only Openbox on it.

Are the repositories updated? For example, can I get the new version of the kernel, firefox, latest software updates, etc...

Does it have synaptic?

Ubuntu is the only distro that I've used for a considerable amount of time, is Debian too hard for me to try out?

Cheers :cool:

---

### Post by Sean Moran on 2011-03-26
> **Random_Dude said:**
> I'm also gaining an interest on Debian.
I've got an old computer that I would like to make my test machine (so I can play around with different distros when I'm bored).

Does Debian come with a default environment and window manager installed? Since it's an old computer I was planing on running only Openbox on it.

Are the repositories updated? For example, can I get the new version of the kernel, firefox, latest software updates, etc...

Does it have synaptic?

Ubuntu is the only distro that I've used for a considerable amount of time, is Debian too hard for me to try out?

Cheers :cool:

I don't use Debian so I can't claim expertise, although I've tried out a few debian distros without looking into the depth of them.  The only suiggestion is to start with dpkg.  dpkg -i is the one to install, and if you try somethng like **dpkg -i synaptic** it might prove successful, depending on the repos you're running.  I can't test it out from here because I'm not running debian, but the fundamental package manager is dpkg.

Like apt-get install, use dpkg -i for debian and debian will understand.  If synaptic isn't part of the repos, you should at least be able to find apt-get or aptitude.  I'm not sure on the debian repos.

---

### Post by Ibidem on 2011-03-26
Too hard?  How long have you used Ubuntu? Do you know the command line, and can you change config files by hand in nano/vi if things break?
Firefox is not available in Debian: Iceweasel is the equivalent.
The default will depend on how you install.  The official CDs give gnome, but if you want Openbox, I'd try the LXDE blend.  A net install has no window manager or X server.
Debian has Synaptic, Aptitude (both curses and gtk, both being much better than Synaptic IMHO), and several other package managers (such as Wajig).  I believe Aptitude is the official one.
If you want the latest whatever, DO NOT USE DEBIAN STABLE. 
Debian stable is stable as in "will not change at all, short of packages that **might** be updated in a couple months to the version that's being added to unstable now, IF it fixes a reported bug AND it is just a minor change."  
Debian Sid is the closest to what ordinary Ubuntu is based on; it regularly updates, but always breaks something.  LTS versions of Ubuntu come from unstable (10.04==Squeeze codebase, minus the last changes).
Experimental is a repository to add to Sid, more current, always broken.
Unstable is supposed to update from Sid when the packages are fixed.  It doesn't always work that way, and is always a little behind upstream.

---

### Post by NightwishFan on 2011-03-26
Alright I was hoping to avoid this but I might as well give a quick run through. :)

Ubuntu and Debian are largely similar. Even the default selection of packages on Ubuntu 10.10 and Debian 6 are similar. In my humble opinion Ubuntu actually has a trimmer (but more wise and well rounded) selection as it is designed to fit on one CD. Debian's full Gnome Desktop requires about 1.1gb compressed to a live image. I do give points to Ubuntu on this one.

Installing Debian is not hard. The main difference is Debian has a few more steps, but it is mostly the same questions as the Ubuntu installer. I actually recommend new users try the Debian 6 live CD/USB instead of the "by package" installer. The setup steps are the same but the system installs to a working form in under 5 minutes. I give points to Debian for flexibility as they make it easy to obtain an image with XFCE, LXDE, etc.
[Debian Live CD/USB]("http://www.debian.org/CD/live/")

Once you get into the system (I will use Gnome as an example). You will find a mostly familiar environment (only lacking a few configuration utilities such as computer janitor and the hardware drivers and language tool). Debian 6 actually includes the Software Center though.

One major change you have to contend with is that Debian uses su instead of sudo by default. You CAN set it up to use sudo quite easily or by default (just leave your root password blank in the installer). However the create user utility does not seem to automatically grant users the ability to be sudo, so you still have to set it up manually (for new users) regardless. I advice you just learn to use su, gksu. (or just run the handy "root terminal" in the menu).
[Sudo in Debian]("http://wiki.debian.org/sudo")

The only thing the keeps me with an Ubuntu CD around is that Debian often makes things harder than they need to be. For example, if you install compiz, to a new user it is not apparent how to enable it as there is no gui. After you figure out how to enable it, you notice you do not have window decorations because you have no plugins enabled by default. (Just install ccsm and enable the plugins and then re-enable compiz, and add it to the startup applications). To be honest, I do not mind, however in some corner cases you will run into situations like this that Ubuntu makes much much easier. Also note that some packages that you are used to being set up by default on Ubuntu (like plymouth) require manual set up.

It does lack the engineering of Canonical in some areas such as the pulseaudio server being set up right, and apparmor and the profiles from Ubuntu. Even skilled users miss this stuff and rue setting it up themselves. 9/10 packages on the system have sane defaults though, so try not to be too discouraged by this.

On to the good stuff. Speed. Debian seems like everything is compiled/set up to be slightly more conservative. I am unable to confirm this but it really shines on older hardware. Not as much as people tout it to be but it is a shade smoother under trouble. I would say the difference is as little as 5-10% lighter than Ubuntu though.

Universal OS. Debian does not really seem to be as "gnome biased" as Ubuntu. Or does it strictly rely on packages like plymouth (even though plymouth is available). Just makes everything seem more neat and flexible. Also the installer images are flexible as well (boot with desktop=xfce to install xfce system). There is also a really cool multi-arch DVD that has Gnome, KDE, Xfce, LXDE, and some server packages for both 32-bit and 64-bit + the source code. Rounds out to a nice 4.4gb.
[Debian Official Multi-Arch DVD Torrent]("http://cdimage.debian.org/debian-cd/6.0.1a/multi-arch/bt-dvd/")

Even though it is not completely endorsed by the FSF, Debian is highly committed to being open and free. It does not hide problems and all development is visible to the public. It also has a strong focus on using open source where possible (even though it includes non-free firmware and etc in the repos). You can easily get a system that is Stallman friendly even though the Debian project itself is not fully free in their eye.

[QUOTE="Free Software Foundation"]Debian's Social Contract does say that all software in the main distribution will be free software. However, Debian also provides a repository of nonfree software. According to the project, this software is “not part of the Debian system.” We understand that's important for organizational reasons, but users would be hard-pressed to make a distinction. The repository is hosted on many of the project's main servers, and people can readily learn about software available through it by browsing Debian's online package database. This does too much to steer users towards proprietary software for us to endorse it.

Previous releases of Debian also included nonfree blobs with the kernel Linux. Starting with the release of Debian 6.0 (“squeeze”) in February 2011, these blobs have been moved out of the main distribution to separate packages in the nonfree repository.[/QUOTE]

The flexible releases. (Note I do not describe something being release quality or more bug free as "stable" only something that changes as little as possible.) I prefer Ubuntu's model slightly more at times though Debian Stable is always "released as working" and not just long time supported like the Ubuntu LTS. (Not that the LTS is not high quality, just Debian is really focused on it working right). If you like newer stuff, just change your sources to say "testing" instead of "stable" and run apt-get dist-upgrade as root, and you are running the newest stuff, and it will constantly upgrade.
[What Debian is right for me?]("http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html")

Debian is not as popular as Ubuntu but it does not lack devoted users and developers. Some of which are also Ubuntu developers. Some Debian devs are moving to make Debian work a lot closer with derivatives like Ubuntu as well. This link shows a lot of the recent work: [http://www.omgubuntu.co.uk/?s=debian](http://www.omgubuntu.co.uk/?s=debian)

To learn more just check out the Debian web page. The bottom line is, if you know your way around an Ubuntu system (apt-get, sources.lst etc) then Debian should work fine. There is nothing a post to the mailing list or a quick search will not solve for you.
[Debian Support]("http://www.debian.org/support")

---

### Post by PhilGil on 2011-03-26
> **Random_Dude said:**
> IAre the repositories updated? For example, can I get the new version of the kernel, firefox, latest software updates, etc...
Be aware that Debian offers three different versions: Stable, Testing and Unstable. Which you choose to install will depend on your tolerance for breakage and your desire for the newest packages. Debian stable is much like an Ubuntu LTS version, so you'll typically only see security updates. Testing and Unstable do offer new versions of packages.

There is also a backports repository for Stable and some repositories maintained by third parties. However, there's nothing like the ecosystem of repositories available for Ubuntu.

> **Random_Dude said:**
> IDoes it have synaptic?
Yes, I think it's installed by default in Squeeze.

> **Random_Dude said:**
> IUbuntu is the only distro that I've used for a considerable amount of time, is Debian too hard for me to try out?Probably depends on how much you've poked around under the hood in Ubuntu, there's not much difference between the two once you strip off the top layer. I didn't find the transition from Ubuntu to Squeeze too difficult. The conventional wisdom that Debian is too hard for the average user is mostly a myth.

---

### Post by PhilGil on 2011-03-26
> **NightwishFan said:**
> On to the good stuff. Speed. Debian seems like everything is compiled/set up to be slightly more conservative. I am unable to confirm this but it really shines on older hardware. Not as much as people tout it to be but it is a shade smoother under trouble. I would say the difference is as little as 5-10% lighter than Ubuntu though.

I run Debian Squeeze (Stable) on a couple of old Dell P4's with 512mb of system RAM. They idle at 105-110 MB of RAM with a full Gnome desktop installed and are reasonably snappy in operation. You could probably get Ubuntu to run almost as light, but only with a lot of customization.

---

### Post by koenn on 2011-03-26
> **Sean Moran said:**
> ... The only suiggestion is to start with dpkg.  dpkg -i is the one to install, and if you try somethng like **dpkg -i synaptic** it might prove successful, depending on the repos you're running.  ...  but the fundamental package manager is dpkg.

use dpkg -i for debian and debian will understand. ...

nonsense.
apt is the standard package manager on debian. It works like a frontend to dpkg, but that's how Ubuntu does it too. 
You can use dpkg directly, but you onlu need to do that in cases of serious troubleshooting.

---

### Post by uRock on 2011-03-26
Moved to Recurring Discussions

---

### Post by boydrice on 2011-03-26
> **Random_Dude said:**
> I'm also gaining an interest on Debian.
I've got an old computer that I would like to make my test machine (so I can play around with different distros when I'm bored).

Does Debian come with a default environment and window manager installed? Since it's an old computer I was planing on running only Openbox on it.

Are the repositories updated? For example, can I get the new version of the kernel, firefox, latest software updates, etc...

Does it have synaptic?

Ubuntu is the only distro that I've used for a considerable amount of time, is Debian too hard for me to try out?

Cheers :cool:

Debian has huge repositories of packages so I would be shocked if something you needed wasn't there.  

Debian Squeeze will not have the latest and greatest software but Debian Backports helps [http://backports.debian.org/]("http://backports.debian.org/").

You can make Debian be whatever you would like so yes you can install openbox but it is not a default wm.

Debian is as hard as you make it, if you don't read the documentation and aren't willing to do a little homework then chances are you will have an issue.  

If you want a pre-customized Debian install with openbox as the default checkout Crunchbang Linux [http://crunchbanglinux.org/wiki/about]("http://crunchbanglinux.org/wiki/about").

---

### Post by uRock on 2011-03-26
> **boydrice said:**
> Debian is as hard as you make it, if you don't read the documentation and aren't willing to do a little homework then chances are you will have an issue.

Too bad there site has very out of date documentation. Hopefully that has been fixed since the last time I tested Debian.

---

### Post by Random_Dude on 2011-03-26
Thank you all for the help. :)
It seems that I might live with the differences between the two. But nothing like trying it out.

Cheers :cool:

---

### Post by boydrice on 2011-03-26
> **uRock said:**
> Too bad there site has very out of date documentation. Hopefully that has been fixed since the last time I tested Debian.

Hmm, that hasn't been my experience but I don't doubt that the potential for some outdated material exists.  I have found the majority of what I have read applicable to my needs.

---

### Post by johntaylor1887 on 2011-03-26
> **PhilGil said:**
> The conventional wisdom that Debian is too hard for the average user is mostly a myth.

Define *average user*.

---

### Post by boydrice on 2011-03-26
> **johntaylor1887 said:**
> Define *average user*.

Define user first, then we can qualify the average piece.

---

### Post by PhilGil on 2011-03-26
> **johntaylor1887 said:**
> Define *average user*.
Guess I should have said average Linux user. A user that's installed and configured Ubuntu a couple of times probably wouldn't have too much trouble with Squeeze.

---

### Post by Hur Dur on 2011-03-26
> **Random_Dude said:**
> I'm also gaining an interest on Debian.
I've got an old computer that I would like to make my test machine (so I can play around with different distros when I'm bored).

Does Debian come with a default environment and window manager installed? Since it's an old computer I was planing on running only Openbox on it.

Are the repositories updated? For example, can I get the new version of the kernel, firefox, latest software updates, etc...

Does it have synaptic?

Ubuntu is the only distro that I've used for a considerable amount of time, is Debian too hard for me to try out?

Cheers :cool:
Debian does not come with a desktop environment or window manager installed. Just grab the net install CD, and install x-window-system-core and Openbox. 

Debian has the largest repositories of any distro, but you will not find bleeding edge software there. It focuses mainly on an extremely stable system.

Synaptic is just a front-end to APT, so yes, Debian does have it. Most likely in the repository.

Ubuntu is very similar to Debian, so you shouldn't have trouble using it.

@uRock, I don't think the documentation is out of date. Maybe it hasn't been updated in a while, but most things in it still apply to the latest stable Debian release.

---

### Post by CharlesA on 2011-03-26
I did a netinstall of Squeeze and it seemed almost the same as the Ubuntu installer, but then I didn't use the GUI installer, I used the normal one.

---

### Post by beew on 2011-03-29
I have not been successful in installing Debian testing. When I booted into the live usb it kept asking me for password and everything I have found on the web and the Debian forums didn't work. Debian stable installed ok but the software is too old. There is no way I would use old crap like that, I uninstalled it the next day, to heck with "stability" if that means going horse and buggy while you can have a great ride on a race car (with more risk of course). 

Now I have a partition installed with LMDE, kind of the closest thing to Debian testing. Haven't done much with it at the moment but it is quite similar to Ubuntu, except it feels a bit older and less polished (The Mint interface is ugly, but the Debian one is actually just as bad)

However the machine I put it on doesn't require any propietary driver and that is one big advantage of Ubuntu if you need those,--and a point that upsets the purists. Installing those are not so easy in Debian or LMDE (though they are talking about porting the Ubuntu feature "Additional driver" to LMDE)

---

### Post by NightwishFan on 2011-03-29
> **beew said:**
> I have not been successful in installing Debian testing.
I will be happy to help.

> When I booted into the live usb it kept asking me for password and everything I have found on the web and the Debian forums didn't work.
What do you need root for from there? To be honest I do not know how either other than to launch the root terminal.

> Debian stable installed ok but the software is too old.
Squeeze is not very old, most of the stuff has to be newer than Ubuntu 10.04.

> There is no way I would use old crap like that, I uninstalled it the next day, to heck with "stability" if that means going horse and buggy while you can have a great ride on a race car (with more risk of course).
No need to be so mean about it. Debian has newer stuff as well, but stable is something to be admired in my opinion. Also note you can upgrade to testing with ease from your existing stable install. As a matter of fact that is how I always get testing.

> Now I have a partition installed with LMDE, kind of the closest thing to Debian testing.
Never quite understood Mint... Well as long as it works and people like it.

> Haven't done much with it at the moment but it is quite similar to Ubuntu, except it feels a bit older and less polished (The Mint interface is ugly, but the Debian one is actually just as bad)
I think over half of the Ubuntu packages are directly derived from Debian. So what the heck?

> However the machine I put it on doesn't require any propietary driver and that is one big advantage of Ubuntu if you need those,--and a point that upsets the purists. Installing those are not so easy in Debian or LMDE (though they are talking about porting the Ubuntu feature "Additional driver" to LMDE)
I agree it is more for experts but at least in squeeze most drivers are as hard as installing a package and rebooting.

I hope you change your mind about Debian even if you do not use it. It is a great distro.

---

### Post by cariboo on 2011-03-29
Aside for older software, what didn't it do that newer versions will? In most cases newer software may only be a security update, or perhaps a new feature is added. It shouldn't stop you from actually getting things done.

---

### Post by beew on 2011-03-29
> **NightwishFan said:**
> I will be happy to help.


What do you need root for from there? To be honest I do not know how either other than to launch the root terminal.


 
They asked for a login password as soon as I booted into the live usb (??!!) So I couldn't even get off first base. Not that I need to be root for anything.

Debian stable is old. Still using OOO 2X

---

### Post by kelvin spratt on 2011-03-29
> **beew said:**
> I have not been successful in installing Debian testing. When I booted into the live usb it kept asking me for password and everything I have found on the web and the Debian forums didn't work. Debian stable installed ok but the software is too old. There is no way I would use old crap like that, I uninstalled it the next day, to heck with "stability" if that means going horse and buggy while you can have a great ride on a race car (with more risk of course). 

Now I have a partition installed with LMDE, kind of the closest thing to Debian testing. Haven't done much with it at the moment but it is quite similar to Ubuntu, except it feels a bit older and less polished (The Mint interface is ugly, but the Debian one is actually just as bad)

However the machine I put it on doesn't require any propietary driver and that is one big advantage of Ubuntu if you need those,--and a point that upsets the purists. Installing those are not so easy in Debian or LMDE (though they are talking about porting the Ubuntu feature "Additional driver" to LMDE)
What is hard about changing every entry Sqeeze to testing in the apt sources file then #apt-get update then #apt-get dist-ugrade then you have debian testing and guess what change sources to sid and yes you can guess you have Debian sid. I wish people would check things before making totally wrong claims to install nvidia do it the nvidia way.
                                          
[Re: Easy install guide for nvidia]("http://www.salixos.org/forum/viewtopic.php?f=30&t=1542&start=10#p11748")            
 [[IMG]http://www.salixos.org/forum/styles/1thank_salix/imageset/icon_post_target.gif[/IMG]]("http://www.salixos.org/forum/viewtopic.php?p=11748#p11748")by **[mandog]("http://www.salixos.org/forum/memberlist.php?mode=viewprofile&u=827")** on 28. Dec 2010, 19:56 
 # apt-get install kernel headers ####### what your kernel is 
2. Go to nvidia.com and select your OS, architecture and graphics card from the drop-down menus.
3. Save the installer to home directory
4. Open a terminal, login as root (su ) 
5. cd /home/your name
sh NVI                                           press tab it should then auto complete like this
NVIDIA-Linux-<arch>-<version>.run then ad this --no-x-check so then you have,
6.sh NVIDIA-Linux-<arch>-<version>.run--no-x-check
let nvidia build and set up xorg 
when finished reboot
nothing hard in that.

---

### Post by TBABill on 2011-03-29
> **beew said:**
> I have not been successful in installing Debian testing. When I booted into the live usb it kept asking me for password and everything I have found on the web and the Debian forums didn't work. Debian stable installed ok but the software is too old. There is no way I would use old crap like that, I uninstalled it the next day, to heck with "stability" if that means going horse and buggy while you can have a great ride on a race car (with more risk of course). 
 
Seriously? Horse and buggy? Yes, software is older (Iceweasel is at 3.5.15 I think and Chromium is at 6.xxxx), but it is also rock solid. And you can enable backports and have Iceweasel 4.0, Libre Office and lots of other newer apps. And this is ONLY speaking to Debian Stable. Run Testing and you can have lots of newer apps, but a bit behind those distros that make them available immediately (so they can be tested first)
 
> Now I have a partition installed with LMDE, kind of the closest thing to Debian testing. Haven't done much with it at the moment but it is quite similar to Ubuntu, except it feels a bit older and less polished (The Mint interface is ugly, but the Debian one is actually just as bad)
 
However the machine I put it on doesn't require any propietary driver and that is one big advantage of Ubuntu if you need those,--and a point that upsets the purists. Installing those are not so easy in Debian or LMDE (though they are talking about porting the Ubuntu feature "Additional driver" to LMDE)
 
How is Debian's interface "just as bad" as Mint's when it looks visually just like Ubuntu? All you have to do is change the theme and you can hardly tell the difference between Ubuntu and Debian. 
 
One interesting and positive note: the Mint devs (Ikey leading) are working on tools to make proprietary drivers as easy to install on LMDE as they are on Ubuntu and Mint. That'll be a nice relief for those wanting the Debian base instead of Ubuntu, or Ubuntu users who would like to experiment with or use Debian without feeling lost trying to get drivers going.

---

### Post by NightwishFan on 2011-03-29
> **beew said:**
> They asked for a login password as soon as I booted into the live usb (??!!) So I couldn't even get off first base. Not that I need to be root for anything.
I just used a live usb today and it did nothing of the sort. I believe you, its just that is not the correct behavior so something is wrong with the image. Did you get the new official live image from the Debian web page?
[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)

> Debian stable is old. Still using OOO 2X
No... Debian 6 has 3.x
[http://packages.debian.org/squeeze/openoffice.org](http://packages.debian.org/squeeze/openoffice.org)

Debian 5 Lenny is old stable. Even then it is still newer than Ubuntu 8.04.

---

### Post by beew on 2011-03-29
> **TBABill said:**
> 
How is Debian's interface "just as bad" as Mint's when it looks visually just like Ubuntu? All you have to do is change the theme and you can hardly tell the difference between Ubuntu and Debian. 

The colour, the Mint menu, the Mint logo?  It has a Winodws 9X feel to it.

When I have time I am going to install new theme, new colour and get rid of the mint menu. I tried changing the colour but it is odd looking right now, need more experimentations.
 
> One interesting and positive note: the Mint devs (Ikey leading) are working on tools to make proprietary drivers as easy to install on LMDE as they are on Ubuntu and Mint. That'll be a nice relief for those wanting the Debian base instead of Ubuntu, or Ubuntu users who would like to experiment with or use Debian without feeling lost trying to get drivers going.

Yes, read about it. It is good news.

---

### Post by beew on 2011-03-29
> **NightwishFan said:**
> I just used a live usb today and it did nothing of the sort. I believe you, its just that is not the correct behavior so something is wrong with the image. Did you get the new official live image from the Debian web page?
[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)



Could be a bad image. But I have downloaded several images over a period of 2 months and  always got the same problem so I gave up.

I will download the image and try it out. Since you have tested it so I won't be wasting my time. Thanks dude.

EDITED: the link is for "stable release", I am talking about testing.

---

### Post by NightwishFan on 2011-03-29
I have never used the testing image. At this point I do not see the point. Nothing in Wheezy is notably newer than in Stable, and you can simply upgrade to testing after the install.

---

### Post by fudoki on 2011-04-01
> **PhilGil said:**
> Be aware that Debian offers three different versions: Stable, Testing and Unstable. Which you choose to install will depend on your tolerance for breakage and your desire for the newest packages. Debian stable is much like an Ubuntu LTS version, so you'll typically only see security updates. Testing and Unstable do offer new versions of packages.

There is also a backports repository for Stable and some repositories maintained by third parties. However, there's nothing like the ecosystem of repositories available for Ubuntu.


Yes, I think it's installed by default in Squeeze.

Probably depends on how much you've poked around under the hood in Ubuntu, there's not much difference between the two once you strip off the top layer. I didn't find the transition from Ubuntu to Squeeze too difficult. The conventional wisdom that Debian is too hard for the average user is mostly a myth.

Ubuntu is derived from Debian, and Ubuntu "polish", advancements, and fixes are returned to Debian and immediately incorporated into the Debian "Testing" and "Unstable" repositories as appropriate.

Think of Debian and Ubuntu as sine waves on a graph with Debian having a period of two years and Ubuntu a period of six months between releases.

Right now, Debian "Stable" is equal to Ubuntu 10.04 and 10.10, but as time passes, Debian "Stable" will fall further and further behind, with only the "Unstable" variant keeping pace with Ubuntu.  Testing is in the middle.

For all practical purposes Debian and Ubuntu are nearly identical technology-wise right now, since Debian 6.0 "Squeeze" was released a week or so ago.

I switched from Debian to Ubuntu on my newest machine about a year ago, because the Debian "Stable" kernel did not fully support my motherboard, X4 processor, etc.  Running Ubuntu is like running a more thoroughly tested and polished copy of Debian "Unstable".  You are safer with Ubuntu because it has been professionally "wrung out" (the "technical" term... hahahaha).  Debian lets the users do the testing in Unstable, and relies on their feedback to direct their efforts while Ubuntu deliberately bears down on the newest code to push it out every six months.

Since the creation of the Ubuntu distro, the cycle time for Debian has been shortened from 4-5 years to two years due to the feedback loop between Debian and Ubuntu.  The two companies cooperate a lot, to the great benefit of everyone.  I have been using Debian for many years, and swear by it.  That's why I also trust Ubuntu.  If you are running Debian and you need something really new, you can use the Ubuntu version in almost all cases, with caveats.

On older machines I always run Debian.  Solid, perfect, error free - it will spoil you.  But on new hardware, and especially new laptops, you had best run Ubuntu is you want everything (all the new features) to work.  Yes, you can get it to work in Debian - but being an engineer helps...

But on an older machine, loading Debian, or an Ubuntu LTS release, will make the old box just "sing".

Ubuntu LTS releases and Debian releases are functionally equivalent.  They have different "feels" in tuning and configuration, but the guts are the same, as they are branches of the same fine "tree".

---

