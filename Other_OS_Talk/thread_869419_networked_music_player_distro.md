---
title: "networked music player distro"
date: 2008-07-24
forum: Other OS Talk
---

### Post by kayakstudio on 2008-07-24
Hello,
I'm going to buy a single board computer (533Mhz with 256MB ram), small touch screen and speakers. I'm going to make a fiberglass box to put it in. I need to distro to install on it that will do nothing more than play music off a NFS server. the files are mostly MP3 and I hope to install the distro on a CF card. I've been searching good and can't find anything. I don't want to use a small distro and just have rythmbox or something playing. I'm looking for a single purpose distro. 

Do any of you know of any distros that do this?

thanks!

---

### Post by evets25 on 2008-07-25
I don't know of any distros that are specifically designed for this (although I'm sure they exist) but I do know of a music player called mpd that would be perfect for you. mpd is a music player that works using a server/client model. On a regular desktop, it runs as a system service, and you connect to it with a graphical client such as sonata, a good gtk front-end/client for mpd. It is perfectly suited to play music over a network, with the kind of situation you describe. See [here]("http://www.musicpd.org/") for more details.

---

