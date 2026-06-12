---
title: "what linux needs?"
date: 2008-01-09
forum: Recurring Discussions
---

### Post by Xbehave on 2008-01-09
We need to stop worrying about market share and instead considerate on
in kernel
we need a stable kernel, 2.4 doesnt cut it anymore, 
we need reiser4 and zfs in the kernel (even if zfs need license agreements for distros)
we need suspend+hibernate hooks, but removal of suspend resume functions

out of kernel:
we need security (be it a repo that controls SElinux, apparmor)
we need a good office suite, sure OO is as good as MS but that doesnt mean its good. FF wasnt as good as IE, it was much better
aparently we need good video/music editing software (not image as gimp & kirka are good)
suspend+hibernate that works with kernel hooks but doesnt live in kernel

hardware:
we need better graphics card and sound card support (even if we use prop drivers)
we need better wireless support

ubuntu:
we need better ps3 support
we need a mixer audio system that controls program volumes like vistas
suspend+hibernate sorted automatically to use any option that will work
an auto post install question as to weather to install restricted software
wine ubuntu repo used by default 

fresh ideas? alot of compiz stuff is fresh and thats why its so much better than the alternatives. but as we cant stop people using our ideas we need fresh new software. i think that alot could be done to secure emerging markets (games console as pc, ultra portables, phones)
how integrated will a linux ultraportable be with a linux phone and a linux desktop, Is theyre an easy way they can be setup to use eachother ? what about transfering CPU intensive tasks to your desktop so it takes a minute not an hour ?

how ready are we for quantum computing? its not going to happen tomorrow but all the components are being developed so its not too long before supercomputers will be upgrading, so the kernel will have to be capable of processing data at near instant speed.

---

### Post by DoctorMO on 2008-01-09
Let me know when you've programmed some of the things on the list.

---

### Post by k99goran on 2008-01-09
I think that at this point Ubuntu is good enough to serve a large segment of computer users. I think what it needs is to be installed by default on more computers.
In terms of development, the project I am most interested in now is Wine. I'd like to see it more integrated in Ubuntu.

---

### Post by pjkoczan on 2008-01-10
Let me know when you get your version numbers correct. The Linux kernel is 2.6 (and a very mature 2.6), not 2.4.

---

### Post by zipperback on 2008-01-10
> **Xbehave said:**
> We need to stop worrying about market share and instead considerate on
in kernel
we need a stable kernel, 2.4 doesnt cut it anymore, 



The kernel IS stable. And the current release of the kernel source is 	2.6.23.13


> 
out of kernel:
we need security (be it a repo that controls SElinux, apparmor)

We have it.

> 
we need a good office suite, sure OO is as good as MS but that doesnt mean its good. FF wasnt as good as IE, it was much better

OpenOffice.org is a great office suite.

FireFox is excellent.

> 
aparently we need good video/music editing software (not image as gimp & kirka are good)
suspend+hibernate that works with kernel hooks but doesnt live in kernel


There are several really good video and music editing packages available.


> 
hardware:
we need better graphics card and sound card support (even if we use prop drivers)

We have the most commonly used graphcs and soundcards used.
ndiswrapper can also be used to use windows drivers under Linux in some cases as well. ndiswrapper works with more than just wifi card drivers.



> 
we need better wireless support


We have EXCELLENT wifi support.

> 
ubuntu:
we need better ps3 support

Linux runs on the ps3.

> 

we need a mixer audio system that controls program volumes like vistas



we have NUMEROUS applications for sound control which work equal or better than that already.





> 
suspend+hibernate sorted automatically to use any option that will work
an auto post install question as to weather to install restricted software
wine ubuntu repo used by default 

You mean like the restricted driver manager that AUTOMATICALLY notifies you that you have the option of instaling them? We already have that.

You also have the ability to install wine and numerous other items via synaptic, apt-get, add/remove, and several other methods.


> 
fresh ideas?

Ok. Start working on them. There are thousands of people working on fresh ideas for Linux on a daily basis. Open your code editor and start working on what you want. It's open source.


> 
how ready are we for quantum computing? its not going to happen tomorrow but all the components are being developed so its not too long before supercomputers will be upgrading, so the kernel will have to be capable of processing data at near instant speed.

Future hardware will be able to run Linux as it becomes available for development. It open source software so anyone that wants to work on making something work with Linux is free to do so.

