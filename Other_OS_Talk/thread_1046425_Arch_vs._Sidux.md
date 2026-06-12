---
title: "Arch vs. Sidux"
date: 2009-01-21
forum: Other OS Talk
---

### Post by snowpine on 2009-01-21
Hi everyone, in a nutshell I am thinking about trying one of these "rolling release" distros I've heard about. Basically I am looking for a 2nd OS to dual boot with Ubuntu, something that will teach me a different side of Linux from the 6-month cycle I'm used to. What are the pros and cons of Sidux vs. Arch?

---

### Post by namegame on 2009-01-21
If you want to learn a "new" side of linux I would recommend trying Arch. Sidux is still Debian. Ubuntu is based on Debian. I would imagine that it would probably be very similar to Ubuntu other than the rolling release cycle.

Arch on the other hand would be a different experience. It's not Debian/Red Hat/whatever based. It's binary based and "optimized" for the i686 architecture. I have learned much more from Arch than I have learned from any other Linux distribution I have used regularly, which includes Ubuntu, Debian, Fedora, Red Hat, CentOS, and Solaris. 

Just my opinion of course.

---

### Post by Antman on 2009-01-21
sidux works really well. I have tried Arch once and it seemed really fast, but at that time I wasn't into tinkering that much so I stopped working with it.

I may try it again once KDE 4.2 is released.

---

### Post by smartboyathome on 2009-01-21
Arch is better, imo, because creating deb packages is a PITA, while makepkg makes things very easy.

---

### Post by snowpine on 2009-01-21
Thanks everyone who's responded so far! Looks like there are a lot of Arch fans around here (I'm not surprised.) Keep them coming!

One additional question, does anyone have experience with either OS on the eee pc?

---

### Post by winterblues on 2009-01-21
I'll recommend any Debian based distro, just for the simple fact that APT is awesome. Been using Linux since 98'. I ran Arch for a week but found the tinkering too much, although I must say "you'll get an education" in Linux, but so did I installing Debian AND Slack 10 yrs. ago.

---

### Post by djhyland on 2009-01-21
I like Gentoo myself.  I realize it isn't everyone's cup of tea, but I think compiling packages is neat.

---

### Post by namegame on 2009-01-21
> **winterblues said:**
> I'll recommend any Debian based distro, just for the simple fact that APT is awesome. 

To me, the output of APT compared to yaourt/pacman is horrendous.

---

### Post by albinootje on 2009-01-21
> **namegame said:**
> To me, the output of APT compared to yaourt/pacman is horrendous.

I think Arch Linux is great, but the packages through pacman/yaourt are not signed with gpg, which makes installing a little faster than with apt.
And I'm not sure what you mean with the output of apt, but i find apt-get and apt-cache pretty cool since quite a while.

---

### Post by SomeGuyDude on 2009-01-21
Since I have yet to find anything as awesome as Yaourt, Arch gets my vote.

---

### Post by RedSquirrel on 2009-01-21
> **snowpine said:**
> Hi everyone, in a nutshell I am thinking about trying one of these "rolling release" distros I've heard about. Basically I am looking for a 2nd OS to dual boot with Ubuntu, something that will teach me a different side of Linux from the 6-month cycle I'm used to. What are the pros and cons of Sidux vs. Arch?

When I was playing around with Debian in the past, I was satisfied with Debian sid itself, so I haven't tried sidux. I have used Arch, though. (I currently use Gentoo.)

Debian tends to do a better job than Arch of keeping up with security updates.

As others have said, between Arch and sidux, you will find Arch to be a *very* different experience and sidux will only be slightly different.

Arch packages are sometimes a bit newer than sid/sidux, so you're really on the bleeding edge (which can be both a pro and a con).


Since I haven't looked at the sidux website recently, I decided to take a quick glance. I came across this strange comment on [this]("http://sidux.com/index.php?module=pnWikka&tag=welcome") page:

> Unfortunately, the Debian installer does not support sid...:-k

I'm suprised by that comment. In my experience, the installer *does* support installing sid, as long as you use the 'expert' mode or (equivalently) change the debconf priority to "low".

---

