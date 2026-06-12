---
title: "Anybody have advice for debian-etch sources.list?"
date: 2006-07-16
forum: Repositories &amp; Backports
---

### Post by tommcd on 2006-07-16
I hope nobody minds a debian question here. I have been using ubuntu for about 3 months ( and lovin' it!!). So I thought I would try my hand at a "hardcore" distro, so I installed debian etch on an old Emachines PC I use as a test box. The install went fine. My problem was when I need to set up a sources.list file. Debian has no noob-friendly synaptic package manager (at least as far as I know). I tried one that was suggested at debian forums but it broke my system (possibly because I used apt-get upgrade instead of apt-get dist-upgrade).

[http://forums.debian.net/viewtopic.php?t=7623](http://forums.debian.net/viewtopic.php?t=7623)

Anybody here ever use debian? Any advice for setting up a sources.list file to get multimedia codecs and media players via apt-get?
Any advice appreciated, as I am trying to learn as much as I can about linux, thanks!!

---

### Post by Jagot on 2006-07-16
Etch does come with Synaptic.

Look at the bottom of this page for repo's for multimedia, etc:

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

You may also want to have a look at this page:

[http://www.apt-get.org/](http://www.apt-get.org/)

You can search for any package you want and it will throw up a repo that you can add to obtain it.

---

### Post by tommcd on 2006-07-16
Awesome jagot!! Thanks!! I will try and reinstall etch again and I will add those repos to my sources.list file. That 2nd link you gave is great. Just type in a package and it spits out a repository! It's almost idiot-proof!!
Where in etch is synaptic? Is it under system>administration? Is it installed by default? I did not see it.

The ubuntu forums are the best! Thanks again!

---

### Post by nolihc on 2006-07-16
Do you have any idea what apt-get and the prompt do? Read a little about it or stay with ubuntu....

---

### Post by tommcd on 2006-07-16
> **nolihc said:**
> Do you have any idea what apt-get and the prompt do? Read a little about it or stay with ubuntu....

Not sure what you mean by that. Apt-get in debian  works the same as in ubuntu. Debian is not as noob-friendly as ubuntu, and the help you can get in these forums is great. Jagot's reponse to my question is proof of that. Nobody at debian forums gave those suggestions.
I have no plans to leave ubuntu. It's great IMO. I just want to try debian to learn more about linux.

---

### Post by tommcd on 2006-07-16
To read about apt-get:

[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by MetalMusicAddict on 2006-07-16
> **Jagot said:**
> Etch does come with Synaptic.

Look at the bottom of this page for repo's for multimedia, etc:

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

You may also want to have a look at this page:

[http://www.apt-get.org/](http://www.apt-get.org/)

You can search for any package you want and it will throw up a repo that you can add to obtain it.

Thanx Jagot. Im in the same boat as tommcd but I havnt installed yet.

---

### Post by Jagot on 2006-07-16
> **tommcd said:**
> Where in etch is synaptic? Is it under system>administration? Is it installed by default? I did not see it.

Yep - it should be there.  Failing that, whilst you're logged in as root hit alt+f2 and type synaptic.

It should be installed by default.  Etch is of course the testing version of Debian so sometimes packages don't get installed that should because of errors.  If what I've already said doesn't work then you should be able apt-get synaptic.

---

### Post by tommcd on 2006-07-16
Thanks again Jagot> I'll try that when I get debian reinstalled.

---

### Post by matthew on 2006-07-16
I have Debian Etch running on a test box...I don't think Synaptic was installed by default, but if you discover it is not installed all you need to do is use apt-get to install it. Here's a basic sources.list for you for Debian Etch (btw, if you're reading this and confused, do *NOT* use these repos for Ubuntu...you *WILL* mess up your installation.) Note the country code in this one. The server in France works best for me from Morocco. Use the country code nearest you if you can. (eg. us for USA, etc.)

```
deb ftp://ftp.fr.debian.org/debian testing main contrib non-free

deb http://www.debian-multimedia.org testing main
```

---

### Post by Jagot on 2006-07-16
Synaptic was installed for me when I did a network install of Etch, twice I think.

---

