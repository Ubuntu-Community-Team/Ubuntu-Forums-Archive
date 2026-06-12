---
title: "Is Arch REALLY worth installing?"
date: 2010-06-07
forum: Recurring Discussions
---

### Post by PsychoDevon on 2010-06-07
I am considering switching from Mint/Ubuntu to Arch.

Today, I tried out openSUSE, and realize for the final time that KDE is NOT for me. I've considered Arch for a couple of days now, and here are the reasons why:

*When including the AUR, a MASSIVE collection of repository packages that are easy to install.

*A rolling release system, which in my opinion seems very appealing

*I only install what I WANT. Not what comes with it.



But, with all of this in my mind, I would really like to see those who switched to Arch and see what they say.


So, here is what I want you to say in your reply:


1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


Those questions are of course for Arch users only. If you don't use Arch, feel free to say what you think of Arch.

---

### Post by tjwoosta on 2010-06-07
1. Ive used ALL of the major distros and many obscure ones as well.
2. Immediately fell in love.
3. Sure is, just as easy as any other distro but no reinstalling every few months.
4. Definitely, its been over two years and Ive completely lost the urge to distro hop.

---

### Post by PsychoDevon on 2010-06-08
> **tjwoosta said:**
> 1. Ive used ALL of the major distros and many obscure ones as well.
2. Immediately fell in love.
3. Sure is, just as easy as any other distro but no reinstalling every few months.
4. Definitely, its been over two years and Ive completely lost the urge to distro hop.


Are the repositories in Arch comparable to those in Debian/Ubuntu/etc.?

---

### Post by Shazzam6999 on 2010-06-08
1: I distro hopped a lot before Arch. Now I just try out the new Ubuntu every now and then and hop between dwm and openbox a lot, which takes all of five seconds.
2: I was intimidated before installing Arch but after installing it everything was great. It took me a little while to get used to everything but it's great. Being able to install only the packages you want is wonderful; I have use one program for what I need (ie: one mail client, one irc client, etc.) and it's the program I love the most.
3: Sure, I've never had anything break (well without me breaking it like an idiot), I use it for college.
4:<3 Arch

It's intimidating at first but after a few installs it becomes extremely simple, the documentation is excellent and makes the transition really easy.

> re the repositories in Arch comparable to those in Debian/Ubuntu/etc.?

My experience with Debian is pretty limited but in my limited experience the repos in Arch are more extensive than the repos. Pacman is an excellent package manager as well.

Of course, I'm biased though.

---

### Post by wilee-nilee on 2010-06-08
Since arch takes a little more hands on installation I tried it out in a virtual just to see if I could get it to run. Had no problems the arch wiki's are very detailed, especially the beginners one. When I have more time this summer I'm going to do a regular install on the HD.

---

### Post by handy on 2010-06-08
OP, it sounds like you are a good candidate for Arch.

Try it in a VM if you can?

The only way to know if you like it is to install it & use it. Like everything else the more you do it the better you understand & the more your understanding expands.

Don't take the easy way out with one of the auto install forks as you'll miss out on the vital education that comes with the process of installation. The easier installs are best for those who already know how Arch works.

I distro hopped until I found Arch, about 2.4 years ago. Since then I sometimes have a look at another system out of interest, on my test machine, thus far none but Haiku could take the place for at least some of what I do on Arch.

I find Arch to be the easiest system I've ever used to maintain. I love the rolling release system, & how easy it is to get out of trouble if you ever upgrade into it (3->4 times since I've been using it).

Here are some how-tos I wrote, on critical topics. You may never need to downgrade a kernel, (I had to once) though the other 2 how-to you will need to do. I wish I had of read these how-tos when I first started using Arch. 

Look for the titles starting with **[Arch]** there are only 3 of them:

[http://spiralinear.org/index.php?board=9.0](http://spiralinear.org/index.php?board=9.0)

---

### Post by Cuddles McKitten on 2010-06-08
Arch is good and fun to play with, but you WILL end up breaking it after a while (probably by just updating it).  sudo pacman -Syu isn't always your friend.  The best way to describe it is a used, old, or custom car.  If you like figuring out what's wrong with it and don't mind replacing the alternator yourself, then it'll be fun.

If you're using the box for work, servers, etc. don't get Arch.  If you want something to learn with, that's eminently customizable, and doesn't treat you like a child with everything carefully bubble wrapped, then go for it.

---

### Post by tjwoosta on 2010-06-08
> **PsychoDevon said:**
> Are the repositories in Arch comparable to those in Debian/Ubuntu/etc.?

If you include AUR then definately. The actual supported arch repos really aren't very extensive, but AUR more then makes up for it.

---

### Post by handy on 2010-06-08
> **Cuddles McKitten said:**
> Arch is good and fun to play with, but you WILL end up breaking it after a while (probably by just updating it).  sudo pacman -Syu isn't always your friend.

If you're using the box for work, servers, etc. don't get Arch.  If you want something to learn with, that's eminently customizable, and doesn't treat you like a child with everything carefully bubble wrapped, then go for it.

If you upgrade into trouble, you can be back where you were beforehand after about 5 minutes of easy work downgrading the offending package(s). Provided you have them in your cache.

One of the how-tos I linked to previously goes into this.

Arch is the quickest to fix system I have ever used due to the ease of downgrading a troublesome package. Which by the way from my experience is something that rarely ever has to happen anyway. ;)

---

### Post by Bachstelze on 2010-06-08
No.

Also recurring.

---

### Post by tjwoosta on 2010-06-08
> **Cuddles McKitten said:**
> Arch is good and fun to play with, but you WILL end up breaking it after a while (probably by just updating it).  sudo pacman -Syu isn't always your friend.


I suppose this depends on your hardware, and which software you use. 

As I said before Ive been using it for over 2 years, in that time there was only once that an update broke my setup. It was back when the intel drivers were going through regression, to fix it I simply had to switch from xf86-video-intel to xf86-video-intel-legacy and reboot. Even then everything was well known and documented on the forums and main page. I will say that its very important that you pay attention to pacmans output though. There are often times where it will tell you in the output what you need to do after the update to avoid breaking your system. for example sometimes you need to change the names of certain daemons in your rc.conf and such.

> 
If you're using the box for work, servers, etc. don't get Arch.  If you want something to learn with, that's eminently customizable, and doesn't treat you like a child with everything carefully bubble wrapped, then go for it.

I do agree with this.

---

### Post by handy on 2010-06-08
> **Bachstelze said:**
> No 


In your humble opinion. :)

There is NO accounting for taste, & yours is as valid as anyone else's.

Freedom of choice is what it is all about...

---

### Post by Daisuke_Aramaki on 2010-06-08
My experience - Arch is good. But not in the same league as Sorcerer, Lunar, CRUX or Slack. True, the rest are differently modeled distros, but it just doesn't measure up against these four.
That's why I don't use it. Also, I am not a fan of AUR.

---

### Post by Bachstelze on 2010-06-08
> **handy said:**
> In your humble opinion. :)

Their is NO accounting for taste, & yours is as valid as anyone else's.

I never said otherwise. :) The long answer would be: "Why would you care about my or anyone else's opinion? Just try it for yourself, it's free."

---

### Post by tjwoosta on 2010-06-08
> Also, I am not a fan of AUR.

Any particular reason?

---

### Post by cariboo on 2010-06-08
This has been asked and answered many times. Moved to Recurring.

---

### Post by chessnerd on 2010-06-08
A fully set up computer is like a sandwich ready to be eaten. The operating system is the bread, something only necessary to hold the ingredients (applications) in while you enjoy your lunch. Sure, bad bread can ruin a sandwich, and good bread can make a sandwich better, but it really isn't the most important part.

So ask yourself this:

Is is REALLY worth it to bake your own bread?

The bread might taste better, and you can choose the ingredients, but pre-packaged bread is cheap already, and the bread isn't the most essential part of the sandwich anyway...

It is up to you. I've had home-made bread before (literally, not figuratively) and it was delicious. However, bread from the store isn't terrible. Unless you have a gripe with the available bread, I'd suggested buying it pre-made.

---

### Post by screaminj3sus on 2010-06-08
1) What OS you used before Arch.
Windows 7/Ubuntu

2) What were your initial impressions.
Install definitely has a learning curve, but documentation is excellent and easy to follow. Arch install with full gnome used like 500mb less ram than ubuntu. Pacman seems to work just as well as apt-get in ubuntu.

3) After installation, is using it easy-to-use day-to-day?
Yeah, but its repos aren't as extensive as ubuntu's and I ended up having to compile lots of stuff from aur (its pretty easy though, but annoying for things like chromium where I get nice daily updates in ubuntu's ppa)

4) Are you happy using it.
I just recently stopped using it and went back to ubuntu but I did enjoy using it. You can get a really lean system and the rolling release is great.

---

### Post by BoneKracker on 2010-06-08
> **Daisuke_Aramaki said:**
> My experience - Arch is good. But not in the same league as Sorcerer, Lunar, CRUX or Slack. True, the rest are differently modeled distros, but it just doesn't measure up against these four.
That's why I don't use it. Also, I am not a fan of AUR.

What have you got against Gentoo?

---

### Post by PsychoDevon on 2010-06-08
Thanks everyone

