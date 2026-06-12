---
title: "Connection Problems"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by jybeard on 2008-05-01
I can't get updates.  

I keep getting a Failed to Fetch message.  

I've tried to fix the problem by going to Software Sources and finding the best mirror, but it keeps telling me that I have a bad connection.  

I get on the internet just fine, at a great speed.  

Any ideas?

---

### Post by aheckler on 2008-05-01
Can you type "cat /etc/apt/sources.list" in the terminal and paste the output here please?

---

### Post by DrCoolSanta on 2008-05-01
It seems to me that you are not running one of the newer versions, something like Edgy. I have been having issues with Edgy, I needed it because the kernels of the newer distro won't work with my hardware, and so I never even upgraded. This might even help if you are using a newer version.
How I did was, I typed this in the terminal
> sudo gedit /etc/apt/sources.list
and then commented every line that was not, you comment by putting a #. Then I went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and then scrolled to the search part, typed some package name in the keyword and then clicked on a random result. In the download subheading choose i386, this should show you a mirror list, just download from a mirror to confirm that it is fast and works for you, like many didn't for me. Copy the line and put it in the file we opened earlier. Replace the security.ubuntu.com/ubuntu part in it with the copied text.
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main universe
Save and close, then run Synaptic and reload, this process can be done through Synaptic but never worked for me.

---

### Post by jybeard on 2008-05-01
[PHP]Can you type "cat /etc/apt/sources.list" in the terminal and paste the output here please?[/PHP]

#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by aheckler on 2008-05-01
Hmm ok, try running "sudo apt-get update" and paste the output here.

Then run "sudo apt-get upgrade" and paste the output here.

---

### Post by jybeard on 2008-05-01
> **aheckler said:**
> Can you type "cat /etc/apt/sources.list" in the terminal and paste the output here please?


#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

jybeard@Home1:~$ sudo gedit /etc/apt/sources.list
[sudo] password for jybeard:
jybeard@Home1:~$ sudo gedit /etc/apt/sources.list
jybeard@Home1:~$ sudo gedit /etc/apt/sources.list
jybeard@Home1:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by aheckler on 2008-05-01
Ack, sorry I worded that a bit weird. I need you to type ```
sudo apt-get update
``` in the terminal and then paste the output of **that** command here.

And then type ```
sudo apt-get upgrade
``` in the terminal and then paste the output of **that** command here.

I don't need to see your sources.list again, that was my fault. :-P

---

### Post by jybeard on 2008-05-01
> **aheckler said:**
> Ack, sorry I worded that a bit weird. I need you to type ```
sudo apt-get update
``` in the terminal and then paste the output of **that** command here.

And then type ```
sudo apt-get upgrade
``` in the terminal and then paste the output of **that** command here.

I don't need to see your sources.list again, that was my fault. :-P

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.





Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free mplayer 2:1.0~rc1-0ubuntu13.2+medibuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ubuntu-docs 7.10.5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main bzip2 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libbz2-1.0 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5-minimal 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main tzdata 2008a-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libkrb53 1.6.dfsg.1-7ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-client 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main rsync 2.6.9-5ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-autoipd 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common-data 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-core5 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-daemon 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-client3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsys2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsimage2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libgs8 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-common 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-bsd 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-client 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox-gnome-support 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.124.0ubuntu1~gutsy1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript-x 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gthumb 3:2.10.6-0ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-glib1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-qt3-1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libicu36 3.6-3ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main mysql-common 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libmysqlclient15off 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main network-manager-gnome 0.6.5-0ubuntu11~7.10.0
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main unzip 5.52-10ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by aheckler on 2008-05-01
Ok, can you post the output of ```
cat /etc/hosts
``` please? Don't worry, we're close to solving the problem :)

---

### Post by jybeard on 2008-05-01
> **aheckler said:**
> Ok, can you post the output of ```
cat /etc/hosts
``` please? Don't worry, we're close to solving the problem :)