### Post by handy on 2009-01-21
I used Sidux in its early days & have been using Arch for 9 months or so.  I very much prefer Arch; I prefer the Arch community, documentation, simplicity, package management system & [*_the ease of escaping trouble if you happen to get caught by an upstream bug_*]("http://ubuntuforums.org/showpost.php?p=6283883&postcount=3") (which has happened to me twice in 9 months).

For those that get put off by the setting up & configuration of Arch; it all but stops once you have Arch set up how you want it to be.  After that, any configuring is due to the user's desires to try a different DE/WM, or network configuration or ...  Of course if you upgrade into trouble you have to get out of it, but it is usually not hard or time consuming when you know how, & being able to downgrade so quickly you can be back where you were before you entered -Syu in a matter of a few minutes as per the link above.

My Arch/Xfce has to be the most efficient & laziest OS/GUI I have ever used (apart from some areas of the boring OSX, though I much prefer the complete openness & configurability of the installation system of the Arch distro & when combined with the huge repo's of free software all tied to the -Syu --aur upgrade-ability of Arch, the Leopard way pales in comparison to Arch in so many ways, at least for me on my 24" iMac). 

The only clumsiness in my Arch/Xfce installations is X, this being due to Xorg's inherent complexity, (which must make it the most likely place for most distro's to get it wrong) though Arch didn't get it wrong, it is still the clumsy bit imho.  Also, due to the Xfce Settings/Menu Editor system which [*_requires some work_*]("http://wiki.xfce.org/faq#menu") with a text editor to get it fully functional & the fiddling around to get Xfce's GTK theme how I wanted it to be, (again with a text editor) in gtkrc, both of these complaints(?) are not really Arch's problem though. :-)

The new Arch user also has to learn to become comfortable with the pacman (yaourt) package management system & [*_handling the .pacnew & pacsave files correctly_*]("http://wiki.archlinux.org/index.php/Pacnew_and_Pacsave_Files").  Most of the .conf.pacsave files you can ignore & delete, rarely one comes through that needs to have a portion cut & pasted into the original .conf file.

Here is a thread with too much information on the subject :-) :

*_[http://ubuntuforums.org/showthread.php?t=881270&highlight=pacnew](http://ubuntuforums.org/showthread.php?t=881270&highlight=pacnew)_*

---

### Post by Rumor on 2009-01-21
> **snowpine said:**
> Thanks everyone who's responded so far! Looks like there are a lot of Arch fans around here (I'm not surprised.) Keep them coming!

One additional question, does anyone have experience with either OS on the eee pc?

I've run Arch on my eee 901. There are some very good articles in the Arch wiki for installing it on the various eee architectures and several active threads in the forums if you should get stuck.

I've used Arch for a couple years on my main PC and it has been rock solid for me.

---

### Post by vishzilla on 2009-01-21
I havent used Sidux, but I recommend Arch. I have been using it for 2 weeks now. Its a different experience altogether

---

### Post by namegame on 2009-01-21
Stupid double post

---

### Post by namegame on 2009-01-21
> **albinootje said:**
> I think Arch Linux is great, but the packages through pacman/yaourt are not signed with gpg, which makes installing a little faster than with apt.
And I'm not sure what you mean with the output of apt, but i find apt-get and apt-cache pretty cool since quite a while.

Just as an example:

Output from pacman:

[IMG]http://www.pro-linux.de/berichte/jpgs/archlinux-0.8/arch_pacman.png[/IMG]
Output from apt-get:

[IMG]http://www.debianadmin.com/images/mono/1.png[/IMG]

To me the pacman output is much easier to read and therefore understand.

---

### Post by snowpine on 2009-01-22
Thanks again everyone for the suggestions! So far, Arch is winning in the polls, but I am going to wait until the weekend (when I have some spare time) to make the final decision. 

Namegame, thanks for posting that pacman output! For some reason, it reminds me of the output from tazpkg in SliTaz. I am a big SliTaz fan; are there any other similiarities with Arch?

---

### Post by hrod beraht on 2009-01-22
> **snowpine said:**
> What are the pros and cons of Sidux vs. Arch?