I am going to try it on a virtualbox right now.


One question I have: I have followed numerous walkthroughs of installing Arch, and I have to ask:

AT WHAT POINT DO I NAME MY USER ACCOUNT!?!?!?

I have seen where you set your root password and where you change your hostname....but is your hostname your username?

---

### Post by Shining Arcanine on 2010-06-08
> **PsychoDevon said:**
> I am considering switching from Mint/Ubuntu to Arch.

Today, I tried out openSUSE, and realize for the final time that KDE is NOT for me. I've considered Arch for a couple of days now, and here are the reasons why:

*When including the AUR, a MASSIVE collection of repository packages that are easy to install.

*A rolling release system, which in my opinion seems very appealing

*I only install what I WANT. Not what comes with it.



But, with all of this in my mind, I would really like to see those who switched to Arch and see what they say.


So, here is what I want you to say in your reply:


1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


Those questions are of course for Arch users only. If you don't use Arch, feel free to say what you think of Arch.
Why do you dislike KDE? If you dislike KDE, why not use GNOME? I think both Ubuntu and openSUSE are good GNOME distributions.

---

### Post by PsychoDevon on 2010-06-08
> **Shining Arcanine said:**
> Why do you dislike KDE? If you dislike KDE, why not use GNOME? I think both Ubuntu and openSUSE are good GNOME distributions.


I do use GNOME by default in most of my distro's, it's just that I've only used KDE in Kubuntu, and quite honestly, Ubuntu wasn't made for KDE in mind as much as openSUSE was. So, I figured I'd give it a shot...and the shot failed. lol.


Edit:

But to answer your question, I prefer GNOME by default to KDE by default. KDE definitely has very different features than GNOME in terms of interface and design...but, I prefer how GNOME handles those opposed to KDE.

---

### Post by tjwoosta on 2010-06-08
> **PsychoDevon said:**
> Thanks everyone

I am going to try it on a virtualbox right now.


One question I have: I have followed numerous walkthroughs of installing Arch, and I have to ask:

AT WHAT POINT DO I NAME MY USER ACCOUNT!?!?!?

I have seen where you set your root password and where you change your hostname....but is your hostname your username?

[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_4:_Add_a_user_and_setup_groups](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_4:_Add_a_user_and_setup_groups)

---

### Post by handy on 2010-06-08
> **PsychoDevon said:**
> Thanks everyone

I am going to try it on a virtualbox right now.


One question I have: I have followed numerous walkthroughs of installing Arch, and I have to ask:

AT WHAT POINT DO I NAME MY USER ACCOUNT!?!?!?

I have seen where you set your root password and where you change your hostname....but is your hostname your username?

Follow the Beginners' Guide to the letter. It will tell you everything you need to know, unless you are one of the becoming more rare everyday people that have a problem with wireless networking.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by BoneKracker on 2010-06-08
> **handy said:**
> Follow the Beginners' Guide to the letter. It will tell you everything you need to know, unless you are one of the becoming more rare everyday people that have a problem with wireless networking.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Pffft.  We don't need to stinkin' Beginners' Guide. :p

By the way, your Beginner's Guide neglects to tell the user that before using 'adduser', they ought to review (and modify, if necessary) the defaults used by adduser (found in /etc/login.defs normally), and also edit the (hidden) default user dot-file templates in /etc/skel.

---

### Post by handy on 2010-06-08
> **BoneKracker said:**
> Pffft.  We don't need to stinkin' Beginners' Guide. :p

By the way, your Beginner's Guide neglects to tell the user that before using 'adduser', they ought to review (and modify, if necessary) the defaults used by adduser (found in /etc/login.defs normally), and also edit the (hidden) default user dot-file templates in /etc/skel.

:lolflag: [-X

The easiest most trouble free first installs happen for those that follow the Beginner's Guide. If you are a distro wiz, then you can just use the [Official Installation Guide]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide") to gather an understanding about how Arch does its thing.

When I did my first install I had both of them open in tabs in Firefox on my 2nd machine, not that that was required, I just wanted to understand as much about what I was doing as I could. I also bounced around the Arch wiki whilst installing as well, for the same reason. 

Not necessity, personal choice. :)

Because Arch does things differently, the Beginners Guide is a great interpreter for those of us who aren't elite. ):P

Whatever the guide requires should be in it by now, as the guide is incredibly well maintained. It is the prime tool that gives new Arch users an opportunity to try Arch in the first place. Many if not most of whom come from the Ubuntu realm & are looking for more control of their system.

---

### Post by BoneKracker on 2010-06-08
> **handy said:**
> Because Arch does things differently, the Beginners Guide is a great interpreter for those of us who aren't elite. ):P

Whatever the guide requires should be in it by now, as the guide is incredibly well maintained. It is the prime tool that gives new Arch users an opportunity to try Arch in the first place. Many if not most of whom come from the Ubuntu realm & are looking for more control of their system.

Yeah, I was only kidding.  It looks like a really good document.

---

### Post by eagleton on 2010-06-08
> **PsychoDevon said:**
> 

1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


Those questions are of course for Arch users only. If you don't use Arch, feel free to say what you think of Arch.

1) Mostly Ubuntu and Fedora, but also Opensuse for some time.
2) I liked the clarity of the system and the documentation. Usually you can fix problems very fast.
3) Yes it is - once in a while, you change a configuration file, but that's it. Sometimes there are massive updates, when elementary libs (like libpng) are updated. I was thinking about installing it on other PCs as well, but in the end I couldn't be bothered to do the same work several times. Problems arise when a program you hardly use breaks and you notice it too late to get some work done. This is less likely with distros like Ubuntu, although it can happen as well. I especially liked the very fast package management.
4) I've been happy using it, and consider to return to it at some point, possibly with Gnome 3. I've learned a lot. 

Maybe the biggest drawback is security - no signed packages, no SELinux or Apparmor by default, no automatic security updates. You can install SELinux, but it takes some work, and you depend on the AUR.

---

### Post by handy on 2010-06-08
> **eagleton said:**
> ...
Maybe the biggest drawback is security - no signed packages, no SELinux or Apparmor by default, no automatic security updates. You can install SELinux, but it takes some work, and you depend on the AUR.

Out of interest, how do these security issues effect Arch users?

---

### Post by BoneKracker on 2010-06-08
> **handy said:**
> Out of interest, how do these security issues effect Arch users?

> **chessnerd said:**
> A fully set up computer is like a sandwich ready to be eaten. The operating system is the bread, something only necessary to hold the ingredients (applications) in while you enjoy your lunch. Sure, bad bread can ruin a sandwich, and good bread can make a sandwich better, but it really isn't the most important part.

So ask yourself this:

Is is REALLY worth it to bake your own bread?

The bread might taste better, and you can choose the ingredients, but pre-packaged bread is cheap already, and the bread isn't the most essential part of the sandwich anyway...

It is up to you. I've had home-made bread before (literally, not figuratively) and it was delicious. However, bread from the store isn't terrible. Unless you have a gripe with the available bread, I'd suggested buying it pre-made.

Nice analogy.

I don't think it's entirely apt though, in a couple of important ways.  

It's more like a ship and its cargo.  The cargo is what's important, but if the ship sucks, the cargo suffers, doesn't get where it needs to be on time, or doesn't get there at all.

A good way for a ship to suck is trying to be all things at once.  A cargo ship that tries to also be a cruise ship, an ocean liner, an oil tanker and a warship is going to do none of these things well.  Even if it manages to the combine all those capabilities into a single vessel, it's going to be a bloated, lumbering behemoth of great inefficiency.  Nobody who wants a ship wants all of these things and anybody who gets one is going to be dissatisfied.

Does that mean you should build your own ship?  No.  You can buy ships "off the shelf" that satisfy a general purpose.  However, they are still going to be "generally" and "approximately" matched with your needs.  Almost universally, any that happens to come configured with all the features you need will do so at the expense of a general policy of providing everything anyone could possibly want.  So instead of a bloated, lumbering behemoth of an all-purpose ship, you've got a somewhat-less-bloated lumbering behemoth of a ship that generally suits your general type of cargo in most situations.

And some purposes simply cannot be satisfied by an all-purpose ship.  It is never going to be an attack submarine, a racing yacht, or a littoral assault vessel.  Just not gonna happen.

Anyone who wants a ship that provides exactly what they want without being too small to carry their cargo, too deep of draft to go where they want to go, or just plain being slower than it needs to be because it's carrying the unnecessary weight of features they don't want and can't rip out withing leaving gaping, irreparable wounds, will either custom-order a ship (e.g. Suse Builder), assemble one to their own specifications from pre-built assemblies (Arch), build one from parts they've machined themselves (Gentoo), or build their own mine and shipyard (LFS).

---

### Post by Tibuda on 2010-06-08
> **chessnerd said:**
> A fully set up computer is like a sandwich ready to be eaten. The operating system is the bread, something only necessary to hold the ingredients (applications) in while you enjoy your lunch. Sure, bad bread can ruin a sandwich, and good bread can make a sandwich better, but it really isn't the most important part.

So ask yourself this:

Is is REALLY worth it to bake your own bread?