127.0.0.1 localhost
127.0.1.1 Home1.static.rvsd.ca.charter.com Home1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by aheckler on 2008-05-01
Ok, open the /etc/hosts file for editing with

```
gksudo gedit /etc/hosts
```

Then edit **the second line** so the file looks like this:

```
127.0.0.1 localhost
127.0.1.1 Home1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Save it and close. Then try:

```
sudo apt-get update && sudo apt-get upgrade
```
and see what happens

---

### Post by jybeard on 2008-05-01
> **aheckler said:**
> Ok, open the /etc/hosts file for editing with

```
gksudo gedit /etc/hosts
```

Then edit **the second line** so the file looks like this:

```
127.0.0.1 localhost
127.0.1.1 Home1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Save it and close. Then try:

```
sudo apt-get update && sudo apt-get upgrade
```
and see what happens

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libc6-dev
The following packages will be upgraded:
  avahi-autoipd avahi-daemon bzip2 cupsys cupsys-bsd cupsys-client
  cupsys-common firefox firefox-gnome-support flashplugin-nonfree ghostscript
  ghostscript-x gthumb language-pack-en language-pack-gnome-en
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libbz2-1.0 libcupsimage2 libcupsys2 libgs8 libicu36 libkrb53
  libmysqlclient15off mplayer mysql-common network-manager-gnome
  openssh-client python2.5 python2.5-minimal rsync ssh-askpass-gnome tzdata
  ubuntu-docs unzip
40 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 41.8MB of archives.
After unpacking 70.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free mplayer 2:1.0~rc1-0ubuntu13.2+medibuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ubuntu-docs 7.10.5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main bzip2 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libbz2-1.0 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5-minimal 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main tzdata 2008a-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libkrb53 1.6.dfsg.1-7ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-client 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main rsync 2.6.9-5ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-autoipd 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common-data 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-core5 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-daemon 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-client3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsys2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsimage2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libgs8 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-common 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-bsd 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-client 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox-gnome-support 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.124.0ubuntu1~gutsy1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript-x 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gthumb 3:2.10.6-0ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-glib1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-qt3-1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libicu36 3.6-3ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main mysql-common 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libmysqlclient15off 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main network-manager-gnome 0.6.5-0ubuntu11~7.10.0
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main unzip 5.52-10ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by aheckler on 2008-05-01
Well shoot. We appear to have made *some* progress but we obviously haven't fixed it. I haven't actually experienced this bug myself, so I've asked some people with more experience to take a look at your problem. Someone should be along shortly to help you out. :)

---

### Post by jybeard on 2008-05-01
Thanks for your help I really appreciate it.  This is just way beyond my experience level.

---

### Post by ByteJuggler on 2008-05-01
> **jybeard said:**
> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

OK... so you're referring to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com), and yet, apt's trying to connect to localhost??  How odd.  Perhaps you've got a proxy set... Please post the output of:

```
env | grep 4001
```

and

```
grep -r 4001 /etc/
```

Edit: Also please post output of:

```
dpkg -l *proxy* |grep ^i 
```

---

### Post by agent8131 on 2008-05-01
It looks like you're using the anon-proxy package but it isn't working.  I'm not really familiar with that package but you could try:

```
/etc/init.d/anon-proxy restart
```

or:

```
env -u HTTP_PROXY -u http_proxy apt-get update && apt-get dist-upgrade
```

---

### Post by jybeard on 2008-05-01
> **agent8131 said:**
> It looks like you're using the anon-proxy package but it isn't working.  I'm not really familiar with that package but you could try:

```
/etc/init.d/anon-proxy restart
```

or:

```
env -u HTTP_PROXY -u http_proxy apt-get update && apt-get dist-upgrade
```

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by jybeard on 2008-05-01
> **ByteJuggler said:**
> OK... so you're referring to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com), and yet, apt's trying to connect to localhost??  How odd.  Perhaps you've got a proxy set... Please post the output of:

```
env | grep 4001
```

and

```
grep -r 4001 /etc/
```

Edit: Also please post output of:

```
dpkg -l *proxy* |grep ^i 
```




After the first code:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
jybeard@Home1:~$ env | grep 4001
http_proxy=http://localhost:4001 
HTTP_PROXY=http://localhost:4001 
jybeard@Home1:~$ grep -r 4001 /etc/
/etc/rc5.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/group-: Permission denied
/etc/init.d/anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/gshadow-: Permission denied
/etc/mnogosearch/TraditionalChinese.freq:    4001 &#65533;U
/etc/mnogosearch/langmap/ar.arabic.quran.lm:&#65533;_  4001
/etc/mnogosearch/langmap/ca.latin1.lm:_ca       40010
/etc/mnogosearch/langmap/sk.ascii.lm:.  4001
grep: /etc/passwd-: Permission denied
/etc/rc2.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/kde3/kdebug.areas:24001         Quanta (parser)
/etc/kde3/kdebug.areas:34001        klyx
/etc/kde3/kdebug.areas:44001        KexiDB (driver impl)
grep: /etc/ppp/chap-secrets: Permission denied
grep: /etc/ppp/pap-secrets: Permission denied
/etc/rc4.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/at.deny: Permission denied
/etc/rc6.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/apt/secring.gpg: Permission denied
grep: /etc/apt/trustdb.gpg: Permission denied
/etc/udev/rules.d/45-libsane.rules:SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="4001", MODE="664", GROUP="scanner"
/etc/udev/rules.d/45-libsane.rules:# Artec/Ultima 1236 USB | Artec/Ultima Ultima 2000 (0x4001)
/etc/udev/rules.d/45-libsane.rules:SYSFS{idVendor}=="05d8", SYSFS{idProduct}=="4001", MODE="664", GROUP="scanner"
/etc/rc1.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
/etc/default/anon-proxy:PORT="4001"
grep: /etc/fuse.conf: Permission denied
grep: /etc/shadow: Permission denied
grep: /etc/.pwd.lock: Permission denied
/etc/rc3.d/S20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/sudoers: Permission denied
grep: /etc/security/opasswd: Permission denied
/etc/rc0.d/K20anon-proxy:[ -z "$PORT" ] && PORT="4001"
grep: /etc/gshadow: Permission denied
grep: /etc/X11/Xwrapper.config: Permission denied
grep: /etc/ssl/private: Permission denied
/etc/environment:HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
/etc/environment:http_proxy=http://localhost:4001 # +ANON_MARK+
grep: /etc/cups/classes.conf: Permission denied
grep: /etc/cups/printers.conf.O: Permission denied
grep: /etc/cups/printers.conf: Permission denied
grep: /etc/cups/ssl: Permission denied
grep: /etc/shadow-: Permission denied


and the second code:

ii  anon-proxy     00.02.39-8.3     Proxy to surf the web anonymously
ii  smproxy        1:1.0.2-0ubuntu1 X client - smproxy

---

### Post by ByteJuggler on 2008-05-02
OK you've got the anon-proxy package installed and as others have said, it's for whatever reason not working, hence breaking apt-get.  Do you know about this (the anon proxy and why it's installed) and do you want to keep it, or can we uninstall it?  If it was an incidental/accidental install as a result of something else you've installed, then I'd suggest just uninstalling it.  Uninstalling it is probably the easiest way to fix the problem permanently for now.  (The "env -u HTTP_Proxy" bits would also work, but you'd have to put that in front every time you use apt-get then.)

To uninstall it:

```
sudo apt-get purge anon-proxy
```

---

### Post by jybeard on 2008-05-02
> **ByteJuggler said:**
> OK you've got the anon-proxy package installed and as others have said, it's for whatever reason not working, hence breaking apt-get.  Do you know about this (the anon proxy and why it's installed) and do you want to keep it, or can we uninstall it?  If it was an incidental/accidental install as a result of something else you've installed, then I'd suggest just uninstalling it.  Uninstalling it is probably the easiest way to fix the problem permanently for now.  (The "env -u HTTP_Proxy" bits would also work, but you'd have to put that in front every time you use apt-get then.)

