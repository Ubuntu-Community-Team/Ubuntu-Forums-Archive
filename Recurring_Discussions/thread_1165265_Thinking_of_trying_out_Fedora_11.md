---
title: "Thinking of trying out Fedora 11"
date: 2009-05-20
forum: Recurring Discussions
---

### Post by Kimm on 2009-05-20
Well, since I have some issues with Ubuntu, I'm concidering trying out Fedora 11 when it comes out, but I do have some reservations. Mind you, I used Fedora before I moved to Ubuntu (but: I moved to ubuntu just after Warty came out ;) )

For one, I'm not used to *.rpm packaging, and I found YaST in OpenSuSE to be kind of buggy, what does Fedora use and is it any good? how large are the repos? I'm also worried I wont be able to find packages for what I want, seems people only release Ubuntu packages these days :D

Perhaps you could suggest some other distro for me to try? Preferably hassle-free (So Slackware and Gentoo are out of the count, hehe)

Main reason I want to try something else is that with the last two releases of Ubuntu I've been having some issues that I cant get to the bottom with (some regarding PulseAudio, which I hear other distros have implemented better).

---

### Post by RiceMonster on 2009-05-20
Fedora uses yum and has large repos. It's one of the major distrbutions, so I wouldn't worry about lack of available software.

As for how well does yum work, I don't remember I only used Fedora briefly as version 9, however I'm going to be installing the new version on my new computer which I'm buying in a few weeks.

---

### Post by LoloftheRings on 2009-05-20
Fedora has some good package managers. For command line, it used yum, which is pretty similar to apt. For instance, 'apt-get install application' equals 'yum install application' with yum. The graphical tool is PackageKit (if I'm not mistaking). Synaptics is better in my opinion but it's also just fine.

Repo's are smaller than Ubuntu's repo's. You may need to add some repo's but there's good documentation for it. Nvidia/Ati drivers can also be a pain in the back, but once you get past em, it works just fine.

I would say, give it a try and see for yourself! You could also install Fedora on a Flash drive using either Ubuntu's or Fedora's live usb utility.

Happy trying around

---

### Post by Dragonbite on 2009-05-20
Fedora is pretty good (you did read they pushed back  the release date for Fedora 11 by one week?).  It doesn't take long to get the hang of it, really.

Yum is slightly different than apt-get.  The biggest complaint I had trying Fedora was the lack of a good, browsable package management application (like Synaptic).  The Add/Remove Programs program was a pain. It took me a while to go through to install OpenOffice.org!

I finally downloaded Yumex, which is a package manager GUI which was alright, though slow.

Fedora, though, has had pretty good hardware detection, though I already knew my wireless (Broadcomm) was going to be an issue.

OpenSUSE is the other one I've really tried and it's alright though I am not 100% satisfied with Yast.

Basically I stick to the "big 3"; Ubuntu, openSUSE and Red Hat (Fedora and/or CentOS)

---

### Post by Kimm on 2009-05-20
So far it sounds all good, I probably wount wait long before switching then.

> **Dragonbite said:**
> Fedora is pretty good (you did read they pushed back  the release date for Fedora 11 by one week?)

I did read that, do you think it would be safe to install the preview?

---

### Post by Screwdriver0815 on 2009-05-20
the first thing you need to do with yum is installing "yum-fastestmirror" because otherwise the download of the packages takes ages.

The graphical frontend is named "Pirut" and to be honest: in my eyes it is sh.. so you should use the commandline instead to install packages.

Fedora itself is quite good but the version 10 (which I have tested) had some issue with the graphics and sound as I tested it. And it was too slow and unrelieable for me.

As other suggestion I would say: try Mandriva. Thats what I do at the time. Mandriva is really nice (in KDE) . It has some good features like a comfortable Computer Control Center where you can manage everything in one place.
The Packagemanager is really good (much better than yum). The networkmanager is also the best I have seen yet.... I think I stick with it on the Laptop

---

### Post by gnomeuser on 2009-05-20
> **Kimm said:**
> 
I did read that, do you think it would be safe to install the preview?

Running it right now.. no suspect ticking sounds from my laptop.

I am a former Fedora developer and I know the system fairly well, feel free put questions in private messages.

One thing you will need to know is that for legal reasons, there are no codecs nor any non-free drivers, rpmfusion.org is where you want to go after that it is all good.

Aside that enjoy your Fedora experience.

---

### Post by gnomeuser on 2009-05-20
> **Screwdriver0815 said:**
> the first thing you need to do with yum is installing "yum-fastestmirror" because otherwise the download of the packages takes ages.


Install the yum-presto plugin (a F11 only feature), that will save roughly 80% of the download by using deltas for the rpm files. yum-fastestmirror isn't problem free but if needed you can enable it as well.

> 
The graphical frontend is named "Pirut" and to be honest: in my eyes it is sh.. so you should use the commandline instead to install packages.


False, Fedora has used Packagekit since Fedora 9. Please try a recent version of Fedora if you are going to guide other users. Pirut has been long gone, no supported version of Fedora uses it anymore.

> 
Fedora itself is quite good but the version 10 (which I have tested) had some issue with the graphics and sound as I tested it. And it was too slow and unrelieable for me.


Please file bugs, also slow needs to be defined. Remember that since Fedora does most of it's work upstream those supposed performance and stability issues will likely hit other distros as they adopt this work so it is important to get them tracked down.

> 
As other suggestion I would say: try Mandriva. Thats what I do at the time. Mandriva is really nice (in KDE) . It has some good features like a comfortable Computer Control Center where you can manage everything in one place.
The Packagemanager is really good (much better than yum). The networkmanager is also the best I have seen yet.... I think I stick with it on the Laptop

Mandriva is a fine distribution, my dad has run it for years. If Fedora isn't right it is worth trying, as is Foresight Linux and openSUSE.

---

### Post by Random-penguin on 2009-05-20
My issue with Fedora is the fact that it is bleeding edge (the latest kernel etc) and this can (and does on my self built system) cause problems.

 I agree with Screwdriver0815, Mandriva for me is the best RPM distro; configuration tools are mature, the community is knowledgeable and very helpful and it works perfectly on my Eeepc 701 ;) However if you don't pay subscription (as far as I'm aware) x64 bit is unavailable (big problem for me).

