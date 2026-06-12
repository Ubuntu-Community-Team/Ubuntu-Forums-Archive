---
title: "Fastest OS?"
date: 2008-09-01
forum: Other OS Talk
---

### Post by Riyonuk on 2008-09-01
I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)

---

### Post by tdrusk on 2008-09-01
> **Riyonuk said:**
> I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)

One of the fastest OS is Gentoo. Everything is compiled for your computer. You tell all the Gentoo all the hardware you have and it makes it work with that hardware, but not with anything else. This is what makes it fast. 

Gentoo is hard. You have to compile everything for your computer, which takes longer than just apt-get.

If you don't want that hassle, get Arch Linux. If you want apt get Debian. It is extremely fast and stable also.

---

### Post by insane_alien on 2008-09-01
to get the absolute best performance out of your OS then yes, you would need to compile your own kernel so you don't have stuff in it that you'll never need.

however, with modern computers you would need to benchmark to the microsecond to tell if it was making a difference or not.

---

### Post by Fri13 on 2008-09-01
> **Riyonuk said:**
> I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)

To get fastest system, you need to compile your own operating system (Linux is the operating system, not just a kernel).
It is actually bretty dificult for first timer to compile it, and it is 99% change that first time goes wrong, so do not remove old Linux from grub/lilo. 

Then you need to make your system faster, remove all unwanted services from booting, change Xorg for faster one (for of the Xorg), desktop environment to window manager etc etc.

Linux is very fast operating system but usually there is bundled so much stuff for it by default, so it is slower.

I suggest you start training things by not using Ubuntu, but changing distribution to Gentoo so you can "more easily" customize your own system. But I dont promise you get over 3-5% speed gain by that. Biggest speed improvents comes if you dont start services what you dont need.

---

### Post by Wiebelhaus on 2008-09-01
[PUPPY]("http://www.puppylinux.org/") is the fastest with a GUI I've found.

---

### Post by Wiebelhaus on 2008-09-01
> **tdrusk said:**
> One of the fastest OS is Gentoo. Everything is compiled for your computer. You tell all the Gentoo all the hardware you have and it makes it work with that hardware, but not with anything else. This is what makes it fast. 

Gentoo is hard. You have to compile everything for your computer, which takes longer than just apt-get.

If you don't want that hassle, get Arch Linux. If you want apt get Debian. It is extremely fast and stable also.

Yea! apparently the newest revision of Debian is kicking some major tail , I've yet to test though , can't wait for release , I've always adored Debian which is why I love Ubuntu , Ubuntu is Debain that has been refined with a fine tooth comb.

---

### Post by tdrusk on 2008-09-01
> **sx66gns said:**
> Yea! apparently the newest revision of Debian is kicking some major tail , I've yet to test though , can't wait for release , I've always adored Debian which is why I love Ubuntu , Ubuntu is Debain that has been refined with a fine tooth comb.
Nah Ubuntu just made Debian it easier. Ubuntu adds a bunch of programs for everybody. 

Both are good for different things/people.

Riyonuk: Maybe try Mepis. It is kind of a mix between Ubuntu and Debian. It's VERY fast since it is Debian Etch based and has a light KDE interface.

---

### Post by Wiebelhaus on 2008-09-01
> **tdrusk said:**
> Nah Ubuntu just made Debian it easier. Ubuntu adds a bunch of programs for everybody. 

Both are good for different things/people.

Riyonuk: Maybe try Mepis. It is kind of a mix between Ubuntu and Debian. It's VERY fast since it is Debian Etch based and has a light KDE interface.


Just made it easier? Laughable man.

---

### Post by fistfullofroses on 2008-09-01
You should also look into micro-distributions such as SliTaz, Puppy, DSL, and so on. These distributions are meant to work on machines with very limited hardware. When you use them on newer hardware, you get a very responsive system.

While Gentoo is speedy in use, you are going to spend quite a bit of time setting it up, only to gain fractions of seconds. I would think it not worth while. Were I to use a source-based system, it would likely be Linux From Scratch.

---

### Post by tdrusk on 2008-09-01
> **sx66gns said:**
> Just made it easier? Laughable man.
I meant Ubuntu made Debian easier. Of course they have done a lot for Debian's development, but ease of use and promotion are the main reasons people use Ubuntu over Debian on their desktops.

---

### Post by Riyonuk on 2008-09-01
OMG, you guy's just threw a bunch of random OS's at me XD

If it's millioseconds were talking about here, then I'd go with Arch. One thing though, it will be my "stable" computer, and I can't risk the system not working, as it will have school related documents. And with Arch, you update every single day, which is kinda retarded, I NEVER updated Windows, not even once. Maybe that's why mine's so fast :P

---