To uninstall it:

```
sudo apt-get purge anon-proxy
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  anon-proxy*
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 352kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104636 files and directories currently installed.)
Removing anon-proxy ...
Stopping Anonymising Proxy Service: anon-proxy.
Stopping Anonymising Proxy Service: anon-proxy.
Purging configuration files for anon-proxy ...
Setting up mnogosearch-common (3.2.41-2) ...
Template #1 in /var/lib/dpkg/info/mnogosearch-common.templates does not contain a 'Template:' line
dpkg: error processing mnogosearch-common (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 mnogosearch-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MaindotC on 2008-05-02
How do you think this happened to begin with?  Was it the network configuration portion of the installation, does his network not have dhcp, something along those lines?

---

### Post by ByteJuggler on 2008-05-02
> **jybeard said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  anon-proxy*
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 352kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104636 files and directories currently installed.)
Removing anon-proxy ...
Stopping Anonymising Proxy Service: anon-proxy.
Stopping Anonymising Proxy Service: anon-proxy.
Purging configuration files for anon-proxy ...
Setting up mnogosearch-common (3.2.41-2) ...
Template #1 in /var/lib/dpkg/info/mnogosearch-common.templates does not contain a 'Template:' line
dpkg: error processing mnogosearch-common (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 mnogosearch-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

OK, so it seemed to have uninstalled and then installed mnogosearch-common, which according to the description is: 

> full-featured web search engine (common files)
MnogoSearch is a web search engine that consists of two parts.

The first part is the indexing mechanism (indexer).
It crawls over HTML hypertext references and stores found words and
new references into a database.

The second part is a web front-end that provides search functions
using the data collected by the indexer. For more information, look at
[http://search.mnogo.ru/](http://search.mnogo.ru/)

This package contains common files for all database types. A
mnogosearch-<databasetype> package is also needed to use
mnogosearch. Only one database type package can be installed.

Do you know of this?  Can we uninstall this also?  

Sine it appears anon-proxy deinstalled (even if it didn't fully complete successfully due to the other problems), can you now access/use apt-get?

---

### Post by ByteJuggler on 2008-05-02
> **strAlan said:**
> How do you think this happened to begin with?  Was it the network configuration portion of the installation, does his network not have dhcp, something along those lines?

I have no idea. Offhand there's nothing I know of that one might install that uses anon-proxy.  Certainly, I can say fairly confidently dhcp has nothing to do with it.  I'm guessing it might have something to do with that other package mentioned in the message "MnogoSearch", some sort of web search engine, but that doesn't list anon-proxy as a dependency, so I'm not really sure why that is dragged into this.  I've searched using Synaptic for pacakges depending on "anon-proxy" and the only listed package I could find was "tor", which is "Tor is a connection-based low-latency anonymous communication system which addresses many flaws in the original onion routing design."  

To the OP: Do you have "tor" installed?

---

### Post by jybeard on 2008-05-02
> **ByteJuggler said:**
> I have no idea. Offhand there's nothing I know of that one might install that uses anon-proxy.  Certainly, I can say fairly confidently dhcp has nothing to do with it.  I'm guessing it might have something to do with that other package mentioned in the message "MnogoSearch", some sort of web search engine, but that doesn't list anon-proxy as a dependency, so I'm not really sure why that is dragged into this.  I've searched using Synaptic for pacakges depending on "anon-proxy" and the only listed package I could find was "tor", which is "Tor is a connection-based low-latency anonymous communication system which addresses many flaws in the original onion routing design."  

To the OP: Do you have "tor" installed?



In response to your last two replies:

1)  I have no idea what Mnogosearch is and I still cannot download updates using apt get....

2)  I have no idea what Tor is or why it would be on my system.  I did a search in my "Add/Remove" section and found nothing with Tor in it.

3)  One of the major uses for my system lately has been using Kbitorrent....maybe that has something to do with it?  

4)  Sorry I can't be of more help and thank you very much for yours!

---

### Post by jybeard on 2008-05-02
> **ByteJuggler said:**
> OK, so it seemed to have uninstalled and then installed mnogosearch-common, which according to the description is: 



Do you know of this?  Can we uninstall this also?  

Sine it appears anon-proxy deinstalled (even if it didn't fully complete successfully due to the other problems), can you now access/use apt-get?



 apt-get install update
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by agent8131 on 2008-05-02
> **jybeard said:**
> apt-get install update
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

You'll want to use
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by jybeard on 2008-05-02
> **agent8131 said:**
> You'll want to use
```

