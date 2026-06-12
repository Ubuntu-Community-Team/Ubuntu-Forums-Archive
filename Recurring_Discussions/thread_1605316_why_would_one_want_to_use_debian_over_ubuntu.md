---
title: "why would one want to use debian over ubuntu?"
date: 2010-10-25
forum: Recurring Discussions
---

### Post by fuzzylogic25 on 2010-10-25
to my understanding (correct me if im wrong please), ubuntu is debian with added packages and other additions/modifications.

so, unless you dont like the way ubuntu is set up (in terms of packages/additions/modifications made/installed), why else would you use debian? Is debian more stable/secure/fast etc?

I know some distros like slackware for example, is extremely stable compared to other distros. but ubuntu and debian seem to just be the same. I guess i thought debian more for power users, who want more control.

---

### Post by cascade9 on 2010-10-25
IMO debian is faster, and more stable than ubuntu. You can also use a rolling release with debian testing/unstable(sid)...not that unstable is 'unstable' really. 

You'll get diferent opnions though, thats just mine.

---

### Post by Laxman_prodigy on 2010-10-25
> **fuzzylogic25 said:**
> to my understanding (correct me if im wrong please), ubuntu is debian with added packages and other additions/modifications.

so, unless you dont like the way ubuntu is set up (in terms of packages/additions/modifications made/installed), why else would you use debian? Is debian more stable/secure/fast etc?

I know some distros like slackware for example, is extremely stable compared to other distros. but ubuntu and debian seem to just be the same. I guess i thought debian more for power users, who want more control.


The basic reason is that it is the source distribution in the sense that it is the core one. Many are of the view that it does not make sense to use anything which is based on something unless it makes it even better; and these people mostly consider Ubuntu as something which doesn't make Debian better.

And there is stability of Debian over Ubuntu, but hey, it has a cost. The cost of little outdated packages. But that doesn't effect many because it is tried and tested system and there is backport services for few newer packages.

And many more newer packages can be built from Debianized source and installed.

However, for compensating that, people use the testing branch of Debian which is considered to be very stable too.

Other than that, you can configure Debian to be exactly how you like with say, Window managers only, different desktop environments. I know Ubuntu has it all. But, there is more control over the system.

And some(many?) don't like the corporate structure of Ubuntu. And the thing goes on....

---

### Post by NMFTM on 2010-10-25
Some people might use Debian so they don't have to say they use a "newb" distro. Or a distro that's too mainstream and popular. Saying "I run Debian" sounds a little more hardcore than "I run Ubuntu".

---

### Post by Spice Weasel on 2010-10-25
Faster, more stable, runs on more processor architectures.

e: Also, you can get a rollercoaster updates scheme if you use testing/unstable.

---

### Post by Grenage on 2010-10-25
Because hardcore 1337 hax0rs don't pwn the NSI using Ubuntu.

Also, it's cleaner.

---

### Post by fatality_uk on 2010-10-25
Stuff what other people have said!

---

### Post by Oxwivi on 2010-10-25
What fatality_uk just said. >_>

Debian's released ages from each other, so if Debian works, it just will. No frequent updates with new stuff which can possibly break the system or a feature.

---

### Post by TBABill on 2010-10-25
The stigma of Ubuntu is strong in the Linux world. It's like what I faced when I bought a motorcycle. Many adult males believe the only motorcycle on the road in the US should be a Harley. I purposely bought a Triumph America (cruiser) and love it. That put me outside the norm and I now ride something very unique in my area, which is similar to some people not wanting to be so mainstream. This is certainly not the case for all users, but I have seen many posts by Debian users who like to remove the "mainstream" and run the base system Ubuntu is derived from.

---

### Post by Spice Weasel on 2010-10-25
> **Oxwivi said:**
> What fatality_uk just said. >_>

Debian's released ages from each other, so if Debian works, it just will. No frequent updates with new stuff which can possibly break the system or a feature.