### Post by cardinals_fan on 2008-09-01
[SliTaz]("http://www.slitaz.org/en/") is fast and light, but I've had some issues using it (hardware problems :().
[URL="http://www.slackware.com/"]
Slackware[/URL] is very fast if installed correctly.

[Paldo]("http://www.paldo.org/") is absurdly fast, but I can't use it because NVIDIA broke their latest drivers for my card (which are included in Paldo), and I can't get the older ones to install.  This is a truly awesome OS, and I really wish that I could use it.

[Vector Light]("http://vectorlinux.com/") is fast and decent (if you can stomach slapt-get).
[URL="http://www.archlinux.org/"]
Arch[/URL] is very fast, but I've had some stability problems.
[URL="http://www.netbsd.org/"]
NetBSD[/URL] is fast and clean.  It has some problems with my hardware (that means you, NVIDIA!), but is a great OS.

[Haiku]("http://www.haiku-os.org/") is so fast that it's obscene, but the hardware/software support is abominable.  It's also very unstable (early in development).

---

### Post by tel93 on 2008-09-01
> **Riyonuk said:**
> I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)

Debian + XFCE with NO GNOME apps

---

### Post by init1 on 2008-09-01
The fastest would be FreeDOS, but I doubt that you would want to use that ;)
You can compile your kernel, but I don't think it's worth the trouble. A minimal Debian install is rather fast. In fact, they should be coming out with a new stable some time this month.

---

### Post by swoll1980 on 2008-09-01
Pcbsd really fast and it's full a featured kde desktop as well. My 6 year old celeron flew with pcbsd installed on it. I don't like kde so it's not for me. If they ever get a gnome version I'm there.

---

### Post by kk0sse54 on 2008-09-01
Most distros when installed via a minimal install along with a light WM and a slimmed down boot time can be blazing fast of course there are some that stand out in front of others which seemed to have all been named for the most part. Adding to the list you can check out Crux if your up to using a distro aimed for advanced users

---

### Post by tdrusk on 2008-09-01
> **Riyonuk said:**
> ]And with Arch, you update every single day, which is kinda retarded, I NEVER updated Windows, not even once. Maybe that's why mine is so fast :P
Nobody is forcing you to upgrade Arch. It is a rolling release. It is not mentally challenged, just different.

---

### Post by rsambuca on 2008-09-01
I think any OS will be fast on that rig.  The only difference you will see on that system is whether things open in the blink of an eye or just half a blink of an eye.

---

### Post by mips on 2008-09-02
> **Riyonuk said:**
> And with Arch, you update every single day, which is kinda retarded,...

It's a rolling release distro....

I must keep this in mind next time I see users of other distros biatching about getting newer versions of software etc. ;)

---

### Post by LateNiteTV on 2008-09-02
you can compile freebsd from source. blazing fast on all my systems.

---

### Post by karlmp on 2008-09-02
xubuntu

---

### Post by gjoellee on 2008-09-02
Some suggestions:

-Yoper (supports all .deb, .rpm and .tar
-wattOS
-Fresco
-Xubuntu
-Damn Small Linux
-Puppy Linux
-Gentoo
-Debian
-Turbolinux
-Small Linux
-Feather Linux

---

### Post by Vexed Arcanist on 2008-09-02
Xubuntu is a bad idea.  The current state of Xubuntu is Ubuntu with XFCE.  It is very bloated for an XFCE DE.  If you are gonna go that route just use Ubuntu's server install and install XFCE4 on it's own, don't include Ubuntu-Desktop or use Xubuntu.  Build what you need on top of that.

TinyMe is a very fast, very slim version of PCLinuxOS.  Wanted to toss it in to this discussion.

If you just want to cut some of the slowness out of the standard Ubuntu, disable Compiz (right click desktop, switch to Effects or whatever the last tab is, and go with None).  Then rotate out heavier gnome apps for slimmer apps that can function just as well, on a case by case basis.  You can also opt for a different WM if you want to get rid of Gnome, but then you are best served doing a net install and building up.

---

### Post by snowpine on 2008-09-02
I have been messing around with SliTaz lately. It is so incredibly fast, mostly because it is only 25mb and runs entirely from RAM. Yet somehow, it feels completely modern. Definitely worth checking out if you don't have a lengthy list of "must have" applications (the repositories are currently a bit limited).

ps I like Xubuntu, but it is not even in the same league as the other options people have been mentioning.

---

### Post by Riyonuk on 2008-09-02
My ideal distro would be one like Arch, in which you start from scratch, but one that's updated half a year, like Ubuntu. It's funny, I read alot about how people wan't those updates, but why? So you fixed a couple of bugs...amazing. Of course this is Linux we're talking about here, and I'm sure there's lots of developers that need those bug fixes. But do I really need to have version 3.09 of Firefox instead of .08? Will the world implode? I think not :P

---

### Post by zmjjmz on 2008-09-03
Fastest OS?
Probably an old BASIC OS from the 70s.
Sure it can't do much, but you wanted speed right?

---

### Post by fwojciec on 2008-09-03
> **Riyonuk said:**
> My ideal distro would be one like Arch, in which you start from scratch, but one that's updated half a year, like Ubuntu. It's funny, I read alot about how people wan't those updates, but why? So you fixed a couple of bugs...amazing. Of course this is Linux we're talking about here, and I'm sure there's lots of developers that need those bug fixes. But do I really need to have version 3.09 of Firefox instead of .08? Will the world implode? I think not :P

Maybe try "stable" version of Frugalware.  Their "current" version is essentially a rolling release, while "stable" follows a 6 months release cycle.  Frugalware uses pacman, Arch linux package manager.

Slackware or Debian might also be good options if you want a stable set of packages that aren't constantly updated.

---

### Post by wolfen69 on 2008-09-03
give this thread a break. the fastest is what you have. but someone out there is faster..... so? someone is always faster. i live with it.

---

### Post by wolfen69 on 2008-09-03
> **fwojciec said:**
> Maybe try "stable" version of Frugalware.  Their "current" version is essentially a rolling release, while "stable" follows a 6 months release cycle.  Frugalware uses pacman, Arch linux package manager.

Slackware or Debian might also be good options if you want a stable set of packages that aren't constantly updated.

btw, frugalware aint going anywhere.

---

### Post by djbsteart1 on 2008-09-03
XFCE is getting pretty heavy, go with JWM, ICE, LXDE or the like, also, DSBSD is insanely fast, but for your needs, PC-BSD would be about right.

---

### Post by cardinals_fan on 2008-09-03
> **wolfen69 said:**
> btw, frugalware aint going anywhere.
Do you have any evidence to back that claim up?

---

### Post by snowpine on 2008-09-03
> **wolfen69 said:**
> give this thread a break. the fastest is what you have. but someone out there is faster..... so? someone is always faster. i live with it.

Yes, but it is fun to discuss! :) If it weren't for these forums, I would still suffering through "vanilla" Ubuntu Gnome on my old laptop...

I just figured out last night how to run SliTaz as a persistent Live USB, hooray! It is super-fast.

---

### Post by Stan_1936 on 2008-09-03
**Vector Linux Light Edition**........... WOW!!!

**Blazing speed**, almost made me feel that the system was Core 2 Duo when  it is nowhere near even a Pentium4.  It will work on systems with 64 MB RAM.  It uses Fluxbox and is a Slackware based distro.

HIGHLY RECOMMEND taking a look!!!

---

### Post by Antman on 2008-09-03
> **Riyonuk said:**
> I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)
If you want speed, try Sidux. The full KDE version installs in under 8min, and the XFCE version installs in under 4min. It's also a rolling distro (Debian Sid with custom scripts) so you only need to install it once and just update from then on.

---

### Post by Antman on 2008-09-03
> **zmjjmz said:**
> Fastest OS?
Probably an old BASIC OS from the 70s.
Sure it can't do much, but you wanted speed right?

:lolflag:

---

### Post by Bart_D on 2008-09-03
> **Antman said:**
> If you want speed, try Sidux. The full.... XFCE version installs in under 4min....

Could you please post(if possible) the RAM resources used(i.e. how much) by the XFCE version?

---

### Post by crimesaucer on 2008-09-03
> **Riyonuk said:**
> "..... And with Arch, you update every single day, which is kinda retarded, I NEVER updated Windows, not even once. Maybe that's why mine's so fast....." :P


With Arch, you choose to update just like you do with windows or any other distro, in fact windows is the OS with automatic updates.....



What I'm saying is that if you are happy with your Arch install, then you could just use it "as is" and never do a pacman -Syu again.



Or, you could be a regular person and check the "Recent Updates" box on the Archlinux home page, and then choose to update when you see apps that matter to you: [http://www.archlinux.org/](http://www.archlinux.org/)


With Archlinux, it's about having a very fast OS and the newest packages installed with all of their dependencies. 


For example, the minute a new Linux kernel gets released, they are pretty much available in the testing repository, and then about 2 weeks later the testing kernel is moved into the core repository once all of the bugs are fixed..... 


I prefer monitoring my Arch updates, the same way I did with Ubuntu, except that in Arch I don't have to do a full distro upgrade every 6 months, plus Ubuntu does a package freeze way before they even release the finalized version, so if you want the absolute newest Linux packages that aren't available in the Ubuntu repositories, then you usually have to build them yourself or add different repositories to your sources list (unless they backport it).


With "retarded" Arch, you don't need to do any of this..... You install it once, and update it when you need to..... an update takes about 5-30 seconds..... maybe up to 1-2 minutes if something major updates like the entire Gnome2.22.3, or if the Linux kernel updates along with a bunch of other packages. And if you like to build packages then you build from the ABS or AUR..... which are both WAY easier then ./configure, make, and make install.


At worst, you have to edit a few configuration files with the .pacnew files..... which is super easy with the Gnome app called "meld".


The way they make Arch is that you shouldn't have to do a fresh install ever again (which I sort of doubt, since it was best to fresh install when they went from Arch Duke to Arch Don't Panic). But a fresh Arch install should be as good as an "Ubuntu LTS" (1 year and 6 months), and your apps will always be the newest instead of 1.5 years behind.