The bread might taste better, and you can choose the ingredients, but pre-packaged bread is cheap already, and the bread isn't the most essential part of the sandwich anyway...

It is up to you. I've had home-made bread before (literally, not figuratively) and it was delicious. However, bread from the store isn't terrible. Unless you have a gripe with the available bread, I'd suggested buying it pre-made.

the problem is that the pre-packaged bread get old every six-months...

---

### Post by Tibuda on 2010-06-08
> **BoneKracker said:**
> Anyone who wants a ship that provides exactly what they want without being too small to carry their cargo, too deep of draft to go where they want to go, or just plain being slower than it needs to be because it's carrying the unnecessary weight of features they don't want and can't rip out withing leaving gaping, irreparable wounds, will either custom-order a ship (e.g. Suse Builder), assemble one to their own specifications from pre-built assemblies (Arch**, Ubuntu Minimal**), build one from parts they've machined themselves (Gentoo), or build their own mine and shipyard (LFS).
Ubuntu can also be used to install a bare minimal system...

I don't use Arch to build a system from scratch, but just to have packages available without having to compile them. That's what makes Arch really worth installing IMHO.

---

### Post by BoneKracker on 2010-06-08
> **danielrmt said:**
> Ubuntu can also be used to install a bare minimal system...
Not really.  What's "minimal" is a matter of perspective.

Re Arch: 

I wouldn't try to sell anyone on using a source-based distro, but I think it's worth understanding why some people too.

Compiling is not about "having to", it's about "being able to", (conveniently and efficiently).  Arch is facilitating this to some extent with its build system, which is a good thing, but it doesn't seem to be end-user oriented yet (more of a tool for packagers than user-admins).  I suspect it will broaden to become both, like portage, paludis, and pkgcore, eventually.

Lots of packages come with important compile-time options.  If one is not able to choose among these, one has the same old problem of "one size does not fit all", just to a lesser extent.  Some packages have loads of compile-time options.  Also, tuning for i686 is better than i386, but its still not the same as building for the specific CPU you are running on.

There is a time trade-off, but contrary to popular belief, the only time investment is in _learning_.  Some people don't want to invest the time needed to understand things like a compiler.  Others already do because they code.  Still others want to learn just because they want to.

But once set up, a source-based system takes no more time to manage than any other (more CPU time, _yes_, admin time, _no_).  And I'd be willing to bet it takes an equal amount of hands-on time for an experienced person to set up a new Gentoo or Arch system.

In fact, I would posit that it it takes less time to administer a 100% source-based system than a binary one which also happens to have a handful of apps on it built from source.

Another reason some people use source-based distros is because some projects require a high degree of customization (for example, building an embedded system, which is the fastest growing use of Linux).

All that said, I'm well aware that most people have no use for any of that, which is why I don't try to push source-based systems on anyone.

---

### Post by handy on 2010-06-08
> **danielrmt said:**
> Ubuntu can also be used to install a bare minimal system...

I don't use Arch to build a system from scratch, but just to have packages available without having to compile them. That's what makes Arch really worth installing IMHO.

I also use Arch because system maintenance is mostly boring. :)

---

### Post by scottuss on 2010-06-08
1) OpenSuse / Ubuntu / Fedora

2) Very fast, slightly complicated to get working as I wanted.

3) No. Things break far too often to use it as a day to day system. Many will argue that it's my fault, or a stable Arch system can be obtained by doing X,Y,Z. This is very true, you can. BUT the time needed to do this was too much for me. I just want things to work with minimal tweaking.

4) I can see where Arch is useful for some people, and if I had the time / patience / incliniation to do so, I'd run Arch. However, sometimes my other half uses my laptop, friends / family sometimes quickly use it and things need to "just work". Personally, I've also got better things to do than fix stuff when it breaks, which when I've used Arch (several times over the past 2 years or so) has happened a lot.

P.S - No Arch fanpeople need to reply telling me what would get it working nicely, I know this, I've been through the documentation (I've contributed too) and I'm not a noob. Cheers.

---

### Post by alphaniner on 2010-06-08
1) Ubuntu 7.04 to 9.04 including some built from minimal install, latest Debian Stable and Testing.

2) It was very easy to set up with the help of the Beginner's Guide.  I had no problems getting binary drivers installed, and only one snag getting the desktop up and running.  I found the solution to the sang pretty quickly, with the help of the BG and/or the wiki.

3) It's perfectly easy to use and day-to-day use is largely uneventful.

4) From a media prespective it's great.  I can watch avi's (etc.), DVDs and listen to music with no problems.
But I've had some minor issues with Firefox, and some more-than-minor issues with Deluge and OpenOffice.  And last I checked, sustained write speeds to all of my USB thumb drives were measured in Kb/s.  I know it wasn't the drives; I don't think it was the machine, but I didn't confirm it.

---

### Post by Tibuda on 2010-06-08
> **BoneKracker said:**
> I wouldn't try to sell anyone on using a source-based distro, but I think it's worth understanding why some people too.
I think you misunderstood me. When I said I dislike having to compile stuff I was not referring to source-based distros like Gentoo, but to distros with frozen binary packages like Ubuntu. If you want to have the latest version of an app in those distros, and the app developer does not have a DEB package or a PPA available (which is very rare), then you have to compile the app yourself. This is what I dislike about those distros, and what I like about Arch.

> All that said, I'm well aware that most people have no use for any of that, which is why I don't try to push source-based systems on anyone.
I can see why someone would use a source-based distro, but it is not for me. "Use what works for your".

---

### Post by snowpine on 2010-06-08
> **PsychoDevon said:**
> 1) What OS you used before Arch.
2) What were your initial impressions.
3) After installation, is using it easy-to-use day-to-day?
4) Are you happy using it.

1) Started with Ubuntu originally and tried a lot of other distros.
2) I really enjoyed the install process following the Beginners Guide. Gnome desktop was fast and responsive. Easy to install the applications I needed/wanted.
3) Updating the system (pacman -Syu) is really easy. I did not particularly enjoy using a rolling release distro (decided I prefer stable time-based releases for the most part). I suffered from frequent, frustrating X crashes.
4) I'm not using Arch any more.

---

### Post by kelvin spratt on 2010-06-08
> **snowpine said:**
> 1) Started with Ubuntu originally and tried a lot of other distros.
2) I really enjoyed the install process following the Beginners Guide. Gnome desktop was fast and responsive. Easy to install the applications I needed/wanted.
3) Updating the system (pacman -Syu) is really easy. I did not particularly enjoy using a rolling release distro (decided I prefer stable time-based releases for the most part). I suffered from frequent, frustrating X crashes.
4) I'm not using Arch any more.

I've used Arch since 1997 as my main distro. And have never had the Xserver crash in all that time, It is also the most stable distro I have used, can't say the same for Ubuntu/fedora

---

### Post by scottuss on 2010-06-08
> **kelvin spratt said:**
> I've used Arch since 1997 as my main distro. And have never had the Xserver crash in all that time, It is also the most stable distro I have used, can't say the same for Ubuntu/fedora

I had no end of trouble with X.. oh and HAL too.

---

### Post by kelvin spratt on 2010-06-08
> **scottuss said:**
> I had no end of trouble with X.. oh and HAL too.

Are you sure its not policykit  that you had problems with.
hal has been around for a long time the so called replacements have not.

---

### Post by Barrucadu on 2010-06-08
I used to have loads of problems with X&#8230; until I just deleted my xorg.conf and let it do its own thing.

1) I had a long period of distro-hopping, but the last thing I used for more than 2 days before switching to Arch was Ubuntu, built up from a minimal install.

2) "Ooh, cool."

3) It's as easy as you set it up to be, not really sure about this question&#8230; I guess to mean maintenence, which is simple; just update frequently, and check the pacman output for any notices.

4) Yes.

---

### Post by screaminj3sus on 2010-06-08
> **scottuss said:**
> I had no end of trouble with X.. oh and HAL too.

My arch install didn't have hal :p

---

### Post by Yes on 2010-06-08
> **kelvin spratt said:**
> I've used Arch **since 1997** as my main distro. And have never had the Xserver crash in all that time, It is also the most stable distro I have used, can't say the same for Ubuntu/fedora

:p

---

### Post by Barrucadu on 2010-06-08
> **kelvin spratt said:**
> I've used Arch since 1997 as my main distro.

That's pretty incredible; running Arch 5 years before the first release

---

### Post by dE_logics on 2010-06-08
You might like Sabayon minimal (my sig)... this is easier to install, you don't even have to configure the initial ram image to make it boot. It boots out of the box but to commandline, so you can setup what you like without any pains.

KDE, although hard initially is the most productive desktop environment. Here's my path - 

Gnome>xfce>KDE

And I'm permanent with KDE.

---

### Post by scottuss on 2010-06-08
> **kelvin spratt said:**
> Are you sure its not policykit  that you had problems with.
hal has been around for a long time the so called replacements have not.

> **screaminj3sus said:**
> My arch install didn't have hal :p


But that's the point: I don't want to know whether the problem was policykit or HAL. All I know is whenever I got errors they referred to HAL and people on IRC and in the forums said there were known issues with HAL at the time I was using it. I'm not saying the issues can't be fixed if you've got the time / patience, but I'm just being honest in saying that I don't. It's not Arch's fault, but it's not mine either! :)

