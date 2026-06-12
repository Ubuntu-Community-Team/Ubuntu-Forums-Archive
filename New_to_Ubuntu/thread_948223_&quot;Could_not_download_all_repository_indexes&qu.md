---
title: "&quot;Could not download all repository indexes&quot;"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by treesloth on 2008-10-15
Hi to all.  Please pardon the fact that this is already frequently posted.  I was able to quite a number of threads about this, but the solutions didn't apply.

I'm getting the (apparently very common) message:

"Could not download all repository indexes"

This happens whenever I try to add/remove apps, check for updates, etc.  I have attached to this post the file "ubuntu_error_and_sources.list.txt", which has the full text of the error messages and my sources.list file.  If it matters, I have a reasonably extensive background in UNIX administration, mainly on FreeBSD, so don't be afraid to lay on the technolingo. :-)  Sadly, I have very little Ubuntu experience-- I'm trying to change that.  If there's a good post about troubleshooting this, I'd appreciate having it pointed out.

Many thanks in advance.

---

### Post by SunnyRabbiera on 2008-10-15
uhh you may want to just give us the errors you got directly, as that file isnt working for me.

---

### Post by treesloth on 2008-10-15
Sure, no problem.  I was hoping to avoid a super-cluttered post, but so it goes.  Here's the contents of the attached file:


From the error message dialog box:

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:)
404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:)
404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:)
404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:)
404 Not Found [IP: 91.189.88.45 80]


*************************************************************************************

The sources.list file:


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy
main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe
multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main
restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main
restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main
restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main
restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by hyper_ch on 2008-10-15
I think Edgy has run out of support... it's only 18 months and edgy was release october 2006.

---

### Post by SunnyRabbiera on 2008-10-15
what version of ubuntu are you using?

---

### Post by jemate18 on 2008-10-15
i think you need to upgrade to the latest version.. your distro version aint supported anymore...

---

### Post by treesloth on 2008-10-15
> **jemate18 said:**
> i think you need to upgrade to the latest version.. your distro version aint supported anymore...

Well, crap... Unfortunately, 6.10 is the latest version that will actually install on my laptop.  For some reason, the laptop (the first Tablet PC model ever to hit the market, AFAIK) won't recognize disks from later versions, and the in-place upgrade always screws up the installation.  Oh, well.  Time to work through those problems, then.  Thanks for the replies.

---

### Post by hyper_ch on 2008-10-15
have you tried 8.10 yet?

---

### Post by treesloth on 2008-10-15
> **hyper_ch said:**
> have you tried 8.10 yet?

No, but only for lack of time.  I'm going to make an attempt in the next couple of days.

---

### Post by Nepherte on 2008-10-15
You might want to wait till it is officially released instead of trying a beta.

---

### Post by hyper_ch on 2008-10-15
nepherte:
what major improvements do you expect the next few days from it? it's constantly being updates... each day a couple of things... and as the "release date" is close, there won't be many change and no drastic changes ;) so the current beta is pretty much "stable" already.

---

### Post by semitone36 on 2008-10-15
> **treesloth said:**
>  won't recognize disks from later versions

This sounds like a problem with your disk drive, not the disk itself.

But yes, each ubuntu release gets about 18 months of repository support and then the repositories are closed.  This is why you are getting all of those 404 errors.  I recommend doing a clean install using a disk you burned yourself.  Also, when burning the .iso be sure to have the burn speed set as low as it will go.  This decreases the chances of corrupting data.

---

### Post by treesloth on 2008-10-15
> **semitone36 said:**
> This sounds like a problem with your disk drive, not the disk itself.

But yes, each ubuntu release gets about 18 months of repository support and then the repositories are closed.  This is why you are getting all of those 404 errors.  I recommend doing a clean install using a disk you burned yourself.  Also, when burning the .iso be sure to have the burn speed set as low as it will go.  This decreases the chances of corrupting data.

It's almost certainly the drive/laptop.  In fact, I have 2 sets of the original restore CDs for the system.  Neither will boot.  In fact, Linux is the only thing that will install in any form at all.

Sadly, though, it's all academic now.  I took some bad advice and ran a command, "sudo rm -rf", or something like that.  Apparently that's not the Linux "Find and Fix" system.  If only someone had warned me...

---

### Post by semitone36 on 2008-10-16
> **treesloth said:**
> I took some bad advice and ran a command, "sudo rm -rf", or something like that.  Apparently that's not the Linux "Find and Fix" system.  If only someone had warned me...

Ouch. I am really sorry for that.  I caught someone trying to give a newbie the rm -rf command once and ever since then I keep my signature on as a warning.  Some people can be pretty cruel.[-(

But as far as your drive goes I have a similar problem.  The laser on my laptop only reads CDs, not DVDs and I dont have the funds at the moment for a new drive.  Hopefully in your case your comp is still under warrantee?

---

### Post by treesloth on 2008-10-16
> **semitone36 said:**
> Ouch. I am really sorry for that.  I caught someone trying to give a newbie the rm -rf command once and ever since then I keep my signature on as a warning.  Some people can be pretty cruel.[-(

But as far as your drive goes I have a similar problem.  The laser on my laptop only reads CDs, not DVDs and I dont have the funds at the moment for a new drive.  Hopefully in your case your comp is still under warrantee?

Heh, I was totally kidding about the rm -rf.  In fact, I wrote it as a joke right after seeing your signature.  I've been in the UNIX world for a fair amount of time, and while I'm far from all-knowing, it wouldn't be easy to get me to wipe out my entire filesystem. :-)

Sadly, the warranty is long-gone, but it's no big loss.  This laptop is used for pretty much nothing learning Linux.  It would be great to turn it into an Ubuntu tablet, with functional digitizer, etc, but no big deal either way.  Strangely, it's good that its CD drive is external-only... makes troubleshooting it as easy as swapping USB plugs.

---

### Post by semitone36 on 2008-10-16
Oh a wise-guy huh? :)

Well then I wish you luck!

---

