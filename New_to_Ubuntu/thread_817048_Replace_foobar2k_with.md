---
title: "Replace foobar2k with?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by D.Sync on 2008-06-03
I had been trying to replace foobar2k with media player for Linux such as 'Amarok', 'Banshee' and even 'Rhythmbox'. So far I had been quite satisfied with Rhythmbox but it rescans my music directories everytime I load it. For a vast music directories of 639 albums, it isn't an ideal choice for me. Besides, I already tagged all those album titles correctly and they can be viewed just fine on foobar2k. However, some of those albums title seems to be wrongly displayed (it seems like Rhythmbox is trying to modify the album title itself) on Rhythmbox. For example, an album title named 'Naruto OP & ED Single' which viewed just fine at foobar2k might be displayed at 2 albums with 'Naruto OP & ED Single' and 'Naruto OP & ED'. Kinda weird eh?

I would like a media player that can organize my vast music collection just fine with crossfading features. Any additional features such as 'mixer' will do just fine.

Hopefully you can share your thoughts with me. :)

---

### Post by eriqjaffe on 2008-06-03
I think a combination of MPD as the database back-end and a GUI front-end like Sonata or GMPC would be good.

It can be a little tricky to configure, but it works very well.  I have over 20,000 tracks and it runs without a hiccup.

---

### Post by D.Sync on 2008-06-03
How does they work? Why does it need me to connect?

---

### Post by eriqjaffe on 2008-06-03
It's a client-server setup.  MPD runs in the background as the server, and requires something to connect with it to play.  You can, if you are so inclined, connect to and play from MPD from any PC on your local network.

That being said, it's actually a very lightweight solution, and MPD handles large databases *very* efficiently.

---

### Post by Inxsible on 2008-06-03
If you are looking for a lightweight music player, do check out cplay. Its in the repos and can be installed by```
sudo aptitude install cplay
```Its a terminal based player. Here's K.Mandla's [blog]("http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/") on how to use it. I find it to be awesome, given the fact that I can ssh into my Linux box from any other machine and start up the music -- without having to walk over.

Yeah..I'm lazy....tell me about it !!!!


BTW...mpd is also lightweight...and you can use a GUI client on it... I don't think you can do that with cplay.

All good choices :)

---

### Post by rudihawk on 2008-06-03
I give a vote for exaile. Its like amarok, however it is much faster I feel.

---

### Post by SunnyRabbiera on 2008-06-03
Most players in linux emulate either winamp or itunes I am afraid as they are the most popular ones.
Now me I swear by amarok, it doesnt look very good in its initial setup but can be improved.

---

### Post by D.Sync on 2008-06-03
I'm currently using MPD + GMPC. Song playback is really fast and the transition from song to songs are continuous without any hiccup. 

However, I have some simple question about configuring GMPC [here]("http://ubuntuforums.org/showthread.php?t=817207"). Hopefully got solution?

Btw, I had tried Amarok before and it took up most of my computer resources since I have a 40k / 399+ albums with me. GMPC do the best.

---

### Post by SunnyRabbiera on 2008-06-03
did you try exaile yet?
banshee is another good one to try.

---

### Post by D.Sync on 2008-06-04
I had tried Exaile but it lacks several features:
-> no crossfading support
-> when I double click on an album, it add those tracks to a playlist instead of displaying the tracks only for the album.

---