Not having HAL was an issue for me, apparently my USB devices would not "plug and play" if HAL wasn't running. And Gnome would go mental!

---

### Post by eagleton on 2010-06-08
> **handy said:**
> Out of interest, how do these security issues effect Arch users?

Well, as long as nobody breaks into your system and you don't catch malware, it's mainly a psychological issue - do you feel safe using a system like Arch? 

I haven't heard of any serious security problems happening so far, but the potential is there IMO, which bothered me a bit (security by obscurity should never be good enough). It was one reason for me to check out on Ubuntu again.

---

### Post by Spike-X on 2010-06-08
Arch sounds interesting. If I ever have a: a free week off, and b: the second-hand laptop a friend of mine has been promising for the last couple of months, I'll give it a go.

---

### Post by handy on 2010-06-08
> **eagleton said:**
> 
Well, as long as nobody breaks into your system and you don't catch malware, it's mainly a psychological issue - do you feel safe using a system like Arch? 

I've not had any problems or ever heard of anyone having any on the Arch forum so I feel quite comfortable & as safe as I'd feel using anything else that wasn't windows. :)

> **eagleton said:**
> 
I haven't heard of any serious security problems happening so far, but the potential is there IMO, which bothered me a bit (security by obscurity should never be good enough). It was one reason for me to check out on Ubuntu again.

It is great to have so many choices. This is one of the things I love about GNU/Linux systems.

---

### Post by Pogeymanz on 2010-06-08
> **PsychoDevon said:**
> 
So, here is what I want you to say in your reply:


1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


Those questions are of course for Arch users only. If you don't use Arch, feel free to say what you think of Arch.


1) I used mostly Ubuntu, but I had played with OpenSUSE, SimplyMEPIS, Debian, Puppy, DSL.

2) It was awesome, but intimidating. The biggest hurdle was understanding how to connect wirelessly from the command line. Other than that, I loved the philosophy and fine-grained control.

3) Pretty easy. You don't HAVE to update everyday. Check the front page of archlinux.org before you update. In 3 years I've had very little go wrong and I've never reinstalled.

4) Incredibly. There is nothing I would change about Arch. Seriously.

Although, the original question: is it worth it? I don't know. Depends on you.

---

### Post by RedSquirrel on 2010-06-08
> **handy said:**
> I've not had any problems or ever heard of anyone having any on the Arch forum so I feel quite comfortable & as safe as I'd feel using anything else that wasn't windows. :)

I guess you never saw [this]("http://bbs.archlinux.org/viewtopic.php?id=12192"). :P :biggrin:



> **Pogeymanz said:**
> 4) Incredibly. There is nothing I would change about Arch. Seriously.

Some sort of [signing]("http://bugs.archlinux.org/task/5331") mechanism would be great.

---

### Post by BoneKracker on 2010-06-08
I would never want something like AppArmor or SELinux installed by default.  That should be a user's choice.  The binary distros that offer SELinux allow you to "opt out", but still leave hooks dangling all over the place (e.g. "contexts").

Anybody who's never tried a BSD should definitely do that.  I think I was most impressed by the quality of OpenBSD (seemed like the highest-quality free software product I have ever used), but FreeBSD is probably more in most people's line.  I think using a BSD at least once is an important experience because it shows you a more UNIX-like system, which helps you to understand how Linux is different.

---

### Post by handy on 2010-06-08
> **RedSquirrel said:**
> 
I guess you never saw [this]("http://bbs.archlinux.org/viewtopic.php?id=12192"). :P :biggrin: 

Not that I remember... ;)

I only use SSH on the LAN, & run an IPCop box which hopefully makes intrusion more difficult here.

> **RedSquirrel said:**
> 
Some sort of [signing]("http://bugs.archlinux.org/task/5331") mechanism would be great.

It looks like a slow train coming.

Thanks for both of those important links, I'll certainly keep my eye on the progress of the 2nd one.

---

### Post by BoneKracker on 2010-06-08
> **RedSquirrel said:**
> I guess you never saw [this]("http://bbs.archlinux.org/viewtopic.php?id=12192"). :P :biggrin:

"Arch Overlord" gets pwned.  :lol: :p


> **RedSquirrel said:**
> Some sort of [signing]("http://bugs.archlinux.org/task/5331") mechanism would be great.
What's the point?  It sounds like most of them are freely installing things from this "AUR" anyway.  Does that have any kind of security testing or code auditing going on?

---

### Post by Yes on 2010-06-08
> **BoneKracker said:**
> "Arch Overlord" gets pwned.  :lol: :p



What's the point?  It sounds like most of them are freely installing things from this "AUR" anyway.  Does that have any kind of security testing or code auditing going on?

People vote and add comments on AUR packages.  And of course you could always look at the code.

---

### Post by BoneKracker on 2010-06-08
> **Yes said:**
> People vote and add comments on AUR packages.  And of course you could always look at the code.

Yeah, how often do you actually do a thorough inspection of source code of a package before installing it?  Be honest now.  About the only time I look at somebody else's source code is if I'm trying to interface with some library or trying to patch a bug.  I'm not smart enough to understand half the code I do see.

Signing, in conjunction with an actual network of trust based on real identities, mitigates the problem of less-than-comprehensive security auditing allowing malicious code to be introduced through such unofficial or community repositories, because the code can actually be traced to somebody who is responsible for it.  Also, it prevents the code from being tampered with after it has been introduced to the repository.

It's a good idea.

---

### Post by handy on 2010-06-09
> **BoneKracker said:**
> "Arch Overlord" gets pwned.  :lol: :p 

:lolflag: 

Wow, what a title. :)

Shame I can't live up to it, I'm still an Arch noob who does the best he can with it... ;)

---

### Post by Yes on 2010-06-09
I don't, and I never said I did.  It's no different from downloading a program in Windows, or installing from source in any other distro.  You're trusting that it's going to be safe.

---

### Post by Shining Arcanine on 2010-06-09
> **danielrmt said:**
> Ubuntu can also be used to install a bare minimal system...

I don't use Arch to build a system from scratch, but just to have packages available without having to compile them. That's what makes Arch really worth installing IMHO.

A "bare minimal system" uses roughly 8MB of RAM and less than 16MB of space. I do not think you can achieve that with Ubuntu.

> **BoneKracker said:**
> Not really.  What's "minimal" is a matter of perspective.

Re Arch: 

I wouldn't try to sell anyone on using a source-based distro, but I think it's worth understanding why some people too.

Compiling is not about "having to", it's about "being able to", (conveniently and efficiently).  Arch is facilitating this to some extent with its build system, which is a good thing, but it doesn't seem to be end-user oriented yet (more of a tool for packagers than user-admins).  I suspect it will broaden to become both, like portage, paludis, and pkgcore, eventually.

Lots of packages come with important compile-time options.  If one is not able to choose among these, one has the same old problem of "one size does not fit all", just to a lesser extent.  Some packages have loads of compile-time options.  Also, tuning for i686 is better than i386, but its still not the same as building for the specific CPU you are running on.

There is a time trade-off, but contrary to popular belief, the only time investment is in _learning_.  Some people don't want to invest the time needed to understand things like a compiler.  Others already do because they code.  Still others want to learn just because they want to.

But once set up, a source-based system takes no more time to manage than any other (more CPU time, _yes_, admin time, _no_).  And I'd be willing to bet it takes an equal amount of hands-on time for an experienced person to set up a new Gentoo or Arch system.

In fact, I would posit that it it takes less time to administer a 100% source-based system than a binary one which also happens to have a handful of apps on it built from source.

Another reason some people use source-based distros is because some projects require a high degree of customization (for example, building an embedded system, which is the fastest growing use of Linux).

All that said, I'm well aware that most people have no use for any of that, which is why I don't try to push source-based systems on anyone.

I think that it is always good for people to learn more about how their systems work and at the same time, a great deal of issues that afflict other systems are non-issues on Gentoo Linux, such as the following:

[http://ubuntuforums.org/showthread.php?t=1505275](http://ubuntuforums.org/showthread.php?t=1505275)

Because of that, I tend to suggest that people use Gentoo Linux to avoid having such issues.

> **danielrmt said:**
> I think you misunderstood me. When I said I dislike having to compile stuff I was not referring to source-based distros like Gentoo, but to distros with frozen binary packages like Ubuntu. If you want to have the latest version of an app in those distros, and the app developer does not have a DEB package or a PPA available (which is very rare), then you have to compile the app yourself. This is what I dislike about those distros, and what I like about Arch.


I can see why someone would use a source-based distro, but it is not for me. "Use what works for your".

In that case, you might like Sabayon Linux. It is a hybrid. While it uses binary packages, it is based on Gentoo Linux and I believe that the Sabayon Linux developers provide instructions for how to compile things through its parent distribution's package manager, which opens the possibility to using source-based packages from Gentoo Linux's overlays, proposed ebuilds from Gentoo Linux's bug tracker and ebuilds produced by version bumps, which involve copying an official ebuild to a local overlay, renaming the ebuild to reflect a newer version, running a command to generate a Manifest file containing hashes to make Gentoo Linux's package manager happy and then installing the newer package on Sabayon Linux via its parent distribution's package manager.

Note that this is based on information I have read. I have never used Sabayon Linux to do these things in it because I use Gentoo Linux, although trying it has been on my to do list.

---

### Post by BoneKracker on 2010-06-09
> **handy said:**
> :lolflag: 

Wow, what a title. :)

