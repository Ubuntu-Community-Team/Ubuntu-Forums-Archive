---
title: "Problem with Update Manager"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by ferfykins on 2017-02-15
Few problems... first in software manager, the update is stuck and wont finish installing...not sure how to fix that... 
[s]Next, i was wondering if there are any text editors for ubuntu that are similar to notepad++ on windows.. I like the color feature, different colors to distinguish code plus the autocomplete option for () and {}
Also, i was wondering what pdf viewer is best, or closest to adobe acrobat for linux... Adobe was my favorite for windows, so i'd like something similiar that can run on ubuntu default window manager



Last and probably most important, i wonder if it's possible for someone to walk me through installing jdk and eclipse on ubuntu... over skype... i've googled installation instructions and can't figure it out..
Also half of the installation instructions are 3-5+ year old topics.. so yeah idk[/s]

---

### Post by QIII on 2017-02-15
Hello!

"Laundry list" threads become confusing very quickly as different people try to answer different questions.  Some people think multiple questions per thread is more efficient.  That is not our observation.

For that reason, we would prefer one subject per thread.

It would be easier on you and anyone who would like to help if you would edit your post to include only one question (change the thread title to be more specific as well) and make separate posts for each of the other questions.

Cheers!

---

### Post by ferfykins on 2017-02-15
> **QIII said:**
> Hello!

"Laundry list" threads become confusing very quickly as different people try to answer different questions.  Some people think multiple questions per thread is more efficient.  That is not our observation.

For that reason, we would prefer one subject per thread.

It would be easier on you and anyone who would like to help if you would edit your post to include only one question (change the thread title to be more specific as well) and make separate posts for each of the other questions.

Cheers!


Thanks!

---

### Post by oldrocker99 on 2017-02-15
To answer your first question, if the software updater is or has become stuck, open a terminal and type:```
sudo apt-get -f install
```

That should fix your problem. If not, let us know.

---

### Post by ferfykins on 2017-02-22
> **oldrocker99 said:**
> To answer your first question, if the software updater is or has become stuck, open a terminal and type:```
sudo apt-get -f install
```

That should fix your problem. If not, let us know.

getthiserror:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wildmanne39 on 2017-02-22
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
That error usually means you have like the terminal and software center open, you can only have one instance running at a time, if that is not the case rebooting usually clears it up.

---

### Post by ferfykins on 2017-02-22
Yep you were right wildmanne39

i did the command again:[COLOR=#000000][FONT=&quot]sudo apt-get -f install  

seemed to work, but when i open software manager, the update is still there, and when i try installing update, it just sticks.....[/FONT][/COLOR]

---

### Post by deadflowr on 2017-02-22
What's the update for?
(what's the package?)

---

### Post by ferfykins on 2017-02-22
"OS Updates"

i can list the contents as well:
gir1.2-goa-.1.0
humanity-icon-theme
indicator-application
irssi
libnm-gtk-common
libpam-cgfs
network-manager
python3-disupgrade
snap-confine
snapd
ubuntu-core-launcher
ubuntu-release-upgrader-core
ubutnu-release-upgrader-gtk

---

### Post by wildmanne39 on 2017-02-22
Please run the following commands and post the results so we can see the errors:
```
sudo apt update && sudo apt upgrade
```
Thanks

---

### Post by ferfykins on 2017-02-22
it ran fine wildmanne39, no errors at all...

I think that fixed the problem thanks wildman!! I'll post later if i encounter the same problem

---

### Post by wildmanne39 on 2017-02-22
It probably did, in 16.04 and above we are not supposed to use the old:
```
sudo apt-get update
```
anymore, it leaves packages at times that are kept back, and the:
```
sudo apt upgdate
```
tries to fix it like aptitude does.

---

### Post by ferfykins on 2017-02-22
It still shows as needed to update in software manager

---

### Post by wildmanne39 on 2017-02-22
Please do:
```
sudo apt update && sudo apt upgrade
```
post the out put here between code tags.

---

### Post by ferfykins on 2017-02-22
```
Get:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu yakkety InRelease                    
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://us.archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]   
Hit:5 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu yakkety InRelease
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Get:7 http://us.archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB] 
Ign:8 http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  InRelease
Hit:10 http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release
Get:11 http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release.gpg [481 B]
Ign:11 http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release.gpg
Reading package lists... Done   
W: GPG error: http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EDB7AED941EEDB57
E: The repository 'http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

---

### Post by wildmanne39 on 2017-02-22
Please post the output of:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```
This should not be to hard to fix.

---

### Post by ferfykins on 2017-02-22
Output of: [COLOR=#000000][FONT=&amp]cat /etc/apt/sources.list[/FONT][/COLOR]

```
# deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.2)]/ yakkety main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ yakkety main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ yakkety universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety universe
deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ yakkety multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety multiverse
deb http://us.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu yakkety partner
# deb-src http://archive.canonical.com/ubuntu yakkety partner


deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
# deb-src http://security.ubuntu.com/ubuntu yakkety-security main restricted
deb http://security.ubuntu.com/ubuntu yakkety-security universe
# deb-src http://security.ubuntu.com/ubuntu yakkety-security universe
deb http://security.ubuntu.com/ubuntu yakkety-security multiverse
# deb-src http://security.ubuntu.com/ubuntu yakkety-security multiverse



```


output of: [COLOR=#000000][FONT=&amp]ls /etc/apt/sources.list.d/

[/FONT][/COLOR]google-chrome.list  google-chrome.list.save  irssi.list  irssi.list.save  notepadqq-team-ubuntu-notepadqq-yakkety.list

---

### Post by wildmanne39 on 2017-02-22
Please do:
```
sudo -H gedit /etc/apt/sources.list.d/
```
when the window opens enter your password then gedit will open then remove:
```
 google-chrome.list google-chrome.list.save irssi.list irssi.list.save notepadqq-team-ubuntu-notepadqq-yakkety.list 
```
save and close gedit then run:
```
sudo apt update && sudo apt upgrade
```
see if that fixes it.

This is the error:
```
The repository 'http://download.opensuse.org/repositories/home:/ailin_nemui:/irssi-test/xUbuntu_16.10  Release' is not signed.
```
I am not sure what opensuse is doing there but it is a problem, possibly not the only one but it looks like it is.

---

### Post by ferfykins on 2017-02-22
when i try using: [COLOR=#000000][FONT=&quot]sudo -H gedit /etc/apt/sources.list.d/


I get an error:
[/FONT][/COLOR]“/etc/apt/sources.list.d” is a directory.
Please check that you typed the location correctly and try again."

---

### Post by howefield on 2017-02-23
> **ferfykins said:**
> when i try using: [COLOR=#000000][FONT=&quot]sudo -H gedit /etc/apt/sources.list.d/

Try 

```
sudo -H nautilus /etc/apt/sources.list.d/
```

Or open the Software Sources application and untick the relevant repositories from the "*Other Software*" tab, this will make it easier to re-enable them if/when needed. Close out and you'll be prompted to reload your software sources, accept it.

---

