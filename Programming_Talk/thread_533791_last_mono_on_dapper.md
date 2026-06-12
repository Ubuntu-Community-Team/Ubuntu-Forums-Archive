---
title: "last mono on dapper"
date: 2007-08-24
forum: Programming Talk
---

### Post by chelala on 2007-08-24
Hi I have dapper is there a way to have last updated mono and monodevelop on dapper.

The one on the repository is a little outdated, I've read the debian repo is in here [http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/) Can I use that repository to install mono on ubuntu ?

I understand the LTS policy but is there any chanse besides (UPGRADE to Fiesty) I have low bandwidth and i want to keep 6.06.1 LTS until next one gutsy +1

thanks in advance

Harold J. A. Chelala

---

### Post by apetresc on 2007-08-24
The only way to get an upgraded Mono without upgrading Ubuntu is to either build it yourself (:() or get a backport (:)). I don't do .NET so I'm not sure if there is a mono backport for Dapper, but there probably is since Dapper is LTS and Mono is a very important package. You should go to the [Backports and Repositories forum](http://ubuntuforums.org/forumdisplay.php?f=41) and ask around there if this package has been backported to Dapper.

If all else fails, you can build it yourself using the code from here: [http://go-mono.com/sources-stable/](http://go-mono.com/sources-stable/)

Good luck :) I hope you find what you're looking for.

---

### Post by keifer on 2007-08-24
If you want the latest monodevelop, don't look to the backports, the package in gutsy is a version behind. I'd check to see if the latest mono packages are there (they probably are, .net support is probably good for enterprise clients), and then build monodevelop from source.

---

### Post by pmasiar on 2007-08-24
You cannot expect stable server to have latest libraries - it is oxymoron. Either you have stability (and you don't bother with upgrade treadmill), or you have cutting edge versions of program, with emphasis on "cutting" - you can get hurt :-) There is no way around it. 

Or you manage and take responsibility for dependencies yourself - and then you better know what you are doing.

---

### Post by Dragonbite on 2007-08-28
Have you heard of or tried [[COLOR="Blue"]Badgerports[/COLOR]]("http://directhex.mfgames.com/")?

> The primary purpose of badgerports is to provide recent versions of the Mono framework, and associated packages such as F-Spot, Banshee, and Monodevelop. There are also other suites, including MythTV, GStreamer, and NTFS-3G (writeable driver for Microsoft NTFS). Suggestions for other packages to include are welcome, but don't be offended if I decline for whatever reason.

It's a repository you can add to Synaptic that updates more frequently than Ubuntu's (theoretically). 

The first time you check for updates, it will probably come with a huge list of updates right off the bat.

---

### Post by chelala on 2007-08-29
WAO, That&#347; so good to know, It worked just perfect. I whish there is a central place with info about all those great repos. the gandalf for compiz for dapper, the badgerports... thanks a lot it is updating fine, that I will install though.

---