I personnaly would try Debian.... It's very stable (Ubuntu's based on it) and thus quite conservative what is put out (things shouldn't break).

I've also had some good experience with DreamLinux. Again great GUI configuration tools and it looks great!!!

However why not stay with what you know and find solutions to your issues or file a bug report :D

---

### Post by Kimm on 2009-05-20
> **gnomeuser said:**
> Running it right now.. no suspect ticking sounds from my laptop.

I am a former Fedora developer and I know the system fairly well, feel free put questions in private messages.

One thing you will need to know is that for legal reasons, there are no codecs nor any non-free drivers, rpmfusion.org is where you want to go after that it is all good.

Aside that enjoy your Fedora experience.

Sounds awesome, backing up my data now and I'll probably do the install tomorrow 

:popcorn:

---

### Post by adrianx on 2009-05-20
[Here]("http://fedoraproject.org/wiki/Releases/11/FeatureList") is a feature list for Fedora 11. Not that everything will necessarily be smooth sailing (or to everyone's satisfaction :)), but the list is still very impressive.

---

### Post by Screwdriver0815 on 2009-05-20
> **gnomeuser said:**
> 
False, Fedora has used Packagekit since Fedora 9. Please try a recent version of Fedora if you are going to guide other users. Pirut has been long gone, no supported version of Fedora uses it anymore.

okay.... my fault... I thought it is named like that. The issue I faced was: when you search for packages even by exactly their name, it often did not find anything. Then you search manually and find it on the second line of the packagelist... all experienced in F9 and F10. But anyway... maybe I am too spoilt by apt and Synaptic.
So in Fedora, using yum in the terminal is much more efficient.

> **gnomeuser said:**
> 
Please file bugs, also slow needs to be defined. Remember that since Fedora does most of it's work upstream those supposed performance and stability issues will likely hit other distros as they adopt this work so it is important to get them tracked down.

slow... Booting was slow... and for example scrolling through an internetsite was like pulling on a chewing gum whereas Ubuntu was like a rocket in comparison. I don't know why. 
Asking in the fedoraforums wasn't succesful... fidling around with the graphicsdriver didn't help...  
I have deleted it because it was not useful for me. So filing bugs isn't possible anymore. 

But anyway: in my eyes Fedora is a really good distro. I liked it anyway and maybe I will try it again in the future.

---

### Post by mamamia88 on 2009-05-20
dang didn't even know it was coming out think i'll give it a go myself

---

### Post by samjh on 2009-05-20
> **Kimm said:**
> For one, I'm not used to *.rpm packaging, and I found YaST in OpenSuSE to be kind of buggy, what does Fedora use and is it any good? how large are the repos? I'm also worried I wont be able to find packages for what I want, seems people only release Ubuntu packages these days :DYou'll find commercial software tend to release theirs in rpm packages (eg. Adobe, Sun).

Fedora uses yum and PackageKit.  I personally prefer to use yum, but PackageKit is not bad.  Both are slower than apt-get/aptitude and synaptic, but you may find their interfaces and options more intuitive (mileage may vary).  The days of rpm's "dependency hell" are long gone.

The size of the repositories are almost as large as Debian's.  You should have no problems finding the packages you need, with the exception of proprietary codecs.  For proprietary codecs, go to [www.rpmfusion.org](www.rpmfusion.org) and follow the configuration instructions.  They also package proprietary video drivers (eg. Nvidia) as well.

You'll find that Fedora's packages are more up-to-date than Ubuntu's (or even Deian sid!), and they tend to backport new upstream releases more readily than Ubuntu does.  For example, I've recently found that Battle for Wesnoth, FlightGear, SimGear, and plib are more up-to-date than Debian sid.

One little thing: Fedora tends to have less fragmented packages than Debian or Ubuntu.  By fragmented, I'm talking about Debian's tendency to separate software into tiny little packages and the use of meta-packages and dependencies to install them all.  Fedora tends to bundle software into one (or few) packages.  This might contribute to Fedora's comparatively lower package count.

> Perhaps you could suggest some other distro for me to try? Preferably hassle-free (So Slackware and Gentoo are out of the count, hehe)Debian.

> Main reason I want to try something else is that with the last two releases of Ubuntu I've been having some issues that I cant get to the bottom with (some regarding PulseAudio, which I hear other distros have implemented better).Fedora has done a great job with PulseAudio.  When I compared Fedora's alpha with Jaunty's beta, audio worked infinitely easier on Fedora.

---

### Post by Mehall on 2009-05-20
if desperate, you can install "apt-rpm", the rpm port of apt, which allows you to "apt-get install" packages like you would in a Debian system. It't a complete port, as far as I can see, and I ain't had any issues with it.

yum's not too bad though, anyway

---

### Post by Dragonbite on 2009-05-21
If I remember right, using Yum in the command line was easier and provided better information than Apt-Get, but Synaptic beats them all. 

I don't know what the heck Kubuntu is using (it doesn't look like adept) but it's a royal pain!

---

### Post by ghindo on 2009-05-21
> **Dragonbite said:**
> I don't know what the heck Kubuntu is using (it doesn't look like adept) but it's a royal pain!KPackageKit, I believe.

