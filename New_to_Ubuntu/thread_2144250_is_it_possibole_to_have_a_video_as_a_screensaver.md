---
title: "is it possibole to have a video as a screensaver?"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-11
Hey guys. I wanted to know if it is possibole to have a video as a screensaver?

---

### Post by GameX2 on 2013-05-11
Apparently, yes, but I couldn't get it to work (Yet).  Install Xscreensaver:

```
sudo apt-get install xscreensaver
```

And put this code in your startup applications:

xscreensaver -nosplashCheck the FAQ for how to play a video clip:
[http://www.jwz.org/xscreensaver/faq.html#mpeg](http://www.jwz.org/xscreensaver/faq.html#mpeg)

---

### Post by ibjsb4 on 2013-05-11
This is dated, but may still be valid.  I have never tried it so can't say for sure.

[http://ubuntuforums.org/showthread.php?t=1368224](http://ubuntuforums.org/showthread.php?t=1368224)

---

### Post by DragonGirl123 on 2013-05-12
i installed xscreensaver ,but im confused on what should i do next.

---

### Post by pootan on 2013-05-12
I remember also you could do this through VLC somehow.

---

### Post by DragonGirl123 on 2013-05-12
> **GameX2 said:**
> Apparently, yes, but I couldn't get it to work (Yet).  Install Xscreensaver:

```
sudo apt-get install xscreensaver
```

And put this code in your startup applications:

xscreensaver -nosplashCheck the FAQ for how to play a video clip:
[http://www.jwz.org/xscreensaver/faq.html#mpeg](http://www.jwz.org/xscreensaver/faq.html#mpeg)
I dont understand the program prefrences thing i have to do , can somebody help?

---

### Post by zombifier25 on 2013-05-12
> **DragonGirl123 said:**
> I dont understand the program prefrences thing i have to do , can somebody help?

Well, once you installed xscreensaver, in your home folder there would be a hidden file called .xscreensaver that contains the screensavers config. Scroll to this part of the file, which contains the list of the screensavers (yours may differ):
```
blablabla
- GL:                           hilbert -root                               \n\
- GL:                           tronbit -root                               \n\
                                unicode -root                               \n\

```
See those entries ending with \n\? Those are the screensavers. What you need to do is add a new entry to the end of the list, like that page says:
```
     "My Movie"  mplayer -really-quiet -nosound -nolirc          \
                   -nostop-xscreensaver                          \
                   -wid $XSCREENSAVER_WINDOW                     \
                   -fs -loop 0                                   \
                   $HOME/movies/my_movie.mp4                   \n\

```
Replace movies/my_movie.mp4 with actual link to the video file you want to play. Oh, and install MPlayer first if you haven't.

---

### Post by Merrattic on 2013-05-12
^^^ That works a treat. very clever :)

---

### Post by DragonGirl123 on 2013-05-13
> **zombifier25 said:**
> Well, once you installed xscreensaver, in your home folder there would be a hidden file called .xscreensaver that contains the screensavers config. Scroll to this part of the file, which contains the list of the screensavers (yours may differ):
```
blablabla
- GL:                           hilbert -root                               \n\
- GL:                           tronbit -root                               \n\
                                unicode -root                               \n\

```
See those entries ending with \n\? Those are the screensavers. What you need to do is add a new entry to the end of the list, like that page says:
```
     "My Movie"  mplayer -really-quiet -nosound -nolirc          \
                   -nostop-xscreensaver                          \
                   -wid $XSCREENSAVER_WINDOW                     \
                   -fs -loop 0                                   \
                   $HOME/movies/my_movie.mp4                   \n\

```
Replace movies/my_movie.mp4 with actual link to the video file you want to play. Oh, and install MPlayer first if you haven't.
Hello , sorry for the long time that took me to reply. First i wanted to say i did that and it is still a black screen.Also when i try to preview it ,it gets an error.Any help ? :(

---

### Post by DragonGirl123 on 2013-05-13
Anyone? :(

---

### Post by DragonGirl123 on 2013-05-13
Yay got it working :D

---

### Post by ibjsb4 on 2013-05-13
Want to tell us how and :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