Shame I can't live up to it, I'm still an Arch noob who does the best he can with it... ;)

To be fair, that happened back in 2005, which was around the time the brute-force attacks on password-protected ssh began in earnest (probably due to some script added to metasploit or some similar script-kiddie package).

Back then, many people were using password-protected ssh (as opposed to disabling password-based authentication and using only key-based authentication, which is now widely understood to be the smart thing to do).

On the other hand, the main reason he got pwned was probably because his password was "denise83" or something.

---

### Post by Shining Arcanine on 2010-06-09
Did sshd lack the ability to disallow root logins or did people simply not know that it is a good idea to disallow root logins when running sshd?

---

### Post by BoneKracker on 2010-06-09
> **Shining Arcanine said:**
> Did sshd lack the ability to disallow root logins or did people simply not know that it is a good idea to disallow root logins when running sshd?

It's had that ability as long as I can remember.  In fact, didn't this guy said he had root login disallowed?

What happened was that brute-forcing passwords suddenly become more feasible, for a number of reasons, and various tools became available that made it easy for anybody to proceed to try in an automated fashion, to locate machines running sshd and attempt to login using brute force methods.

Since then, as a natural response, people have made it more difficult to do that.

---

### Post by handy on 2010-06-09
> **BoneKracker said:**
> To be fair, that happened back in 2005, which was around the time the brute-force attacks on password-protected ssh began in earnest (probably due to some script added to metasploit or some similar script-kiddie package). 

I read the entire thread, it is really quite funny, considering who phrakture is, they have been sticking it to him for 5 years, the thread will never close. :)

Yes he had an easy password, but the primary cause was a bug in SSH, which allowed it overwrite his settings, which had before the overwrite denied root access.

***[Edit:]** The bug was fixed pretty quickly... :)*

---

### Post by Shining Arcanine on 2010-06-09
> **BoneKracker said:**
> It's had that ability as long as I can remember.  In fact, didn't this guy said he had root login disallowed?

What happened was that brute-forcing passwords suddenly become more feasible, for a number of reasons, and various tools became available that made it easy for anybody to proceed to try in an automated fashion, to locate machines running sshd and attempt to login using brute force methods.

Since then, as a natural response, people have made it more difficult to do that.

It would seem that he did not:

> yeah it was an alternate port - I had it setup to deny root access, but it looks like an ssh upgrade via pacman fudged that... 

I do not know how Arch Linux handles configuration files during upgrades, but I am certain that either would not have happened or it would have been his fault if he had been running Gentoo Linux. Gentoo Linux never overwrites configuration files with newer versions. You need to explicitly tell it to do that each and every time.

---

### Post by BoneKracker on 2010-06-09
> **Shining Arcanine said:**
> Gentoo Linux never overwrites configuration files with newer versions. You need to explicitly tell it to do that each and every time.
To be more precise, there's a user-configurable list of files that should be automatically updated vs. being presented to the user, through the tool of their choice, for acceptance, rejection, or modification of each change.

How does Ubuntu manage that, by the way (been so long I don't remember).

---

### Post by MedianMajik on 2010-06-09
Ouch, you guys are cold as hell.  Let me rephrase and walk away with what little dignity I have.

Arch has fantastic documentation and will become whatever you make it. Just give it a shot.

handy,
The irc channel for Arch provides excellent support so I mention it.

BoneKracker,
What I should have said is "don't feel put off by moving away from Ubuntu/Debian as it is easy to get things working in Arch."

---

### Post by handy on 2010-06-09
> **MedianMajik said:**
> 
Are you willing to modify config files by hand, use IRC, and feel comfortable in a console?  If so, do it. 

You haven't quite got it right.

I've been using GNU/Linux for nearly 4.5 years & Arch for 2.3 & I have never used IRC in my life.

Yep, you do have to modify config files to use Arch, but not many & not often. You get introduced to far more than you need to deal with in the installation process.

I tend to think that MedianMajik hasn't really used Arch as what you are saying doesn't quite ring true, from my experience anyway.

Though I'll admit, some people do find following the Beginners' Guide harder than others. 

As far as all of MedianMajik's supplied links are concerned, anyone who is truly interested in Arch should go & spend some time reading the Arch wiki. Arch doesn't want to become popular & climb the ranks of DistroWatch.com. It only wants to be itself.

---

### Post by BoneKracker on 2010-06-09
> **MedianMajik said:**
> Are you willing to modify config files by hand, use IRC, and feel comfortable in a console?  If so, do it.
It's not quite that simple.  The decision is at distro level (and package level) whether user handling of config files is generally expected during updates.  The individual decision is whether to use a distro that requires this (and hopefully provides tools for it), or not.

> **MedianMajik said:**
> My two cents: A nice feature of Arch is that debian commands can be easily tweaked to become Arch commands.  There is no reason for you to stop using Ubuntu forums, etc.  The system is what you make it.

Interesting. What exactly is involved in this unique feature of Arch?

---

### Post by Shining Arcanine on 2010-06-09
> **BoneKracker said:**
> To be more precise, there's a user-configurable list of files that should be automatically updated vs. being presented to the user, through the tool of their choice, for acceptance, rejection, or modification of each change.

How does Ubuntu manage that, by the way (been so long I don't remember).

As far as I know, Ubuntu assumes "upgrade scripts knows best" and tries to automate everything that has to do with config files in the background.

---

### Post by LoloftheRings on 2010-06-09
1) What OS you used before Arch.
Well.. I started with Windows, when I found out about Ubuntu. After using it for a while, I started switching. I tried about 10 distri when I got back to Ubuntu. Then, I found out about Arch, still using it now.

2) What were your initial impressions.
Very hacky, I loved it. When done, it feels like you created something that's really your's, although I just followed the beginners guide.

3) After installation, is using it easy-to-use day-to-day?
Absolutely, no difference with Ubuntu.

4) Are you happy using it.
Oh yea. But you don't want Arch when you are using an Ati video card. I used to, and I had to downgrade my Xorg packages and kernel every time.. It's really borked up.

It really feels like you have total control. Great! You don't wanna be using it when you don't wanna put some love in your OS though

---

### Post by handy on 2010-06-09
The ATi thing has improved dramatically on the FOSS side, & the AMD closed side at the moment.

I'm using the kernel .34, the associated dev packages for the ATi GPU, & xorg-server 1.8 at the moment & it's working fine.  The packages in the stable repos are working at least as well.

---

### Post by screaminj3sus on 2010-06-09
If you don't do a lot of 3d and aren't on a laptop the ati oss drivers are very usable right now (on 4xxx series and below). But power management still blows. fglrx is usable but video playback is still very disapointing compared to nvidia and even the open source drivers.

---

### Post by meganox on 2010-06-09
> **PsychoDevon said:**
> I am considering switching from Mint/Ubuntu to Arch.

1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


1. Ubuntu

2. Install was way easier than I was expecting thanks to the excellent wiki. Learned so much setting up things like power management and X11, the transparency of the system really lets you see what's goin on under the hood.

3. I'd say it's easier than Ubuntu.  When there's a problem I'm much more likely to find what package or file is causing it. 

Example: hibernation never worked under Ubuntu, I didn't know where to begin debugging and assumed I just had bad hardware for it. But because I had to install and configure it myself in Arch, the particular option that prevented it working got set right as I worked through the config.

4. Very. I was gravitating towards text based programs and tiling layouts, and it was so much easier to build a simple system than to try and strip Ubuntu down.

The reasons I switched are, Ubuntu was behind with some packages I wanted up to date. Even on a 6 month release cycle, some packages are many months older, and sometimes the versions that make the freeze have bugs that got fixed just outside the freeze, it's infuriating waiting for the fixed package.

Also, I found some design decisions to be bizarre, the whole notification bubble halfway down the screen was a farce IMO. I don't need a bubble to tell me I'm changing the volume, and I definitley don't need IM notifications pushed down the screen to accomodate a bubble that isn't even there. 

Having said all that, I have to say how grateful I am to Ubuntu and the community, I would never have been able to learn the skills I needed without a couple of years on a distro that makes entry to Linux that easy.

---

### Post by handy on 2010-06-09
> **screaminj3sus said:**
> If you don't do a lot of 3d and aren't on a laptop the ati oss drivers are very usable right now (on 4xxx series and below). But power management still blows. fglrx is usable but video playback is still very disapointing compared to nvidia and even the open source drivers.

On my HD2600Pro, I can't fault video playback. It is better than I have ever experienced with the fglrx/Catalyst drivers.

My display is 1920x1200 pixels.

I run nVidia on my 2nd machine & it is certainly not better than the ATi. It also uses a 24" display.

I'm sure hardware matters. Neither of these machines have anything near cutting edge GPU's in them.

---

### Post by screaminj3sus on 2010-06-09
> **handy said:**
> On my HD2600Pro, I can't fault video playback. It is better than I have ever experienced with the fglrx/Catalyst drivers.

