---
title: "gnome equivalent to kdesvn / tortoisesvn"
date: 2006-10-17
forum: Programming Talk
---

### Post by rogier.de.groot on 2006-10-17
Is there any program for gnome/ubuntu which has the functionality of kdesvn in kubuntu or tortoisesvn in windows?

---

### Post by cwaldbieser on 2006-10-17
> **rogier.de.groot said:**
> Is there any program for gnome/ubuntu which has the functionality of kdesvn in kubuntu or tortoisesvn in windows?

rapidsvn?

---

### Post by rogier.de.groot on 2006-10-18
I mean it should integrate into nautilus, so you can just right-click a folder and select SVN checkout/update/commit/import which is what kdesvn and tortoisesvn do. Rapidsvn doesn't AFAIK.

---

### Post by dpm on 2006-10-18
I'd also be quite interested in finding out whether there is such a thing. I've been using TortoiseCVS on Windows and I'm planning to migrate to SVN + TortoiseSVN in the near future, but I haven't found any equivalent for nautilus in Linux.

---

### Post by cwaldbieser on 2006-10-19
> **rogier.de.groot said:**
> I mean it should integrate into nautilus, so you can just right-click a folder and select SVN checkout/update/commit/import which is what kdesvn and tortoisesvn do. Rapidsvn doesn't AFAIK.

Could it be done with the nautilus shell scripts + the command line SVN client?  

I use Kubuntu myself so I use kdesvn, though I mostly use the stand-alone client.

---

### Post by KungfooChris on 2007-01-16
I would like to know if there is any update on this or if anyone else has anything that may work.  Currently, I am using TortoiseSVN through VMware, since I have to use Windows XP for Photoshop CS2.  I just have mapped a SMB share as a drive through winxp in vmware and I just update that way.  It works, but I would like to use a linux svn client instead. I was using Kubuntu and KDEsvn, but I prefer ubuntu over kubuntu.  I figure I could use KDEsvn on gnome, I just haven't tried with fear of screwing things up.  I do how ever use Yakuake terminal application on gnome without any issues.  Just don't have the ability to have transparency like in KDE.  

Thanks for any ideas,

-- Chris S.

---

### Post by RoundSparrow on 2007-11-04
I too am interested in this.

---

### Post by dpm on 2007-11-04
Well, it seems that something like that exists: it is called [NaughtySVN]("http://naughtysvn.tigris.org/") and works as an extension of Nautilus in the same way TortoiseSVN does.

I haven't tried it, though, so I cannot really tell whether it is usable or stable, and I even do not know if it has been packaged for any distribution, so it would be interesting if someone who's used it could share his/her experience with it.

And if anybody is interested in contributing to it, [here]("http://osdir.com/ml/org.user-groups.linux.madurai.general/2006-01/msg00000.html") is some more info.

---

### Post by bobbocanfly on 2007-11-04
As said above, with a little hacking, this could easily be done with shell scripts. A deb postinst script to set things up, a config file in etc and a couple of scripts placed in your nautilus folder. Pretty easy i would guess.

---

### Post by davim on 2008-01-30
Check this out: [http://subdiversvn.sourceforge.net/](http://subdiversvn.sourceforge.net/) it used to be toytoiseSVN...

---

### Post by pmasiar on 2008-01-31
pysvn workbench?

---

### Post by WARnux on 2008-04-11
I'm using
**kdesvn** and **kdiff3** in ***Gnome*** right now...

You don't need kde to run at least those two kde apps.

Just right click on the working repository, open it with kdesvn, and it works.

---

### Post by sa-mejia on 2009-03-14
Here are two more Nautilus Scripts that try to work like Turtoise SVN.  Although I have not yet tried them myself, at first glance it seems that the first is better.

[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/)

[http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion](http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion)

Santiago.

---

### Post by Vadi on 2009-03-14
nautilussvn is prolly the best solution

---

### Post by xv1700 on 2009-12-18
Today is a great day, I have been disappointed by the Nautilus scripts, esvn, pysvn, kdesvn etc. but today I found RabbitVCS ([http://www.rabbitvcs.org/](http://www.rabbitvcs.org/)) and it is a fantastic rip off of Tortoise with nice markups in Nautilus and everything.

Only started using it today but so far, so good.

---

### Post by peterpall on 2010-06-03
On the pre-alpha Ubuntu Maverick I am currently using there is a package named rabbitvcs-nautilus that - according to [http://www.rabbitvcs.org/](http://www.rabbitvcs.org/) should so the trick with the overlay icons --- AND ACTUALLY IT DOES! STRIKE!

Wow... ...just installed this package. And - I have several hundred folders under version control - nautilus needed about three seconds for to calculate which folder has to be marked with a red or a green icon. But it works.

A Tortoise svn-like tool for linux. Finally.

---

### Post by Simian Man on 2010-06-03
[Thunar]("http://goodies.xfce.org/projects/thunar-plugins/thunar-vcs-plugin") has had this for years.  I use it every day.

---

