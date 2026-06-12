---
title: "After Hardy Heron upgrade, update manager freezes"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Nutopia on 2008-05-06
Hi!

This weekend I updated by old version of Ubuntu and then went ahead with the Hardy Heron(8.04) upgrade. Everything works great except Update Manager, which freezes after I press either the "Check" or "Install Updates" buttons. The box goes gray and sits - does nothing. Any ideas? Bug?

---

### Post by Hospadar on 2008-05-06
try updating in the command line ```
sudo apt-get upgrade
``` also you could try re-installing update manager ```
sudo apt-get install --reinstall update-manager update-manager-core
```

If neither of those work, try disabling any third-party repositories (wine, medibuntu) that you may have installed.  Go to System-Administration->Software Sources.

---

### Post by mills on 2008-05-06
have you tried reinstalling it?

i'd do it from synaptic but only becuase i'm not sure of the terminal command

---

### Post by Nutopia on 2008-05-06
I'm updating from terminal now - seems to be working. If I have another problem with update manager I will be sure to re-install it. 

Thanks for the help!

---

### Post by Nutopia on 2008-05-09
Hey folks,

I'm able to update from the command line, but still not from Update Manager. I reinstalled update manager using this command:

> 
sudo apt-get install --reinstall update-manager update-manager-core

Still no luck. Basically, when I open update manager I'm able to press the "Install Updates" button but then the window just turns gray and sits there.

Any other suggestions would be helpful.

---

### Post by shiellb on 2008-05-12
Thanks Hospadr.  I followed your advice and all is well.  :guitar:

---

### Post by JoshuaRL on 2008-05-12
> **Nutopia said:**
> Hey folks,

I'm able to update from the command line, but still not from Update Manager. I reinstalled update manager using this command:



Still no luck. Basically, when I open update manager I'm able to press the "Install Updates" button but then the window just turns gray and sits there.

Any other suggestions would be helpful.

Try removing update manager first, and purging it with:
```

sudo apt-get remove --purge update-manager update-manager-core

```

Then install it again:
```

sudo apt-get install update-manager update-manager-core

```

If that doesn't work, try launching it from the terminal and tell us what errors it throws:
```

update-manager

```

---

### Post by Mr. Svinlesha on 2008-05-13
I'm having similar problems, only worse: when I type a "sudo" command into the terminal, I get the following response:
> *sudo: unable to resolve host Ubuntu*

When I start update manager from the terminal, it tells me: 

> *current dist not found in meta-release file*

Suggestions?

---

### Post by JoshuaRL on 2008-05-13
> **Mr. Svinlesha said:**
> I'm having similar problems, only worse: when I type a "sudo" command into the terminal, I get the following response:


When I start update manager from the terminal, it tells me: 



Suggestions?

Man, what version are you running?  Have you had any serious problems lately?  Did you try to enable repos from other distros or anything?  Does running the following commands fix anything?
```

gksu apt-get install -f
gksu dkpg --configure -a

```
I know that's supposed to be sudo, but since it's having problems you may as well try getting creative.

---

### Post by Mr. Svinlesha on 2008-05-13
I've just downloaded the latest version of Hardy Heron.  And I've not had any problems with it so far, except for just this thing with the updates.

When I try your suggestion, I'm informed that it's an "invalid option."

What does it mean, "unable to resolve host Ubuntu"?

---

### Post by sunstriker on 2008-05-13
> **Mr. Svinlesha said:**
> I'm having similar problems, only worse: when I type a "sudo" command into the terminal, I get the following response:


When I start update manager from the terminal, it tells me: 



Suggestions?

Unable to resolve host means that you have conflicting hostnames in your /etc directory. You need to change it with sudo hostname and change it to the same name in /etc/hosts. Although I think you could change it more nicely with some gui tool. Not at my ubuntu box atm, sorry.
To change it you have to become root (type su, then the root password) If root user isn't enabled you can enable him in the Administration>Users tool

---

### Post by Mr. Svinlesha on 2008-05-13
When I installed the previous version, I added a lot of 3rd party repositories and whatnot.

Is that the problem?

---