My display is 1920x1200 pixels.

I run nVidia on my 2nd machine & it is certainly not better than the ATi. It also uses a 24" display.

I'm sure hardware matters. Neither of these machines have anything near cutting edge GPU's in them.

Don't get me wrong, its definitely better than it was. Before I couldn't even use opengl output without terrible flickering and REALLY pixelated video. Now I can finally get tear free playback if I use mplayer with opengl output, use unredirect fullscreen windows in compiz, and force vsync in ccc, and watch the video in fullscreen. But video playback is a really basic feature that should work decently. The fact that I have to use a certain program and workarounds is still ridiculous. With the oss drivers, and nvidia's proprietary driver it just works with no tearing in any player, and same thing with windows.

---

### Post by handy on 2010-06-09
I've been using mostly the open drivers since last August 2009, & the improvements that I've experienced are phenomenal. Many people think that it is all developing so slowly, but that is their mistake as they are obviously looking at the situation from a purely personal perspective.

The changes that have happened in well under 12 months are spectacular. Primarily thanks to AMD's help in making the technical details available & also to a lesser degree their contributions code wise.

I'm sure that within the next 12 months you will have excellent video & more via the open drivers.

I've been using the dev' versions of the kernel, mesa & such for some time (occasionally go back to stable) it has rarely given me any trouble, when it does I stop using it for a couple of weeks while the development sorts out the problem(s).

Anyway, the only thing we can be sure of is change. :)

---

### Post by WinterMadness on 2010-06-10
i dont really like arch because in order to use it youll need to access tutorials just to get a gui going. You need to find out where it stores the repo information and work with it.

Seems kind of illogical to me. It should have clear instructions for basic usage in the / folder at the very least

---

### Post by keifer on 2010-06-10
> **PsychoDevon said:**
> 1) What OS you used before Arch.

2) What were your initial impressions.

3) After installation, is using it easy-to-use day-to-day?

4) Are you happy using it.


1) Mac OS X, FreeBSD, NetBSD, OpenBSD, Darwin, and various Linux distros.

2) Sane defaults, fair documentation, helpful community. Having rc setup similar to BSDs was nice.

3) Yes. Gentoo had given me some worries about a rolling release, but I have always found Arch to be as stable as any other major distro.

4) It gets the job done, and stays out of your way while doing it. Linux is no longer my day to day OS, but Arch is still my favorite distribution. I make sure I keep an install disk handy.

---

### Post by swoll1980 on 2010-06-10
I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

---

### Post by BoneKracker on 2010-06-10
> **swoll1980 said:**
> I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

:lol: :p

"Arch is Bloatware"

---

### Post by Tibuda on 2010-06-10
> **swoll1980 said:**
> I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

No, it has been said thousand times in this thread. You can achieve that with ubuntu minimal disk.

---

### Post by BoneKracker on 2010-06-10
> **danielrmt said:**
> No, it has been said thousand times in this thread. You can achieve that with ubuntu minimal disk.

Wouldn't that depend on how one defines "minimal"?

As an example, I don't use tcpd because it is redundant with features of xinetd.  Therefore, I don't want that extra tcp wrappers code in any of my binaries.  Does Ubuntu Minimal allow me to "opt out" of tcp wrappers, or does it force it on me?

---

### Post by Tibuda on 2010-06-10
> **BoneKracker said:**
> Wouldn't that depend on how one defines "minimal"?

As an example, I don't use tcpd because it is redundant with features of xinetd.  Therefore, I don't want that extra tcp wrappers code in any of my binaries.  Does Ubuntu Minimal allow me to "opt out" of tcp wrappers, or does it force it on me?

Yes, but both distros "force" different things. Arch does not allow me to not install source headers, while in Debian/Ubuntu, they are only installed in *-dev packages. In Arch, both SSH server and SSH client are in the same package (openssh), while in Debian/Ubuntu they are in different packages (openssh-server and openssh-client). I don't have any use for a SSH server in my laptop, but I use the SSH client often. See also [this Techsnap rant](http://www.youtube.com/watch?v=flmX9GYwyiI) about Arch package dependencies.

EDIT: Do I care? No. I always have the latest stable kernel, the latest Firefox, the latest OpenOffice, the latest GIMP. What I want to say is that there are more reasons for people to use Arch than "have a customized system that only has the stuff you want". This is surely not the reason I use Arch.

---

### Post by Tomone on 2010-06-10
> **chessnerd said:**
> A fully set up computer is like a sandwich ready to be eaten. The operating system is the bread, something only necessary to hold the ingredients (applications) in while you enjoy your lunch. Sure, bad bread can ruin a sandwich, and good bread can make a sandwich better, but it really isn't the most important part.
I hate to go off on a tangent and complain about an analogy, but I can't this one go without saying something. I have a problem with this because bread is the MOST IMPORTANT part of a sandwich. Without good bread, you can't have a good sandwich. This also applies to pizza and anything else made with bread.
I like bread.

---

### Post by BoneKracker on 2010-06-10
> **danielrmt said:**
> Yes, but both distros "force" different things. Arch does not allow me to not install source headers, while in Debian/Ubuntu, they are only installed in *-dev packages. In Arch, both SSH server and SSH client are in the same package (openssh), while in Debian/Ubuntu they are in different packages (openssh-server and openssh-client). I don't have any use for a SSH server in my laptop, but I use the SSH client often. See also [this Techsnap rant](http://www.youtube.com/watch?v=flmX9GYwyiI) about Arch package dependencies.

EDIT: Do I care? No. I always have the latest stable kernel, the latest Firefox, the latest OpenOffice, the latest GIMP. What I want to say is that there are more reasons for people to use Arch than "have a customized system that only has the stuff you want". This is surely not the reason I use Arch.
Arch doesn't have anything to do with what I just said.  I meant that Ubuntu Minimal's ability to deliver a "minimal" system was questionable, depending on how one defines "minimal".  I would add that Arch's is as well, if maybe somewhat less so.

---

### Post by eagleton on 2010-06-11
> **BoneKracker said:**
> :lol: :p

"Arch is Bloatware"

Well, concerning Openoffice it's true - in Arch you have to install the [complete thing]("http://bbs.archlinux.org/viewtopic.php?pid=600608"), while it's modularized in Ubuntu and Fedora. So every update of Oo.org in Arch is over a 100megs. Fedora is best here, as it has delta updates and modularized packages of Oo.org, which comes handy for people with slow connections.

---

### Post by del_diablo on 2010-06-11
> **WinterMadness said:**
> i dont really like arch because in order to use it youll need to access tutorials just to get a gui going. You need to find out where it stores the repo information and work with it.

1. Intall xorg
2. Install VESA
3. Start TWM
4. Get on configuring the system?
I like arch for bothering to be barebone, because its so much worth it.

---

### Post by dyltman on 2010-06-11
> 1) What OS you used before Arch.

Ubuntu, openSUSE, Windows, Mac OS x, fedora, mint.

> 2) What were your initial impressions.

The installation was really hard, I had never done something similar before but I wanted to do this to learn more about linux etc and yeah you did learn a hell lot from installing it.

> 3) After installation, is using it easy-to-use day-to-day?

Yes, very easy. It feels like everyday it gets easier and easier to use.

> 4) Are you happy using it.

Yes, once you get past the installation it becomes a very cool OS and you really feel like you have control, you know where to go when you have a problem etc.

---

### Post by MisfitI38 on 2010-06-11
> **swoll1980 said:**
> The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that.. 

One could easily make the argument that *any* system with a package manager could potentially 'fail miserably' at providing an OS that 'only has the stuff you want on it' especially in the hands of an inexperienced user bent on blaming their dissatisfaction, frustrations and ignorance on external forces. 
However, a more reasonable view would be to acknowledge that there are different levels of minimalism, that these levels must be compromised when balanced with convenience or expedience, and that creating such a strawman argument as quoted above does not lend any weight to one's position.
 
One could just as easily conclude that if *you* have failed to create an Arch system which 'only has the stuff you want on it', then the fault lies in *your* inability to do so, especially in light of the tools and documentation provided with Arch. 
ABS is a user-customizable ports system, allowing one to create their own build scripts and system-trackable packages, simply and easily. By creating and customizing their own PKGBUILDs to pull in upstream sources, the only limitations are within the capable user's imagination and creativity. The resulting builds, and therefore the resulting system, can be as simple or as bloated as you make it.

Arch only claims to be what you make it.

> ..so whats the point?
The point in using it? Undoubtedly, Arch users choose their distro because it's fun, enjoyable, and it suits them.

---

### Post by RiceMonster on 2010-06-11
> **swoll1980 said:**
> I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

Well obviously it's not Ubuntu, so there is clearly no point.

---

### Post by LowSky on 2010-06-11
> **kelvin spratt said:**
> I've used Arch since 1997 as my main distro. And have never had the Xserver crash in all that time, It is also the most stable distro I have used, can't say the same for Ubuntu/fedora

Really 1997? I ask because the first release was on March 11, 2002.

> Arch Linux is an independently-developed i686/x86-64 community distribution, based on a rolling-release model and targeted at competent GNU/Linux users which offers large binary repositories and full-featured package management as well as a ports-like packaging system. Development focuses on a balance of minimalism, elegance, code correctness and modernity. **Version 0.1 (Homer) was released March 11, 2002. **