As for quantum computers. Do you actually understand how quantum computers work? I don't think you do. However, once they are available for the general public, if it is possible to get Linux running on them, I'm pretty sure that it will happen. 

- zipperback
:popcorn:

p.s. I've been working with computers since about 1977.

---

### Post by zipperback on 2008-01-10
One of the reasons there are so many different distributions of Linux is because different people have different ideas of what would go into a perfect distribution of Linux.

If you think a distribution is missing something, then by all means, please create an application to meet whatever need you might have, and then release it under an open source license (GPL is an excellent choice of course) so that others are free to openly use and modify if they need, of course  you an always create your own distribution if you want, and if you find that enough people agree with you and like your ideas then your distribution will become popular.

It's open source, so feel free to try and create your own.

I prefer Ubuntu which is based on Debian. It works for 100% of my current requirements for my personal and business needs.

- zipperback
:popcorn:

---

### Post by Darkhack on 2008-01-11
> **Xbehave said:**
> We need to stop worrying about market share

Most users and developers don't care too much about market share.  It's a motivation and has some importance (if you have zero users, why bother working on the software?) but the focus is developing based on the community's needs and not how large that community is.

> **Xbehave said:**
> we need a stable kernel, 2.4 doesnt cut it anymore

We have a stable kernel.  Linus' tree is considered stable and right now is at 2.6.23.13.  Also most distributions don't use a vanilla kernel, so that point is moo (you know, like a cow's opinion?  It just doesn't matter).  It's the job of the distributor to stabilize the kernel.  Linus has said this time and time again.  Use a more stable distro like RHEL if you want that.  You also have the option of using 2.6.16.x which is like an LTS version of the vanilla kernel.  It's still receiving updates and a team has been formed to work on it since Linus abandoned the even/odd versioning system.

> **Xbehave said:**
> we need reiser4 and zfs in the kernel (even if zfs need license agreements for distros)
we need suspend+hibernate hooks, but removal of suspend resume functions

Didn't you just say we needed a stable kernel?  Reiser4 and ZFS are highly unstable at this point (I don't even think Solaris boots on ZFS yet, just has R/W support).  Suspend/Hibernation is part of ACPI support which is being worked on.  The best way to help out is to file bug reports on all machines which won't do this properly.  You might also try the latest vanilla kernel or Andrew's -mm tree.

> **Xbehave said:**
> we need security (be it a repo that controls SElinux, apparmor)

We have that.

> **Xbehave said:**
> 
we need a good office suite, sure OO is as good as MS but that doesnt mean its good. FF wasnt as good as IE, it was much better

True, IE sucks, but there is room for improvement in Firefox too as is the case with all software.  The reason OpenOffice sucks is because it is based on the proprietary StarOffice from Sun Microsystems and uses a lot of Java which has an performance impact.  It also uses it's own engine for rendering the GUI and just binds to GTK+, Win32, etc for appearance purposes.

KOffice 2 is in development and is looking sharp.  Definitely give that a try if you don't like OpenOffice.  Maybe take a look at AbiWord and Gnumeric as well.

> **Xbehave said:**
> aparently we need good video/music editing software (not image as gimp & kirka are good)

I find it ironic you would say that we need improved audiovisual applications and then say The GIMP is good enough despite a raging fanbase that says otherwise.  I'm not a photo person so I only do the most basic of edits, but The GIMP is lacking a lot of features such as CMYK support used by a lot of print shops (though I hear there is a third party plugin, but I haven't tried it).  The GIMP is good enough for me, but lacks too many professional features.

> **Xbehave said:**
> 
hardware:
we need better graphics card and sound card support (even if we use prop drivers)
we need better wireless support

Write to the company that manufactures your hardware which doesn't work and ask for open specifications.  Nine times out of ten it's the fault of the company keeping secrets on the device's interface that won't allow kernel developers to write device drivers.

> **Xbehave said:**
> 
we need a mixer audio system that controls program volumes like vistas

Hardy Heron (8.04) has PulseAudio which has this feature.

> **Xbehave said:**
> 
an auto post install question as to weather to install restricted software

We already have a dialog that appears to install restricted codecs when you try to play them.  Isn't that good enough?  Enabling the full repo for other stuff is just a few clicks away.

