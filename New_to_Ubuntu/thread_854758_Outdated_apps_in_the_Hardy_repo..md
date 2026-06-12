---
title: "Outdated apps in the Hardy repo."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by occams_beard on 2008-07-09
I wanted to install Eclipse, so I fired up Synaptic and found that the version in the repo is way outdated v3.2 (over a year old)... whoops.

Also did a search for Netbeans IDE, and discovered that it's outdated too at v6.0 when the  current version is 6.1.

Gnome Do, looked pretty neat... but, yep, it's also a version out of date... As were several other apps I wanted to install.

Sure, I can (possibly) install this stuff manually... But doesn't that negate the whole point of package managers like apt?

Am I missing something, or are apps in Ubuntu's repo supposed to be outdated?  I thought one of the benefits of Ubuntu was the ability to keep everything up to date via apt. :confused:

---

### Post by halitech on 2008-07-09
I think most of the apps are the verified stable apps that make it into the repos. If you want/need the latest version, I think you have to do it manually. (I could be wrong about this)

---

### Post by occams_beard on 2008-07-09
Who verifies their stability and what exactly constitutes a "stable" app?  Eclipse, for instance, is used by thousands of people, and the version in Ubuntu's repo is 2 versions out of date and is pushing two years old. 

Maybe I'm wrong, but it seems like the Eclipse community would have a better gauge on its stability than the Ubuntu repo maintainers.

---

### Post by halitech on 2008-07-09
the software developers would when making sure that it is stable with the version of Ubuntu they are developing at the time. Just because a program is stable in the developers environment doesn't mean it will be stable on all of them and maybe the Ubuntu developers found something that caused it to crash so they decided to stick with an older version.

---

### Post by occams_beard on 2008-07-09
Well, I did install the current version of Eclipse manually (what a pain) and it works fine. Also, the only dependency Eclipse has AFAIK is gtk, so there's really no reason the current version shouldn't be included in the repo.  And having an ancient version in the repo just seems ridiculous. 

Also, Netbeans is 100% Java, so it only depends on there being a JDK installed...

Sorry, I just don't get it. Who or what updates the repo?

---

### Post by nowshining on 2008-07-10
u'll find a lot of programs outdated and doing what u did by going to the publishers site is the only way to get an updated version.

