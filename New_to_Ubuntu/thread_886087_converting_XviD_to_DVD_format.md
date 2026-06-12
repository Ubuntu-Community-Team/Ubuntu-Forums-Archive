---
title: "converting XviD to DVD format"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by jethier on 2008-08-10
How do I convert XviD into a format watchable on my hard drive?

---

### Post by kahlil88 on 2008-08-10
Unless you plan to burn the video to a DVD, there is no point in converting it. Just install VLC and/or MPlayer and you should be good to go. I can't really remember which codecs (if any) are necessary to play XviD, but let's take this one step at a time - **sudo apt-get install mplayer**

---

### Post by spiderbatdad on 2008-08-10
mencoder
[http://www.linux.com/feature/121385](http://www.linux.com/feature/121385)
There is also a gui for mencoder: gmencoder...you have to install libgnomeui-dev and libgnomeui-32. I haven't had much luck using gmencoder yet, but I've only tried it on the Intrepid alpha release. It keeps crashing on me...probably will run fine on hardy. mencoder from the cli can do just about anything media wise, if you have the patience to read the guide.

---

### Post by jethier on 2008-08-10
> **kahlil88 said:**
> Unless you plan to burn the video to a DVD, there is no point in converting it. Just install VLC and/or MPlayer and you should be good to go. I can't really remember which codecs (if any) are necessary to play XviD, but let's take this one step at a time - **sudo apt-get install mplayer**


Thanks. worked just fine, all the different files in the folders through me off, but when i clicked the first file the movie started playing and has been fine so far.

What I'm used to seeing is an .avi file that you click and away it goes.

---

### Post by jethier on 2008-08-10
> **spiderbatdad said:**
> mencoder
[http://www.linux.com/feature/121385](http://www.linux.com/feature/121385)
There is also a gui for mencoder: gmencoder...you have to install libgnomeui-dev and libgnomeui-32. I haven't had much luck using gmencoder yet, but I've only tried it on the Intrepid alpha release. It keeps crashing on me...probably will run fine on hardy. mencoder from the cli can do just about anything media wise, if you have the patience to read the guide.

Thanks for the web site, looks informative.

---

### Post by Pro-reason on 2008-08-10
> **jethier said:**
> How do I convert XviD into a format watchable on my hard drive?

Your title and the body of your message ask two completely different questions.

If you want to be able to view stuff, I advise you to enable the Medibuntu repositories and then go into Synaptic and install the package "*non-free-codecs*".

If you want to burn a DVD so that you can watch it on your TV set and DVD player, then there is different software for that, also available in Synaptic.

---

### Post by jethier on 2008-08-10
> **Pro-reason said:**
> Your title and the body of your message ask two completely different questions.

If you want to be able to view stuff, I advise you to enable the Medibuntu repositories and then go into Synaptic and install the package "*non-free-codecs*".

If you want to burn a DVD so that you can watch it on your TV set and DVD player, then there is different software for that, also available in Synaptic.

Yes, two different questions. All figured out now.

---

