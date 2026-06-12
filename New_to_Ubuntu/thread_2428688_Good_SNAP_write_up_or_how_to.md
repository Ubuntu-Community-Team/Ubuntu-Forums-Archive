---
title: "Good SNAP write up or how to"
date: 2019-10-07
forum: New to Ubuntu
---

### Post by jason.jackal on 2019-10-07
I am looking for a good SNAP write up or how-to. Very new to Ubuntu and SNAP.

Thank you

---

### Post by rbmorse on 2019-10-07
man snap really is a good place to start.  Whoever did the entry did a nice job and writes well.  I'm quite impressed.

---

### Post by TheFu on 2019-10-07
snaps are new to everyone. They should be optional, but Canonical decided to force them and there have been lots of workflow breakage due to this choice.

For 18.04 and earlier, it is still mostly possible to live snap free.

snapcraft.io is the main website.
There are a few different Ubuntu tutorials (those obnoxious step1, step2, step .... 15 wizard webpages. Google finds them easily.

I haven't read the snapd manpage, because if it shows up on my systems, I purge it.  When I can install VLC and have it work with all my other tools automatically on my desktop ,will read/play media files from anywhere on my network or on an external flash disk, then I'll know that the vlc snap is ready.  They aren't there and don't seem to be headed in that direction.

For now, **sudo apt purge snapd** is the easy answer. Don't know how well that will work for 19.10 and later. There have been statements made that Canonical will be only distributing some well-used packages as snaps going forward. If that is true, I'll miss Ubuntu.

---

### Post by PaulW2U on 2019-10-07
And when you've worked through the man page you can refer to the official snap documentation at [Getting started]("https://snapcraft.io/docs/getting-started") which should answer any remaining questions that you may have.

---

### Post by jason.jackal on 2019-10-07
> **PaulW2U said:**
> And when you've worked through the man page you can refer to the official snap documentation at [Getting started]("https://snapcraft.io/docs/getting-started") which should answer any remaining questions that you may have.

The snap link is what I needed, as you pointed out. I am reading the snap man today, so I am huddled down with my tea, lunch and Chrono Trigger OST playing.... LETS GO!!!

---

### Post by rpaco on 2019-10-07
Is there another version of Linux that does not use snaps? . I had to delete Firefox from Snap directory and reinstall in .mozilla to get flash to work.  Tried to do a backup, but it could not  access snap dir. So I will be looking elsewhere.

---

### Post by Skaperen on 2019-10-07
> **rbmorse said:**
> man snap really is a good place to start.  Whoever did the entry did a nice job and writes well.  I'm quite impressed.

all i saw was a reference document for a command.  why that was in chapter 8 is unknown to me.  i guess the web link is the next place to go.

> **PaulW2U said:**
> And when you've worked through the man page you can refer to the official snap documentation at [Getting started]("https://snapcraft.io/docs/getting-started") which should answer any remaining questions that you may have.

based on the contents list and not on reading straight through (because that much reading can take too much time so i want to optimize it an find the answers to my questions as directly as possible) this page is not the one to answer my main question.

i went to the [snapcraft.io]("https://snapcraft.io") website.  i followed along "Learn how to snap an app in 30 minutes", selecting my language (one of them is missing) and OS (Windows is "coming soon" and BSD is not even there, at all.  at least, Linux is there) but all i got were the steps to install some things.  i get to learn what i should only need to do once?

looks like i will need to learn to live with YAML.  won't happen!

my real questions are:

why?

what does snap give me (better) that other things do not give me (as good)?

where is a document that can justify why we should use snap?

---

### Post by Skaperen on 2019-10-07
> **PaulW2U said:**
> And when you've worked through the man page you can refer to the official snap documentation at [Getting started]("https://snapcraft.io/docs/getting-started") which should answer any remaining questions that you may have.


Slackware was not in the list on the website.

---

### Post by Skaperen on 2019-10-07
> **TheFu said:**
> There have been statements made that Canonical will be only distributing some well-used packages as snaps going forward. If that is true, I'll miss Ubuntu.

me. too.   but, at least, i know my way around Slackware, and a good amount of Centos (last job before retiring).

---

### Post by mastablasta on 2019-10-08
> **Skaperen said:**
> 
my real questions are:

why?

what does snap give me (better) that other things do not give me (as good)?

where is a document that can justify why we should use snap?

to me it gives the option to run the latest application on older version of the OS (the LTS). and a si understand you can also run an older version of the app on latest version of the OS. sometimes this is good to have especially with some games or if the features that changed you favourite app do not suite you.

for others: [https://ubuntuforums.org/newreply.php?do=newreply&p=13891079](https://ubuntuforums.org/newreply.php?do=newreply&p=13891079)
> **lammert-nijhof said:**
> Snaps
- do run on any distro, except the obsolete ones not supporting snaps (Ubuntu first support 14.04). 
- run sandboxed, so in a kind of container, 
- are more secure against attacks 
- can't crash the system 
- comes with its own package manager snapd
- runs from a kind of read only virtual disk.
- are updated automatically and only the modified parts of the virtual disk are sent.
- you will have the newest version of the App, also if for deb files only an older version is supported,
- full automatic and manual snapshot support and rollback to a previous version of that virtual disk
- have a central storage for distribution, to avoid websites that distribute malware.

Flatpack and Appimage are more vulnerable for attacks and both do not support snapshots. Flatpack only supports KDE, Gnome and FreeDesktop and their security is somewhat questionable. Appimage can be run on any distro by making the file executable, but then you have to add a link to the image in the menus or docks yourself. "Appimaged" should solve that, but than you have to install it like snapd. AppImage programs are not sandboxed.

---

### Post by jason.jackal on 2019-10-08
I noticed that snapd is installed by default on Ubuntu Server. Is this correct or did I mess something up? Still new to Linux and Ubuntu.

---

### Post by cruzer001 on 2019-10-08
yep

[https://packages.ubuntu.com/bionic/ubuntu-server](https://packages.ubuntu.com/bionic/ubuntu-server)

---

### Post by PaulW2U on 2019-10-10
> **jason.jackal said:**
> I noticed that snapd is installed by default on Ubuntu Server.
Presumably a default as many server users will want to take advantage of the [Livepatch]("https://ubuntu.com/livepatch") service which requires the installation of the 'canonical-livepatch' snap (for LTS releases). I think it's only the [flavours]("https://wiki.ubuntu.com/UbuntuFlavors"), apart from Ubuntu MATE, that don't now include the installation of snapd by default.

---

### Post by cruzer001 on 2019-10-10
I have removed snaps from the server edition, but I still have LivePatch.

---

### Post by PaulW2U on 2019-10-10
Obviously this thread has strayed well away from the original request for a link to good snap documentation so I apologise to the forum staff if I am taking this thread even further off-topic.

@cruzer001, how do you know you still have Livepatch enabled? What do you see that indicates patches have been applied to your kernel?

---