### Post by JoshuaRL on 2008-05-13
> **sunstriker said:**
> Unable to resolve host means that you have conflicting hostnames in your /etc directory. You need to change it with sudo hostname and change it to the same name in /etc/hosts. Although I think you could change it more nicely with some gui tool. Not at my ubuntu box atm, sorry.
To change it you have to become root (type su, then the root password) If root user isn't enabled you can enable him in the Administration>Users tool

**Please be careful with the root user.**  It is [forum policy now](http://ubuntuforums.org/showthread.php?t=765414) to not tell anyone how to log in as root through graphical means.  I know that's not what you're saying here, but if you advise anyone to become root, it's always good to warn them about it.

> **Mr. Svinlesha said:**
> When I installed the previous version, I added a lot of 3rd party repositories and whatnot.

Is that the problem?

Have you done anything else with your install yet?  If not, it might be easier for you to reinstall.  If I understad your problem correctly, your system doesn't recognise either sudo or gksu.  That is a problem.

---

### Post by Mr. Svinlesha on 2008-05-14
I haven't made any specific modifications yet, if that's what you mean.

But will reinstalling will fix the problem?  Or do you mean starting from gparted and doing the whole thing from scratch?

---

### Post by JoshuaRL on 2008-05-14
Yeah, at the very least reinstalling from the Live CD should fix it.  It's a drastic thing to suggest, but with sudo messed I think it may be easier.

But I may be wrong, so do a little more research.

---

### Post by Thingymebob on 2008-05-14
You should all read this thread
[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")
its a simple fix.

this will cause gksudo to fail to start, hence the update manager window freezes after you click install when you would normally be prompted for a password

---

### Post by Mr. Svinlesha on 2008-05-15
Thanks, **thingy**.

But if we start at the beginning: I run "cat /etc/hosts" and get the following:

> 127.0.0.1 localhost
127.0.1.1 svinlesha-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


So, unlike **Darkade**, I don't have an extra domain name attached to my host name.  So I can't use "gksudo gedit /etc/hosts" to change it (since it already appears to be correct).

Suggestions (other than reinstallation)?

---

### Post by Mr. Svinlesha on 2008-05-15
Bump

---

### Post by Thingymebob on 2008-05-15
Mr. Svin,
From your original post you say you get the error
> sudo: unable to resolve host Ubuntu
so you need to change your /etc/hosts to read:
```

127.0.0.1 localhost
127.0.1.1 Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
That should solve that error, not sure about the  *current dist not found in meta-release file*, I'm guessing you may have a bad repository set in
/etc/apt/sources.list,
each should read something along the lines of
*deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **hardy** main restricted universe multiverse*

Like I say this is a guess but I would check all of your entries have **hardy** set correctly, either that or one of the 3rd party repos you added doesn't yet support hardy.

---

### Post by Mr. Svinlesha on 2008-05-15
**Thingymebob:**

A thousand and one thank yous!  It seems to be working so far, and I'm downloading a whole mess a updates as I write this.

I might need some help with the repository list.

---

### Post by Mr. Svinlesha on 2008-05-15
Here's my list. Can you point me to what I need to change in it?

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) 
## Medibuntu - Ubuntu 7.04 "feisty fawn" 
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs) 
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
# deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

# deb [http://98111.free.fr/apt/](http://98111.free.fr/apt/) gutsy free

---

### Post by mkaram_99 on 2008-05-15
> **Hospadar said:**
> try updating in the command line ```
sudo apt-get upgrade
``` also you could try re-installing update manager ```
sudo apt-get install --reinstall update-manager update-manager-core
```

If neither of those work, try disabling any third-party repositories (wine, medibuntu) that you may have installed.  Go to System-Administration->Software Sources.

Thank you, the reinstall worked for me, I can use update manager again!

---

### Post by Thingymebob on 2008-05-15
Right, the dist upgrade comments out all 3rd party repositories so you will need to uncomment them (remove the # at the start of the line) if you want to re-enable them and change the distribution to hardy
I've made some changes below (in bold) add added some comments, **Note:** I haven't uncommented anything so if you want them re-enabled you'll have to remove the # at the start of each relevant line
```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://no.archive.ubuntu.com/ubuntu/ **hardy** universe
# deb-src http://no.archive.ubuntu.com/ubuntu/ **hardy** universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ **hardy**-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ **hardy**-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu **hardy**-security universe
# deb-src http://security.ubuntu.com/ubuntu **hardy**-security universe

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
[B]## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free
[/B]

[B]#Don't know what anything below here is, try changing feisty/gutsy to hardy and 
#see what happens or re-visit the site you got these from for more info[/B]
# deb http://www.telemail.fi/mlind/ubuntu feisty fonts
# deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

# deb http://98111.free.fr/apt/ gutsy free
```

---

### Post by Mr. Svinlesha on 2008-05-15
Thanks once again **Thingy.**

Could I just remove...> # deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
# deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

# deb [http://98111.free.fr/apt/](http://98111.free.fr/apt/) gutsy free...from the list entirely?

I don't know what they are anymore myself, and I probably added them when I first starting fooling around with Ubuntu during the Feisty Fawn distro.

Actually, as I look over the list, I'm wondering if I really need any of those repositories.  Should I keep them?  If not, how do I get rid of them?

---

### Post by Thingymebob on 2008-05-15
Yeah just remove them if you want,
Best to keep the multiverse, universe, security etc even medibuntu (thats where google earth, video audio codecs, acrobat etc are) even if you don't use them just leave them commented for now.

You can do this graphically from Administration->Software sources in future if needed.

---

### Post by Mr. Svinlesha on 2008-05-15
Great.

Thanks once again for the help.

---

### Post by rockerphil on 2008-05-15
i'm sure this has been said before, but i'll say it again. i really don't see the purpose for the GUI update manager, sudo apt-get dist-upgrade does the exact same thing, and to be totally honest it was the only way i could upgrade to Hardy since i run Fluxbuntu and the update manager GUI said i had to have one of the "supported" Ubuntu derivatives to upgrade, so i see no purpose for the GUI.

---

### Post by Mr. Svinlesha on 2008-05-16
Hmmm... still getting the same error message.

I followed your instructions and modified the /etc/apt/sources.list file with gedit.

I then went to System > Administration > Sofware Sources and removed a couple of "medibuntu" entries that referred to Feisty Fawn.  I suspect now that I probably shouldn't have done that.

Anyway, whatever I did, I can't launch System > Preferences > Art Manager anymore, and I'm still getting the *current dist not found in meta-release file* error message when I launch the update manager from the terminal.

Any other suggestions? Here's my current sources.list:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe #Added by software-properties

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe #Added by software-properties

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) 
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs) 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free


---

### Post by Mr. Svinlesha on 2008-05-16
Bump.

---

### Post by johninmihno on 2008-05-16
Fantastic! Purging and then installing solved this same problem for me. Thanks.

---

### Post by Thingymebob on 2008-05-16
Removing repos shouldnt break any software, this propably happened during an upgrade.

For art manager go to system->Administration->synaptic package manager
search for gnome-art and reinstall

Error must be the medibuntu entry. remove it completely (the last 5 lines) and then add it again like this:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by Mr. Svinlesha on 2008-05-16
God, I hate to keep bugging you like this, but...

I removed the medibuntu references and reinstalled as per your instructions above.  Now, when I launch update manager from the terminal, I get two of those messages instead of one.

I marked gnome-art for reinstallation in the synaptic package manager, but it made no difference.  When I try to start it, the start screen pops up for about a quarter of a second and then disappears.

Should I try removing and reinstalling it instead?

---

### Post by Thingymebob on 2008-05-16
lets try something different then

back up your /var/lib/update-manager/meta-release 
and replace with
```

Dist: warty
Name: Warty Warthog
Version: 04.10
Date: Wed, 20 Oct 2004 07:28:17 UTC
Supported: 0
Description: This is the warty warthog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/warty/Release

Dist: hoary
Name: Hoary  Hedgehog
Version: 05.04
Date: Fri, 08 Apr 2005 08:18:19 UTC
Supported: 0
Description: This is the Hoary Hedgehog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hoary/Release

Dist: breezy
Name: Breezy Badger
Version: 05.10
Date: Thu, 13 Oct 2005 19:34:42 UTC
Supported: 0
Description: This is the Breezy Badger release
Release-File: http://archive.ubuntu.com/ubuntu/dists/breezy/Release

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: edgy 
Name: Edgy Eft
Version: 6.10
Date: Thu, 26 Oct 2006 12:00:00 UTC
Supported: 1
Description: This is the Edgy Eft release
Release-File: http://archive.ubuntu.com/ubuntu/dists/edgy/Release
ReleaseNotes: http://changelogs.ubuntu.com/EdgyReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz.gpg

Dist: feisty
Name: Feisty Fawn
Version: 7.04
Date: Thu, 19 Apr 2007 13:00:00 +0200
Supported: 1
Description: This is the 7.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/feisty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 1
Description: This is the 7.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/gutsy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg

Dist: hardy 
Name: Hardy Heron
Version: 8.04 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hardy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz.gpg
```

as for gnome-art try running it from a terminal and see what errors you get when it exits

---

### Post by Mr. Svinlesha on 2008-05-16
Starting with the last one first: gnome-art from the terminal.
> /usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 10 levels...
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

Alas, it is nothing but gobbledygook to my eyes.

I'll have to RTFM the second one.  

Back shortly.

---

### Post by Mr. Svinlesha on 2008-05-16
With regard to the first problem: /var/lib/update manager is empty.  It doesn't contain a meta-release file.

---

### Post by Thingymebob on 2008-05-16
its /var/lib/update**-**manager (with a dash)
if it is truly empty then thats probably the cause (in this case ignore the first command in the code section below)
```

sudo cp /var/lib/update-manager/meta-release /var/lib/update-manager/meta-release.old
sudo gedit /var/lib/update-manager/meta-release

```
then copy,paste & save

---

### Post by Mr. Svinlesha on 2008-05-16
Yes, I meant update-manager.

Well, followed your instructions.  meta-release is now in place.

I still get the same message when I start update-manager, though.

Frustrating, isn't it?

I guess I should add that at least its back to one message line again, as opposed to two.  So we seem to be getting closer.

---

### Post by Thingymebob on 2008-05-16
so I think  we now need to change  ~/.update-manager-core/meta-release to read
```

cp ~/.update-manager-core/meta-release ~/.update-manager-core/meta-release.old
gedit ~/.update-manager-core/meta-release
```
```

Dist: warty
Name: Warty Warthog
Version: 04.10
Date: Wed, 20 Oct 2004 07:28:17 UTC
Supported: 0
Description: This is the warty warthog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/warty/Release

Dist: hoary
Name: Hoary  Hedgehog
Version: 05.04
Date: Fri, 08 Apr 2005 08:18:19 UTC
Supported: 0
Description: This is the Hoary Hedgehog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hoary/Release

Dist: breezy
Name: Breezy Badger
Version: 05.10
Date: Thu, 13 Oct 2005 19:34:42 UTC
Supported: 0
Description: This is the Breezy Badger release
Release-File: http://archive.ubuntu.com/ubuntu/dists/breezy/Release

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: edgy 
Name: Edgy Eft
Version: 6.10
Date: Thu, 26 Oct 2006 12:00:00 UTC
Supported: 1
Description: This is the Edgy Eft release
Release-File: http://archive.ubuntu.com/ubuntu/dists/edgy/Release
ReleaseNotes: http://changelogs.ubuntu.com/EdgyReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz.gpg

Dist: feisty
Name: Feisty Fawn
Version: 7.04
Date: Thu, 19 Apr 2007 13:00:00 +0200
Supported: 1
Description: This is the 7.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/feisty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 1
Description: This is the 7.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/gutsy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg

Dist: hardy 
Name: Hardy Heron
Version: 8.04 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hardy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz.gpg
```
again, backup the old first

You appear to be being affected by this bug [https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552]("https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552") in gnome art, you may want to subscribe to the bug so you can get updates on its status. You may want to try gnome-art NG (gnome-art next generation) [http://developer.berlios.de/projects/gnomeartng/]("http://developer.berlios.de/projects/gnomeartng/"), unfortunately its not in any repositories but the developer does offer a .deb package

---

### Post by Mr. Svinlesha on 2008-05-16
I did a quick scan and the two files looked pretty much identical.  I went ahead with the copy paste, save, and then tried to open um from the terminal.

Same result.

I just want to say that I really, really appreciate you taking out the time to help me with this.  I'm sure you have better things to do on a Friday afternoon/evening.

---

### Post by Mr. Svinlesha on 2008-05-17
Bump.

---

### Post by Mr. Svinlesha on 2008-05-18
Bump.

---

