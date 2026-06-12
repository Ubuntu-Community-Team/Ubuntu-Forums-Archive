---
title: "[SOLVED] Repository Update Error"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by aheicher on 2008-06-25
Ok, so my repository update is having a few problems, here are the update packages it cant fetch:
```
GPG error: http://volatile.debian.org etch/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC61E0B0BBE55AB3Failed to fetch http://archive.ubuntu.com/dists/hardy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/dists/hardy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
Any ideas?

---

### Post by iaculallad on 2008-06-25
What about using your terminal to update:

```
sudo apt-get update && sudo apt-get upgrade
```

Does it show the same error?

---

### Post by aheicher on 2008-06-25
yeah, same error.  although I believe the URL's for those packages are wrong, but they are the universe packages so i dunno how to change them

---

### Post by iaculallad on 2008-06-25
Try commenting this entry in your source.list file:

> [http://volatile.debian.org](http://volatile.debian.org) etch/volatile

in

```
gksu gedit /etc/apt/sources.list
```


Then retry your update via terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Or try to post us your sources.list file.

---

### Post by aheicher on 2008-06-26
I commented the line to no avail, here is the sources.list file, in all its glory:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb http://moblock-deb.sourceforge.net/debian hardy main
# deb-src http://moblock-deb.sourceforge.net/debian hardy main
deb http://archive.ubuntu.com hardy main universe
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
# deb http://volatile.debian.org/debian-volatile etch/volatile main contrib # non-free
```

There you are, anything look weird to you?

---

### Post by iaculallad on 2008-06-26
What about changing your download Server to "Main Server" in the Software Sources?

System->Administration->Software Sources, under the "Ubuntu Software" tab, "Download From:" = Main Server. Click Close open up the terminal and:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by avtolle on 2008-06-26
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

Try uncommenting that line, reload and try again.

---

### Post by aheicher on 2008-06-26
Nope, neither of these things worked, and I got exactly the same error

---

### Post by aheicher on 2008-07-02
*bump*

Still have the same problem, has anybody heard of this before?

---

### Post by hyper_ch on 2008-07-02
1st line: you added a repository to which you did not add gpg keys... hence the warning
2nd line: it seems you can't reach archive.ubuntu.com right now.... that will be solved with time
3rd line: just a warning that it couldn't fetch all the current indexes of all repos (that's because of 2nd line)

Nothing to worry about

And you might want to make your sources.list more readable using this:

```

# Hardy Main
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

# Hardy Updates
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe

# Hardy Backports
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

# Hardy Partner
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Hardy Proposed
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe

# Hardy Security
deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe

# Hardy Awn
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

# Hardy Do-Core
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main

# deb http://moblock-deb.sourceforge.net/debian hardy main
# deb-src http://moblock-deb.sourceforge.net/debian hardy main
# deb http://volatile.debian.org/debian-volatile etch/volatile main contrib # non-free

```

You might even want to comment the sources repos...

```

# Hardy Main
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

# Hardy Updates
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe

# Hardy Backports
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

# Hardy Partner
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Hardy Proposed
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe

# Hardy Security
deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe

# Hardy Awn
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

# Hardy Do-Core
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main

# deb http://moblock-deb.sourceforge.net/debian hardy main
# deb-src http://moblock-deb.sourceforge.net/debian hardy main
# deb http://volatile.debian.org/debian-volatile etch/volatile main contrib # non-free

```

---

### Post by robertchahine on 2008-07-02
i had this problem two weeks ago,
all what i did is:
go to system panel>administation>software sources
click on ubuntu software tab(first tab), and chose "other" from the "download from" list.it will open a new window, simply click on "select best server".
then open terminal and do
```
sudo apt-get update && sudo apt-get upgrade
```.
that solved my problem

---

### Post by jre on 2008-07-02
Do you have MoBlock installed? If yes, perhaps it is blocking the repository.
Open a terminal and type "tail -f /var/log/moblock.log" to see live what IPs are blocked. Then update your packages and check if the server gets blocked. If yes, then you have to whitelist it.

---

### Post by aheicher on 2008-07-04
Well you see, Ive had this error for about 30 days now, and I believe I know what the problem is.  When it attempts to download the updates, it attempts to contact: ```
http://archive.ubuntu.com/dists/hardy/universe/binary-i386/Packages.gz
``` when it should be contacting ```
http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz
```  Any way to edit this in a way to make it contact the correct URL?  I don't believe its listen in sources.list...

EDIT: After noticing there is a second page to all this, I tried these solutions, neither worked.  And I do not have moblock installed anymore

---

### Post by jre on 2008-07-07
Good, you found the error on your own :-)
It has to be in /etc/apt/sources.list or in a file in the folder /etc/apt/sources.list.d/ !
Is there a line
```
deb [http://archive.ubuntu.com/ universe](http://archive.ubuntu.com/ universe)
```?
Change it to
```
deb [http://archive.ubuntu.com/ubuntu universe](http://archive.ubuntu.com/ubuntu universe)
```

The rest of the entry is figured out by apt automatically.

---

### Post by aheicher on 2008-07-08
Thank you! Finally, I preformed that edit and it worked like a charm, thanks a lot

---

