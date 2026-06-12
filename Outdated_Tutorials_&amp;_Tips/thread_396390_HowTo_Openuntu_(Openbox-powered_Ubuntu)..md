---
title: "HowTo: Openuntu (Openbox-powered Ubuntu)."
date: 2007-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by moore.bryan on 2007-03-29
After searching around for quite some time and never finding a post or thread that completely answered my questions (and pushed forward by needing to completely reinstall my system), I thought this guide might be something useful to others.

I make no claims of being an expert on this, but I know it works on my machine because I used it last night to fix everything.  If you choose to try this out, this guide (just as with Ubuntu) carries no warranty or promise of working.  I would love any feedback from the community on how to make this HowTo better, though.  What I don't want to see happen is a thousand programs being added in this or lengthened past, maybe, 12-or-so steps.

====================

Step 1: Make sure to grab the "Server Edition" CD/DVD because we're not going to be installing the full system.

Step 2: When you restart the computer, log-in to the command-line interface (CLI) with the username and password you created during installation.

Step 3: Edit your repositories (repos) list so you can have access to all the programs available.
```
sudo nano /etc/apt/sources.list
```Replace all text in the sources file with the following:
> 
## BACKPORTS
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## BASE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## UPDATES
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## MOBLOCK
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
Step 4: We now need to make the advanced packaging tool (APT) read the new repos and upgrade any files already on the system if need be.
```
sudo aptitude update && sudo aptitude upgrade
```Step 5: Now, we want to install those programs which are necessary (or at least useful) for functionality.  I know some of these programs are not fundmental, but I find them irreplaceable.
```
sudo aptitude install --with-recommends x-window-system-core xserver-xorg xbase-clients make xfe openbox obconf menu ivman aterm iceweasel sylpheed audacious audacious-plugins adesklets libimlib2 openoffice.org xine deluge debhelper python-dev libx11-dev libxft-dev libxpm-dev libimlib2-dev dpatch python-central
```
Step 6: The PyPanel version in the repos is somehow broke, so you need to install it by hand; not a problem, just download the Python-Xlib tarball from [here]("http://sourceforge.net/projects/python-xlib/") and PyPanel-2.4 from [here]("http://sourceforge.net/projects/pypanel/").  Extract both by 
```
tar -xvzf python-xlib-0.13.tar.gz && tar -xvzf PyPanel-2.4.tar.gz
```and then install both with:
```
cd python-xlib-0.13 && sudo python setup.py install && cd ..
cd PyPanel-2.4 && sudo python setup.py install && cd ..
```Step 7: Since this is a bad, bad world full of dangers, now we'll install a firewall.  *Ubuntu-Firewall* is the most comprehensive and configurable firewall for Linux, in my opinion.  Make sure to the view the README, since it contains all the details.  Download the package from [here]("http://rob.pectol.com/ubuntu-firewall.tgz"), then
```
sudo tar -xvzf ubuntu-firewall.tgz && cd ubuntu-firewall
sudo chmod 755 ubuntu-firewall-installer.sh && sudo ./ubuntu-firewall-installer.sh
```Step 8: To keep those prying government eyes off your stuff, download and install MoBlock.  First, get [this]("http://www.ubuntuforums.org/attachment.php?attachmentid=20162&stc=1&d=1164741758") package and then [this]("http://http://www.ubuntuforums.org/attachment.php?attachmentid=20163&stc=1&d=1164741758") one, installing the libnfnetlink1 first; then:
```
sudo gpg --keyserver subkeys.pgp.net --recv DEDA0559 && sudo gpg --export --armor DEDA0559
sudo aptitude update && sudo aptitude install --with-recommends moblock-nfq
```Step 9: Reboot by
```
sudo reboot
```Step 10: Log-in to Openuntu (Openbox-powered Ubuntu) and start the graphical interface with:
```
startx
```

---

### Post by sabitha on 2007-03-30
any screenshot ? :D

---

### Post by frodon on 2007-03-30
Why all these extra repositories ? not sure that every user who follow this guide want them.

Do you know that PLF no longer exist BTW ?

---

### Post by moore.bryan on 2007-03-30
> **sabitha said:**
> any screenshot ? :D
[I]not yet... haven't had time to make it look pretty.
;-)
[/I] > **frodon said:**
> Why all these extra repositories ? not sure that every user who follow this guide want them.
Do you know that PLF no longer exist BTW ?
*when i first started ubuntu, i got sick an tired of not being able to install things, only to later find out it was because i didn't have the repos; this way, most repos are already there.  i got the repo list from the [ubuntu edgy user guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") .*

---

### Post by popey on 2007-04-03
I'm replying to this thread to highlight a pending name clash.

I recently started a project called Obuntu (not based around Openbox) which of course conflicts with the name you have given your Openbox derivative of Ubuntu.

I've created a bunch of wiki pages, a launchpad team, project and repository for our project, and having googled around at the time I didn't see any reference to obuntu anywhere so figured the name was "free" as such.

I'd like to open the discussion about what we do about this. I am not suggesting either of us change name initially, just that we start talking to eachother so nobody gets annoyed later on down the line.

Suggestions welcome.

---

### Post by moore.bryan on 2007-04-04
> **popeydc said:**
> I'm replying to this thread to highlight a pending name clash.

I recently started a project called Obuntu (not based around Openbox) which of course conflicts with the name you have given your Openbox derivative of Ubuntu.

I've created a bunch of wiki pages, a launchpad team, project and repository for our project, and having googled around at the time I didn't see any reference to obuntu anywhere so figured the name was "free" as such.

I'd like to open the discussion about what we do about this. I am not suggesting either of us change name initially, just that we start talking to eachother so nobody gets annoyed later on down the line.

Suggestions welcome.
[I]popeydc... 

i checked-out your stuff and it looks awesome!  i have no problem changing the name; mine was chose randomly and with little thought, yours seems to have been well-constructed.

thanks for giving me the heads-up... that was a very gentlemanly move.
[/I]

---

### Post by moore.bryan on 2007-04-04
*could a mod please rename this thread from "HowTo: Obuntu (Openbox-powered Ubuntu)" to "HowTo: Openuntu (Openbox-powered Ubuntu)"...*

---

### Post by popey on 2007-04-04
That's very good of you, we do appreciate it.

All the best!

:)

---

### Post by headshredder on 2007-05-27
Just a little tip for all you Openbox-users...

When you install Docker en run a WM-applet like wmfire or wmclock, it integrates very neatly onto your desktop. Try it.

[ATTACH]33629[/ATTACH]

---

