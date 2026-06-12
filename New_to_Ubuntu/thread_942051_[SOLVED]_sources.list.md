---
title: "[SOLVED] sources.list"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-08
I want to "update" the /etc/apt/sources.list file which apt-get uses. You see, I moved from one part of the world to another recently.

Is there a default way to get the sources.list file to change itself to the best/closest servers? If not, where can I get a "standard" copy of the sources.list file?

Thanks.

P.S.: Some googling suggested using apt-setup. I don't think that exists anymore.

---

### Post by drs305 on 2008-10-08
Synaptic, Settings, Repositories, Download From, Other. Click on that and then you can select "Best Server" or one closer to your location.

You can also get to the same menu via System, Administration, Software Sources on the main tab (Ubuntu Software), 'Download from'.

---

### Post by mc4man on 2008-10-08
Open software sources from system -> admin. On the main page expand the drop down 'download from',  look thru listings or open 'other'

---

### Post by Eto_Demerzel on 2008-10-08
Thanks. But there's something interesting. I opened my sources.list file and found that two lines have changed. It now says:

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates restricted main universe multiverse
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy main universe restricted multiverse

(It had given [http://archive.linux.duke.edu/](http://archive.linux.duke.edu/) as the best server)

The rest of the file is unchanged. Many servers mentioned there still say Gutsy Gibbon. (The Ubuntu 8.04 LTS which I have now is an upgrade over 7.10). That's why I wanted to create/make a "brand new" sources.list file. How do I do this?

---

### Post by bumanie on 2008-10-08
You could try to manually choose a different server - when I chose a 'local' server, the list changed completely other than a couple of entries re the main canonical servers.

---

### Post by drs305 on 2008-10-08
> **Eto_Demerzel said:**
> 
The rest of the file is unchanged. Many servers mentioned there still say Gutsy Gibbon. (The Ubuntu 8.04 LTS which I have now is an upgrade over 7.10). That's why I wanted to create/make a "brand new" sources.list file. How do I do this?

Here is the default Hardy 8.04.1 sources.list for an eastern US install. You can copy it and add any additional repos you have. When you change the server in synaptic or via software sources it will update the servers as well.

If you have the Medibuntu repo list in a separate file you should be ok, if it is listed in the main sources.list file you will have to add it.

You may also note that in your sources.list it still may list the original feisty cd-rom. Normally this is not updated if you do an on-line update. You probably won't want the first line of this sources.list as it references a 64-bit cd-rom, even though it is commented out. Use your existing one instead.

```

**#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted**
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by Sef on 2008-10-08
> Is there a default way to get the sources.list file to change itself to the best/closest servers? If not, where can I get a "standard" copy of the sources.list file?

Have you tried System > Administration > Software Sources > Ubuntu Software?

---

### Post by Eto_Demerzel on 2008-10-08
> Have you tried System > Administration > Software Sources > Ubuntu Software? 

Ya, I have, and I've checked all options too (main, universe, restricted, multiverse and source code)

> You may also note that in your sources.list it still may list the original feisty cd-rom. Normally this is not updated if you do an on-line update.

That's right, I'd done an online update. I do have the original cd-rom mentioned in my list. Thanks, drs305. 

Thanks, guys!

---