The big difference is choice in what you want your distro to be.
Sidux is a fine distribution, but when you install it you get an installation where the desktop environment and applications and such were chosen by Sidux. When you install Arch, you get an installation where everything was chosen by *you*.

Bob

---

### Post by albinootje on 2009-01-22
> **namegame said:**
> 
To me the pacman output is much easier to read and therefore understand.

Okay, I see what you mean.

I've used Arch Linux for several months a while ago, at first I was delighted about it.
One friend of mine also switched to Arch Linux, and loves it.

For me, after a while, I decided to switch to Ubuntu again because I need to be able to support the Ubuntu users.
However, I'm planning to have some triple boot Linux on my desktop to play around though.
And switching my users from Ubuntu to Arch on esp. the older machines is an idea.

What I don't like so much about the Arch Linux rolling.. is that you need to read much more to find out what is a security update, and what is not.

---

### Post by crimesaucer on 2009-01-22
> **djhyland said:**
> I like Gentoo myself.  I realize it isn't everyone's cup of tea, but I think compiling packages is neat.

I use the ABS and AUR to compile every package myself. I am able to configure C[XX]FLAGS/MAKEFLAGS in my /etc/makepkg.conf file.

---

### Post by smartboyathome on 2009-01-22
> **crimesaucer said:**
> I use the ABS and AUR to compile every package myself. I am able to configure C[XX]FLAGS/MAKEFLAGS in my /etc/makepkg.conf file.

And there is even customizepkg for further customizations. :D

---

### Post by fwojciec on 2009-01-22
> **albinootje said:**
> What I don't like so much about the Arch Linux rolling.. is that you need to read much more to find out what is a security update, and what is not.

There are no security updates in rolling release -- you simply use the latest stable versions of software.

Having said that, if you don't like the idea of rolling release then you're unlikely to enjoy using Arch.

---

### Post by snowpine on 2009-01-22
Actually, does Sidux even count as "rolling release" since it is tied in with the Debian development/release cycle? My understanding is that most packages are frozen right now while they are putting the finishing touches on Lenny, then there will be a lot of updates after.

---

### Post by RedSquirrel on 2009-01-22
> **fwojciec said:**
> There are no security updates in rolling release -- you simply use the latest stable versions of software.

... which may or may not be patched for security vulnerabilities.



> **snowpine said:**
> Actually, does Sidux even count as "rolling release" since it is tied in with the Debian development/release cycle? My understanding is that most packages are frozen right now while they are putting the finishing touches on Lenny, then there will be a lot of updates after.

sidux is based on Debian sid. sid is the development branch, where packages are being updated all the time. I suggest you familiarize yourself with the various branches of [Debian]("http://www.debian.org"). ;)

---

### Post by fwojciec on 2009-01-22
> **RedSquirrel said:**
> ... which may or may not be patched for security vulnerabilities.

Preferably packages are unpatched and provided in their latest versions as the original developer intended -- that prevents things like the famous Debian ssl fiasco.

Patching packages for security is required mostly when distros, like Debian, use non-current versions of software.  Software developers, generally, fix security problems pertaining to their software first, and release new version of their software once the problem is resolved.  Distros like Arch just package the new version of software, distros like Debian apply security fixes to the version of the source that happens to be deemed stable or current by distro's own standards.

---

### Post by cb951303 on 2009-01-22
I think every linux user should try Arch once :) It's a great experience :popcorn:

---

### Post by RedSquirrel on 2009-01-22
> **fwojciec said:**
> Software developers, generally, fix security problems pertaining to their software first, and release new version of their software once the problem is resolved.

Generally, yes, but not in all cases. There are times when the developer releases a patch that is to be applied to the latest version and the version number is _not_ incremented, or at least it isn't incremented for some time. In these cases, without patching, you can have the latest version, but still be vulnerable.

It seems to me that most distros miss these updates. Debian and Gentoo are two that seem to do a reasonable job of keeping up with these updates.

---

### Post by smartboyathome on 2009-01-22
> **RedSquirrel said:**
> Generally, yes, but not in all cases. There are times when the developer releases a patch that is to be applied to the latest version and the version number is _not_ incremented, or at least it isn't incremented for some time. In these cases, without patching, you can have the latest version, but still be vulnerable.

