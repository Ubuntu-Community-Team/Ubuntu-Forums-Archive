---
title: "Having a load of trouble."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by rokumanxes on 2008-04-29
So, I finally got my wireless working last night, so I was pretty happy about that.  I got my graphics card sorted out too.
Just when everything was looking up...

Stuff went screwy.

My laptop shut off last night.
I apparently didn't turn it off like I meant to, silly me.

Well, I started it up, and noticed the top bar was...
Funky.

The order was all off, and such.  Something came up, said there was an error, and said something about the synaptics package manager.

I couldn't get it to connect either, so...  I wasn't happy about that really.

I clicked to go to the synaptics package manager, and this showed up:
[IMG]http://img.photobucket.com/albums/v682/1charmed1/Screenshot.png[/IMG]

Um...  Help?

Totally new here....
:confused:

---

### Post by wannadumpwindows on 2008-04-29
Open a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

And then paste the output here.

---

### Post by rokumanxes on 2008-04-29
[QUOTE=Sources.list]# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
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


deb [http://repository.debuntu.org/feisty](http://repository.debuntu.org/feisty) multiverse
deb-src [http://repository.debuntu.org/feisty](http://repository.debuntu.org/feisty) multiverse[/QUOTE]

Okay then....

---

### Post by aheckler on 2008-04-29
Do "sudo gedit /etc/apt/sources.list" and take out the last two lines of that file. Then save and close. Then run "sudo apt-get update" and you should be good to go.

---

### Post by wannadumpwindows on 2008-04-29
It looks like you need to delete the last two lines. They are repos for feisty. The first one is line 59, the one that the message says is causing the issue. But both repos are for feisty fawn AKA Ubuntu 7.04

---

### Post by wannadumpwindows on 2008-04-29
After that, in a terminal type

```
sudo apt-get update
```

Sorry for the extra post.

---

### Post by rokumanxes on 2008-04-29
> **wannadumpwindows said:**
> After that, in a terminal type

```
sudo apt-get update
```

Sorry for the extra post.

Thanks everyone, it worked, but... To avoid making another topic...

Can anyone help me restore the ORIGINAL top bar?
I'd like it all back... if possible...

---

### Post by wannadumpwindows on 2008-04-29
Right click on the bottom one, and click add new panel. And then you can add all your stuff back to it, and move it anywhere you want.

---

