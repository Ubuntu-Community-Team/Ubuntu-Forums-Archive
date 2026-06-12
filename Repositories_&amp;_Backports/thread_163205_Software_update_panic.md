---
title: "Software update panic"
date: 2006-04-20
forum: Repositories &amp; Backports
---

### Post by nighttime on 2006-04-20
Ok, I've been happily using ubuntu in my 900MHz Intel celeron µP with a P6STB ECS motherboard for a while now.

See, the thing is, I have screwed up other ubuntu installations in the past by installing software from weird repositories (all of them from ubuntu). But that was because I altered my /etc/apt/sources.list file and didn't bother changing it back to the original (I was young and unexperienced...).

The whole panic thing comes from the fact that yesterday when I was installing these updates:

firefox
lightweight web browser based on Mozilla

New version 1.0.8-0ubuntu5.10


firefox-gnome-support
Support for Gnome in Mozilla Firefox

New version 1.0.8-0ubuntu5.10


python-vte
Python bindings for VTE widget set

New version: 1:0.11.15-0ubuntu3


update-manager
GNOME application that manages apt updates

New version: 0.42.2ubuntu12~breezy1

My monitor just went black. The computer was still on, I could hear the fan so it wasn't a power failure, I also tested the monitor with my other computer and it worked perfectly. The keyboard wasn't working (I tried ctrl-alt-deling) and when I tried to turn off the computer by force it just wouldn't respond. I had to use the power supply switch on the back...

Then I tried turning it back on... nothing. The box's front panel LEDs did light up, so did the CD drive's, but I heard no beep and the monitor was all black. This is exactly what happened to one of my other computers (which got messed up when I installed some updates), except that other one had a... 'promiscuous' sources.list and instead of the monitor going black during software updating, it froze, when I turned it back on it gave me a "kernel panic" error, I turned it off and on again and It had died, I mean, really died! the motherboard got messed up, I know because I tested it with other hardware, another HD, another µP, other RAM and nothing (I even took it to a friend's place where they fix motherboards and he told me it would be cheaper to buy a new one, I know, I know, but he's my friend and I trust him).

Now, my computer, the one that went black, it turned on normally after an hour or two of inactivity (phew!). I'm using a standard sources.list with this one, yes I have meddled with it a little but I made a backup and I turn it back to normal when I'm done downloading software from non-standard repositories. I have lost much faith in ubuntu since this happened because I'm doing normal updates with a normal sources.list and still getting this problem, I don't wanna be afraid every time I download software updates.

Anyway, I trust that my sources.list is standard, but in case there's something weird with it, here it is:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://mx.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://mx.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://mx.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

I added some multiverse repositories but they're commented out.

Anyway, I would like to know if the updates I mentioned earlier are standard, tested, safe ones. Im not installing them until I'm sure they're ok to install, don't want what happened yesterday to happen again.

Thanks in advance for your help.

---

### Post by nighttime on 2006-04-22
Oh well, I can't wait forever for an answer. I'll just install the updates and hope for the best. If this computer gets screwed up too because of this I'm switching distros and giving ubuntu bad references every time somebody asks.

Maybe you think I'm speculating when I say it's because of the updates that my machines have been dying, but It's been too many "coincidences", I mean, it's allways while the updates are installing or after they do that my computers have crashed.

Anyway... wish me luck.

---