[http://packages.debian.org/unstable/](http://packages.debian.org/unstable/)
[http://packages.debian.org/testing/](http://packages.debian.org/testing/)

---

### Post by TBABill on 2010-10-25
The stigma of Ubuntu is strong in the Linux world. It's like what I faced when I bought a motorcycle. Many adult males believe the only motorcycle on the road in the US should be a Harley. I purposely bought a Triumph America (cruiser) and love it. That put me outside the norm and I now ride something very unique in my area, which is similar to some people not wanting to be so mainstream. This is certainly not the case for all users, but I have seen many posts by Debian users who like to remove the "mainstream" and run the base system Ubuntu is derived from.

---

### Post by Oxwivi on 2010-10-25
Yeah,. and a base system is quite appealing when you want to avoid anything fancy.

---

### Post by smellyman on 2010-10-25
thats like saying why use Ubuntu over Mint

---

### Post by fuzzylogic25 on 2010-10-25
ok i see. but just because they release versions at much later periods than ubuntu doesnt mean it is more stable.

also, when you say packages, do you just mean all the software that comes with it? my understanding of linux is very little. All I think about is there is the linux kernal, then you install a gui interface like gnome to it, then applications....im sure thats not how it goes lol but thats all i know right now.

---

### Post by Oxwivi on 2010-10-25
It does mean it's more stable. The long time it takes to release a version really takes cares of the bugs.

Yes, the softwares from their official repository is as old as the release. Likewise the kernel and other core stuff is also outdated in a few years. But you can always add the program's own repository.

---

### Post by NightwishFan on 2010-10-25
The main reason I would consider using Debian is that they focus on completeness, 3 different kernels, 12 different arches, 20,000 or more packages per arch. Also their package dependencies are much simpler and cleaner as was said (plymouth is a good example).

The problem with Debian is that it seems to lack a forward focus. Ubuntu has clear defined goals and ambitions for both it's server and desktop platforms and sometimes is rightfully aggressive with those goals. Also, I prefer the normal release & LTS over the stable or rolling model of Debian.

---

### Post by BouldRake on 2010-10-25
Number one reason most of my boxes are Debian - less crap in the base install.  No need to remove network-manager, OpenOffice, Compiz, etc.  This makes it easier to configure, in the same way it's easier to decorate your living room if you don't have to strip the old wallpaper first.  The downside of that, of course, is it's not easy to get things exactly the way you want them if you don't know what you're doing (or Ubuntu is more new user friendly, in other words).

Debian has root.

If Ubuntu has a problem, it probably means you upgraded in the first six weeks of a new release.

If Debian crashes, it probably means you hit your PC with a sledgehammer.

The clear downside is the age of some of the programs.  Not often a problem, but sometimes it matters.  I've lost track of the number of times I've had to compile Pidgin from source, for example, after one of the protocols changes.

---

### Post by NightwishFan on 2010-10-25
No, Ubuntu has can optionally use the debian (alternate) installer or enable root user post install it is quite simple. Also, you can install the same "gnome-desktop" sort of packages as Debian. To be quite honest, run: "tasksel install gnome-desktop --new-install" in Debian and it will install probably more packages than the default Ubuntu.

---

### Post by m4tic on 2010-10-25
Use kubuntu!!!

---

### Post by urukrama on 2010-10-25
Some of the reasons why I moved from Ubuntu to Debian:

[LIST=1]
[*]It is lighter. A minimal Debian install contains less packages than a minimal Ubuntu install. As I work with old hardware, this means that Debian runs better on my computers, and also allows me to easily build up a system the way I like it.

[*]Debian has a longer release cycle than Ubuntu. I don't want to update every six months, but neither want to be stuck with 3 year old packages if you use LTS releases. Debian Testing is as good as a rolling release if you want it to be. 

[*]Debian is more stable. Debian Stable is meant to be very stable, but  Debian Testing is (in my experience) very stable too. Debian's main concern is not the latest or greatest, or a great design, but stability. I like a distro who has that as its main focus. Ubuntu's main focus with LTS releases is also not stability, just a longer support cycle (contrary to what is often thought).

[*]I don't use Gnome, so most of the innovations Ubuntu offers are irrelevant to me, as they affect Gnome and sometimes very little else. And some of the innovations that do affect non-Gnome users I really don't like.
[/LIST]

I don't have any ill feelings towards Ubuntu. I just realised Debian was a lot closer to what I wanted my OS to be.

---

### Post by limestone on 2010-10-25
Ubuntu is NOT Debian. It's based on Debian. Ubuntu has its own tools and is more of a starter distro that helps you alot with getting started. Debian also has a strict Free-software only policy, ubuntu provides also Non-free.

---

### Post by snowpine on 2010-10-25
The best analogy I can think of is that Debian is Star Wars and Ubuntu is The Phantom Menace. Some people prefer the original, and you aren't likely to change their mind once it's made up. :)

---

### Post by Grenage on 2010-10-25
> **snowpine said:**
> The best analogy I can think of is that Debian is Star Wars and Ubuntu is The Phantom Menace. Some people prefer the original, and you aren't likely to change their mind once it's made up. :)

