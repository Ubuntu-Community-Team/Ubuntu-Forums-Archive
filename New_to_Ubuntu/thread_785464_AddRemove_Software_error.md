---
title: "Add/Remove Software error"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by mppareto on 2008-05-07
Hi fellow ubuntu guys,
this is my first time using linux and posting, so bear with me. Anyways, I've been trying to install some software using the "Add/Remove..." under Applications. I've done this several times to install and uninstall programs. However, just the other day I got an error, which still persists. It says:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.22.1.1-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.22.1.1-0ubuntu3_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)"



Trying to add packages using Synaptic Package Manager, I get this:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/indi_3.5.9-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/indi_3.5.9-0ubuntu2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars-data_3.5.9-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars-data_3.5.9-0ubuntu2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars_3.5.9-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kstars_3.5.9-0ubuntu2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



Any ideas what this could be?? Any help would be appreciated!


p.s. I'm using Ubuntu 8.04.

---

### Post by shifty_powers on 2008-05-07
what are you actually trying to install?

and have you tried apt-get on the command line?

```
sudo apt-get install package
```

---

### Post by muteXe on 2008-05-07
Or synaptic package manager from the menu, the gui version of apt-get?

---

### Post by shifty_powers on 2008-05-07
> **muteXe said:**
> Or synaptic package manager from the menu, the gui version of apt-get?

heh true. teach me to read the post properly, thought he had already used it...

plus if we know what you are trying to install, then we might be able to find a .deb file for it, to save you the hassle ;) Also does this happen with anything else you try to install or just this package?

in fact isn't there a ubuntu repository as a website, where you can get anything in the current hardy repo's? or am i imagining things?

---

### Post by mlentink on 2008-05-07
@mppareto: first of all: Welcome to the free world!

Do you remember what you installed recently? 

I see you've already tried Synaptic, which is basically the same as the 'apt-get ...' command in terminal. So you don't have to try that again. (doesn't hurt if you do).

---

### Post by muteXe on 2008-05-07
Oops it looked like I didn't read his post properly :)

---

### Post by bumanie on 2008-05-07
Go to System --> Software Sources and check the first four boxes and make sure the cd-rom box at the bottom is unchecked. Then go to third party software and check any boxes there. That should get you started. After that you should run > sudo apt-get update in terminal. Following that you should update your /etc/apt/sources.list

---

### Post by gandaran on 2008-05-07
I think you added a repository that synaptic cannot connect to, try disabling this repository or post the output of ' gedit /etc/apt/sources.list ' so we can look where the problem is.

---

### Post by mppareto on 2008-05-07
> **bumanie said:**
> Go to System --> Software Sources and check the first four boxes and make sure the cd-rom box at the bottom is unchecked. Then go to third party software and check any boxes there. That should get you started. After that you should run  in terminal. Following that you should update your /etc/apt/sources.list

Hey, thanks for the ideas, although still no luck.

I tried sudo apt-get update and I got the same errors. It also recommends me to run 'sudo apt-get update' to solve the problem - go figure *rolls eyes*. As for the "Software Sources" idea, all four of the top checkboxes are checked and the CD-rom is NOT checked.

ugh!

---

### Post by mppareto on 2008-05-07
> **gandaran said:**
> I think you added a repository that synaptic cannot connect to, try disabling this repository or post the output of ' gedit /etc/apt/sources.list ' so we can look where the problem is.

Here's the output. From what I recall from way back when in computer science, the "#" are comments, so all deb file thingies should be accessible. Here it is anyways:

<<Start File>>

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

<<End File>>

---

### Post by bumanie on 2008-05-07
What you have said is correct re # and your /etc/apt/sources.list looks OK to me. Sounds like an inability to get adequate connection to a server. May be you should try a different server. Go back to software sources and click on the down arrow next to 'download from' and choose 'other'. Your computer is then scanned for the best/closest server to your location - I have had less problems with updates and downloading ubuntu software since changing to a closer server. Hope this works.

---

### Post by gandaran on 2008-05-07
looks okay, try clicking on does link's in your first post, download those files to you desktop, then double click on them to install, see if you can install them, I was able to!
I see you have the backporks repository enabled, the backports and proposed are not recommended.

---

### Post by mppareto on 2008-05-07
Tried to change server and still no luck - same error messages :-(

I wonder if my university (Boston University - where I pretty much only use this computer) has some firewall preventing this. I could try this at home tonight, although I think i did the other day and still no luck. I know my friend had issues with some file-sharing programs before, but that's another story...

---

### Post by gandaran on 2008-05-07
you can also use synaptic to remove broken packages, click on the filters button, see if anything there in the broken sector

---

### Post by mppareto on 2008-05-07
> **gandaran said:**
> you can also use synaptic to remove broken packages, click on the filters button, see if anything there in the broken sector

It seems I had no dependency issues. :-( I wonder if my port is blocked, so that it can't access it.

---

### Post by mlentink on 2008-05-07
> **mlentink said:**
> 
Do you remember what you installed recently? 

I am not at all convinced this would have something to do with your repo's or anything.
I would still like to know what you have installed (and configured) in those last add/remove sessions you were talking about.

---

