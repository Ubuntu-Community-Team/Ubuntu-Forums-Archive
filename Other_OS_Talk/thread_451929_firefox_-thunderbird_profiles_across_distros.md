---
title: "firefox -thunderbird profiles across distros"
date: 2007-05-22
forum: Other OS Talk
---

### Post by tchoklat on 2007-05-22
Hi,

I use Feisty after a short foray with Sabayon. I now am playing with a few other distros; Sam, PSLinuxOS, Fedora etc.

Question?

I want to share my Thunderbird and Firefox profiles that I have setup on my Ubuntu /home partition, but I am having issues. I think that I am doing it right;

Load alt distro
Open terminal
type firefox -profilemanager

... and set up the profile pointing to the /home profile created in Ubuntu. I do this also for Thunderbird. But it doesn't seem to work. Oddly it worked as sudo, then would not work if I ran the app without superuser privileges.

Am I missing something as I read posts that others have it up and running OK?


tchoklat

---

### Post by scrooge_74 on 2007-05-22
I dont know if it is the same.  The setup I had a while back was different distros in the same machine, but a single /home. Which all distros used.

I have also setup a dual boat in which the XP and Ubuntu all point to the same /home folder so if I read emails on XP they appear in the same place when I open them using Ubuntu

---

### Post by tchoklat on 2007-05-22
yeh that is i effect what I am doing. whilst I have different homes for each distro (don't know why I did that) the profiles all point to the one profile on the one /home which happens to be the Ubuntu home.

still doesn't work though, but thanks

tchoklat

---

### Post by scrooge_74 on 2007-05-22
you could change in fstab to which /home partition you are pointing in each distro, I think that would make things easier

---

### Post by rsambuca on 2007-05-23
I have a small FAT32 partition for my FF and TB profiles.  I share the profiles across XP, Vista, and four linux distros.  I just pointed the profiles to the same directory and it seemed to work fine.

---

### Post by tchoklat on 2007-05-23
yes I created a FAT 32 and moved my Ubuntu profiles there and have pointed the other distro's to there and all is kool. thanks guys!

Tchoklat

---

### Post by ThinkBuntu on 2007-05-23
Some name your Thunderbird folder .thunderbird, and others .mozilla-thunderbird. I imagine a symbolic link would take care of this pretty easily.

---