[color=#FF6666]**U can always file a bug report on these in launchpad to let them know of these.**[/color]

Remember tho, they won't get included into hardy officially but might by backports, otherwise the apps only get security updates but NO upgrades to newer versions.

---

### Post by brian_p on 2008-07-10
> **occams_beard said:**
> Maybe I'm wrong, but it seems like the Eclipse community would have a better gauge on its stability than the Ubuntu repo maintainers.

Gory detail at:

[https://bugs.edge.launchpad.net/ubuntu/+source/eclipse/+bug/123064](https://bugs.edge.launchpad.net/ubuntu/+source/eclipse/+bug/123064)

If you have the time and skills:

[http://lists.debian.org/debian-java/2008/06/msg00036.html](http://lists.debian.org/debian-java/2008/06/msg00036.html)

But if you are desperate for a recent version:

[https://launchpad.net/~eclipse-team/+archive](https://launchpad.net/~eclipse-team/+archive)

---

### Post by billgoldberg on 2008-07-10
> **occams_beard said:**
> I wanted to install Eclipse, so I fired up Synaptic and found that the version in the repo is way outdated v3.2 (over a year old)... whoops.

Also did a search for Netbeans IDE, and discovered that it's outdated too at v6.0 when the  current version is 6.1.

Gnome Do, looked pretty neat... but, yep, it's also a version out of date... As were several other apps I wanted to install.

Sure, I can (possibly) install this stuff manually... But doesn't that negate the whole point of package managers like apt?

Am I missing something, or are apps in Ubuntu's repo supposed to be outdated?  I thought one of the benefits of Ubuntu was the ability to keep everything up to date via apt. :confused:

Since a new version of ubuntu comes out every 6 months, the devs decided to go for a "feature freeze".

That means the programs won't get updated to their next versions most of the time (there are exeptions like firefox).

The only updates for the programs you'll get are security or stability updates.

---

### Post by occams_beard on 2008-07-10
> 
Gory detail at:

[https://bugs.edge.launchpad.net/ubun...se/+bug/123064](https://bugs.edge.launchpad.net/ubun...se/+bug/123064)


Thanks for that brian_p. It's interesting reading.

> 
u'll find a lot of programs outdated...
U can always file a bug report on these in launchpad to let them know of these.


Then I'd have to file a bug report for nearly every app I want to install from the repo. Clearly something is wrong with this picture.

> 
Since a new version of ubuntu comes out every 6 months, the devs decided to go for a "feature freeze".

That means the programs won't get updated to their next versions most of the time (there are exeptions like firefox).


I'm not sure I buy that because the version of Eclipse currently in the repo dates back to the Feisty or Edgy days... 

Either way I find it amazing one has to wait 6 months and upgrade to an entirely new version of the OS, just to hopefully get somewhat "recent" versions of applications he or she depends on.  Seems like the repo concept is fundamentally flawed.

Is this unique to Ubuntu, or is it the same for all distros?  Also, wouldn't it make more sense to give the actual application developers access to the repo and let THEM maintain their apps?

---

### Post by SunnyRabbiera on 2008-07-10
debian does something simular, relying on stable versions of most apps...
latest doesnt always equal greatest.

---

### Post by occams_beard on 2008-07-10
> 
debian does something simular, relying on stable versions of most apps...
latest doesnt always equal greatest. 


It does if an application introduces a feature that you absolutely need to get your work done.  

Also, stuff like Eclipse and Netbeans are huge projects with 100s of devs, 1000s of users, corporate backing, etc... They don't release garbage. Their latest versions are always solid.  And besides, so what if they aren't stable?  I could see if it's something like a video driver that could screw up X... But these are IDEs, so what if they crash? It's not Ubuntu's problem.

---

### Post by halitech on 2008-07-13
It may not be Ubuntu's problem but new users will look at an app crashing as the system is no better then windows so why change everything and have to learn alot of things over again for a system that is no better then what they are leaving. You and I may know the difference between an app crash and a OS crash but my guess is that 90% of the general public wouldn't know the difference even with a pop up message saying "App XXXXXX has crashed, please restart it".

---

### Post by TSS on 2008-07-13
I had a similar thought about Eclipse the other day.  The version in the repositories still gets the job done, but that being said, Eclipse is a fairly stable application.  I would imagine at least the version between the current one and the one we have should be stable enough by now.  It would be nice to see it get updated in the repositories, but I'm not the one doing the grunt work, so I'll be happy with the version I have. :-)

---

### Post by Bachstelze on 2008-07-13
Please read this:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

That's how Ubuntu works. Don't like it? Don't use Ubuntu. As simple as that.

---

### Post by occams_beard on 2008-07-16
> It may not be Ubuntu's problem but new users will look at an app crashing as the system is no better then windows so why change everything and have to learn alot of things over again for a system that is no better then what they are leaving. 

This is the weirdest explanation yet. So you're saying that because a user might think Ubuntu sucks if an application crashes, we get stuck with ridiculously outdated applications? Yay, just what I need... an OS that treats like more of a child than MS does. What about the Freedom(tm) and Choice(tm) to use current applications!!!??!!?!

>  The version in the repositories still gets the job done...It would be nice to see it get updated in the repositories, but I'm not the one doing the grunt work, so I'll be happy with the version I have.

It might get the job done for you, but I need Mylyn to do my work. The version in the repo is 3.2, Mylyn was introduced in 3.3, and the current version is 3.4. 

Also, why settle just because you're not doing the "grunt work?" Surely the repo maintainers would find your criticism useful in improving Ubuntu. The squeaky wheel gets the grease.

> 
Please read this:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

That's how Ubuntu works. Don't like it? Don't use Ubuntu. As simple as that. 


And herein lies the fundamental flaw of desktop Linux as it stands today. Users are dictated to by the distro (The State?) which versions and which apps they get. We're back to 1997 and having to compile our apps again, and/or go through dependency hell just to use up-to-date software... Package repos are nearly impossible to keep current, and are just flat out broken.

And even worse, rather than accepting constructive criticism of this obvious flaw, users are told  "hey, don't use it."  Brilliant. The more experience I have with the FOSS community, the more I'm seeing this belligerent attitude.  For a great example, just take a look at the recent KDE 4 debacle. Users complain, KDE devs call them "poisonous" and say "we don't even need users." :confused:

---

### Post by halitech on 2008-07-18
never said we were stuck with the apps, there is always 2 choices (at least). 1. use what is provided 2. download from the developer and install 3. find a distro that has the apps you want 4. email the people that look after the repos and ask them to look at updating to newer versions of the software you are looking for. the freedom and choice  you are talking about is in numbers 1, 2 and 3. 

Personally I don't use any of the software you have mentioned. Does that mean I don't care? Not at all, I think that we should have access to the latest software available but I also look at it that I would rather have the most stable version that someone that knows more then me has tested to make sure that it works with the operating system I am using. I'm also still using 7.10. Why? because I choose to stay with it. Why? because it works for what I do and I don't see the need to upgrade right now.

> Package repos are nearly impossible to keep current, and are just flat out broken.
Not sure I would agree that they are broken but if I'm reading the first part the way you mean it, you basically just answered your own question in a way on why packages are not the latest version.

---

### Post by mjwhitfield on 2008-07-18
> **occams_beard said:**
>  Users are dictated to by the distro (The State?) which versions and which apps they get.Here comes the clue train, last stop - you.

When you pick a distro, you're asking someone else to package your Linux desktop and manage your software repo's for you. You need the pick the distro that suits you best.  If you want the latest software all the time, use Arch or Gentoo.  If you want stable, use Debian.

When you pick the distro you pick the package management and repo's as well. If the Ubuntu repo's just don't make you horny enough, swap to one that does.

---

