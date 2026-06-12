---
title: "Installing Software Offline"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by leftfootleashed on 2008-05-15
Hi,

I'm intending to upgrade from Gutsy to Hardy by way of a clean install. However, I've got a lot of software and such that I've gotten to like on Gutsy and want to take it with me. I'm loath to download it all again as my Internet connection has a very low download limit.
So basically, my question is:
**Can I back up installed packages to a second hard drive in order to instal them again without connecting to the Internet?**
or failing that:
**Is there a way I can download package installers onto a removable disk?**
i.e. using my university's bandwidth ;).

Thanks in advance,

Dave

---

### Post by RequinB4 on 2008-05-15
#1 is possible, but I couldn't give you a tutorial

for #2 - packages.ubuntu.com.  Make sure you get all the dependancies

---

### Post by Inxsible on 2008-05-15
> **leftfootleashed said:**
> Hi,

I'm intending to upgrade from Gutsy to Hardy by way of a clean install. However, I've got a lot of software and such that I've gotten to like on Gutsy and want to take it with me. I'm loath to download it all again as my Internet connection has a very low download limit.
So basically, my question is:
**Can I back up installed packages to a second hard drive in order to instal them again without connecting to the Internet?**
or failing that:
**Is there a way I can download package installers onto a removable disk?**
i.e. using my university's bandwidth ;).

Thanks in advance,

DaveI don't think backing up installed packages would help since you would be missing a lot of dependencies when you move to Hardy and you would have to download those latest packages anyway.

But I think you can download installers by using a flag in the aptitude (i think its download -- but please check the manpages to be sure) Once you download them on the university computer, you can move them to a removable disk.

---

### Post by Paqman on 2008-05-15
Sounds like you want [APTonCD](http://aptoncd.sourceforge.net/). It's in the repos.

---

### Post by leftfootleashed on 2008-05-16
Thanks for all your help. I think APTonCD is definately for me.

Cheers,

Dave

---

### Post by hyper_ch on 2008-05-16
all the downloaded packages are stored in /var/apt/.... (not at my computer right now).... so, just backup all the .deb files in there and next time just copy them back... you'll still need to install the packages but you won't be required to download them.

---

### Post by leftfootleashed on 2008-05-16
Further to my original question, I have some Kubuntu and Xubuntu live CDs that I used to check out KDE and Xfce desktops. I've decided to stick with GNOME for the moment, but I quite liked a couple of bits of software on KDE and Xfce. Is it possible to install this software from these CDs?

Thanks again,

Dave

---

### Post by shifty_powers on 2008-05-16
think so. you need to add by going into synaptic, settings, repositories, third party sources, add cd-rom... ;)

---

### Post by leftfootleashed on 2008-05-16
@ hyper_ch: Thanks, that would be useful to keep in mind - however, I can't find that directory. I have a /var/lib/apt but I can't find any .deb files in there. I'd appreciate it if you could find the exact directory and let me know. Cheers!

---

### Post by leftfootleashed on 2008-05-16
@shifty_powers: Thanks, works great. In fact when I put the CD in just now it detected the packages on it and opened the repository in synaptic for me.

---

### Post by hyper_ch on 2008-05-16
> **leftfootleashed said:**
> I'd appreciate it if you could find the exact directory and let me know. Cheers!

or you could try to find the exact directory yourself ;) already tried?

---

### Post by shifty_powers on 2008-05-16
heh glad to help. know what it's like when you don't have internet, dowesn't work on ubuntu ;)

---

### Post by leftfootleashed on 2008-05-16
@hyper_ch: Yeah I've already tried all the directories that look vaguely similar to your suggestion

@shifty_powers: Yeah, unfortunately Ubuntu treats the lack of an internet connection as an error - much like Windows Vista incidentally, which throws up errors when I try to use my router offline as a print server

---