sudo apt-get update
sudo apt-get dist-upgrade

```

 sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc6-dev
The following packages will be upgraded:
  avahi-autoipd avahi-daemon bzip2 cupsys cupsys-bsd cupsys-client
  cupsys-common firefox firefox-gnome-support flashplugin-nonfree ghostscript
  ghostscript-x gthumb language-pack-en language-pack-gnome-en
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libbz2-1.0 libcupsimage2 libcupsys2 libgs8 libicu36 libkrb53
  libmysqlclient15off mplayer mysql-common network-manager-gnome
  openssh-client python2.5 python2.5-minimal rsync ssh-askpass-gnome tzdata
  ubuntu-docs unzip
40 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 41.8MB of archives.
After unpacking 70.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free mplayer 2:1.0~rc1-0ubuntu13.2+medibuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-en 1:7.10+20080229
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ubuntu-docs 7.10.5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main bzip2 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libbz2-1.0 1.0.4-0ubuntu2.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5-minimal 2.5.1-5ubuntu5.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main tzdata 2008a-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libkrb53 1.6.dfsg.1-7ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-client 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main rsync 2.6.9-5ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-autoipd 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common-data 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-common3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-core5 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main avahi-daemon 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-client3 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsys2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsimage2 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libgs8 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-common 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-bsd 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-client 1.3.2-1ubuntu7.6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox-gnome-support 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.124.0ubuntu1~gutsy1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ghostscript-x 8.61.dfsg.1~svn8187-0ubuntu3.4
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gthumb 3:2.10.6-0ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-glib1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libavahi-qt3-1 0.6.20-2ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libicu36 3.6-3ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main mysql-common 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libmysqlclient15off 5.0.45-1ubuntu3.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main network-manager-gnome 0.6.5-0ubuntu11~7.10.0
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main unzip 5.52-10ubuntu1.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.6_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.6_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/m/mplayer/mplayer_1.0~rc1-0ubuntu13.2+medibuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by MaindotC on 2008-05-03
> **ByteJuggler said:**
>  Certainly, I can say fairly confidently dhcp has nothing to do with it.  

I thought DHCP would have something to do with it because it seems that he was issued the incorrect DNS information and default gateway which is redirecting him to a proxy.

---

### Post by jybeard on 2008-05-03
Problem Solved!!

I just restarted my computer and tried the upgrade again and everything is downloading fine.  I'm not sure which step of the way fixed it exactly(since I hadn't restarted during the whole process) but thank you to all you guys for the help.

I appreciate it and hopefully when I become a little more experienced I can be of assistance to someone else.

---

### Post by ByteJuggler on 2008-05-03
> **strAlan said:**
> I thought DHCP would have something to do with it because it seems that he was issued the incorrect DNS information and default gateway which is redirecting him to a proxy.

Well, yes at first glance one might think that, except on closer inspection (as per my "env | grep" output) it became clear that it's due to apt-get using the specified HTTP proxy, which is set in the HTTP_PROXY environment variable, as a result of the anon-proxy package being installed.  When the original poster now rebooted, this cleared the HTTP_PROXY variable of the current session, which is why it's now working correctly.  :-)  (So to the original poster: It's the removal of the anon-proxy pacakge, followed by the reboot, that fixed it.  Strictly speaking the reboot shouldn't have been neccesary and merely opening another session should've sufficed, but anyway!)

---