Bah, that's too harsh; The Phantom Menace was only marginally better than the Star Wars Holiday Special.

---

### Post by NightwishFan on 2010-10-25
It had Ray Park and Liam Neeson in it though.

---

### Post by bonixavier on 2010-10-25
I prefer to use Debian as an easy distro over Ubuntu because I don't like the marketplace that Ubuntu is becoming. Buy DVD player on Maverick was too much for me. Will Ubuntu require us to run Steam too in a while?
Besides, I don't like the lack of choices of the standard install cd of Ubuntu. And what if I don't want to upgrade to Grub 2? Who said that /dev/sda8 would be handling my booting?

---

### Post by NightwishFan on 2010-10-25
> **bonixavier said:**
> I prefer to use Debian as an easy distro over Ubuntu because I don't like the marketplace that Ubuntu is becoming. Buy DVD player on Maverick was too much for me. Will Ubuntu require us to run Steam too in a while?
Besides, I don't like the lack of choices of the standard install cd of Ubuntu. And what if I don't want to upgrade to Grub 2? Who said that /dev/sda8 would be handling my booting?

I suppose you can feel that way however the purchasing of software is a good thing and not at all manditory. Not everyone needs to use entirely foss. :/

---

### Post by snowpine on 2010-10-25
> **Grenage said:**
> Bah, that's too harsh; The Phantom Menace was only marginally better than the Star Wars Holiday Special.

But it has excellent CG effects.

---

### Post by bonixavier on 2010-10-25
> **NightwishFan said:**
> I suppose you can feel that way however the purchasing of software is a good thing and not at all manditory. Not everyone needs to use entirely foss. :/

To each his own. I'm not radically against all and any proprietary software and I have a proprietary  Nvidia driver installed here. It's just that Maverick crossed a line. To me. If you or anyone likes it, great. I have to thank Ubuntu for introducing me to the Linux world, but I've found that it was time for us to go separate ways.

---

### Post by NightwishFan on 2010-10-25
And so it has. Well I hope you change your mind, but I think you will be good regardless, there is a lot of good projects out there.

---

### Post by Grenage on 2010-10-25
> **snowpine said:**
> But it has excellent CG effects.

Ah, touché.

---

### Post by kaldor on 2010-10-25
> **NMFTM said:**
> Some people might use Debian so they don't have to say they use a "newb" distro. Or a distro that's too mainstream and popular. Saying "I run Debian" sounds a little more hardcore than "I run Ubuntu".

That and...

1) Dependencies aren't as frustrating as on Ubuntu. Ever try *apt-get remove firefox*?

2) No hardware issues (for me); something gets knocked out every Ubuntu release.

3) Even Testing and Unstable have less stability issues than Ubuntu. I remember an update taking out my kernel in Ubuntu 8.10. I've updated the kernel multiple times in Debian testing without any issues.

4) Quicker boot by a few seconds.

5) Easier to tweak.

6) GNOME on Debian runs faster than Xubuntu on my hardware.

7) I can view 1080p videos on YouTube without video lag.

Good reasons :)

---

### Post by NightwishFan on 2010-10-25
Some of those are merely packaging issues (no pulse, etc) however I can agree some packages are more convenient. As for Firefox it removes:
```
firefox firefox-branding firefox-gnome-support
```

>_>???

---

