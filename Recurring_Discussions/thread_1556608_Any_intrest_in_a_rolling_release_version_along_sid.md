---
title: "Any intrest in a rolling release version along side LTS &amp; 6-month?"
date: 2010-08-19
forum: Recurring Discussions
---

### Post by AnimeOmega on 2010-08-19
First of all, I'm sorry if this thread exists already :(. I come in peace, I mean no harm. 

I've just came back from Arch Linux because my HDD died on me and I wanted to install something that will get me back on my feet. So I tried Ubuntu 10.04 and I'm very impressed. It looks polished, it feels speedy and I loved the whole "Ayatana Project" thingys (:

*Rolling release is "an approach that refers to a continuously developing software system, as opposed to one with versions that must be reinstalled over the previous versions." ([http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release))*

I miss that about Archy D:

I'm not saying "stop the LTS and 6-month versions" just have a unstable/testing rolling release version for developers to send bleeding edge packages. 

What are the benefits:
+ Generally it's easier to fix 1 program/bug vs. fixing whatever went wrong when you made a version jump upgrade.
+ You sacrifice a bit of stability to get early bug fixes, possible performance increase/optimization and new features.   
+ Choice, choice is awesome (: There's a LTS for those that want more stability, 6-month snapshots + minor upgrades for those that want a middle ground and a rolling release version for those that want to live on the edge. 
+ Developers get a new playground to test bleeding edge packages and *6-month and LTS benefit from the bug reports from the guys (and gals!) using the rolling release version*.

Please don't misunderstand, I don't want want Ubuntu to be a clone of another distro. Just to offer this choice, if it's possible. By possible I mean, if a significant number of users want it and the devs can maintain it. If those conditions are not satisfied, no problem, I'll live with the Alpha/Beta/RC releases + PPAs.

Since I mentioned PPAs, any PPA repository/directory? For example, if I search for "firefox" I get a URL to: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Google works, but maybe there's a site that keeps a list that I don't know about.

Anyone using Debian Unstable ([http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)) + Ubuntu (gnome with ubuntu's patches + ayatana project) repos? How is that working out? Anything I should know if I ever want to try that? Links?

Thanks for reading, feel free to share your thoughts (:

---

### Post by fatality_uk on 2010-08-19
> Any intrest in a rolling release version along side LTS & 6-month?
Not here!!!

---

### Post by snowpine on 2010-08-19
A reasonable question, and one that's been asked before. :)

The reason it will not happen is this: Ubuntu gets most of its code from Debian Unstable (code name "Sid"), which is a rolling release distro. They take a "snapshot" of Sid every 6 months and use it to make the next Ubuntu release. Logistically, you can't have a rolling release distro that's based on another rolling release distro... it just wouldn't make any sense and would be an immense duplication of effort. 

The closest you can get to "rolling release Ubuntu" is to use the Testing release (currently 10.10 Maverick), then when it goes stable in October, upgrade to the next Testing release (11.04) as soon as possible. (Or use Debian ;)!)

---

### Post by AnimeOmega on 2010-08-19
@snowpine:

Oh, I see. Thank you for the informative reply. (:

May I ask if it's possible to use Sid's repos for everything except the gnome packages and the ayatana stuff?

---

### Post by snowpine on 2010-08-19
> **AnimeOmega said:**
> @snowpine:

Oh, I see. Thank you for the informative reply. (:

May I ask if it's possible to use Sid's repos for everything except the gnome packages and the ayatana stuff?

I would not recommend using Debian repos in Ubuntu, no. It's true that Ubuntu is based on Debian, but they make enough changes that the repositories aren't compatible.

---

### Post by AnimeOmega on 2010-08-19
@snowpine:

I see, thanks again, actually meant installing Debian Sid and adding Ubuntu's repos. But the incompatibility would still be there, oh well :(.

EDIT: Actually, I think it can be done :D! A quick google search got me:
[http://www.debianadmin.com/adding-ubuntu-repositories.html](http://www.debianadmin.com/adding-ubuntu-repositories.html)

---

### Post by Spice Weasel on 2010-08-19
One word - Sidux!

---

### Post by snowpine on 2010-08-19
> **AnimeOmega said:**
> EDIT: Actually, I think it can be done :D! A quick google search got me:
[http://www.debianadmin.com/adding-ubuntu-repositories.html](http://www.debianadmin.com/adding-ubuntu-repositories.html)

Be very, very carefully following unsupported 3rd-party tutorials from 2006! :)

---

### Post by alexfish on 2010-08-19
NO

but you could try Live Magic if you want it debian based

or if based on Ubuntu try UCK

---

### Post by del_diablo on 2010-08-19
There is already Ubuntu rolling: Its called Debian sid.

---

### Post by Tibuda on 2010-08-19
The closest thing you can do in ubuntu is always use the testing version and change your sources.list right everytime the new repositories are online. I used to do this before switching to Arch. Maybe Canonical could just add a "testing" symlink to the current testing version (like Debian does).

---

### Post by cariboo on 2010-08-19
This has been asked several times before in one form or another, moved to recurring.

---

### Post by papangul on 2010-08-19
A version of linux mint based on debian testing is in the works and is likely to be relased anytime now:
[http://www.linuxmint.com/blog/?p=1467](http://www.linuxmint.com/blog/?p=1467)

There is another very good option - PCLinuxOS Gnome ZenMini Desktop: [http://www.pclinuxos.com/?page_id=186](http://www.pclinuxos.com/?page_id=186)

The later is based on pclinuxos and has synaptic(apt-rpm backend) and nautilus elementary.

---

### Post by murderslastcrow on 2010-08-19
Don't be silly. Why should Canonical lose more money maintaining that when very few people would use it and there are projects out there already (like Sid) that suit those purposes quite well?

You can also test the Alphas if you want to feel more on the edge. I think we need to consider that it's not just us doing stuff in our spare time- we can't push Canonical too far without them taking a hit.

Things are great the way they are now- I don't see how a rolling Ubuntu would be a huge improvement when we already have plenty of distros for that.

---

### Post by tjktyler on 2010-08-19
If you need updated packages, one of the easiest (IMO) ways to get new PPAs is Ubuntu Tweak. It keeps an updated list of select PPAs from Launchpad with bleeding-edge apps, with everything from kernel backports to extra themes. Plus, Ubuntu Tweak is a great all-around app. Customize your desktop, manage Compiz, clean and purge packages and the APT cache. Lots of fun stuff to keep you busy. ;)

---

### Post by NightwishFan on 2010-08-20
I think the rolling release model has too many disadvantages, especially for mass deployments.

---

### Post by Starks on 2010-08-20
I've gotten Sid and Experimental repos working pretty well with Ubuntu in the past.

---

### Post by papangul on 2010-08-20
> **murderslastcrow said:**
> Why should Canonical lose more money maintaining that when very few people would use it and there are projects out there already (like Sid) that suit those purposes quite well?
Imagine the proverbial average joe buying a computer with the rolling release version of Ubuntu preinstalled. He will never have to go through a distribution upgrade process(along with the "last release was the best release ever, current release is the worst release in history" issues). Also he will be automatically using the latest versions of software, without needing to add any ppa for that.

Maybe, for ordinary desktop users, the full potential of the centralized package management system is harnessed in a rolling release system.

---

