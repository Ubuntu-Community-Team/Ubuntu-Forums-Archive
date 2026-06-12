---
title: "[SOLVED] HOWTO: Install Linux DC++ (the easy way)"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-15
Written by **[mird]("http://ubuntuforums.org/member.php?u=18027")**
Edited by **arnieboy**
**What is DC++?**
> DC++ announces the freedom to share! DC++ is an open source client for the Direct Connect protocol. Direct Connect allows you to share files over the internet without restrictions or limits. The client is completely free of advertisements and has a nice, easy to use interface. Firewall and router support is integrated and it&#8217;s easy and convenient to use functionality like multi-hub connections, auto connections and resuming of downloads. 

*09/Aug/2005* - More CVS commits, as per usual see the [project changelog]("http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain") for details. New package details in the instructions below.

*24/Jul/2005* - Another recent commit (see the [project changelog]("http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain") for details) and a new package which should also (hopefully) fix the dependency issues for anyone not using Backports. I've updated the instructions below to reflect the new package.

*01/Jul/2005* - There were a few commits to the dcpp repository in the last week (see the project changelog for details) so I've built and packaged it up for all. Also added menu file for those that wanted it (plz test k thx!). To install (or upgrade to) the latest package follow the steps below.

---

I've built and packaged the latest version (plus some patches - currently only the user-commands patch by s4kk3 as mentioned [here]("http://www.ubuntuforums.org/showthread.php?p=141959#141959")) of Linux DC++ for anyone who is interested. Development on this particular project is a bit unorganised and rather intermittent but I'll do my best to maintain the latest version. Note that this is considered unstable software. **There are bugs'o'plenty and although it works quite satisfactorily for me, it may not for you. Please submit useful bug reports to the [project's bugtracker]("http://developer.berlios.de/bugs/?group_id=2230").**

There may be some additional dependencies which I didn't note as this is the first time I've tried to decipher dependencies from a built binary. Never-the-less do let me know if you have any problems.

INSTALL / UPGRADE

1. Install dependencies.
```
sudo apt-get install libatk1.0-0 libbz2-1.0 libc6 libgcc1 libglade2-0 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libstdc++6 libxml2 zlib1g
```
2. Fetch the package.
```
wget http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb
```
3. Install the package.```

sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
```
And that's it! There should now be a *Linux DC++* icon under Applications -> Internet.

---

### Post by deception on 2005-10-15
You can also add it under "Add Applications" under the Applications menu :KS 

Thanks for posting ;)

---

### Post by era on 2005-10-17
For the benefit of those of us who don't (or didn't) know why we would or would not want to do this, perhaps you could explain what DC++ is?

(Apparently a file-sharing client which sort of looks like IRC -- [http://dcplusplus.sourceforge.net/](http://dcplusplus.sourceforge.net/) )

---

### Post by WetWilly on 2005-10-18
If you dont want the bugs of this old version then please build it from CVS.

[http://www.ubuntuforums.org/showthread.php?t=89603](http://www.ubuntuforums.org/showthread.php?t=89603)

---

### Post by pelago on 2005-10-19
[QUOTE=deception]You can also add it under "Add Applications" under the Applications menu :KS 

Thanks for posting ;)[/QUOTE]
The thing in Add Applications is the normal (i.e. not as good) Direct Connect client, not DC++.

---

### Post by NeoChaosX on 2005-10-22
Hey arnieboy, does the bugs you're talking about include the program not placing finished downloads in the download directory and just leaving them in the Incomplete folder?

---

### Post by arnieboy on 2005-10-22
[QUOTE=NeoChaosX]Hey arnieboy, does the bugs you're talking about include the program not placing finished downloads in the download directory and just leaving them in the Incomplete folder?[/QUOTE]
I wasnt talking abt the bugs, **mird** was. u might wanna mail him if u have any q's.

---

### Post by JeffBlouin on 2005-10-31
Hi,

         Very newbie question but how do I uninstall DC++ or any other .deb package

Thanks...

---

### Post by arnieboy on 2005-10-31
[QUOTE=JeffBlouin]Hi,

         Very newbie question but how do I uninstall DC++ or any other .deb package

Thanks...[/QUOTE]
open synaptic search for the package by name, find it and remove it.

---

### Post by Youghurt on 2005-11-02
Great! And now I just have to increase my FAT partition.

---

### Post by arnieboy on 2005-11-02
[QUOTE=Youghurt]Great! And now I just have to increase my FAT partition.[/QUOTE]
use partition magic in dos mode. create a dos boot diskette, boot into dos, cd to the cdrom folder which contains ur partiton magic (version 8+) and do it from there. its the easiest and the least error prone... beats the windows version hands down. I am not sure but I think even the evaluation version of partition magic has the free and complete dos version included. its generally in a folder called "dos" inside the partition magic folder in program files on windows when u install it.

---

### Post by toots on 2005-11-13
Great application!

---

### Post by arnieboy on 2005-11-13
[QUOTE=toots]Great application![/QUOTE]
lol.. why did u take the link to ur repo down within 2 minutes of posting them? :)

---

### Post by arnieboy on 2005-11-13
[QUOTE=toots]Hi all!

I've made a .deb for this bieautifull app, add the following to your /etc/apt/sources.list:

```
deb http://www.cti.ecp.fr/~beauxir5/ubuntu binary/
deb-src http://www.cti.ecp.fr/~beauxir5/ubuntu source/
```

Then apt-get update and apt-get install linuxdcpp :)


