---
title: "Real or unreal trafic shaping"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by nnjond on 2008-07-07
Hi, can anyone help me?

I'm downloading a large file at a very low rate, but I can surf and dl from Ubuntu, for instance on top, at a normal rate? Is my traffic being "Shaped"? Can I do anything about it?

---

### Post by AOZ on 2008-07-07
What are you downloading if i may ask?

---

### Post by nnjond on 2008-07-07
Another  suite of .AVIs with adequate seeds it seems.

---

### Post by AOZ on 2008-07-07
lol

---

### Post by nnjond on 2008-07-07
???

---

### Post by AOZ on 2008-07-07
ok seriously
what are you using to download and from what server, maybe its not you

---

### Post by jamesrfla on 2008-07-07
You might be able to download a torrent for that file so the download will be quicker.

---

### Post by AOZ on 2008-07-07
and if you are using torrents, try to find another with more seeds

---

### Post by nnjond on 2008-07-07
I'm halfway dl a large file using Transmision. How can I switch without having to start again?

---

### Post by AOZ on 2008-07-07
well you cant because the other torrent is an entirely different file. i suggest coninuing the current download as well as starting the faster one. if you dont have any bandwidth to spare than uv gotta guess which will be fatser, startign a new fatser one or contiuning the slow one.

---

### Post by AOZ on 2008-07-07
oh i think theres also an option in transmission to pause and search for more seeds. you might wanna try that before anythgin else

---

### Post by chalewa on 2008-07-07
are your ports forwarded?

---

### Post by aktiwers on 2008-07-07
I found [deluge-torrent ]("apt:deluge-torrent")to be the best in encrypting traffic to bypass package shaping.
Install it, go to properties and enable all encrpytion and set them all to "force".

This way I can bypass package shaping at my home

---

### Post by jamesrfla on 2008-07-07
I get it! In Transmission Bittorrent Client they use seeds instead of torrents.

---

### Post by S1xp4ck on 2008-07-07
> **nnjond said:**
> Hi, can anyone help me?

I'm downloading a large file at a very low rate, but I can surf and dl from Ubuntu, for instance on top, at a normal rate? Is my traffic being "Shaped"? Can I do anything about it?


Are you using a router?  If yes, have you ensured that your TCP port is open and receiving?  You may need to port forward to your router.

---

### Post by chalewa on 2008-07-07
> **aktiwers said:**
> I found [deluge-torrent ]("apt:deluge-torrent")to be the best in encrypting traffic to bypass package shaping.
Install it, go to properties and enable all encrpytion and set them all to "force".

This way I can bypass package shaping at my home

eh personally i think that they all work pretty well, that being said, i swear rtorrent works consistently better for me.

---

### Post by AOZ on 2008-07-07
> **jamesrfla said:**
> I get it! In Transmission Bittorrent Client they use seeds instead of torrents.

?

---

### Post by aktiwers on 2008-07-07
Really Deluge is the one that works best on my traffic shaping. Like 2x better than other clients

---

### Post by jamesrfla on 2008-07-07
> **AOZ said:**
> ?

You keep talking about seeds. What are they???

---

### Post by S1xp4ck on 2008-07-07
Seeders are people that have the full file and are sharing it.  Peers or "leechers" are those downloading but do not have the full file.

---

### Post by AOZ on 2008-07-07
seeders are users that have that torrent file completely downloaded on their system and are logged into a torrent client. They "seed" you the data/music/watever. The more seeds you have the faster your dl will be

---

