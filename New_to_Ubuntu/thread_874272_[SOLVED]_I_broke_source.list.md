---
title: "[SOLVED] I broke source.list"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mujrim on 2008-07-29
I'm new to Ubuntu, and Linux, in general.  I had an older laptop lying around so I figured I'd mess around with it 2 days ago.
I was following some instructions I found on the internet to enable DVD playback (which didn't work for me anyways), and I altered my source.list file.  I've been trying to find instructions on how to restore it back to default, but I can't find any.

Add/Remove programs now says:
> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


And Synaptec Packet Manager now says
> 
E: Type '--18:54:02--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Can someone please help me?
I'm running the 64 bit version of Ubuntu if that matters.

---

### Post by Joeb454 on 2008-07-29
Open a terminal, and enter ```
cat /etc/apt/sources.list > ~/Desktop/source.txt
``` Then upload the file "source.txt" from your desktop, into another post, so we can take a look at the file :)

---

### Post by mujrim on 2008-07-29
Thanks for the quick reply.
Here's the source.txt file that was generated:
> 
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


---

### Post by aheckler on 2008-07-29
Could it be that his Medibuntu sources.list is messed up? That's what seems to be indicated by the error message he's getting, and I bet the directions he was following were [these]("https://help.ubuntu.com/community/Medibuntu").

mujrim, please type:

```
cat /etc/apt/sources.list.d/medibuntu.list
```

into a terminal and paste the output here. Thanks!

---

### Post by speeddemon8803 on 2008-07-29
The default sources.list for hardy can be found here: [http://ubuntuforums.org/showthread.php?t=783577](http://ubuntuforums.org/showthread.php?t=783577)

Hope this helps! :D

---

### Post by mujrim on 2008-07-29
The output from that is:
> 
--18:54:02--  [http://ww.medibuntu.org/source.list.d/hardy.list](http://ww.medibuntu.org/source.list.d/hardy.list)
           => `hardy.list'
Resolving ww.medibuntu.org... failed: Name or service not known.


Would it have something to do with it being ww instead of www?

---

### Post by aheckler on 2008-07-29
Try running these commands in order:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get upgrade
```

That should get you back on track. I suspect what happened is that your download of the Medibuntu sources.list failed or otherwise messed up, and you got a file of gibberish instead. If you still want to play DVDs, let us know and someone will be along to help you shortly. :)

---

### Post by SunnyRabbiera on 2008-07-29
Yeh looks like a hiccup, but with any luck it can be fixed.
Issue like this happen every so often

---

### Post by mujrim on 2008-07-29
Yup, that did the trick.  Thank you very much everybody for the quick replies.  I really appreciate it.
So, how do I go about enabling DVD playback?

---

### Post by aheckler on 2008-07-29
Paste these in terminal one at a time and then try to play a DVD:

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by mujrim on 2008-07-29
Wow, that was much easier than the instructions I was following.  Worked like a charm.  Thanks again.

---