### Post by kaldor on 2010-10-25
> **NightwishFan said:**
> Some of those are merely packaging issues (no pulse, etc) however I can agree some packages are more convenient. As for Firefox it removes:
```
firefox firefox-branding firefox-gnome-support
```

>_>???

Last time I tried (8.10?) I remember it trying to haul out ubuntu-desktop and a bunch of other applications. Maybe it was my fault or maybe it was fixed? It's been a while since I used Ubuntu as my main OS, but I remember having a lot of issues trying to remove or install certain things without removing/installing a bunch of other things.

---

### Post by NightwishFan on 2010-10-25
It is safe to remove a meta package like ubuntu-desktop. You just want it installed for convenience or upgrades.

---

### Post by kaldor on 2010-10-25
> **NightwishFan said:**
> It is safe to remove a meta package like ubuntu-desktop. You just want it installed for convenience or upgrades.

Ah, misunderstanding then. Scratch my accusation :)

---

### Post by XubuRoxMySox on 2010-10-26
Ubuntu brings Debian's awesomeness to "simple ordinary desktop users" like me. 

Just for fun, I thought I'd try Debian just to see if I could brag about it (*"Wow, look at me, I'm an "advanced" Linux user who has "graduated" from Xubuntu to Debian!"*) Well it worked (mostly, a net-install of Lenny/Xfce) and I was all set to start bragging about mad geek-skillz when I found that my sound didn't work (sound is essential for a dancer!) and my scanner wouldn't work and uh-oh, USB isn't recognized, oboy, what have I done!

I invested over a month in trying to fix my issues in Debian, and when I had it just the way I like it, I discovered two things:

**[COLOR="Purple"]1.[/COLOR]** That my "perfect-just-for-me" Debian net-install was almost identical to my old Xubuntu - except that Xubuntu was ready-made and mine took weeks to learn and put together, and

**[COLOR="#800080"]2.[/COLOR]** Sound still didn't work and some of the graphics in Iceweasel went all weird and stuff... I had abuncha hardware issues that I never had in Xubuntu.

I was going to just keep plodding through these things, but as the start of the school year drew near I realized I wouldn't have time to learn all that stuff and make it work, so I came back to good ol' everything-just-works Xubuntu. They've done all that work for me, and yet they made it so customizable that I could easily change everything to the perfect-just-for-me mixture I wanted without losing sound and scanner and without all the hardware issues.

