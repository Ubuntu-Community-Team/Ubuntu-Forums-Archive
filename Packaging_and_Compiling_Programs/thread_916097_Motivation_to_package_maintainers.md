---
title: "Motivation to package maintainers"
date: 2008-09-10
forum: Packaging and Compiling Programs
---

### Post by uid313 on 2008-09-10
We need more packages in the repository.
To get this, we need to get more package maintainers, make the process easier, and funnier by motivating the package maintainers.

We could give package maintainers motivation by having a highscore list with ranks that they can compete for with each other.
The more packages you contribute the higher level you get which unlocks new ranks. Ranks such as *Package Apprentice, Package Conjurer, Arch Packager, Package Master, Package Wizard, Package Lord*, and the highly prestigious *Lord of the Repository*.

[[IMG]http://img367.imageshack.us/ifs/7586/img366/2/highscorezz4.th.png[/IMG]](http://img367.imageshack.us/ifs/7586/img366/2/highscorezz4.png)

The top contributors could also be rewarded with a special t-shirt, or perhaps to make it cooler a medal or robe.
Imagine the guy wearing the unique prestigious robe of the diligent Lord of the Repository - he will be the envy of everyone, the crowd center around him. He will be the guy every girl wants, and every guy wants to be.

---

### Post by Oldsoldier2003 on 2008-09-10
Though "loot" is always a nice reward and can sometimes be a motivator, I would prefer that the package maintainers continue working the way they do now. We all benefit from them continuing to produce high quality properly formed packages. 

Rushing the process that weeds out the people that aren't paying due diligence to their work is a bad idea in my mind. So is creating an atmosphere that breeds a "rush to publish, must have quantity" attitude would be bad.

Just my personal thoughts on the matter, take from them what you will.

---

### Post by inportb on 2008-09-10
LOL I'm not sure how practical it would be, but I like your drawing =p

---

### Post by gilir on 2008-09-14
The problem is not the number of package maintainers. The problem is the number of reviewers. Look at REVU and all packages waiting. Look at the Ubuntu MOTU Sponsors bugs and all upgrades waiting.

More packagers is just useless if Ubuntu Dev/MOTU don't care/don't have time to review work from contributor.

---

### Post by andrewsomething on 2008-09-14
Not really a direct reply, but just something that people should note. Most packages in Ubuntu do not have a specific Ubuntu maintainer. As Ubuntu inherits nearly all of its packages from Debian, the aim of the Masters of the Universe (MOTU/ubuntu-dev) is to be generalists, not maintainers. They should feel comfortable working on many different kinds of packages making any needed Ubuntu specific changes and addressing issues that arise in the release process, pushing changes that would be usefully in Debian back to them. 

As far as new packages go, while Ubuntu will accept new packages, the best practice is to get them into Debian and maintain them there. This way you can contribute to Ubuntu and Debian at the same time. Also, it shows that you're serious about maintaining the package. As Ubuntu doesn't have specific maintainers, someone could get their package in then walk away with out ever taking care of issues that occur.

---

### Post by Pro-reason on 2008-09-16
> **andrewsomething said:**
> Ubuntu inherits nearly all of its packages from Debian

Actually, I was thinking of jumping ship.  You're making me think I should defect to Debian.  But dammit, I've got Ubuntu stickers on my PC and my bike, now.

---

### Post by andrewsomething on 2008-09-18
> **Pro-reason said:**
> Actually, I was thinking of jumping ship.  You're making me think I should defect to Debian.  But dammit, I've got Ubuntu stickers on my PC and my bike, now.

Just a quick follow up points...

First of all, I mostly speaking of packages in Universe. Many packages in Main are done specificity for Ubuntu (ie we package our own Gnome). Really the main difference between Debian and Ubuntu is the core default desktop experience. Many of the default settings and the integration in the default desktop is Ubuntu specific. 

I maintain a couple packages in Debian myself, as I find that the best way to give back to the community as a whole. No reason for those packages to be Ubuntu specific. By maintaining them in Debian, they are available to Debian users, Ubuntu user, Mint users, and so on down the line of derivatives. 

That said, I use Ubuntu as my main OS as I find the overall experience better. While I can fix many things myself, I still prefer that "it just works" in Ubuntu. While there's obviously a bit of hype in that claim, it's true enough that I see a personal benefit of running Ubuntu. 

As far as Universe packages go, the main benefit of the generalist approach of the MOTU that I see is that it is much easier to get certain fixes sooner. Have a strong core of devs that are allowed to upload fixes for any package in Universe gets more people working on them as opposed to simply leaving it to the individual maintainer. It allows people to use their strengths all over the archive. Of course this is a generalization, there are pros and cons to both approaches. 

Anyway, these are just some thoughts off the top of my head...

---

### Post by BrentNewland on 2008-10-18
It definitely is intimidating. I have a program, wallpaper-tray (randomly changes your wallpaper) that's tuck at 0.4.6 in universe with source at 0.5.5. I said to myself "You know, I could use that newer version and I bet a lot of other people could too! I know where the source is, I should be able to just make a deb file and upload both of those somewhere and someone else will take care of the rest!".

But no. I look into the process and find out I have to find or file bug reports, add tags, do a ton of stuff in the terminal to make a bunch of files (.dsc? .diff.gz? huh?), follow a bunch of preset guidelines and fill out tons of paperwork, then *maybe* attach *something* to a bug report and it might get included, but wait, I *might* have to wait a month to do it because Ubuntu is in a feature freeze.

This is such a pain! Why does it matter if Ubuntu is in a feature freeze if the package is going in universe? Shouldn't that only apply to main? Why isn't there an automated program to make everything you need? Why isn't there a simpler guide on how exactly to get a new version in the repos? Yes, I've followed [this]("https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate"). Step 8 is "DONE". That's great, does my computer automagically upload it directly into the repos?

I wish the process was much simpler. I wish there was an easy guide. I wish I could use a form to upload the new source (for an update), maybe a deb file, and nothing else and have it all taken care of. I wish we didn't have [1200 new package requests](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=needs-packaging) so I could just request someone to get a new program in and be assured it would get there. I wish that I could just make a deb, upload it and the source and have someone review it in a short, simple process (where the longest part is me making the deb) so I could help get that list of packages down. I wish there were people reviewing packages in Universe and Multiverse and adding them to a new "Crappyverse" for all the worthless programs.



Sorry, I'm just really frustrated right now. I started out visiting a link to start a supposedly simple process and have ended with an additional hundred or two packages, three opera windows with about thirty tabs opened, about two hundred pages visited, and a headache.

If the process was simplified a lot, and explained a lot more clearly, I have no doubt that a lot more people would be willing to help.

---

### Post by uid313 on 2008-11-21
We now have the Ubuntu Hall of Fame which is kinda like this in a way.
[http://hall-of-fame.ubuntu.com/](http://hall-of-fame.ubuntu.com/)

---

### Post by lifestream on 2008-11-21
Can you, ummm... not make all the females on that picture not be whores? I do not apreciate it. 

At the very least show some male sticks as asking them to sign their penis.

---

### Post by Pro-reason on 2008-11-22
> **lifestream said:**
> Can you, ummm... not make all the females on that picture not be whores? I do not apreciate it. 

At the very least show some male sticks as asking them to sign their penis.

Don't be such a killjoy.

---