Sources:
[http://en.wikipedia.org/wiki/Arch_Linux](http://en.wikipedia.org/wiki/Arch_Linux)
[http://wiki.archlinux.org/index.php/Arch_Linux](http://wiki.archlinux.org/index.php/Arch_Linux)

---

### Post by BoneKracker on 2010-06-11
> **eagleton said:**
> Well, concerning Openoffice it's true - in Arch you have to install the [complete thing]("http://bbs.archlinux.org/viewtopic.php?pid=600608"), while it's modularized in Ubuntu and Fedora. So every update of Oo.org in Arch is over a 100megs. Fedora is best here, as it has delta updates and modularized packages of Oo.org, which comes handy for people with slow connections.
The whole concept of an office suite is ... dang!  I forgot that yesterday when I was listing compulsive behavioral disorders that Microsoft has saddled humanity with:

1. screensavers
2. defragging
3. Ctrl+Alt+Delete

... and ...

4. Absurdly huge "Office Suites"  wtf

---

### Post by BoneKracker on 2010-06-11
> **RiceMonster said:**
> Well obviously it's not Ubuntu, so there is clearly no point.

I was looking at Distrowatch the other day, and the number of "Independent" distros has become appallingly low.  Among the top (most web hits) distros, there are only a handful left.  And what's really nauseating is the number of so-called "distros" listed there that are basically Ubuntu with somebody's favorite apps and settings.  I was looking to see how Foresight and the other Conary-based distros were coming along, and it's been completely bumped off the list by a bunch of non-value-added wannabes whose innovations amount to a "theme" and _maybe_ choice of window manager.

It is also disturbing how most Ubuntu users have no idea what portions of what they're using came from Ubuntu vs. Debian vs. elsewhere.

---

### Post by BoneKracker on 2010-06-11
[QUOTE=LowSky;9445320]Really 1997? I ask because the first release was on March 11, 2002.

The internet wayback machine agrees with you:
Here's the Arch website in March (courtesy of the Internet Archive Wayback Machine), showing the release announcement.
[http://web.archive.org/web/20020328043401/http://www.archlinux.org/](http://web.archive.org/web/20020328043401/http://www.archlinux.org/)

More, for you Arch fanbois:
[http://web.archive.org/web/*/archlinux.org](http://web.archive.org/web/*/archlinux.org)

Maybe he meant 2007?

---

### Post by screaminj3sus on 2010-06-11
> **swoll1980 said:**
> I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

Any proof of how it "fails" at that, it seems pretty successful at it to me...

---

### Post by squilookle on 2010-06-11
Arch is worth it. I used it for 6 months and was very happy. It is time consuming but easy to install if you follow the guides. Updates are easy to do and I loved always having the latest software.   When I used Ubuntu on the desktop, I found myself downloading Firefox from Mozilla as I didnt like not having the latest version.   Also, it was the only time I got the facebook chat plugin for pidgin working in Linux, as Ubuntu at the time had an old version of a library that did not work with the plugin: Arch had the up to date one that did work.   Arch achieves a balance of giving you the chance to learn alot about your system (by making you use command line tools and update the config files) with the convenience of an update system that is not time consuming, due to its speed and use of binaries.

---

### Post by BoneKracker on 2010-06-11
> **squilookle said:**
> Arch achieves a balance of giving you the chance to learn alot about your system (by making you use command line tools and update the config files) with the convenience of an update system that is not time consuming, due to its speed and use of binaries.

So how the update system achieve this speed and how fast is it compared to other update systems?

---

### Post by squilookle on 2010-06-11
Couldn't tell you exactly how it achieves it. I can tell you it always felt slightly faster than apt-get to me, and a fair bit faster than any rpm based system I ever used. 

There is a "rank mirrors" script that you can run, and it picks out the fastest mirror to download the packages from, that will have had something to with it. 

You update from the CLI using pacman, which is very light weight and did appear to use less memory and CPU than any .deb or .rpm system I ever used, GUI or CLI. Again, this might haved helped with the speed issue, especially as I was on limited hardware at the time.

---

### Post by GSF1200S on 2010-06-11
Yes. Yes it is.

---

### Post by GSF1200S on 2010-06-11
> **BoneKracker said:**
> So how the update system achieve this speed and how fast is it compared to other update systems?

Arch integrates community software into a repo called the "AUR." On top of this, you can use wrappers like Bauerbill, Yaourt, or Clyde which will install from the official repos as well as the AUR. These pkgbuilds (in the aur) are updated and when you run:
```
yaourt -Syu --aur
```
You get updates for everything installed on your system (if any are available).

That said, the AUR isnt perfect (neither is Arch as a whole). I like how you can be uber selective with Gentoo in terms of what you have installed, but to me its often not worth the hassle (that said I am maintaining a Gentoo install atm). Arch is another approach to Linux, focusing on binary packages, rolling release stucture, its AUR/ABS, simplicity, and it being built the way you need it built. Its pretty much perfect for me..

---

### Post by BoneKracker on 2010-06-11
> **squilookle said:**
> Couldn't tell you exactly how it achieves it. I can tell you it always felt slightly faster than apt-get to me, and a fair bit faster than any rpm based system I ever used. 

There is a "rank mirrors" script that you can run, and it picks out the fastest mirror to download the packages from, that will have had something to with it. 

You update from the CLI using pacman, which is very light weight and did appear to use less memory and CPU than any .deb or .rpm system I ever used, GUI or CLI. Again, this might haved helped with the speed issue, especially as I was on limited hardware at the time.

Sounds all good. What's the package manager written in?  Python?

Is the pkg-builder (or whatever it's called) useful at the end user level for building from source, or is it mostly just useful for putting new packages into the repositories?

---

### Post by GSF1200S on 2010-06-11
> **BoneKracker said:**
> Sounds all good. What's the package manager written in?  Python?

Is the pkg-builder (or whatever it's called) useful at the end user level for building from source, or is it mostly just useful for putting new packages into the repositories?

Pacman (Arch's package manager) is written in C. Pacman is very fast, though alot of it depends on using a mirror that is low on latency (you can check the mirrors, mirrorselect, etc). As a comparison, Gentoo's portage is written in python (in my experience, it is not that fast although it is very powerful).

ABS is a build system designed for building things from source. While Pacman offers EVERY package in the main repos (core, extra, community, testing) in binary form, ABS offers EVERY package in source form. At that point, you copy the package folder from your ABS tree into a build directory of your choosing and run:
```
makepkg -s
```
Which will compile from source a binary package specifically for your system, while any dependencies will automatically be installed from the binary repos. If you use third-party tools (which are fantastic) like Pacbuilder, you can even have the dependencies compiled from source as well.

---

### Post by BoneKracker on 2010-06-11
> **GSF1200S said:**
> ABS is a build system designed for building things from source. While Pacman offers EVERY package in the main repos (core, extra, community, testing) in binary form, ABS offers EVERY package in source form. At that point, you copy the package folder from your ABS tree into a build directory of your choosing and run:
```
makepkg -s
```
Which will compile from source a binary package specifically for your system, while any dependencies will automatically be installed from the binary repos. If you use third-party tools (which are fantastic) like Pacbuilder, you can even have the dependencies compiled from source as well.
Written in C.  Nice.

What about user-level configuration of compiler options?  Can a user set system-wide defaults that are respected by all packages and then also set package-specific options?  Are the package-specific options remembered from build to build and version to version?

---

### Post by GSF1200S on 2010-06-11
> **BoneKracker said:**
> What about user-level configuration of compiler options?  Can a user set system-wide defaults that are respected by all packages and then also set package-specific options?  Are the package-specific options remembered from build to build and version to version?

I havent gotten to into cflags, but remember that Arch isnt Gentoo. You can accomplish these things, but it would be a little work. For global values you would edit /etc/makepkg.conf, which contains this section:
> #-- Exclusive: will only run on x86_64
# -march (or -mcpu) builds exclusively for an architecture
# -mtune optimizes for an architecture, but builds for whole processor family
CFLAGS="-march=native -O2 -pipe"
CXXFLAGS="-march=x86-64 -mtune=generic -O2 -pipe"
LDFLAGS="-Wl,--hash-style=gnu -Wl,--as-needed"
#-- Make Flags: change this for DistCC/SMP systems
#MAKEFLAGS="-j2"

For individual Cflags, you would edit the pkgbuild for the specific package you are compiling. So, yes it can be accomplished.

Now, as far as it remembering your cflags when you upgrade, you would need to check Pacbuilders options and see. Perhaps it does have a config file that deals with this, but perhaps not. I will say that Arch has no plans to incorporate USE flags- thats not part of its KISS theory.

**EDIT** Bout to run an errand soon, but when I return I will check and see what Pacbuilder offers in this regard.

---

### Post by llawwehttam on 2010-06-11
1. Ive used a lot of distros, probably 50+
2.Really like it.
3. Really is easy especially with the wiki to help.
4. I've been using it now for about 6 months and don't really want to use anything else.

---

### Post by GSF1200S on 2010-06-11
[poeticrpm@geekdom ~]$ pacbuilder --help
-------------------------------
 PacBuilder, by Andrea Cimitan 
-------------------------------

A tool to massively recompile packages from sources
It currently fetches both ABS and AUR

USAGE:
  pacbuilder [options] package|repository

OPTIONS:
  General:
    --help                  print this help
    --clean                 remove previous log
    --gccinfo               print current compilation flags
    --nocolor               do not use any color
    --notitle               do not print the title
    --noresume              do not resume
  Install:
  (-S),    --install        build specified packages
  (-S) -b, --builddeps      build and install the dependencies
  (-S) -e, --edit           be verbose and edit PKGBUILD
  (-S) -f, --force          force install, overwrite conflicting files
  (-S) -k, --keepdeps       keep makedepends after install
  (-S) -s, --search <regex> search for packages matching <regex>
  (-S) -u, --sysupgrade     build the updated packages
  (-S) -v, --verbose        print makepkg output
  Additional parameters:
    -p, --pretend           print the final list of packages to be installed
    -n, --noconfirm         do not ask for any confirmation
    -m, --match <regex>     only install packages matching <regex>
    -d, --deplist           recursively list all dependencies first
        --export <dir>      copy packages into a dir after build
  Type:
    --world                 recompile both deps and explicit
    --explicit              recompile explicitely installed packages
    --devel                 recompile only installated devel packages
  Target repository:
    --core                  recompile packages in core
    --extra                 recompile packages in extra
    --testing               recompile packages in testing
    --community             recompile packages in community
    --community-testing     recompile packages in community-testing
    --aur                   recompile packages in aur


Output from pacbuilder --help

---

### Post by Barrucadu on 2010-06-11
> **swoll1980 said:**
> I say no. The whole point of Arch was to have a customized system that only has the stuff you want on it. It fails pretty miserably at that, so whats the point?

How? Things don't appear unless you install them (or something which depends on them, of course).

**edit:** Oops, didn't notice there was a whole extra page here..

---

### Post by BoneKracker on 2010-06-11
> **GSF1200S said:**
> Now, as far as it remembering your cflags when you upgrade, you would need to check Pacbuilders options and see. Perhaps it does have a config file that deals with this, but perhaps not. I will say that Arch has no plans to incorporate USE flags- thats not part of its KISS theory.

**EDIT** Bout to run an errand soon, but when I return I will check and see what Pacbuilder offers in this regard.

I appreciate the info.  I've been watching several distros for a while, and thinking about switching (or at least giving it a serious try -- more than just a look).  I can live without USE flags -- sometimes they're more of a problem than a convenience.  (There are only so many packages that I would want to build from source anyway, and I don't mind tweaking them in the terms used by the original developers.)  However, I would like to be able to keep my per-package compile-time configurations persistently, in a convenient manner (i.e., not having to hand-edit makefiles every time I build it).

---

### Post by MisfitI38 on 2010-06-11
> **BoneKracker said:**
>  However, I would like to be able to keep my per-package compile-time configurations persistently, in a convenient manner (i.e., not having to hand-edit makefiles every time I build it).
Simple and straightforward using ABS. 
See 
[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS) and [http://wiki.archlinux.org/index.php/PKGBUILD](http://wiki.archlinux.org/index.php/PKGBUILD)

---

### Post by BoneKracker on 2010-06-12
> **MisfitI38 said:**
> Simple and straightforward using ABS. 
See 
[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS) and [http://wiki.archlinux.org/index.php/PKGBUILD](http://wiki.archlinux.org/index.php/PKGBUILD)

Sounds good.  I think I'll pop it on one of my machines and run it a while.  I've also been thinking about switching a box back to OpenBSD, which I thought was pretty excellent too (although not so much for desktop-ish purposes).

---

### Post by squiddy on 2010-07-01
just try, and you will love it :)

---

### Post by Noz3001 on 2010-07-02
It's worth installing on a separate partition to mess with. That's about it.


My answers:
1) Xubuntu, Gentoo, Fedora 9

2) Too much time spent configuring, didn't get much back. Wasn't as fast as people say. In fact, once I had all the daemons I needed in the array, it was much slower than Ubuntu.

3) No, it breaks a lot. -Syu breaks things leaving you to fix it.

4) No

---

### Post by sukigenseki on 2010-07-02
I don't understand what people were doing to their systems to get pacman to bork their stuff, but for me the only issue I had on Arch that I could never figure out was a Pulseaudio thing. My laptop has an LFE speaker on the bottom that is a crappy sub/speaker hybrid thing, and I have to make a custom analog-output.conf for my Pulseaudio to get that to work with volume change just like everything else otherwise it is either on full blast, or muted which makes the sound on the rest of the speakers tinny and sad. This only friggin' works on Ubuntu though as I have tried every thing I can think of on Arch to get Pulseaudio to behave *any* different than how it does upon installation. I couldn't get OSS to handle my LFE at all, so I said to hell with it and just keep using Ubuntu, because with checkinstall you get some of the perks that pacman gives you just without ABS, and AUR. AUR really kicks *** though.

---

### Post by Noz3001 on 2010-07-03
> **sukigenseki said:**
> I don't understand what people were doing to their systems to get pacman to bork their stuff, but for me the only issue I had on Arch that I could never figure out was a Pulseaudio thing. My laptop has an LFE speaker on the bottom that is a crappy sub/speaker hybrid thing, and I have to make a custom analog-output.conf for my Pulseaudio to get that to work with volume change just like everything else otherwise it is either on full blast, or muted which makes the sound on the rest of the speakers tinny and sad. This only friggin' works on Ubuntu though as I have tried every thing I can think of on Arch to get Pulseaudio to behave *any* different than how it does upon installation. I couldn't get OSS to handle my LFE at all, so I said to hell with it and just keep using Ubuntu, because with checkinstall you get some of the perks that pacman gives you just without ABS, and AUR. AUR really kicks *** though.

You must not have used it for a long time. -Syu breaks eventually

---

### Post by Yes on 2010-07-03
It's not that -Syu breaks, more often the problem is that one of the programs you've updated has a bug or something that ends up breaking stuff.  I've been fine for over a year now, but there have been a couple times in the past where dbus or hal were totally screwy after being updated, and the only solution was to revert to the previous version.  But when you use a rolling release distro, that stuff is just going to happen.

---

### Post by Tibuda on 2010-07-03
> **Noz3001 said:**
> You must not have used it for a long time. -Syu breaks eventually

Nice generalization. It have never happened to me, but I can see how it can happen. That's why I'm not one of those preachers. 'apt-get dist-upgrade' also breaks for the same reason.

---

### Post by Noz3001 on 2010-07-03
> **danielrmt said:**
> Nice generalization. It have never happened to me, but I can see how it can happen. That's why I'm not one of those preachers. 'apt-get dist-upgrade' also breaks for the same reason.

Probably, but do you do that every day?

---

### Post by wojox on 2010-07-03
> Is Arch REALLY worth installing?

Yes, It's a great learning experience. Just read the wiki.

---

### Post by Shazzam6999 on 2010-07-03
> **Noz3001 said:**
> Probably, but do you do that every day?

I don't know any Arch users that do a system update everyday. Seems a lot of the arguments against Arch boil down to unfounded generalizations. Why all the hate?

---

### Post by Yes on 2010-07-03
> **Shazzam6999 said:**
> I don't know any Arch users that do a system update everyday. Seems a lot of the arguments against Arch boil down to unfounded generalizations. Why all the hate?

I try do a full upgrade everyday.  Why wouldn't I?  I used to not but I would forget to do it for a month or longer, and I'd have hundreds of packages that needed to be upgraded.  And it's much more difficult to figure out what package is broken when you've just upgraded 150 packages rather than just two or three.

---

### Post by WinterRain on 2010-07-03
> **Shazzam6999 said:**
> I don't know any Arch users that do a system update everyday. Seems a lot of the arguments against Arch boil down to unfounded generalizations. Why all the hate?

Why all the hate for ubuntu from some people? That's life I guess.

But to stay on topic, at the end of the day, whether I use windows, mac, or linux, I wind up doing the same things on my computer day after day. I just don't see any advantage for using arch to do the same things I'm doing now on ubuntu. Which btw, works 100% perfect. Arch could not do any better. (for me)

Doing hours of configuration isn't going to make my computing experience any better than it already is. When something works flawlessly, why change? But to be honest, I do occasionally like to try out other distros to see what's happening. But something about arch just does not appeal to me. Different strokes for different folks, right? Choice is good, and that's one of the many reasons I use linux.

---

### Post by Tibuda on 2010-07-04
> **Noz3001 said:**
> Probably, but do you do that every day?

yep, unless I see kernel, xorg or glib in the update list, which I would do some research before doing it.

---

### Post by Noz3001 on 2010-07-04
> **danielrmt said:**
> yep, unless I see kernel, xorg or glib in the update list, which I would do some research before doing it.

Was talking about Ubuntu, not Arch

---

### Post by Tibuda on 2010-07-04
> **Noz3001 said:**
> Was talking about Ubuntu, not Arch

hmmmm....

It makes no sense to do it everyday in Ubuntu, because their repos are frozen. It only makes sense if you are using the development version before the feature frezze, which is kind of a rolling release distro.

---