---

### Post by crimesaucer on 2008-09-03
> **Riyonuk said:**
> My ideal distro would be one like Arch, in which you start from scratch, but one that's updated half a year, like Ubuntu. It's funny, I read alot about how people wan't those updates, but why? So you fixed a couple of bugs...amazing. Of course this is Linux we're talking about here, and I'm sure there's lots of developers that need those bug fixes. But do I really need to have version 3.09 of Firefox instead of .08? Will the world implode? I think not :P


When I first installed Arch last year, it was so ahead of the curve. It had the new Gnome2.22 way before Ubuntu, it had the Firefox 3 betas and the newest compiz-fusion with all of the latest plug-ins.


The funny thing is back when people were complaining about not being able to get any of those apps, Arch had those all, with no problems. 


It also had the newset xorg when it came out, with the newest xf86-video-intel driver available for people with the 910 915 chipsets. 


The same thing goes for the absolute newest nvidia drivers..... the list goes on.


Right now I'm using kernel26 2.6.26-3..... in the Arch AUR you can find versions of the 2.6.27-rc4 available..... and all the nvidia-beta 177.70 packages to fix any of the current problems that people have with their newest nvidia graphics cards and KDE4.1, which is also available in a simple update from the Extra repository.....


The packages that they get and release so quickly aren't always as unimportant as a simple bug fix to Firefox. Things like xorg, nvidia drivers, and kernels can really improve the whole computer and performance for everything.

---

### Post by cardinals_fan on 2008-09-03
> **crimesaucer said:**
> 
What I'm saying is that if you are happy with your Arch install, then you could just use it "as is" and never do a pacman -Syu again.

You won't get security updates that way...

---

### Post by rsambuca on 2008-09-03
> **crimesaucer said:**
> 
The way they make Arch is that you shouldn't have to do a fresh install ever again (which I sort of doubt, since it was best to fresh install when they went from Arch Duke to Arch Don't Panic). But a fresh Arch install should be as good as an "Ubuntu LTS" (1 year and 6 months), and your apps will always be the newest instead of 1.5 years behind.
Actually, the regular Ubuntu releases are guaranteed security updates for 18 months.  LTS releases are 3 years for desktop, 5 years for servers.

---

### Post by crimesaucer on 2008-09-03
> **rsambuca said:**
> Actually, the regular Ubuntu releases are guaranteed security updates for 18 months.  LTS releases are 3 years for desktop, 5 years for servers.

I never installed a LTS, so I wasn't sure..... I knew there was something about 18 months, anyway, you're still either compiling your own packages, using third party repositories, or hoping that something gets backported in:


from the Ubuntu Backports page: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

> 
Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

Backports is an official Ubuntu repository and maintained by knowledgeable Ubuntu developers who are often present on IRC and other communications media. But note that software in backports will not receive review or updates from the Ubuntu security team itself. 



