---
title: "Splash Screen not loading properly"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-11
Hello all

After a recent update from 12.04 LTS to 14.04 LTS my Ubuntu Splash Screen takes a lot longer to load and this screen shows instead:

[[IMG]http://s7.postimg.org/ldyz0qodz/IMAG1769.jpg[/IMG]]("http://postimg.org/image/ldyz0qodz/")

...then eventually this splash shows for about 1 second (below) and I'm then into the OS. You may notice the splash seems to be done in some kind of raw text, rather than the Ubuntu themed splash too:

[[IMG]http://s22.postimg.org/ygg8qt11p/IMAG1770.jpg[/IMG]]("http://postimg.org/image/ygg8qt11p/")

After checking online this does not seem to be normal behaviour, so could anyone advise as to why this is happening or better yet how to solve it?

Danke

---

### Post by Dennis N on 2014-05-11
There is a **ubuntu-text** Plymouth theme that is used when the default theme with graphics cannot be. That is what you are seeing. I also developed this problem on a computer having Nvidia graphics after installing Xubuntu 14.04, where the default theme (with graphics) worked previously. Other graphics systems (Intel, AMD) that I use continue to employ the regular splash theme with 14.04.

I removed the word 'splash' from the grub boot line and it boots with a black screen up to the log in screen. That is an option.

If you want to try for the regular splash screen, there are quite a few purported solutions: google "fix plymouth splash nvidia". I have no recommendation on these. Many are old, so consider that.

---

### Post by Drowz0r on 2014-05-12
Yeah I've noticed a Lubuntu machine have the same issue, while a different Lubuntu machine not, so it seems Ubuntu and varient related...

That makes sense, the machines showing the ubuntu-text have NVIDIA cards, while the other machine is a laptop with on-board AMD graphics.

Yeah I saw an absolute feast of threads for 10.04 and such, searching in "Plymouth theme" gives me better results though. Thanks :D

---

### Post by Drowz0r on 2014-05-13
Just posting if anyone needs and marking thread as solved, here is the solution:

[http://youtu.be/1jIegOR6A0M](http://youtu.be/1jIegOR6A0M)

---

