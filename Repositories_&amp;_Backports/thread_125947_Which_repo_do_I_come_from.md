---
title: "Which repo do I come from ?"
date: 2006-02-05
forum: Repositories &amp; Backports
---

### Post by 1sy8 on 2006-02-05
Hi all.

The story : 
I wanted to play with R (a GPL software at r-project.org) so I installed r-base. 
No problems whatsoever. 

Still, on their site, they say 

> After a release of Debian "stable", no new packages get added by Debian to
keep the release as 'stable' as possible. This implies that the R release
contained in the official Debian release will become outdated as time passes.
As courtesy to the R users on the Debian "stable" platforms, the "stable"
directory on CRAN contains so-called 'backports' of the current R binaries 
for the "stable" distribution of Debian.

The backport from r-project is only for i386.

My questions :
0- Is the Ubuntu team just using the Debian stable package or do they package the current R release for Ubuntu ? Related question, is there a list or any other way to know the origin (just the Debian package, repackaged from Debian, directly packaged from upstream, etc ..) of each package present in the Ubuntu repos ?

1- How to ask Ubuntu to include a software as part of the distribution ?

2- How do I know which repo a given package is coming from ?

3- Is there a way of choosing the repo I want to get the package from if two or more repos on my sources.list hold the same ?

---

### Post by ubuntumaneh on 2006-02-05
1) in the forums go to: Ubuntu Backports, then Requests.

2) I think there is a better answer for that. Anyway, I use apt-cache showpkg <name of package>.

3) I think apt handles this automatically. Anyway, try a look at man apt-get to see if there is an option like that. I will look it myself, for I never thought of that before. Thank you, then.

---

### Post by 1sy8 on 2006-02-05
For 1-, for R above, it doesn't necessarily need frequent backports as 6 months between Ubuntu releases is ok but it would be great if included 'officially' with the distribution. Now, I don't know if it's not already in the main Ubuntu repo (hence my question number 0 too).

For 2-, ok, your command gives the package name as kept on local disk but I'm afraid the info on where it came from is not there ?!?

For 3- I wonder if APT doesn't just keep track of new versions of package ?

---

### Post by ubuntumaneh on 2006-02-05
1)  cramunhento:~> apt-cache showpkg r-base-core
Package: r-base-core
Versions: 
2.1.1-1(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)

According to my dumb recipe (I really think there is a clever way to do that), I can see that this r-base-core is in universe. I think you should try the dapper forums and convice those people to include it.

2) I think local disk is the same as main, isn't it? 

3) If there is a new version in the repos, apt-get update and apt-get upgrade will do the job. I think that apt keeps track of the version, and evaluate it during the update-upgrade business.

---

### Post by ubuntumaneh on 2006-02-05
OFF TOPIC:

By the way:
Ubuntu+fluxbox on IBM TP365XD
Ram : 8M+64M
--> A few remaining problems ! 

This is really very nice. I like a lot low ram. I wonder with kind of problem you are facing. I use an old computer with 156M, Ubuntu and Windowmaker. Im very proud of it. But you with your computer really rock. Good.

---

### Post by 1sy8 on 2006-02-05
[QUOTE=ubuntumaneh]1)  cramunhento:~> apt-cache showpkg r-base-core
Package: r-base-core
Versions: 
2.1.1-1(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)

According to my dumb recipe (I really think there is a clever way to do that), I can see that this r-base-core is in universe. 
[/QUOTE]

Ok, it's a good recipe for the repos in the distribution. I wonder if packages coming from anywhere else got their location names so nicely appended to the local package ?? 

> 
I think you should try the dapper forums and convice those people to include it.


But I don't know if it's not already on their list ??

> 
3) If there is a new version in the repos, apt-get update and apt-get upgrade will do the job. I think that apt keeps track of the version, and evaluate it during the update-upgrade business.

I think it works fine inside a coherent distribution but then I'm not sure of how it behaves if one begins mixing outside repos like upstream repos. I'm worried of potential clashes.

Off topic:
I had problems with switching back and forth from X to a plain virtual console .. the screen gets scrambled each time and I can't never get it back again.
In fact, it's not running Ubuntu+fluxbox anymore but console only.

---

### Post by ubuntumaneh on 2006-02-05
1) This apt-cache showpkg is telling in brackets after the version number from where it is coming from. This directory /var/lib/apt/lists/ is update with apt-get update. So, if you insert another repo to your sources.list, it will be shown by this method). Im telling it should have a clever way, for I believe there is a script already that shows this information. But I think I will do this myself, for it is a simple matter of reading the output of showpkg.

2) Ask in that subforum of dapper if it is already there. Another way is that you could have a sources.list of dapper, do a apt-get update, then see the information on the package.

3) I have the same feeling. For instance, I don't like to upgrade the package that I get from backports. I keep track of them manually (actually some of the package searches itself for patches and updates, others I have to go to the web, others I created a script). Now, if you mix debian repos with ubuntu repos, you certainly will have problems doing update-upgrade. But maybe it is just my superstition.

off-topic: 
Did you cut some consoles? You usually have six of them, and each one consumes memory. Go hardcore and try old FVWM. Fluxbox may be expensive for you. Also, try to get rid of some modules that are being loaded and you don't need. Actually, I believe you have already done all of this. Anyway, if you solve this problem, I would like to know you solution.

---