..... and you also have to take into consideration the package freezes: [https://wiki.ubuntu.com/ReleaseScheduleTemplate](https://wiki.ubuntu.com/ReleaseScheduleTemplate)



With Archlinux, I read about Linus Torvalds in a digg article releasing kernel 2.6.26 and listing the newest features like linux-uvc, and within 2 days 2.6.26 is already in the Archlinux Testing repository and I have it on my computer.....

---

### Post by cardinals_fan on 2008-09-03
> **crimesaucer said:**
> 
With Archlinux, I read about Linus Torvalds in a digg article releasing kernel 2.6.26 and listing the newest features like linux-uvc, and within 2 days 2.6.26 is already in the Archlinux Testing repository and I have it on my computer.....
Which is good if you like getting the latest software.  If stability is more important, that's not so good.

---

### Post by crimesaucer on 2008-09-03
> **cardinals_fan said:**
> You won't get security updates that way...

Exactly, I was joking, but if you don't update in Windows you won't get security updates either.... but isn't a pacman -Syu about the same as upgrading with apt-get? The only difference is you get new packages versions instead of waiting 6 months.


Not like firefox 3.08 to 3.09..... but more like Firefox 3.08 to 4.0alpha1/beta1/rc1/final when they are available. (actually Minefield)

---

### Post by cardinals_fan on 2008-09-03
> **crimesaucer said:**
> Exactly, I was joking, but if you don't update in Windows you won't get security updates either.... but isn't a pacman -Syu about the same as upgrading with apt-get? The only difference is you get new packages versions instead of waiting 6 months.


Not like firefox 3.08 to 3.09..... but more like Firefox 3.08 to 4.0alpha1/beta1/rc1/final when they are available. (actually Minefield)
My latest "pacman -Syu" annihilated my wireless drivers.  I got it fixed, but it took a while, and I prefer more stability.

---

### Post by crimesaucer on 2008-09-03
> **cardinals_fan said:**
> Which is good if you like getting the latest software.  If stability is more important, that's not so good.

I agree, that's why you can use the Testing repository or wait for it to be moved to Core.


I use Testing and that version upgrade ruined pm-suspend, I finally got it sort of working again with 2.6.26-3..... and it still doesn't work in my testing kernel 2.6.27-rc-1.....


If you aren't into the technical aspect of Linux, then I DON'T recommend Archlinux, or any other distro like it.


If all you want is a fast, easy point and click distro, then use xubuntu or something similar that uses xfce4 and has a simple package manager like aptitude.

---

### Post by mike1234 on 2008-09-03
> **swoll1980 said:**
> Pcbsd really fast and it's full a featured kde desktop as well. My 6 year old celeron flew with pcbsd installed on it. I don't like kde so it's not for me. If they ever get a gnome version I'm there.


Gnome desktop is available in their .pbi repo

[http://www.pbidir.com/bt/category/themes](http://www.pbidir.com/bt/category/themes)

M.

---

### Post by cardinals_fan on 2008-09-03
> **crimesaucer said:**
> 
If all you want is a fast, easy point and click distro, then use xubuntu or something similar that uses xfce4 and has a simple package manager like aptitude.
I'm stuck with Xubuntu for the moment because I can't get the NVIDIA drivers set up properly (the latest version is broken with my card) on Paldo, SliTaz, or Lunar.  And NVIDIA doesn't support NetBSD :(

---

### Post by crimesaucer on 2008-09-03
> **cardinals_fan said:**
> My latest "pacman -Syu" annihilated my wireless drivers.  I got it fixed, but it took a while, and I prefer more stability.

Funny, my pm-suspend thing has got me using my 2.6.26-3 stock Arch kernel instead of the new zenmm-git 2.6.27-rc-1.... which worked really good except for pm-suspend and some other usb auto-mounting problem that I think I caused from not compiling the correct module or setting.


And I was recently thinking about commenting out my Testing repository to focus on a more stable system, once I get everything perfect again (hibernate and my lid suspend still are broke).

---

### Post by ThomasHC on 2008-09-03
> **Fri13 said:**
> To get fastest system, you need to compile your own operating system (Linux is the operating system, not just a kernel).
It is actually bretty dificult for first timer to compile it, and it is 99% change that first time goes wrong, so do not remove old Linux from grub/lilo. 

Then you need to make your system faster, remove all unwanted services from booting, change Xorg for faster one (for of the Xorg), desktop environment to window manager etc etc.

Linux is very fast operating system but usually there is bundled so much stuff for it by default, so it is slower.

I suggest you start training things by not using Ubuntu, but changing distribution to Gentoo so you can "more easily" customize your own system. But I dont promise you get over 3-5% speed gain by that. Biggest speed improvents comes if you dont start services what you dont need.

Linux IS NOT an operating system.
IT IS ONLY the kernel.
All of the libraries, basic programs, compilers(Nano, GCC, etc.) are part of the GNU project.

---

### Post by crimesaucer on 2008-09-03
> **cardinals_fan said:**
> I'm stuck with Xubuntu for the moment because I can't get the NVIDIA drivers set up properly (the latest version is broken with my card) on Paldo, SliTaz, or Lunar.  And NVIDIA doesn't support NetBSD :(

I liked xubuntu when I used it on my old laptop with a Celeron M and only 512MB ram..... Arch i686 with xfce4 on the same laptop was a bit faster and lighter.


Now that I have an AMD Turion64x2 with 4GB ram, I've been using Gnome because I like the panel/menu better and I like the gnome sounds for clicking buttons and logging in..... plus my multimedia buttons work very good. (I know I could use gnome-panel in xfce4 but it wouldn't be the same, multimedia keys can be set with some sort of keybinding app or configuration, but sounds for xfce4 are difficult to find info on.)


I have been wondering what xubuntu AMD64 would feel like, but I don't feel like losing those nice gnome system sounds and the gnome-panel. Compiling packages isn't difficult, and practically every app out today has a special repository that you can add to your sources list to easily install it for ubuntu..... The only thing missed would be major things like a complete new Gnome, xfce4, or KDE upgrade, or new kernels and releases like when the new xorg came out, and if you really needed any of those you could always compile it and install/upgrade it yourself.


But seriously, I only left xubuntu for Arch because I wanted to see what i686 felt like compared to i386 on my old crappy Celeron M..... I already used mostly SVN and testing beta packages on xubuntu, so most my apps were the same. 


Now I wonder what a distro like xubuntu feels like for an AMD Turion 64x2 TL-60.

---

### Post by Antman on 2008-09-03
> **Bart_D said:**
> Could you please post(if possible) the RAM resources used(i.e. how much) by the XFCE version?
Here is my Sidux XFCE usage snapshot. This is before any service tweaking.

---

### Post by Bart_D on 2008-09-03
Thanks....73 MB is pretty good(i.e. low).

---

### Post by Frayer on 2008-09-04
...so...is there a consensus on which one is the fastest OS :D?

I am actually running Puppy right now. I've tried Ubuntu and Xubuntu...so slow. So it seems Arch is fastest?

I am running of a Via linux box...

---

### Post by ukripper on 2008-09-04
Here is mine running sidux (kde-lite) using 55MB RAM no swap while running apt-get dist-upgrade without any tweaking.

At idle it gives me 45MB

---

### Post by snowpine on 2008-09-04
You can't necessarily judge an OS's speed by how much RAM it uses. In some cases, using more RAM is a good thing, if it reduces loading from the hard drive (which is slower that loading something cached in RAM).

---

### Post by ukripper on 2008-09-04
> **snowpine said:**
> You can't necessarily judge an OS's speed by how much RAM it uses. In some cases, using more RAM is a good thing, if it reduces loading from the hard drive (which is slower that loading something cached in RAM).

Bingo! 

Low RAM is related to the older systems. So if it can run on 55MB RAM it surely can run faster on other systems fairly newer to them. It considerably depends on what DE and WM you choose for your hardware with a distro to match.:)