Please email feedbacks to toots at rastageeks dot org, I'm reading those forums regulary..

Romain[/QUOTE]
if this is not another fly-by-night repository, then I will be glad to add it.

---

### Post by lucas on 2006-03-05
Just wondering if anyone has made newer builds for this? :)

---

### Post by ProNoblem on 2006-03-07
[QUOTE=lucas]Just wondering if anyone has made newer builds for this? :)[/QUOTE]
Dito :), 0.674 keeps hanging on my badger, so just wondering if anyone has some new stuff, otherwise I'll just try the cvs version I guess :)

---

### Post by darknightuk on 2006-03-07
> **ProNoblem]Dito :), 0.674 keeps hanging on my badger[/QUOTE]ouch thats sound painful said:**
> Dito :), 0.674 keeps hanging on my badger, so just wondering if anyone has some new stuff, otherwise I'll just try the cvs version I guess :)remember ldcpp is still well into early development don't expect too much from it quite yet it will freeze and crash but it's getting there the cvs seems stable enough at the moment but it has crapped out on me a few times

---

### Post by s_spiff on 2006-03-07
finally a nice sweet how to for something i broke my head over... I did finally install it... but only after looking around like a nut case.. i wish i saw this thread earlier!!! thnx Arnieboy...seems like you're totally into making HOWTO's! too cool!

---

### Post by WetWilly on 2006-03-08
s_spiff, the negative thing about this guide is that the dc++ version is _very_ old and has stupid bugs, it would be better for the stability of the client to build it from cvs, look the howto in my sig.

---

### Post by zacman on 2006-03-14
I tweaked the linuxdcpp package from debian unstable so that the dependencies work with Ubuntu. It's a pretty recent CVS snapshot (02/17/2006) and works great. [Get it here.]("http://bassfreq.home.comcast.net/linuxdcpp_cvs20060217.deb")

---

### Post by rantak on 2006-03-17
Thanks zacman for the new deb, this one seems much more stable than the previous versions. 

I have a small problem though. DC++ won't save my hashes unless run as sudo. Can anyone help with that?

---

### Post by e2k on 2006-03-17
[QUOTE=zacman]I tweaked the linuxdcpp package from debian unstable so that the dependencies work with Ubuntu. It's a pretty recent CVS snapshot (02/17/2006) and works great. [Get it here.]("http://bassfreq.home.comcast.net/linuxdcpp_cvs20060217.deb")[/QUOTE]
Thanks for this one, I'll check it out \\:D/

---

### Post by korami on 2006-03-18
First of all, thanks for the deb zacman.

[QUOTE=rantak]I have a small problem though. DC++ won't save my hashes unless run as sudo. Can anyone help with that?[/QUOTE]

Just a hint Rantak...
Are all of your shared files rehashed, or only part of them? I ask because at the beginning I thought too that my hashes aren't saved, then at a closer look I noticed that only the files with special characters (e.g. "ouvert**ü**r") are being rehashed. This might be related to a known issue I read somewhere about regarding special characters not being handled correctly by linuxdcpp.

---

### Post by rantak on 2006-03-19
[QUOTE=korami]
Just a hint Rantak...
Are all of your shared files rehashed, or only part of them? I ask because at the beginning I thought too that my hashes aren't saved, then at a closer look I noticed that only the files with special characters (e.g. "ouvert**ü**r") are being rehashed. This might be related to a known issue I read somewhere about regarding special characters not being handled correctly by linuxdcpp.[/QUOTE]

No, it's all of the files. If don't run dcpp as sudo, after hashing if go to see my shares theres 0 bytes there. The hashing seems to work correctly, I think I have a problem with some directory ownership or something. It's not a big problem though, because everything works ok when run with sudo.

---

### Post by stevensheehy on 2006-03-26
ldcpp doesn't handle permissions very well because the DC++ core doesn't. You should check your profile folder to make sure you have permissions to write in it. Should be at ~/.dc++

The rehashing of non-ascii chars has been fixed on more recent dc++ cores and we are in the process of porting the latest dc++ core to linuxdcpp.