> **Xbehave said:**
> 
i think that alot could be done to secure emerging markets (games console as pc, ultra portables, phones)
how integrated will a linux ultraportable be with a linux phone and a linux desktop, Is theyre an easy way they can be setup to use eachother ?

This I agree with completely.  I'm not sure what solutions are out there but Linux is running on all sorts of devices from the world's largest supercomputers to handheld devices in our pockets and having software to synchronize data would definitely be helpful.

> **Xbehave said:**
> 
how ready are we for quantum computing? its not going to happen tomorrow but all the components are being developed so its not too long before supercomputers will be upgrading, so the kernel will have to be capable of processing data at near instant speed.

That's the last thing you should worry about.  Quantum computing is way off and even if it came out tomorrow Linux is almost always the first to support new technologies because of its rapid release cycle.  We've had 64 bit and SMP support before it was even a twinkle in Microsoft's eye.  75% of the world's supercomputers run on Linux because of its ability to support such new and powerful technologies.  A few examples which demonstrate this point.

[http://linux.slashdot.org/article.pl?sid=03/08/27/2357227](http://linux.slashdot.org/article.pl?sid=03/08/27/2357227)
[http://linux.slashdot.org/article.pl?sid=05/11/14/2052248](http://linux.slashdot.org/article.pl?sid=05/11/14/2052248)
[http://slashdot.org/article.pl?sid=04/07/18/1530256](http://slashdot.org/article.pl?sid=04/07/18/1530256)

PS - Not to be rude or a spelling nazi, but you need to work on your spelling.

---

### Post by 23meg on 2008-01-11
What "Linux" needs: less of these threads, more people educating themselves and getting involved, more actual effort going into improving it.

---

### Post by mr.propre on 2008-01-11
> **23meg said:**
> What "Linux" needs: less of these threads, **more people educating themselves** and getting involved, more actual effort going into improving it.

Why educating themselves? We need vision of Computer/IT-class.
Not "How to work with windows", but with a computer.
Not "How to work with MS office", but with Office.

They say that (Belgium) school system is neutral, but the only thing you learn about Linux, is when the definition of an OS is explained. They should learn the basics of windows and Linux.

---

### Post by klange on 2008-01-12
So help me god if anyone mentions Photoshop in this topic I will... 

Anyway, we have all of this.
Though I can agree, I'd love a better PS3 linux, but the only thing that's missing is hardware support that we can't possibly get (IE, graphics card drivers, which nVidia and Sony refuse to provide at this time, and none of the "third-party" ones work with the card)

On the topic of video editing, I've been using Cinellera which is *great*. Though I wish it had a more... compliant interface.

---

### Post by popch on 2008-01-12
> **WindowsSucks said:**
> So help me god if anyone mentions Photoshop in this topic I will... .

Photoshop rulz!

PHOTOSHOP RULZ!

Now what, WS

---

### Post by Xbehave on 2008-01-12
this was mainly meant as a Linux isnt perfect but we don't need to compete with windows post in a different thread but from it Ive learn't a bit here so here are a few answers to responses:

ps3 isnt that well supported, well thats the impression you get at:
[http://psubuntu.com/](http://psubuntu.com/) 

> **pjkoczan said:**
> Let me know when you get your version numbers correct. The Linux kernel is 2.6 (and a very mature 2.6), not 2.4.
I know about 2.6 kernel it is infact you dosen't understand kernel numbering.
2.4 was the old stable version of the kernel (a version that doesn't receive new features but just bug, security & driver fixes )
where can a maintained version 2.6.16.x be found kernel.org dosen't list it, and using a distros kernel completely removes the aim of a stable kernel to be something for 3rd party developers to work on.

zfs/reiser4
im not saying thier stable but zfs is what we need so backup capabilities of linux systems can make then 100% reliable
and reiser4 is the ultrafast, ultracompact brother that smaller systems need (its also fairly stable and a lot of kernel politics are coming into play, but i intend to install a 2nd disto on it so will find out if its stable soon)

suspend/hibernation
as a dsktop user i dont see a need for it to be in the kernel, just because other OSs offer hibernate suspend doesn't mean linux should i see no reason for anybody but a laptop to use them.

3rd party/prop software
sorry im a kubuntu user i didn't get such options and flash didnt work without a tweak or manual install.

ive had a look at all the office suits but they each have problems and none of them have the killer edge. IMHO2.6.16.x 2.6.16.x 2.6.16.x  an office suit is alot like a web browser and so the killer edge is in allow a firefox level of customization. I will keep an eye on koffice but ive not been impressed by kspread yet.

i have no idea when it comes to gimp, cinellera but these seam to be common complaints

p.s firefox needs a better spell checker and preferably a grammar checker too

---

### Post by Vadi on 2008-01-12
Users and drivers.

That's it!

---

### Post by zipperback on 2008-01-12
> **23meg said:**
> What "Linux" needs: less of these threads, more people educating themselves and getting involved, more actual effort going into improving it.



I agree. People who post long complaints are generally just adding the FUD rather than solving any issues.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-12
> **Xbehave said:**
> this was mainly meant as a Linux isnt perfect but we don't need to compete with windows post in a different thread but from it Ive learn't a bit here so here are a few answers to responses:

ps3 isnt that well supported, well thats the impression you get at:
[http://psubuntu.com/](http://psubuntu.com/) 



There are NUMEROUS distributions of Linux which will run on the PS3.

Check google for it. Here you go.
[http://www.google.com/search?hl=en&q=ps3+%2B+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=ps3+%2B+linux&btnG=Google+Search)



> 
I know about 2.6 kernel it is infact you dosen't understand kernel numbering.
2.4 was the old stable version of the kernel (a version that doesn't receive new features but just bug, security & driver fixes )
where can a maintained version 2.6.16.x be found kernel.org dosen't list it, and using a distros kernel completely removes the aim of a stable kernel to be something for 3rd party developers to work on.



heh... I've been working with computers since about 1977, so actually I DO have a very solid understanding about how the number system works for software releases such as the kernel. I've been a developer for a good portion of that time. I DO know what I am talking about. :)

Rather than argue with you, I will simply present the facts.

> 

someuser@somecomputer:~$ uname -a
Linux laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux



The current kernel installed on my system is in fact from Ubuntu, and is VERY stable. :KS

> 
zfs/reiser4
im not saying thier stable but zfs is what we need so backup capabilities of linux systems can make then 100% reliable
and reiser4 is the ultrafast, ultracompact brother that smaller systems need (its also fairly stable and a lot of kernel politics are coming into play, but i intend to install a 2nd disto on it so will find out if its stable soon)


You can't have it both ways. Do you want stability or not?You talk of stability requirements, yet you want to use an unstable fs? make up your mind.

> 
suspend/hibernation
as a dsktop user i dont see a need for it to be in the kernel, just because other OSs offer hibernate suspend doesn't mean linux should i see no reason for anybody but a laptop to use them.

Doesn't matter to me either way. When I am done, I just shutdown my system, when I want to use it, I press the power button, boot up, and log in.

> 

3rd party/prop software
sorry im a kubuntu user i didn't get such options and flash didnt work without a tweak or manual install.



Add the repositories to your system and use adept installer to install whatever you want. You can also install other package managers if you want them. Kubuntu is Ubuntu with the KDE desktop. You have the ability to use gnome applications using Kubuntu, just like you can use Kubuntu applications with Ubuntu. I have several Kubuntu applications that I use on a regular basis, and I use the Gnome desktop. :popcorn:


> 

ive had a look at all the office suits but they each have problems and none of them have the killer edge. IMHO2.6.16.x 2.6.16.x 2.6.16.x  an office suit is alot like a web browser and so the killer edge is in allow a firefox level of customization. I will keep an eye on koffice but ive not been impressed by kspread yet.

i have no idea when it comes to gimp, cinellera but these seam to be common complaints

p.s firefox needs a better spell checker and preferably a grammar checker too


This has been discussed at length in several threads.

There are several office suite options available.
OpenOffice.org
Star Office
Several other options.....

-zipperback
:popcorn:

---

### Post by Darkhack on 2008-01-12
> **Xbehave said:**
> where can a maintained version 2.6.16.x be found kernel.org dosen't list it, and using a distros kernel completely removes the aim of a stable kernel to be something for 3rd party developers to work on.

The latest version is 2.6.16.58 which was released on January 6, 2008.  It doesn't have it's own page, but you can find it in [the pub]("http://www.kernel.org/pub/linux/kernel/v2.6/").

> **Xbehave said:**
> 
suspend/hibernation
as a dsktop user i dont see a need for it to be in the kernel, just because other OSs offer hibernate suspend doesn't mean linux should i see no reason for anybody but a laptop to use them.

I use it on my desktop all the time.  If I want to leave for a few hours but not have to do a full shutdown, I put my desktop to sleep or in hibernation.  Also, Linux does run on laptops, so it does need suspend/hibernation support.

> **Xbehave said:**
> 
ive had a look at all the office suits but they each have problems and none of them have the killer edge. IMHO2.6.16.x 2.6.16.x 2.6.16.x  an office suit is alot like a web browser and so the killer edge is in allow a firefox level of customization. I will keep an eye on koffice but ive not been impressed by kspread yet.

OpenOffice is fairly customizable and offers extension support, just like Firefox.  KOffice is currently in the process of developing version 2.0 which is basically an entire rewrite.  Wait for it to stabilize and see if you like it better then.

> **Xbehave said:**
> 
p.s firefox needs a better spell checker and preferably a grammar checker too

I've never had any major problems with Firefox's spell checker.  Always works wonders for me and even recognizes common terms and pronouns.  As for a grammar checker, maybe.  That's a big maybe though considering my past experience with grammar checkers (MS Office) has been nothing but an extremely poor experience.  Microsoft's grammar checker always freaks out at anything above a 4th grade level of writing.

---

### Post by mdsmedia on 2008-01-12
> **zipperback said:**
> 
heh... I've been working with computers since about 1977, so actually I DO have a very solid understanding about how the number system works for software releases such as the kernel. I've been a developer for a good portion of that time. I DO know what I am talking about. :)

Sorry, but time spent "working with computers" does not mean a dam* thing. I've been "working with computers" since 1986, but I'm still a beginner, so please don't try to increase your stocks artificially. BTW, you do realise that computers have changed a little in the last 30 years?

What is a good portion of that time, and what sort of development?

---

### Post by oldos2er on 2008-01-12
> **WindowsSucks said:**
> So help me god if anyone mentions Photoshop in this topic I will... 

 Photoshop, the Godwin's Law of Ubuntu Forums!

---

### Post by mdsmedia on 2008-01-12
> **oldos2er said:**
> Photoshop, the Godwin's Law of Ubuntu Forums!More accurately, the Godwin's Law of Linux discussions.

---

### Post by Vadi on 2008-01-12
I wonder how many people who scream for photoshop can actually use the software for what it's designed for.

The majority would be better off with gnu/ms paint (or picasa) just fine.

---

### Post by xArv3nx on 2008-01-13
Linux needs unity.

I'm sure that if you put everything in the Linux world together, into ONE operating system, you would have something that could beat OS X and Windows.

But, let's be honest here, that's never going to happen.

---

### Post by smartboyathome on 2008-01-13
> **xArv3nx said:**
> Linux needs unity.

I'm sure that if you put everything in the Linux world together, into ONE operating system, you would have something that could beat OS X and Windows.

But, let's be honest here, that's never going to happen.

Nope, it isn't, and that is because everyone has a different idea of what the perfect os is and no one will be able to agree on what would go in it.

---

### Post by popch on 2008-01-13
> **Vadi said:**
> I wonder how many people who scream for photoshop can actually use the software for what it's designed for.

The majority would be better off with gnu/ms paint (or picasa) just fine.

Possibly true. Not relevant. Because the majority of people clamouring for features in linux would probably be better off with paper, pencil, finger paint, game boards and playing cards, anyway.

---

### Post by Vadi on 2008-01-13
Hey, if you're a professional graphics artist, you do need it. If you need to resize a photo or clear that red eye, Picasa will do it for you in two clicks.

And Linux doesn't need unity, at least not as an one OS. It's freedom that Linux is about, that same freedom also spawned umpteen distros. Sure, we could use less of them, but one would never do. It would never satisfy everyone.

---

### Post by Darkhack on 2008-01-13
> **xArv3nx said:**
> I'm sure that if you put everything in the Linux world together, into ONE operating system, you would have something that could beat OS X and Windows.

A distribution is nothing more than a collection of packages with a package manager.  Ubuntu uses APT (originally from Debian) and I could go in and edit Ubuntu to make it just like any other Debian based distro by swapping in/out packages and changing settings.  If I was skilled enough I could even replace APT with RPM and manually alter Ubuntu until it becomes another distro, say Fedora for example.

The point is that "one" distribution of Linux would never be good because everyone's idea of what a distribution should be are different.  Some distros are used for servers, others for desktops, and others for embedded devices and thin-clients.  The best way to improve Linux is to work on individual packages.  Whatever is wrong with Linux that makes it unable to "beat OS X and Windows" (it's not a contest anyway) then the problem most likely lies with bugs or a lack of features for individual packages and very little of it has to do with the distro.

---

### Post by Xbehave on 2008-01-13
> You can't have it both ways. Do you want stability or not?You talk of stability requirements, yet you want to use an unstable fs? make up your mind.
Im talking about 2 different kernel versions so i can have booth. also im talking about a stable kerenl in terms of a consistant platform for stable distros and comercial software to be designed for. besides how unstable are zfs and reiser4, as far as i can tell the main complaint is that reiser4 hasnt been suficently well tested, not having used either i cant really comment. I mean stable in terms of consistent (what the even numberd kernels were), not in terms of not crashing because i can vouch for the ubuntu kernel not being that stable as it locks up quite often on my system (right down to kernel level lock ups)
I also disagree completly that the distros should all stabalise thier own kernels, if each distro produced its own platform for apps then whats the point in them all being linux.

linux does need some unity? a common kernel would help, as would a way to install rpms or yums or debs on any system (alien doesnt always work), but theres no point in forcing it!

---

### Post by airtonix on 2008-01-13
it needs to become like Wintermute from Gibsons stories, or "Server" in Sean Kennedy's "afternow" radio play series.

"A big megacorp turns on shop one day to find its computer mainframe wiped clean. I'm sorry evil slave labour megacorp, you have been hacked by 'Server'"

All hail Server. Server will protect us.

---

### Post by zipperback on 2008-01-13
> **mdsmedia said:**
> Sorry, but time spent "working with computers" does not mean a dam* thing. I've been "working with computers" since 1986, but I'm still a beginner, so please don't try to increase your stocks artificially. BTW, you do realise that computers have changed a little in the last 30 years?

What is a good portion of that time, and what sort of development?


I've been a professionally paid software engineer for well over 20 years.

6502 assembly language, x86 assembly language, Integer Basic, Applesoft Basic, Visual Basic, Visual Basic.net,  Pascal, C/C++, C#, PHP, Perl, Fortran, and a couple of others.

- zipperback
:popcorn:

---

### Post by Vadi on 2008-01-13
That's excellent.

Could you please help code then? We're bursting with ideas, it's coders that are in limited supply.

---

### Post by zipperback on 2008-01-13
> **Vadi said:**
> That's excellent.

Could you please help code then? We're bursting with ideas, it's coders that are in limited supply.


Tell me a little of what ideas you are working with. There may be projects already under development which fill the need. If it's a fresh, new, and useful idea, that I would personally find useful, then yes I would probably be happy to contribute to it.

- zipperback
:popcorn:

---

### Post by Vadi on 2008-01-13
[http://wiki.ubuntu.com/UbuntuDevelopment](http://wiki.ubuntu.com/UbuntuDevelopment) Would be an excellent start, and thank you :)

(that's just for Ubuntu itself though. There are tons of other projects about that you could take a look at too. Or if you're interested in MUD clients any, PM me!)

---

### Post by swoll1980 on 2008-01-14
> **Xbehave said:**
> 

how ready are we for quantum computing? its not going to happen tomorrow but all the components are being developed so its not too long before supercomputers will be upgrading, so the kernel will have to be capable of processing data at near instant speed.

It will be 20 years or so before you have qubits in your home computer. Why would you worry about this now

---

### Post by zipperback on 2008-01-14
> **Vadi said:**
> [http://wiki.ubuntu.com/UbuntuDevelopment](http://wiki.ubuntu.com/UbuntuDevelopment) Would be an excellent start, and thank you :)

(that's just for Ubuntu itself though. There are tons of other projects about that you could take a look at too. Or if you're interested in MUD clients any, PM me!)


Thanks. I'll take a look at that information.

- zipperback
:popcorn:

---

### Post by Vadi on 2008-01-15
Another good link would be the bounties page:

[https://wiki.ubuntu.com/BountyProposals?highlight=%28bounty%29](https://wiki.ubuntu.com/BountyProposals?highlight=%28bounty%29)

---

### Post by Xbehave on 2008-01-18
> **bloor75 said:**
> It will be 20 years or so before you have qubits in your home computer. Why would you worry about this now

yeah but linux doesnt just run on home computers, it will be be 5/10 till its on supercomputers, and depending on how its done an OS trying to run on them will need major changes. e.g one way i can see them working is without clocks, which will probably require a lot of change to kernel code!

"http://wiki.ubuntu.com/UbuntuDevelopment Would be an excellent start, and thank you "
really i thought Ubuntu just packaged everything unlike Novel and red hat that actually make new programs?

---

### Post by zipperback on 2008-01-18
> **Xbehave said:**
> yeah but linux doesnt just run on home computers, it will be be 5/10 till its on supercomputers,

Linux supercomputing isn't a new thing.

[http://www.google.com/search?hl=en&q=linux+%2B+supercomputer&btnG=Google+Search](http://www.google.com/search?hl=en&q=linux+%2B+supercomputer&btnG=Google+Search)
[http://www.internetnews.com/ent-news/article.php/3417221](http://www.internetnews.com/ent-news/article.php/3417221)
[http://www.linux.com/articles/7359](http://www.linux.com/articles/7359)
[http://www.wired.com/science/discoveries/news/2000/03/35113](http://www.wired.com/science/discoveries/news/2000/03/35113)
[http://www.forbes.com/2005/03/15/cz_dl_0315linux.html](http://www.forbes.com/2005/03/15/cz_dl_0315linux.html)
[http://www.news.com/2100-1001-884297.html](http://www.news.com/2100-1001-884297.html)

- zipperback
:popcorn:

---

### Post by Xbehave on 2008-01-18
i think you missed my point, my point is that
quantum computing is a big change
it will only be 5/10 years before quantum supercomputers are about
so the kernel devs only have 5/10 years to make the major changes to keep linuxs huge lead in the supercomputer market (i think 9 out of 10 suppercomputers perfer linux)

---

### Post by Vadi on 2008-01-18
Ubuntu develops it's own applications too that I see. Isn't Synaptic, Add/Remove made by ubuntu?

I don't know really, but I appreciate all the combined effort.

---

### Post by Darkhack on 2008-01-18
> **Xbehave said:**
> so the kernel devs only have 5/10 years to make the major changes to keep linuxs huge lead in the supercomputer market

Are you saying that you expect them to develop against a platform which doesn't even exist yet?  How are they supposed to develop for a quantum computer when none exist?  Also, [Linux already runs on 85% of the top 500 supercomputers]("http://en.wikipedia.org/wiki/Linux#Servers_and_supercomputers").  I don't see that changing any time soon.

May I ask what specifically you think the kernel developers should do?  What prompted you to make that comment about losing marketshare with supercomputers?

---

### Post by Xbehave on 2008-01-20
> **Darkhack said:**
> Are you saying that you expect them to develop against a platform which doesn't even exist yet?  How are they supposed to develop for a quantum computer when none exist?  Also, [Linux already runs on 85% of the top 500 supercomputers]("http://en.wikipedia.org/wiki/Linux#Servers_and_supercomputers").  I don't see that changing any time soon.

May I ask what specifically you think the kernel developers should do?  What prompted you to make that comment about losing marketshare with supercomputers?
I was merely pointing out that its more important than worrying about copying windows. (its alot easier to loose 85% than to gain it)

I could suggest, shifting from a cycle based mode for operations (send requests..wait a cycle..read responses) to a dynamic one where responses are read as they are received (with checks to prevent lockup) but ofc this is irrelevant as alot of kernel developers are physicists so know more than me about quantum computing!

---

### Post by Darkhack on 2008-01-21
> **Xbehave said:**
> I was merely pointing out that its more important than worrying about copying windows. (its alot easier to loose 85% than to gain it)

It's more important to worry about a non-existant platform that it is to develop useful features because we're afraid of "copying" someone?

:confused:

---

### Post by Xbehave on 2008-01-21
> **Darkhack said:**
> It's more important to worry about a non-existant platform that it is to develop useful features because we're afraid of "copying" someone?

:confused:
Its more importnat to keep what youve got than concentrate on getting new stuff to the point you lose what you have!

---

### Post by Darkhack on 2008-01-21
> **Xbehave said:**
> Its more importnat to keep what youve got than concentrate on getting new stuff to the point you lose what you have!

Fair enough, but I don't think that's a problem that Linux is suffering from.  We have a good balance at this point.

---