---

### Post by MikeTheC on 2009-05-21
I really used to like Fedora, and I'm certain it's got many things going for it. I simply find that Ubuntu works better for me (apt, Debian's overall stability, layout of menus/menu items, etc.)

However, here's the thing: You'll never know what distro works best for you without trying them. So, good luck! (Meant sincerely and not sarcastically.)

---

### Post by rookcifer on 2009-05-28
No desktop distro can match Fedora in the security department out of the box.  It has SElinux enabled by default and all network daemons and most root level processes are locked down (contrast this to Ubuntu's AppArmor, where only Cups is locked down).  Fedora also compiles most of its packages with the GCC stack smashing protections (helps stop stack based buffer overflows).  They also use Exec-Shield which will not allow programs to write or execute from memory regions that should not be wrote to or executed from (this helps stop a lot of exploits).

Security is the main reason I use Fedora.  That and it has a nice KDE 4 implementation.

---

### Post by Dragonbite on 2009-05-28
Only 6 days to wait (for the official release)

---

### Post by rookcifer on 2009-05-28
> **Dragonbite said:**
> Only 6 days to wait (for the official release)

Add another week to that.  Release date moved back again. [http://fedoraproject.org/wiki/Releases/11/Schedule](http://fedoraproject.org/wiki/Releases/11/Schedule)

---

### Post by medicalystoned on 2009-05-29
Try puppy linux.   I just put that on an old laptop....I am so impressed, my OLD inspiron3800 is a little screamer now. anyway, check it out.

---

