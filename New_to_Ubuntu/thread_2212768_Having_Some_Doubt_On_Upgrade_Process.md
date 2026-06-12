---
title: "Having Some Doubt On Upgrade Process"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by Akhil_K_A on 2014-03-23
Hello Ubuntu Team.

I'm just a niewbie in linux and kubuntu operating system. In my college they have installed "ubuntu 13.10". That looks great, but little bit hard to use. My friend recommended me to use "Kubuntu". Downloaded the LTS version 12.04 and create a bootable usb drive and tested live mode. Really easy and simple to use. So, I decided to install kubuntu with windows 7. After installing I'm unable to get into kubuntu. I created a thread and got a solution (I'm working on that) [http://ubuntuforums.org/showthread.php?t=2212603](http://ubuntuforums.org/showthread.php?t=2212603)

Here are my doubts and questions.

1. Now I'm on version 12.04, I know there is an another LTS version is going to be release on next month. My question is, is it possible to upgrade to 14.04 automatically from kubundu software updates, or is there any option to upgrade, without losing the data/settings in the current version? 

2. In the live mode, I have seen an option to refresh (F5) on the right mouse click while I'm on desktop. But, after the installation, that option disappears. How to enable the refresh option?

3. In live mode, I'm able to install the default wallpaper package. But, after the installation, I'm unable to install the default wallper package without internet. What is the reason?

4. What is the recommended portion size need for kubuntu to run smoothly without issues (now my kubuntu partition is 15GB)?

---

### Post by deadflowr on 2014-03-23
1) Yes, though it's been some time since I've done it with Kubuntu, upgrading from one to another newer version such as from 12.04 to 14.04 is possible.
It should keep whatever settings and configurations you have, barring changes to default applications and little things like that.
My personal take would be to hold off, if you decide to upgrade, until the first point release comes out.
(The first point release comes out around July/August)
Reason to wait 'til then is because many of the initial problems that come with the original release will have been fixed, or dealt with.
In any case, whether you go that route or simply do a fresh install, backup the files you want.

2)Never paid attention to refresh, for any desktop.. So in that regard, don't know.

3)Don't you already have a selection of Wallpapers to choose from?
Isn't the download wallpaper function simply to grab extra wallpapers, typically those uploaded to kde.org by regular users.

4)If you don't ever save anything, like pictures or movies or files in general, then 15GB is fine.
But if you do save things and like try out many programs, then perhaps upping the space to something closer to 25-30GB.
Not to say 15Gb isn't enough. It can be, depending on the usage.
(For some users, 15GB is far more than they need.)

---

### Post by Akhil_K_A on 2014-03-23
Hi deadflowr.

Thank you so much for the detailed explanation. It really covers all my doubts.

---

### Post by deadflowr on 2014-03-23
I should also state that most users would probably recommend doing a clean install.
Of the many reasons one is because the upgrade method will upgrade everything.
So, users tend to install a lot of different programs, which in turn will add on to the length of time it takes to download and install the new system.
And the longer something takes to do, the chances of something horribly wrong happening increases.

I, myself, have been fortunate enough not to have these issues, but it is something to think about, anyway.

---

### Post by buzzingrobot on 2014-03-23
Installing any Linux in a dual-boot environment with Windows is probably going to be the most difficult and error-prone thing new Linux users ever do. It's understandable why people do it, but Windows assumes it is the only OS on the machine, and Windows 8 works hard to keep it that way.

Kubuntu is a fine system and KDE has obvious similarities with Windows.  But, straight Ubuntu, while different, is not difficult and figuring out how to use it likely takes much less time than figuring out how to fix a problematic Kubuntu install. ;)

In-place upgrades from one release to the next are usually workable. (Nothing is perfect, of course, and the more a user changes a system, the more the chances for a broken upgrade.  After 14.04 releases, you will inevitably see posts here about broken upgrades.)

The usual recommendation is to attempt to upgrade from one release to the next.  Moving from 12.04 to 14.04 would require several successive upgrades in sequence (12.04 -> 12.10 -> 13.04 -> 13.10 -> 14.04).  At the least, 13.04 is no longer supported and its repositories are offline.  If it was me, I'd just do a fresh install of 14.04. Or, wait another month for its release. [EDIT:  See deadflowr's correction on LTS-LTS upgrades below.]

15 gigs is a pretty minimal allotment.  The actual OS will fit. Data and files that you add must also fit within that 15-gig space.  Disk space not partitioned for use by an operating system can't be used by that operating system. It's possible to partition it later and add it to the file system the OS uses.  Much easier, though, to just make the initial allotment large enough.

---

### Post by deadflowr on 2014-03-23
@buzzingrobot, lts to lts is a straight upgrade.
No hop skip and jumping needed.

But on point with the explaination of the more a system changes from the defaults the better the chances the upgrade will have problems.

---

### Post by buzzingrobot on 2014-03-23
> **deadflowr said:**
> @buzzingrobot, lts to lts is a straight upgrade.
No hop skip and jumping needed.



Thanks for that.

---

### Post by Akhil_K_A on 2014-03-23
> **buzzingrobot said:**
> Installing any Linux in a dual-boot environment with Windows is probably going to be the most difficult and error-prone thing new Linux users ever do. It's understandable why people do it, but Windows assumes it is the only OS on the machine, and Windows 8 works hard to keep it that way.

Kubuntu is a fine system and KDE has obvious similarities with Windows.  But, straight Ubuntu, while different, is not difficult and figuring out how to use it likely takes much less time than figuring out how to fix a problematic Kubuntu install. ;)

In-place upgrades from one release to the next are usually workable. (Nothing is perfect, of course, and the more a user changes a system, the more the chances for a broken upgrade.  After 14.04 releases, you will inevitably see posts here about broken upgrades.)

The usual recommendation is to attempt to upgrade from one release to the next.  Moving from 12.04 to 14.04 would require several successive upgrades in sequence (12.04 -> 12.10 -> 13.04 -> 13.10 -> 14.04).  At the least, 13.04 is no longer supported and its repositories are offline.  If it was me, I'd just do a fresh install of 14.04. Or, wait another month for its release. [EDIT:  See deadflowr's correction on LTS-LTS upgrades below.]

15 gigs is a pretty minimal allotment.  The actual OS will fit. Data and files that you add must also fit within that 15-gig space.  Disk space not partitioned for use by an operating system can't be used by that operating system. It's possible to partition it later and add it to the file system the OS uses.  Much easier, though, to just make the initial allotment large enough.

Hi buzzingrobot.

Thanks for the more clarity. I think you are right, there is lot's of difference in the terminal commands also, So, I'm feeling more complicated in solving issues on kubunu. I'm totally fed up with installing and configuring kubuntu. Now I think, It's to replace kubuntu with ubuntu. :)

I will replace it tomorrow :D

I hope, this issue will not occur in ubuntu!

---