It seems to me that most distros miss these updates. Debian and Gentoo are two that seem to do a reasonable job of keeping up with these updates.

The good thing is that with ABS, you can update the programs you want to, and it will fetch the sources and build it for you. If the version number isn't changed at all, then this will get the new security updates. :)

---

### Post by fwojciec on 2009-01-22
> **RedSquirrel said:**
> Generally, yes, but not in all cases. There are times when the developer releases a patch that is to be applied to the latest version and the version number is _not_ incremented, or at least it isn't incremented for some time. In these cases, without patching, you can have the latest version, but still be vulnerable.

It seems to me that most distros miss these updates. Debian and Gentoo are two that seem to do a reasonable job of keeping up with these updates.

Obviously what I described was two the ideal types.  Naturally Arch developers are taking care of the non-standard situations that do come up.  It's just that the overall approach to the problems of security is different in different distros, and number of "security patches" is not necessarily a good indicator of the overall security of the distro, but rather a consequence of the adopted release model.

---

### Post by crimesaucer on 2009-01-22
> **smartboyathome said:**
> And there is even customizepkg for further customizations. :D

Is this compatible with pacbuilder-svn ?

---

### Post by RedSquirrel on 2009-01-22
> **smartboyathome said:**
> The good thing is that with ABS, you can update the programs you want to, and it will fetch the sources and build it for you. If the version number isn't changed at all, then this will get the new security updates. :)

It will get the security updates if you write a PKGBUILD to apply the relevant patch(es). For packages in **Core** and **Extra**, which are "developer-maintained", applying patches is the responsibility of the developers, but they don't always keep up with the updates (not that they don't *want* to, they're just too busy with earning a living and other important things in life). I believe if Arch added more developers, they would be able to keep up, and Arch would more secure than it currently is.

I know that Arch is a DIY distro. Every once in a while, this extends to maintaining the packages in developer-maintained repositories.



> **fwojciec said:**
> Obviously what I described was two the ideal types.  Naturally Arch developers are taking care of the non-standard situations that do come up.  

One would like to think so, but it isn't the case in every situation.



> **fwojciec said:**
> It's just that the overall approach to the problems of security is different in different distros, and [COLOR=Blue]number of "security patches" is not necessarily a good indicator of the overall security[/COLOR] of the distro, but rather a consequence of the adopted release model.
(blue added to highlight that point)

When packages are vulnerable, they should be patched. The release model makes no difference from that point of view.

If a given distro doesn't keep up with security updates, it may be because it doesn't make them a priority or it doesn't have the manpower necessary to keep up. (Developer incompetence is another possibility, but let's not get into that. :D)

Up to this point, no one has mentioned anything about using the *number* of security patches as an indicator of security. In the case of Arch, it doesn't need *more* security patches than Debian, it needs to patch any vulnerable packages so that it can say, "Debian patched xyz-1.2.3 for security and we patched *our* xyz-1.2.3 too. Excellent.". ;)

---

### Post by fwojciec on 2009-01-23
What is your basis for claiming that Arch is insecure?  Can you back this up in any way?  I'd be interested to know, because I could report such issues to the bug tracker and make sure that they get fixed if they are indeed serious...

---

### Post by K.Mandla on 2009-01-23
Arch Linux. There is none higher.

---

### Post by snowpine on 2009-01-23
Thanks for all the great opinions, everyone! After much consideration, I've decided to try them both!!! I installed Sidux+Fluxbox on my old laptop last night, and over the weekend, I will try Arch+Openbox on either my desktop or my eee. 

The Sidux install was super-fast and easy. I was really impressed by the hardware detection of my non-free wireless card. While it was not supported out-of-the-box, instructions for getting the correct module were very clear and simple. Boot time is a little slower than I would like (about 1:50) but once booted it feels fast and only uses 32 out of 256mb of ram. I've installed fluxbuntu-artwork so it is a good-looking and familiar environment for me. 

Next project, Arch...

---

### Post by Antman on 2009-01-23
> **snowpine said:**
> Boot time is a little slower than I would like (about 1:50) but once booted it feels fast and only uses 32 out of 256mb of ram.

