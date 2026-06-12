---
title: "[SOLVED] Playine *.wmv files in 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by bob brazie on 2008-11-07
When I play *.wmv files using movie player the video is jerky and has white background flashes.

Is there a setting I am missing or just the application.

Maybe there is another application someone can suggest if this problem can't be fixed.

Thanks in advance. Bob.

---

### Post by Yuki_Nagato on 2008-11-07
I generally recommend VLC at this time.  I have the same problem, but I just use a different video player.

[http://www.videolan.org/vlc/]("http://www.videolan.org/vlc/")

---

### Post by bob brazie on 2008-11-08
Thanks for the suggestion. Anyone have any other ideas?

Why does the included movie player not work as it is suppost to and is there a way to make it work ?

Thanks in advance.

---

### Post by Steve1961 on 2008-11-08
> **bob brazie said:**
> Thanks for the suggestion. Anyone have any other ideas?

Why does the included movie player not work as it is suppost to and is there a way to make it work ?

Thanks in advance.

Yes there is.  First make sure you have added the medibuntu repository to your sources list.  see this [link]("https://help.ubuntu.com/community/Medibuntu")

Next, open a terminal and copy and paste this command into it:

```
sudo apt-get install w32codecs totem-xine
```

Once that command completes copy and paste this command

```
sudo update-alternatives --config totem
```

Select the entry for /usr/bin/totem-xine, probably by entering a number 2.

That should be it.  Totem will now use xine as it's backend rather than gstreamer, which tends to work much better.

---

### Post by bob brazie on 2008-11-08
I am undderstanding all of this but I do not find a "medibuntu repository" area in the "software sorces" area. Yes I did read the link you provided. <g>

I am new to Linux and am an old dos/windows guy looking for a good change.

Thanks in advance. Bob.

---

### Post by Chunky Dunk on 2008-11-08
Run this command to add the medibuntu repository: 
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

More info here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Steve1961 on 2008-11-08
And once you've ran the command in the above post, run this one as well:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Just copy and paste into the terminal and hit enter.  That's it, now follow the instructions in my previous post and you should be good to go

---

### Post by bob brazie on 2008-11-08
this is what I ended up with and it dowsn't look right to me. <g> There was no number 2 to choose. What do you think?

bob@ubuntu:~$ sudo apt-get install w32codecs totem-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
bob@ubuntu:~$ sudo update-alternatives --config totem
update-alternatives: internal error: /var/lib/dpkg/alternatives/totem corrupt: invalid update mode
bob@ubuntu:~$

---

### Post by Steve1961 on 2008-11-08
It's because medibuntu has not yet been added.  OK, lets try this.  From the menu open System/Administration/Software sources.  Click on the Third party software tab and make sure the medibuntu repository is there and ticked.  If not, try this way.

```
sudo gedit /etc/apt/sources.list
```

once this opens add these lines to the bottom of the file:

```
deb http://packages.medibuntu.org/ intrepid free non-free
```

Save and close.  Now go back to the terminal and paste this line in:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Hit enter and that should do it.  You obviously need to be connected to the internet for this to work.

Now paste the following command in:
```

sudo apt-get update
```

If the update works without errors you should now be able to follow my previous post and install totem-xine and w32codecs

---

### Post by sdowney717 on 2008-11-08
VLC just works better than totem-anything, especially in full screen.
I have let the totem-mozilla plugin remain. I used to use mplayer and every dist upgrade puts it back in.

IF you are running compiz, you likely need to change video output to use x11 to get rid of flashing

---

### Post by Steve1961 on 2008-11-08
Agreed, vlc works best.  That said, gnome-mplayer is coming along as well.

---

### Post by bob brazie on 2008-11-08
This looks like an eror to me. Waht do you think?

Fetched 6923kB in 57s (120kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
bob@ubuntu:~$

---

### Post by Steve1961 on 2008-11-08
> **bob brazie said:**
> This looks like an eror to me. Waht do you think?

Fetched 6923kB in 57s (120kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
bob@ubuntu:~$

So medibuntu was installed after all.  OK, backtrack and remove the medibuntu entry from /etc/apt/sources.list.  Then just try going to System/Administration/Synaptic Package Manager.  Update the cache and search for the packages w32codecs and totem-xine in the gui.

I've just done a clean install of Intrepid on my son's laptop and guarantee those packages are there.

---

### Post by bob brazie on 2008-11-08
They both show up when I clik the w32 codecs nothing shows in the package to update.

When I try to check for install the totem-xine I get this message:

totem-xine:
 Depends: libxine1 (>=1.1.8) but it is not installable
 Recommends: libxine1-ffmpeg  but it is not installable
 Recommends: libxine1-gnome  but it is not installable

---

### Post by Steve1961 on 2008-11-09
This is a really strange one.  When you run sudo apt-get update in a terminal does it complete without errors?  When you open the sources list with sudo gedit /etc/apt/sources.list is everything uncommented (doesn't have a # in front of it) except for bacckports?

---

### Post by bob brazie on 2008-11-09
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by Steve1961 on 2008-11-09
Back that up and replace the contents with the sources.list posted here:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Manual_Method_for_Adding_Repositories)

Then run sudo apt-get update again

Alternatively just edit this section:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted

and make it look like this:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

and remove the comments from this section:

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

Just the deb lines, not the text lines

---

### Post by bob brazie on 2008-11-09
Wow, I think this is too much for me. I can't find some of thoese lines.

Maybe it would be easyer to do a new install and then start this thread again? <g>

---

### Post by Steve1961 on 2008-11-09
For some reason you're sources.list doesn't contain what it should, and that's why you've been having problems.  If you're struggling with the command line stuff try going to system/administration/software sources.  On the ubuntu software tab make sure there's a tick in every box, which 'should' do the job.  There's no need to reinstall.

---

### Post by bob brazie on 2008-11-09
Thanks what should the download from be set to?

I just installed 8.10 on another machine to run inside windows and installed the movie player and my *.wmv files are playing jsut fine.

---

### Post by Steve1961 on 2008-11-09
> **bob brazie said:**
> Thanks what should the download from be set to?

I just installed 8.10 on another machine to run inside windows and installed the movie player and my *.wmv files are playing jsut fine.

The default download location is generally fine, but you can also set it to a specific country if you wish.  It really doesn't matter, but the nearer the location the faster the speed should be.

---

### Post by bob brazie on 2008-11-09
Thanks to eve3ryone on this one!

---

