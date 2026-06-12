---
title: "About Transmission"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-06
is there any transmission's tutorial out there?
Cos with googling, I found none.
Would you mind for doing a favor to me by showing me the place ...
Thank you.

---

### Post by Kopkins on 2012-07-06
You are talking about transmission bittorrent, correct? 

[Similar thread]("http://ubuntuforums.org/showthread.php?t=1226526"). Hopefully this helps. Try searching the forums too.

I learned how to use torrent software just by messing around with the programs. I think that's one of the best ways to learn. 

As a suggestion, I prefer deluge as a bittorrent client.

Kopkins

---

### Post by czgirb on 2012-07-06
I read that thread too before i post the thread ... and I found nothing.
All I want to know is:
* Seeing how many people are seeding
* And how many are Peering.
* How can I speed-up my Transmission? The maximum
* How can I restrict my uploading? The minimum

---

### Post by krustenBrot on 2012-07-06
In the lower left corner is a button shaped like a cog ( at leaast mine is). Click it and you can set the download & upload limits. You can also configure the button right next to it to have a desired speed profile.
The connected peers are shown right under the torrent.

Why don't you try another client if you are unsatisfied with Transmission. Have you read the alternatives in the [wiki]("https://help.ubuntu.com/community/BitTorrent/")?

---

### Post by blackbird34 on 2012-07-06
Once you are torrenting something, Transmission tells you how many are seeding and leeching on your torrent, under the torrent's progress bar...

To put your speeds up, go to edit > preferences > network > peer limits, and add more allowed peers. 
To restrict uploading, edit > preferences > speed, and change upload speed limits. This is a bit contrary to the whole idea of torrents (ie sharing), and i'm not even sure if it will make your torrent faster.... But if you want to do "hit and run" torrenting, so be it :D

Transmission's preferences go straight to the point, you'll find out everything there.

---

### Post by czgirb on 2012-07-07
A few days ago I tried to download 1GB+ file ... although it cost me 20-hours ... but it's done. Right now ... is my turn for being SEEDS.
But it said: **Seeding to 0 of 0 peers. Stalked.**
What should I do?
Am I allowed to **remove the torrent and delete the file** ???
I don't want to be a **leecher** ... it's allowed me to close my computer?

---

### Post by kdane4 on 2012-07-07
Hi,

If your client shows not seeding (you probably meant *stalled*), that means that probably no one is connected to you and downloading it.
Of course you can delete the torrent and file but its courtesy to leave it seeding everytime you turn on your computer maybe just for a few days so that other users who want that specific file will be able to download it too..

---