:( I lost my bragging rights, but I gained a whole new appreciation for the work Ubuntu does in bringing Debian's power and wonderfulness to us ordinary, not-so-geeky kids.

-Robin

---

### Post by MisterGaribaldi on 2010-10-26
I run a private file server with Debian because I know it is rock solid stable and I don't ever have to question it.

However, I can't imagine really running Debian as a desktop OS.

---

### Post by bonixavier on 2010-10-26
> **MisterGaribaldi said:**
> I run a private file server with Debian because I know it is rock solid stable and I don't ever have to question it.

However, I can't imagine really running Debian as a desktop OS.
Why is that? If it's because of the apps' versions, I've found that Squeeze has some nice ones, especially when complemented with the occasional package from Sid.
If it's the "pretty" factor, you can easily get an Ubuntu-like feel with shiki themes, as you can see in the pic I attached.

I usually prefer Slackware, but I've been running Debian more lately because I got tired of installing everything extra manually and I guess I'm a Gnome guy. (I know you can install gnome in Slack).

---

### Post by fuzzylogic25 on 2010-10-27
thank you for all the responses, i have read them all and they provide great value into understanding this difference.

problem i have at the moment is that im a newbie to linux. i have to ask questions on the forum for virtually everything. even for unmounting a drive! so i guess i want to find a distro that will help me learn linux the best. i would like to really dive into the learning of linux, go quite deep so i can really understand the inner workings of everything. i would like to be able to do everything myself.

i feel that maybe ubuntu wont allow that since its doing everything for me (although I feel i do still have to do some work, its not all automatic). so would debian be better for learning linux better?

---

### Post by XubuRoxMySox on 2010-10-27
If you're like me you might find the whole process too frustrating to continue. It depends if you're "technically inclined" or not. If you are "technically inclined," then by all means go with Debian and truly learn it. 

If you're an end-user who just wants a ready-made desktop OS for general use (school, internet, music, e-mail), it doesn't get any easier than Ubuntu.

-Robin

---

### Post by cascade9 on 2010-10-27
> **dixiedancer said:**
> **[COLOR=Purple]1.[/COLOR]** That my "perfect-just-for-me" Debian net-install was almost identical to my old Xubuntu - except that Xubuntu was ready-made and mine took weeks to learn and put together, and
 
 **[COLOR=#800080]2.[/COLOR]** Sound still didn't work and some of the graphics in Iceweasel went all weird and stuff... I had abuncha hardware issues that I never had in Xubuntu.
 
 I've seen you say this before, and UI still wonder if your xubuntu experinces has made you want to make debian into xubuntu. 
 
 If you were using stable (lenny) then you might have to isntall sound drivers, etc which you wont have to on linux distros with newer kernels.

> **MisterGaribaldi said:**
> However, I can't imagine really running Debian as a desktop OS.

It works well. I've been using debian since before there was ubuntu, so maybe I've learnt how to prod and poke debian to get it to do what I want to? 

> **fuzzylogic25 said:**
> thank you for all the responses, i have read them all and they provide great value into understanding this difference.

problem i have at the moment is that im a newbie to linux. i have to ask questions on the forum for virtually everything. even for unmounting a drive! so i guess i want to find a distro that will help me learn linux the best. i would like to really dive into the learning of linux, go quite deep so i can really understand the inner workings of everything. i would like to be able to do everything myself.

i feel that maybe ubuntu wont allow that since its doing everything for me (although I feel i do still have to do some work, its not all automatic). so would debian be better for learning linux better?

I've found that a search engine works almost as well, and a lot faster than asking questions. 

Depending on what you want to learn, what debian version you use, and what hardware you have debian might not actually 'force' you to learn much, if anything. But there is a good chance you would want to learn some stuff with debian (even if you dont 'need' it, things like ATI/nVidia drivers).

---

### Post by snowpine on 2010-10-27
> **fuzzylogic25 said:**
> thank you for all the responses, i have read them all and they provide great value into understanding this difference.

problem i have at the moment is that im a newbie to linux. i have to ask questions on the forum for virtually everything. even for unmounting a drive! so i guess i want to find a distro that will help me learn linux the best. i would like to really dive into the learning of linux, go quite deep so i can really understand the inner workings of everything. i would like to be able to do everything myself.

i feel that maybe ubuntu wont allow that since its doing everything for me (although I feel i do still have to do some work, its not all automatic). so would debian be better for learning linux better?

The "mount" and "umount" commands (the Linux commands to mount and unmount a drive) are identical in Ubuntu and Debian. I am not sure how switching to Debian will help you learn these commands (or others like them). Ubuntu is a fantastic distro for new users to learn Linux. :)

---

### Post by NightwishFan on 2010-10-27
I do not know why folks assume Ubuntu is not advanced. Run the alternate installer in expert mode. Even with all that choice I highly doubt you will do any differently than the default Ubuntu install. ;)

Start from scratch and apt-get what you want.

---

### Post by malspa on 2010-10-27
> **snowpine said:**
> Ubuntu is a fantastic distro for new users to learn Linux.

I had to chuckle when I read that.  Over at the Debian User Forums recently, I mentioned Ubuntu and someone said:

> Recommending Ubuntu to a beginner seems and sounds like sticking the knife in his back.

Some folks over there just hate and Ubuntu and take every opportunity to try to come up with clever Ubuntu put-downs...

Total rubbish, as far as I'm concerned.

---

### Post by bonixavier on 2010-10-27
> **snowpine said:**
> Ubuntu is a fantastic distro for new users to learn Linux. :)
I totally agree. Although I don't use Ubuntu anymore, that's the distro I recommend to people who ask me about Linux.
> **NightwishFan said:**
> I do not know why folks assume Ubuntu is not advanced. Run the alternate installer in expert mode. Even with all that choice I highly doubt you will do any differently than the default Ubuntu install. ;)