---

### Post by fizz on 2006-03-30
sweet... i have some issues with current build, where your some how like half connected to a server. (ie: in search screen it still shows connecting for the server) even though chat is going on and you see room list.

---

### Post by stevensheehy on 2006-03-30
Then you are connected just fine. The problem in search screen is a unicode problem. If the hub name contains non-ascii chars, ldcpp has trouble converting them so it displays the default "connecting" label. If you'll notice, the name on the hub tab is set to it's IP because of the same reason.

---

### Post by talkingwires on 2006-03-31
I've got DC++ up and running, but it refuses to hash my MP3s. Oh, it'll hash my folder.jpg files and M3U playlists, but it won't touch MP3s. Glancing through the XML configs doesn't reveal an extension blacklist. How do I fix this?

---

### Post by stevensheehy on 2006-03-31
[QUOTE=talkingwires]I've got DC++ up and running, but it refuses to hash my MP3s. Oh, it'll hash my folder.jpg files and M3U playlists, but it won't touch MP3s. Glancing through the XML configs doesn't reveal an extension blacklist. How do I fix this?[/QUOTE]
Make sure the mp3 filenames are ascii only (and the folder containing them). If they are, then I don't know. Not really ldcpp's problem since the hashing is done completely by the DC++ core. As I said above, they have fixed some bugs on the hashing in more recent DC++ versions. Naga is in the process of porting it so you can test his branch to see if the newer dc++ core fixes things if you'd like: 
[http://ldcpp.dx.homelinux.org/ldcpp]("http://ldcpp.dx.homelinux.org/ldcpp")

Back up your profile first, as you will lose the sources for your queued items.

---

### Post by talkingwires on 2006-04-01
[QUOTE=stevensheehy]Make sure the mp3 filenames are ascii only (and the folder containing them). If they are, then I don't know. Not really ldcpp's problem since the hashing is done completely by the DC++ core. As I said above, they have fixed some bugs on the hashing in more recent DC++ versions. Naga is in the process of porting it so you can test his branch to see if the newer dc++ core fixes things if you'd like: 
[http://ldcpp.dx.homelinux.org/ldcpp]("http://ldcpp.dx.homelinux.org/ldcpp")

Back up your profile first, as you will lose the sources for your queued items.[/QUOTE]Hey, I'm an idiot. And the program's UI is a little wonky. First closing my shared list, then refreshing it, and finally reopening it gets all the files to appear. Why only JPGs and M3Us would appear automatically, but MP3s wouldn't is beyond me.

---

### Post by Gaimlz on 2006-04-15
Thanks for the great howto. But what's up with this project. Are there any sites, or some new updates? bugfix and so on.

---

### Post by darknightuk on 2006-04-15
[QUOTE=Gaimlz]Thanks for the great howto. But what's up with this project. Are there any sites, or some new updates? bugfix and so on.[/QUOTE] project is still well active if you want the latest dev/test version d/l the cvs ldc++ has some a  long way imo and linux is one of the reasons it's my main O's now

---

### Post by stevensheehy on 2006-04-16
Yeah, I would not recommend installing a package unless it's continually updated, since there have been quite a bit of changes in cvs. You can see a changelog on the main [LinuxDC++]("http://linuxdcpp.berlios.de/articles.php?um=index") site. Me and another guy made a tray icon patch that should make its way into CVS soon. I've got more fixes on the way.

---

### Post by Owdy on 2006-08-05
Thanks for this, but package is guite old. Any updates?

---

### Post by stevensheehy on 2006-08-06
> **Owdy said:**
> Thanks for this, but package is guite old. Any updates?

[http://www.ubuntuforums.org/showthread.php?t=193984](http://www.ubuntuforums.org/showthread.php?t=193984)

---

### Post by Owdy on 2006-08-06
> **stevensheehy said:**
> [http://www.ubuntuforums.org/showthread.php?t=193984](http://www.ubuntuforums.org/showthread.php?t=193984)
Sweet. Thanks.

---

### Post by SteffJay on 2006-10-14
It would be nice if a HOWTO could be made for the DC Server as well.....  I want to try that but i cannot find one anywhere.....  ;)

---

### Post by dustman on 2007-01-22
I installed as you said, but when somebody wants to get files from me, or if I  want to get something from anyone, Linux DC ++ practically shutsdown my internet connection, I cannot enter any websites, GAIM messenger is out of the question and not even getting packages from my terminal seems not working....Why? :((

---

### Post by piyushjain on 2007-02-10
while installing dc++ i encountered the following error...
"Resolving newstuff.orcon.net.nz... failed: Temporary failure in name resolution."
i hv tried a no. of methods to install dc++ but cud not really succeed...
cn any plz help me in installing dc++ on my pc

---

