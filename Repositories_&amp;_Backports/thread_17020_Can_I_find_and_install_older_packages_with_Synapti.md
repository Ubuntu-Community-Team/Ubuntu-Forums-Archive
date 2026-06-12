---
title: "Can I find and install older packages with Synaptic? (Xfce4)"
date: 2005-02-25
forum: Repositories &amp; Backports
---

### Post by Sleeper Service on 2005-02-25
Hi -

I've got Xfce4.1.99(4.2RC2) working fine right now.  But there are a couple of essential things which actually I prefered in 4.0.6 (which was the most up-to-date package i could install with urpmi when I was using Mandrake).

So the question is - is there an easy way for me to get Xfce4.0.6 installed under Ubuntu when the only option I can find with Synaptic is 4.1.99?

---

### Post by bored2k on 2005-02-25
[QUOTE=Sleeper Service]Hi -

I've got Xfce4.1.99(4.2RC2) working fine right now.  But there are a couple of essential things which actually I prefered in 4.0.6 (which was the most up-to-date package i could install with urpmi when I was using Mandrake).

So the question is - is there an easy way for me to get Xfce4.0.6 installed under Ubuntu when the only option I can find with Synaptic is 4.1.99?[/QUOTE]


you will have to look for the apt repository that contains that version you desire
after that u can simply add it in the synaptic repository and block the ubuntu sources until the install so it doesnt collide with ur sources.

---

### Post by Sleeper Service on 2005-02-26
[QUOTE=bored2k]you will have to look for the apt repository that contains that version you desire[/QUOTE]Thanks.  I'll have a go at that.  Any pointers on where to start looking?  I don't know much about the available apt repositories...

---

### Post by Sleeper Service on 2005-02-26
forget that post - I've answered my own question:

[http://www.apt-get.org/](http://www.apt-get.org/) has a searchable database of all the repositories.  Search for the package you're after and it gives each known repository with details of what to put in /etc/apt/sources.list

I'm starting to like apt-get even better than urpmi - just like y'all said I would :)

---

### Post by bored2k on 2005-02-26
[QUOTE=Sleeper Service]I'm starting to like apt-get even better than urpmi - just like y'all said I would :)[/QUOTE]


 :-D 

urpmi has nuffin on apt-get btw, on my short "debian" vacation mostly on mdk 10 [and suse and auroX 10 and slackware 10]  the reason that kept me going back to debian  was good ol` apt-get . not even with [easy urpmi](http://easyurpmi.zarb.org/) was mandrake any fun...


anyways, thanks for posting that apt-get site, i hav nvr really looked 4 any debian apt site as i left that for mdk's urpmi and suse's yast and aurox's yum and whatnot ...

---