---

### Post by ArtF10 on 2008-09-04
> **Frayer said:**
> ...I am actually running Puppy right now. I've tried Ubuntu and Xubuntu...so slow......

Have you tried an Ubuntu Minimal install using XFCE or Openbox?

---

### Post by handy on 2008-09-04
Use a distro' that allows you to not install KDE or Gnome, & run Openbox instead, that will make it noticeably faster.

I do that on Arch.

---

### Post by ArtF10 on 2008-09-04
> **snowpine said:**
> ...In some cases, using more RAM is a good thing, if it reduces loading from the hard drive (which is slower that loading something cached in RAM).

Could you explain this a bit more...I mean is there some way for a user to force more RAM usage(thereby reducing HD loading time) for certain applications/processes?

---

### Post by snowpine on 2008-09-04
> **ArtF10 said:**
> Could you explain this a bit more...I mean is there some way for a user to force more RAM usage(thereby reducing HD loading time) for certain applications/processes?

Well for example I have tried using SliTaz as both a live CD and a hard drive install. It uses about 80mb from the CD and 25mb from the hard drive. But it is faster from the CD, since everything is loaded entirely into RAM. I'm just saying, if you think RAM usage is everything, you'd say "wow, only 25mb, that must be fast," but in fact it is quicker with 80mb used. 

Sorry but I don't know how to control this behavior as a user, just something I've observed. :)

ps Another example I observed was when I installed Fluxbuntu on 3 different computers. It used different amounts of RAM on each computer; the more RAM was available, the more it used. My assumption is the system does this on purpose to maximize its performance. That's the fallacy of saying "Fluxbuntu uses 45mb of RAM"; it might be 35 or 55 on my computer.

---

### Post by Antman on 2008-09-04
> **ArtF10 said:**
> Have you tried an Ubuntu Minimal install using XFCE or Openbox?
+1
I recall doing a Ubuntu Minimal XFCE install and it was pretty darn fast. :guitar:

---

### Post by kevCast on 2008-09-04
Debian. It can be the easiest distro, or the hardest. It's whatever you make it.

---

### Post by Sorivenul on 2008-09-04
FreeBSD + a light WM (OpenBox, FVWM, Xmonad, etc.) tops any Linux distribution I've tried for speed.

As far as Linux distributions go, LFS, Arch, and the mini-distros (DSL, Puppy, SliTaz) have given me the best results.

---

### Post by handy on 2008-09-05
> **ArtF10 said:**
> Could you explain this a bit more...I mean is there some way for a user to force more RAM usage(thereby reducing HD loading time) for certain applications/processes?