1min 50secs.... ?!? OUCH.... :shock:
My sidux systems generally boot in about 23secs.

---

### Post by sertse on 2009-01-23
yeah, that's odd... my boot times the few times I've tried sidux is around the same as Antmans...

Sidux is nice, Arch.. personally I never got past the package selection page. lol :)

---

### Post by snowpine on 2009-01-23
Keep in mind it is a very old computer. :) Boot times for other distros: Crunchbang 2:00, Fluxbuntu 1:30, SliTaz 0:50

I am curious to try Arch because I've heard great things about its boot time.

---

### Post by namegame on 2009-01-23
> **snowpine said:**
>  I am a big SliTaz fan; are there any other similiarities with Arch?

I have never used SliTaz, however I would assume that one of the regulars of this forum, cardinals_fan could answer your question.

---

### Post by cardinals_fan on 2009-01-23
> **snowpine said:**
> 
Namegame, thanks for posting that pacman output! For some reason, it reminds me of the output from tazpkg in SliTaz. I am a big SliTaz fan; are there any other similiarities with Arch?
They both have clean base systems, although SliTaz is even simpler (no runlevels, etc.)  Pacman is more advanced than Tazpkg, but I find the latter a bit more elegant.  Both systems have relatively little standing in the way of the user.  Arch has far more packages available, though SliTaz is growing fast.  Arch has a more active community.

---

### Post by Frak on 2009-01-23
In terms of speed, they both get my vote. Ease of use, Sidux. The sheer knowledge gained from using it, Arch.

---

### Post by RedSquirrel on 2009-01-23
> **fwojciec said:**
> What is your basis for claiming that Arch is insecure? Can you back this up in any way?  I'd be interested to know, because I could report such issues to the bug tracker and make sure that they get fixed if they are indeed serious...

Well, I have not audited all of the Arch packages, but cups is a recent example. FreeBSD had that patched within a day or so, Debian and Gentoo within a few days. I just checked and Arch has fixed that now, but about a month and a half after the others had done so. I would like to see the Arch dev(s) catch this sort of thing much sooner and not have to poke them to patch and rebuild.

It has been suggested on the Arch forums that it is the user's responsibility to keep track of security announcements (on some other distro's pages or elsewhere, since Arch does not provide these announcements) and apply patches as needed. This is in contrast to Arch users who claim that Arch is a rolling release distro and that all you have to do to make your system secure is to keep your system up-to-date.

Furthermore, it has also been mentioned on the forums that the Arch developers tend to rely primarily on version bumps to upgrade packages. This works fine in most cases, but there are exceptions as I mentioned above. It is possible that Arch is doing a better job with these exceptions than I thought, but the cups example seems like a good indicator since it is a fairly important (and popular) package.

Arch doesn't have that many developers compared to other projects that take security seriously. There have been a few threads on the Arch forums which discussed a *range* of security topics (beyond security announcements) and the general answer was [paraphrased]: "That's a good idea, but we all have others things to do." I can accept that answer (and more devs would probably help). I just get a bit tired of reading posts similar to, "All you have to do is 'pacman -Syu' and you're secure.".

(I apologize if my post is a bit incoherent. They're doing renovations next door and it's hard to concentrate. :evil:)

---

### Post by cardinals_fan on 2009-01-23
> **RedSquirrel said:**
> 
Furthermore, it has also been mentioned on the forums that the Arch developers tend to rely primarily on version bumps to upgrade packages. This works fine in most cases, but there are exceptions as I mentioned above. It is possible that Arch is doing a better job with these exceptions than I thought, but the cups example seems like a good indicator since it is a fairly important (and popular) package.

+1

This is one of my issues with using Arch full-time.

---

### Post by albinootje on 2009-01-23
> **RedSquirrel said:**
> 
It has been suggested on the Arch forums that it is the user's responsibility to keep track of security announcements (on some other distro's pages or elsewhere, since Arch does not provide these announcements) and apply patches as needed. This is in contrast to Arch users who claim that Arch is a rolling release distro and that all you have to do to make your system secure is to keep your system up-to-date.


