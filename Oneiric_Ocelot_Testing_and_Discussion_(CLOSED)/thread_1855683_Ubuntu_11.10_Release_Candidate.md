---
title: "Ubuntu 11.10 Release Candidate"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by robgraves on 2011-10-06
I don't know if someone's already asked this, sorry if they have, but I've googled and searched around and i can't seem to find if ubuntu 11.10 oneiric ocelot release candidate is available for download.  According to the wiki it has release candidate scheduled for today.  If anybody knows if its been released or a download link, I'd appreciate it, thank you.

---

### Post by terry_gardener on 2011-10-06
there isn't one. 

they are not releasing a RC version just beta 1 and beta 2 versions. 

if you have been doing the updates, you are up to date anyway. 

also check the sticky 

[http://ubuntuforums.org/showthread.php?t=1747647]("http://ubuntuforums.org/showthread.php?t=1747647")

---

### Post by robgraves on 2011-10-06
ok, I wasn't aware of that...good to know. thank you.

---

### Post by ztrange on 2011-10-06
Ok, so in [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule) they don't mention any RC in the right side. However, just for sake of completeness, could you explain what the Release Candidate phase is and why it won't be released as "standalone"?

Thanks

---

### Post by Alwimo on 2011-10-06
> **ztrange said:**
> Ok, so in [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule) they don't mention any RC in the right side. However, just for sake of completeness, could you explain what the Release Candidate phase is and why it won't be released as "standalone"?

Thanks
Software is in the release candidate phase if it's pretty much good enough to be released but there should be some testing of it in this almost final stage to iron out as many of the problems that arise as possible before it's finally released.

The reasons behind the RC not being released as an .iso could be that you get to it just by updating beta 2 (or any other pre-release version), and it could save bandwidth, and probably more reasons.

But you could get the daily .iso here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by ranch hand on 2011-10-06
Just to add to that, none of the steps A1, A2, B1, B2 or RC (if it were to exist) is really nothing to "stand alone".   They are just snapshots of development on that day, just like the daily.

The only real difference is that the "steps" get ISO testing.  This is important to the functionality of the release image as it points out problems with the image.  Seeing how you have to have a freeze of about 3 days for that ISO testing it does slow down the dailies.

That is about it.

Just keep updating.  If you want to get the final without the rush get the daily a couple of days before the release or now.

---

### Post by Cushie on 2011-10-07
Try here for the latest version:-

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by jruden on 2011-10-07
My belief (correct me if wrong) is that some tasks are only performed as part of the dist upgrade process (sorting out configuration problems/inconsistencies between various versions) and not by the apt-get updates performed later on.

So given that my assumption above is correct there is definitively a value in having a later/better ISO at hand when doing the distribution upgrade as this is more likely to have a better dist upgrade procedure covering even more "fixes" and knowledge how to preferably migrate to newer configuration/meta-data formats.

---

### Post by philinux on 2011-10-07
The RC this cycle is a soft release I believe.

---

### Post by sgage on 2011-10-07
> **jruden said:**
> My belief (correct me if wrong) is that some tasks are only performed as part of the dist upgrade process (sorting out configuration problems/inconsistencies between various versions) and not by the apt-get updates performed later on.

So given that my assumption above is correct there is definitively a value in having a later/better ISO at hand when doing the distribution upgrade as this is more likely to have a better dist upgrade procedure covering even more "fixes" and knowledge how to preferably migrate to newer configuration/meta-data formats.

I believe that if you are already running the Oneiric codebase, you do not need to do dist-upgrades to get to final. You are not moving to a new version of Ubuntu. Dist-upgrade is for going from, say, Natty to Oneiric.

---

### Post by xebian on 2011-10-07
> **sgage said:**
> I believe that if you are already running the Oneiric codebase, you do not need to do dist-upgrades to get to final. You are not moving to a new version of Ubuntu. Dist-upgrade is for going from, say, Natty to Oneiric.

Not true.

apt-get dist-upgrade will remove and/or install packages as necessary.
apt-get upgrade  will NOT  remove and/nor install packages.

---

### Post by jerrylamos on 2011-10-07
> **xebian said:**
> Not true.

apt-get dist-upgrade will remove and/or install packages as necessary.
apt-get upgrade  will NOT  remove and/nor install packages.

I used to do sudo apt-get update, sudo apt-get dist-upgrade until I got several installations totally screwed up. sudo dpkg --configure -a was called for but simply did a shutdown.  That was as recently as last month. 

Synaptic running well on this Ocelot so I've been able to use it to remove images etc. and the remaining disk space used is pretty reasonable.  That's very late in development of course when most things are running pretty well.

Must be nearly time for the next go-around....

Jerry

---

### Post by sgage on 2011-10-07
> **xebian said:**
> Not true.

apt-get dist-upgrade will remove and/or install packages as necessary.
apt-get upgrade  will NOT  remove and/nor install packages.

Not true. apt-get upgrade will CERTAINLY install packages as necessary WITHIN a release cycle. It will not remove packages, though it should not be necessary to remove any packages. It's going from one release to the next that requires dist-upgrade.

Going from, say, Beta 2 to Final Release does not require a dist-upgrade. If you are running Natty, then yes, you will do a dist-upgrade to get to Oneiric.

---

### Post by xebian on 2011-10-07
> **sgage said:**
> Not true. apt-get upgrade will CERTAINLY install packages as necessary WITHIN a release cycle. It will not remove packages, though it should not be necessary to remove any packages. It's going from one release to the next that requires dist-upgrade.

Going from, say, Beta 2 to Final Release does not require a dist-upgrade. If you are running Natty, then yes, you will do a dist-upgrade to get to Oneiric.

Read the manual for apt-get
```

      upgrade
           upgrade is used to install the newest versions of all packages currently installed on the
           system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with
           new versions available are retrieved and upgraded; under no circumstances are currently
           installed packages removed, or packages not already installed retrieved and installed. New
           versions of currently installed packages that cannot be upgraded without changing the install
           status of another package will be left at their current version. An update must be performed
           first so that apt-get knows that new versions of packages are available.

...
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution
           system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. So, dist-upgrade command may remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding the general settings for
           individual packages.

```

---

### Post by sgage on 2011-10-07
Yes, I have read the manual for apt-get. Within a version, you don't need dist-upgrade. In fact, as Jerry alluded, when repos are changing rapidly, a dist-upgrade will break your system. With upgrade, you just wait until the repos are in synch again and dependencies met.

When you change from one version of the distro to the next, you use dist-upgrade. That's why it's called DIST-upgrade. OO Beta 2 and its final release are the same version, and you can get there with upgrade.

I've been doing this for many years. It's always worked. More people bork their systems with inappropriate use of dist-upgrade than just about anything else. They see that upgrade is holding back packages, because of unmet dependencies, so they go aha! I'll use dist-upgrade. Which will cheerfully remove critical packages to try to make it all work.

Again, going from the beta to final is NOT an upgrade to a new version of the distro. It's just another upgrade.

---

### Post by ranch hand on 2011-10-08
Apt-get upgrade and dist-upgrade are tools for your distribution.  You "update" your packages list.  You upgrade your "safe" packages in a distribution.  You dist-upgrade to fully upgrade your distribution including removing and adding packages, as needed, to have a fully up to date version.

You can most certainly upgrade to a different version using dist-upgrade.  You have to change your sources.list to that newer version first.  That is now your distribution.  The actions of upgrade and dist upgrade do not change.

While I have always used apt-get to upgrade versions, this was not the method  recommended by Debian until the upgrade from Lenny to Squeeze (February of 2011).  They recommended "aptitude full-upgrade" for the job.  Full-upgrade is a fairly recent name for dist-upgrade in aptitude which was used primarily for upgrading versions (it is still recognized by aptitude as the same as full-upgrade).  This is the cause of this confusion with folks thinking that apt-get dist-upgrade meant version upgrade.  Easy mistake to make.  Never really got my head around it until I started using Debian full time.  Had a lot of reading to do on the history of commands.

I always run a plane upgrade, first, when changing a version.  This only gets packages that do not need to have added or removed packages for their installation.  Most breakage that I have experienced in version upgrades happens when major changes in package titles happens.  That means that if I do the upgrade first and go back looking for errors the history is not as long doing the dist-upgrade second.

---

### Post by jerrylamos on 2011-10-08
As an ordinary user tester, ranch hand's comments are right on.

During Alpha/Beta testing, dist-upgrade has killed any number of my installs.  I don't do that.

Before an Alpha image is available, I take a test install, modify sources.list and do an update & upgrade.  Usually runs since not many changes have been made yet.

When an Alpha image is available, I install that.  If it will....

then do update & upgrades.  Being unstable code, expect to do some more installs.

Biggest rub this last year for a couple months Install was busted on Narwhal.  That was a "pain".  Right now I'm running Ocelot on a netbook with a USB hard drive. Works fine.  I had an old 2.5" laptop drive laying around and bought a $20 USB case for it.  I have another USB hard drive, a bigger 2.5" hard drive and a $10 case from Tiger Direct.  I archive all sorts of stuff on it just in case one of my pc's goes south.

Another huge pain is when Grub is busted.  Talk about Pain!  I had to re-install Windoze 7 when Oneiric Ocelot blew up Grub.  Yes, I keep Windoze dual boot around when my pc gets replaced the future user may expect Windoze.

Anyway, I never take my "main" install and do an upgrade to the next release.  Too risky.

Lots of fun, lots of learning linux.

Jerry

---

### Post by Alwimo on 2011-10-09
It turns out there will be a release candidate for 11.10...
[http://www.omgubuntu.co.uk/2011/10/ubuntu-11-10-release-candidate-due-shortly/?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/10/ubuntu-11-10-release-candidate-due-shortly/?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by cariboo on 2011-10-09
The release candidate, is just the final image, you can join the iso-testing team [here]("http://iso.qa.ubuntu.com/") and help test the image and report bugs.

---