GRUB not forcing itself into your system?
> **malspa said:**
> Total rubbish, as far as I'm concerned.
Distro-bashing is sooo stupid. EDIT: This is about the post you quoted, not yours.

---

### Post by Grenage on 2010-10-27
[http://pbfcomics.com/archive_b/PBF020-Skub.gif](http://pbfcomics.com/archive_b/PBF020-Skub.gif) :)

---

### Post by gradinaruvasile on 2010-10-27
I installed Debian after 9.10 came out and i wasnt impressed at all by it (on the contrary). 9.04 was wonderfully stable on my 3 computers i used. 9.10 was not (mind you i installed it from scratch after 2-3 months after release). Apps randomly crashing and whatnot.

So i decided to try Debian Testing. I use it since, i had no breakages - some small issues here and there that eventually went away after some upgrades + i had to install a package to make power management work (upower) and correct 1 character  in a config file to make a USB floppy work.
I really like it - it is better than Ubuntu after set up (this is a bit longer but worth it).
Also i like the size of the repositories - In Ubuntu you have to install tons of PPAs to match them.
The packages are much better cared for and upgraded in time. Not to mention the 3 levels of repositories - testing, unstable and experimental that provides the latest of any package, no need to dig around PPAs to find the latest version of package x.
I just like the feeling of "just works", i had some annoyances in Ubuntu when my laptop did not wake up from standby and such.
This being said, i use hardware that is Linux-compliant (mostly the nvidia video cards are to mention here) and had no big issues in Ubuntu euther, but Debian is more stable. Only a bit of knowledge is required.

---

### Post by Stan_1936 on 2010-10-27
> **Spice Weasel said:**
> ...runs on more processor architectures....

**[SIZE="5"]Excuse me! [/SIZE]** What proof do you have of that?  And more importantly, what proof does the Debian developers have of that?

---

### Post by snowpine on 2010-10-27
> **Stan_1936 said:**
> **[SIZE="5"]Excuse me! [/SIZE]** What proof do you have of that?  And more importantly, what proof does the Debian developers have of that?

[http://www.debian.org/ports/](http://www.debian.org/ports/)

---

### Post by NightwishFan on 2010-10-27
> **bonixavier said:**
> I totally agree. Although I don't use Ubuntu anymore, that's the distro I recommend to people who ask me about Linux.

GRUB not forcing itself into your system?

Distro-bashing is sooo stupid. EDIT: This is about the post you quoted, not yours.

No, it is NOT. I can use lilo if I want. People like you are belligerent on purpose.

---

### Post by bonixavier on 2010-10-27
> **NightwishFan said:**
> No, it is NOT. I can use lilo if I want. People like you are belligerent on purpose.

Sorry if I sounded that way. It is sometimes hard to make what you write sound the way you intended in a second language. My point was that I would not follow the default install of Ubuntu, at least regarding the boot manager. This is not me trying to be belligerent, but, from the OSes I've installed, there are only two that shove their boot managers down your throat: Ubuntu and Windows. That is something that really annoys me.  If you look at my post again, you'll see that I'm not here trying to create a comotion with the Ubuntu community. I recommend Ubuntu for the people who ask me without a second thought and I'm very grateful to it for letting me get acquainted with Linux, but, when it comes to my computer, I'd very much rather stick to Grub legacy because I don't have the time at the moment to fiddle with the scripts of Grub 2. Sure, I can boot into my Slack and reinstall Grub legacy, but why should I have to have that work?  If what is said above sounds aggressive, blame it on my poor English skills, not on any combative intentions.

---

### Post by NightwishFan on 2010-10-27
I see, then forgive my being quick to judge. I should say my point (other than to be rude which I did intend my apologies) is that Ubuntu is not intended to be configured from the main methods of installing it. It does have an easy to configure core though I will admit it might be slightly limited for some folks, it is there. The alternate (debian installer) works well, as does the ability to modify and re-package source.

I need to stop projecting my bad week here. I apologize.

---

### Post by Wiredfixer on 2010-10-27
I am little lost on This...

I use Ubuntu on my all day activities, in my work and sometimes in my Home, for gaming i have Windows 7.

Well, i like ubuntu, but in server plataform i have several problems with the updates, i've decided to no Update, or update only the Security Issues.

 Maybe, Debian is more for servers than Ubuntu, stable and that... but how about desktop?

 I use Ubuntu because i have apt and Software Center, in example, i want to see a movie and Ubuntu take care of that, download the codecs and installs for me... Can i do that with Debian? i mean "out of the box"?

 I want to use Debian, im only use Debian once in the past, then Ubuntu appears and make my life so easy, I've used Slackware and Other Distros, but for some exceptions, i like the easy way, i dont want to waste much time in configurations, the Operating System is make for DO THE THINGS EASY!! Whatever you like, included Windows and MacOS.

I dont want to be a Geek with a Ubberl33t system, i want to be a Practical Sysadmin, maybe thats the Microsoft Secret, make the things easier.. but in Security, they are a lot of voids.

 In Linux we make EVERYTHING we want, but maybe need to make things more "flat", If Debian makes my Life Easier in Both World (Desktop and Server), i definitely change to Debian, if other OS make my life Easyer and Secure, i change to it...

---

### Post by NightwishFan on 2010-10-27
If you install Debian with a wired connection it is quite easy to use. It is harder to set up with some things but usually more flexible. The only thing you need is to _know what you want_. Ubuntu makes the default install and some package configuration for the user where Debian does not. (There is more too it than that, but from a practical standpoint that the the main difference).

---

### Post by CharlesA on 2010-10-27
Haven't run into many problems with updates on Ubuntu, but I had a few show stoppers that took a while to figure out.

---

### Post by A_T on 2010-10-27
I've been trying the latest Squeeze live cd - then installed it to my hard drive. Very similar to Ubuntu really. The only thing I really miss is the Launchpad PPAs. The graphical installer has the advantage of offering the very handy "use the largest continuous free space" option which has been inexplicably removed from the Maverick installer.

---

### Post by Ron Jones on 2010-10-27
> **fuzzylogic25 said:**
> problem i have at the moment is that im a newbie to linux. i have to ask questions on the forum for virtually everything. even for unmounting a drive! so i guess i want to find a distro that will help me learn linux the best. i would like to really dive into the learning of linux, go quite deep so i can really understand the inner workings of everything. i would like to be able to do everything myself.

In 2002, I discovered Linux. And, like you, I wanted to dive in and understand it. But, with a wife, a mortgage, and a small business, I had to prioritize the things in which I invested my time. So, instead of "going hardcore" I went the Fedora -> CentOS route, and eventually ended up here at Ubuntu (though my servers still run CentOS)... And am quite thankful that it worked out this way.

If you have the time to put into it, and you really want to understand the inner workings of Linux, Gnome, Gnu software, and all the other cool, eccentric open source offerings out there... 

I recommend you start with something like Debian, and force yourself to learn how to interact with the OS at the command line. Build yourself a web server with no GUI on some old hardware. Buy a book on working with the shell.

Eventually, If you seek to climb some mountain, perhaps you'd be interested in something really crazy like Linux From Scratch ([http://www.linuxfromscratch.org](http://www.linuxfromscratch.org)) or some other version of a "hair shirt."

Just don't become one of those folks who say things like "real coders use vi/vim/Emacs/etc" OR "I build my websites with a text editor."

I enjoy Ubuntu as is. Enough so that just a few weeks ago, when my last PC finally gave up the ghost, I went whole hog, and made the switch from Windows to Linux. With very few exceptions, I've been able to function just fine with the solutions available through the Ubuntu Software Center.

Sure, I'd like a native WYSIWYG web editor with all the features of Dreamweaver. But since I use Drupal and Wordpress, it isn't actually a necessity. And, I'd like to figure out how to get the OpenOffice spreadsheet to sort currency numbers so that I can balance books with Moneydance (a fantastic accounting program that only costs $39.00 and runs on both Windows and Linux). There may be other eccentricities that I have to overcome, but nothing that makes me want to go back to Windows as a user.

In the final analysis, computers, OS's, distributions and desktops are  nothing more than tools we use to make our lives easier, more  productive, more interesting, and fun. They are not ends unto  themselves.

---