Very interesting to hear!
However.. quite some security updates for software in Linux distributions can be taken with grains of salt depending on the setup you're using.

For example, a vulnerability in cups is not that critical for a home desktop user without untrusted users in a big LAN i'd say.

P.s. how does one change the volume in OSX from the commandline ? :)
[http://xkcd.com/530/](http://xkcd.com/530/)

---

### Post by Frak on 2009-01-23
> **cardinals_fan said:**
> +1

This is one of my issues with using Arch full-time.
+2

Another reason why I refuse to run Arch as a server machine.

---

### Post by fwojciec on 2009-01-23
Nevermind -- this is getting way OT.

---

### Post by snowpine on 2009-01-24
Well everyone, here is the update... Sidux was great, but I took it off my old laptop. The reason is that SliTaz is just about the perfect distro for this laptop, now that it has an easy option to install OpenOffice 3, so I deleted the Sidux partition to make more room for SliTaz (the hard drive is only 6gb and I have Fluxbuntu on there too). SliTaz is just ideal for me in many ways, and the boot time was more than 200% faster than Sidux. :)

I downloaded the Arch installer and I'm ready to give it a go. Probably either Openbox or LXDE. I am debating between trying it out in a virtual machine, vs. just "going for it"--what are your thoughts?

---

### Post by albinootje on 2009-01-24
> **snowpine said:**
>  I downloaded the Arch installer and I'm ready to give it a go. Probably either Openbox or LXDE. I am debating between trying it out in a virtual machine, vs. just "going for it"--what are your thoughts?

VirtualBox has Arch Linux in the choices of Linux distributions the moment you create a guest VM.
But if you want to see speed differences the best is of course a native install to your hard disk without emulation/virtualization.

---

### Post by cardinals_fan on 2009-01-24
> **snowpine said:**
> Well everyone, here is the update... Sidux was great, but I took it off my old laptop. The reason is that SliTaz is just about the perfect distro for this laptop, now that it has an easy option to install OpenOffice 3, so I deleted the Sidux partition to make more room for SliTaz (the hard drive is only 6gb and I have Fluxbuntu on there too). SliTaz is just ideal for me in many ways, and the boot time was more than 200% faster than Sidux. :)
SliTaz is a great distro, one of my favorites.  Enjoy :)
> **snowpine said:**
> 
I downloaded the Arch installer and I'm ready to give it a go. Probably either Openbox or LXDE. I am debating between trying it out in a virtual machine, vs. just "going for it"--what are your thoughts?
I would go for it, but it's ultimately up to you.

---

### Post by snowpine on 2009-01-26
Well everyone, I learned one important lesson this weekend: Arch and alcohol do not mix! I did manage to complete the basic install, but then got sleepy and had to set the project aside for the time being. I definitely am starting to understand why people say Arch is a great learning experience. Looking forward to continuing with the process (next steps I think are getting my network working and installing a windows manager) when I can give it my undivided attention.

In other news, I found a very neat "unofficial" Sidux+LXDE remix that includes support for the eee. So that has replaced Cruncheee on my 4gb SD card on the 900ha. [http://www.cap.gediam.de/index-en.htm](http://www.cap.gediam.de/index-en.htm)

---

### Post by JawsThemeSwimming428 on 2009-01-26
> **snowpine said:**
> Well everyone, here is the update... Sidux was great, but I took it off my old laptop. The reason is that SliTaz is just about the perfect distro for this laptop, now that it has an easy option to install OpenOffice 3, so I deleted the Sidux partition to make more room for SliTaz (the hard drive is only 6gb and I have Fluxbuntu on there too). SliTaz is just ideal for me in many ways, and the boot time was more than 200% faster than Sidux. :)

I downloaded the Arch installer and I'm ready to give it a go. Probably either Openbox or LXDE. I am debating between trying it out in a virtual machine, vs. just "going for it"--what are your thoughts?

If it is your first time installing Arch I would recommend a VM. It is different than installing Ubuntu and/or Debian in that you have ALOT more control by default. I would run through the installer and the Beginners Guide ([http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)) once before installing to HDD. Enjoy.

---