If you have a 1Gb of RAM, it is unlikely that you will ever use the swap space on your hdd.  I know my 1Gb RAM machine doesn't, & my Arch install on that machine doesn't even have a swap file/partition installed these days.  From my memory (which is a little rusty these days) I read something some years ago that said RAM is/***was*** on average 250 times faster than a hdd, (it would be considerably faster these days though) there are faster parts of a drive & there are different speeds of RAM, so, that it just to give you an idea.  

You can see that having enough RAM on your machine, so as not to need to use the swap file/partition, is worth it.

---

### Post by ArtF10 on 2008-09-05
> **handy said:**
> ...You can see that having enough RAM on your machine, so as not to need to use the swap file/partition, is worth it.

Ah, so it IS a good thing.  I was ready to pluck out the memory sticks and replace them with some super small capacity old ones I have lying around and was expecting to get a super fast system with Vector Linux(instalable on systems with 64 MB RAM).

You know, until I saw this thread, I never thought twice about how RAM usage would affect speed.  The system on which I am using Xubuntu 8.04(+Compiz Fuzion) uses roughly 200 MB RAM.  Now it feels fast but the CPU Speed is ~999 MHZ(it's an AMD Athlon).  I was really pleasantly surprised at how fast it runs...I can't imagine that Openbox would offer an advantage of moer than a few microseconds(in terms of response time).

---

### Post by Bart_D on 2008-09-05
Ok ok ok....a lot of you seem to believe that RAM usage is not the ONLY indicator of system speed.  Well, as the guy who may have inadvertendly started this memory usage conversation, I'll tell you what....it certainly would be a MASSIVE aid to improving system speed if you could minimize your RAM usage to something below 50 MB.  That much has to be correct, ergardless of whether or not you are using Compiz Fusion.

---

### Post by rsambuca on 2008-09-05
> **Bart_D said:**
> Ok ok ok....a lot of you seem to believe that RAM usage is not the ONLY indicator of system speed.  Well, as the guy who may have inadvertendly started this memory usage conversation, I'll tell you what....it certainly would be a MASSIVE aid to improving system speed if you could minimize your RAM usage to something below 50 MB.  That much has to be correct, ergardless of whether or not you are using Compiz Fusion.
Not necessarily.  Items cached in RAM will be retrieved faster than from-your hard drive.

---

### Post by Sorivenul on 2008-09-05
> **rsambuca said:**
> Items cached in RAM will be retrieved faster than from-your hard drive.

+1  
This is true.  It really seems like Swap vs. RAM in this instance, but correct me if I'm wrong.

---

### Post by snowpine on 2008-09-05
> **Bart_D said:**
> Ok ok ok....a lot of you seem to believe that RAM usage is not the ONLY indicator of system speed.  Well, as the guy who may have inadvertendly started this memory usage conversation, I'll tell you what....it certainly would be a MASSIVE aid to improving system speed if you could minimize your RAM usage to something below 50 MB.  That much has to be correct, ergardless of whether or not you are using Compiz Fusion.

One good way to test this theory is to try the different "flavors" of SliTaz. They have versions that require 128, 64, 32, and 16mb of ram. Which do you think will be fastest? I would test it myself, but I'm lazy. :)

---

### Post by handy on 2008-09-05
WM's like Openbox are lighter & faster than the heavy DE's, Gnome & KDE especially.  My Arch machine was fast when running Gnome, it is noticeably faster running Openbox.

As far as RAM vs Swap is concerned, there is more to it than the OS/DE or WM than you are using, any & all other app's, like Firefox, OpenOffice & Gimp, for instance, use RAM too, you can follow it using system monitor, if you can run it, there are bound to be other tools for tracking it too.  Perhaps they could be suggested by those who know them?

---

### Post by Sorivenul on 2008-09-05
> **handy said:**
> WM's like Openbox are lighter & faster than the heavy DE's, Gnome & KDE especially.  My Arch machine was fast when running Gnome, it is noticeably faster running Openbox.

As far as RAM vs Swap is concerned, there is more to it than the OS/DE or WM than you are using, any & all other app's, like Firefox, OpenOffice & Gimp, for instance, use RAM too, you can follow it using system monitor, if you can run it, there are bound to be other tools for tracking it too.  Perhaps they could be suggested by those who know them?

Again, correct.  Check out Giles Orr's website on WM's and memory usage:
[http://gilesorr.com/wm/memory32.html]("http://gilesorr.com/wm/memory32.html")

As far as my recommends go, htop is a great alternative to System Monitor.  
The main page is here:
[http://htop.sourceforge.net/index.php?page=main]("http://htop.sourceforge.net/index.php?page=main")

---

### Post by handy on 2008-09-05
I just checked & htop is in the Arch unsupported repo'.  When I next boot Arch I'll have a look at it.  Thanks for the link. :-)

---

### Post by SomeGuyDude on 2008-09-06
One of these days, I swear I'll get Arch working. It seems like every time, despite reading the guide, I break something horribly.

Then again, considering what I want is speed and light on the resources and not "to learn Linux deeply", aiming for an OS that has a 40 page "beginner's guide" may be a poor choice...

---

### Post by handy on 2008-09-06
> **SomeGuyDude said:**
> One of these days, I swear I'll get Arch working. It seems like every time, despite reading the guide, I break something horribly.

Then again, considering what I want is speed and light on the resources and not "to learn Linux deeply", aiming for an OS that has a 40 page "beginner's guide" may be a poor choice...

Have you viewed this Arch installation guide movie:

***_[http://video.google.co.uk/videoplay?docid=6213347420565640601](http://video.google.co.uk/videoplay?docid=6213347420565640601)_***

---

### Post by rsambuca on 2008-09-06
> **SomeGuyDude said:**
> One of these days, I swear I'll get Arch working. It seems like every time, despite reading the guide, I break something horribly.

Then again, considering what I want is speed and light on the resources and not "to learn Linux deeply", aiming for an OS that has a 40 page "beginner's guide" may be a poor choice...

I am not sure where you are looking, but the Beginner's Guide that I used at the Arch site was only one page.

---

### Post by SomeGuyDude on 2008-09-06
> **rsambuca said:**
> I am not sure where you are looking, but the Beginner's Guide that I used at the Arch site was only one page.

Print it out. The thing ain't tiny.

Anyway, got the video, got a spare laptop hooked up to the internets, suppose it's a fair enough time to try again.

---

### Post by chucky chuckaluck on 2008-09-06
hey, someguy, i've installed arch successfully on two occassions. the guides were less tl/dr than gentoo's, but still tl/dr. if i can do it, you can do it.

---

### Post by SomeGuyDude on 2008-09-06
> **chucky chuckaluck said:**
> hey, someguy, i've installed arch successfully on two occassions. the guides were less tl/dr than gentoo's, but still tl/dr. if i can do it, you can do it.

Well, rolling Arch right now. Once I get wireless going, we're set.

---

### Post by billgoldberg on 2008-09-06
> **Riyonuk said:**
> I just ordered a new Dell Laptop, and can't wait for it. Is there a way to have like a custom OS, cause I want it to be as fast as possible. Someone told me I would need to make my own kernel? How do you do that? XD

Oh, and here's the laptop I'm getting ;)

[http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690](http://support.dell.com/support/order/details.aspx?c=us&l=en&s=gen&order_number=427877067&validate=94911690)

Give arch a try, and put fluxbox on it.

---

### Post by Cl0ud9 on 2008-09-09
If you want a fast distro, go with CRUX

---

### Post by SomeGuyDude on 2008-09-10
> **SomeGuyDude said:**
> Well, rolling Arch right now. Once I get wireless going, we're set.

Followup. After being unable to get my wireless setup for about four hours despite going through the guide step by step, I gave up and went back to Ubuntu.

Verdict: overall it's very light, definitely as fast as I can imagine an OS being (everything was "instant"), but unless you don't mind a lot of sitting around puttering in text files to make things work right it isn't worth the speed upgrade.

---

### Post by insane_alien on 2008-09-10
arch can be a bit finiky to get set up right first time round but once it's up it usually doesn't need doing again.

i find it helps to dualboot arch to start off with and once you have it running to your satisfaction you can then migrate over.

---

### Post by SomeGuyDude on 2008-09-11
> **insane_alien said:**
> arch can be a bit finiky to get set up right first time round but once it's up it usually doesn't need doing again.

i find it helps to dualboot arch to start off with and once you have it running to your satisfaction you can then migrate over.

I might do that. After all, it's how I moved from Windows to Ubuntu in the first place...

---

### Post by tdrusk on 2008-09-13
I honestly think nothing can beat freedos. It boots in 4 seconds on my Pentium I 24mb RAM craptop.

---

### Post by jaqie on 2008-09-13
> **tdrusk said:**
> I honestly think nothing can beat freedos. It boots in 4 seconds on my Pentium I 24mb RAM craptop.
*shrug* long been a fan of MSDOS 6.22, to be honest. I actually still use it on a 32MB memstick for BIOS flashes, and for running ghost 2003 which I *gasp* bought in 2003 :)
I also have a toshiba libretto 70CT which I run DOS 6.22 on, and play MP3s on. Only thing ive not bothered to set up on it is FAT32 support so I can put my collection on partitions larger then 2GB on it.

---

### Post by SomeGuyDude on 2008-09-13
I think DOS kinda bridges the line between "speed" and "remotely enjoyable to use".

---

