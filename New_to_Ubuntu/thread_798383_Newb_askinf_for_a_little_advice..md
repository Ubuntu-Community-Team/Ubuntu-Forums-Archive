---
title: "Newb askinf for a little advice."
date: 2008-05-18
forum: New to Ubuntu
---

### Post by fubared259 on 2008-05-18
I was looking for anything that will help customize my desktop, a decent media player besides vlc.

Just started using ubuntu so any help would be greatly appreciated.

---

### Post by Bigtime_Scrub on 2008-05-18
After you have installed all the restricted plugins VLC will play anything (at least almost anything). But, if you really dont like VLC there is also MPlayer and Movie Player. Im pretty sure those are in the repositories. 

I wouldnt mess around with too many fancy custimizations until you are comfortable with Ubuntu. From my personal experience, I tried doing too much too fast and I screwed some things up early on. If you are feelings a little adventurous you can always enable compiz-fusion and make you Linux cube and whatnot. Check out the how to guides in this forum under "Desktop Effects and Customizations." 

If you are really dead set on changing things around check out this site which walks you step by step on converting your desktop.

[http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml)

---

### Post by Dirk_Gently on 2008-05-18
Hi and welcome to the world of Ubuntu!

For a media player I usually prefer mplayer. It's easily installed with apt-get if you've enabled the universe and multiverse repositories in your /etc/apt/sources.list. 

Follow eg. this guide [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html")
It's for older releases than hardy, but the mplayer part should work nonetheless, not sure about the w32codec part.

Cheers

---

### Post by fubared259 on 2008-05-18
Thanks for the help. And it is always more fun to jump in head first in my opinion.

---

### Post by viswanathan on 2008-05-18
> **fubared259 said:**
> I was looking for anything that will help customize my desktop, a decent media player besides vlc.

Just started using ubuntu so any help would be greatly appreciated.

dude i think vlc is d best 1 v hve but if u dnt like it try xine or mplayer dude u need to enable multiverse repos for installing this i think its enabled by default if not go to synaptic and enable it or 

```
You need to add the following lines to /etc/apt/sources.list file

gedit /etc/apt/sources.list

enter these two lines and save your file

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

Now you need to run the following command to update the source list

sudo apt-get update

Install mplayer using the following command

sudo apt-get install mplayer


```

:lolflag::lolflag::lolflag::lolflag:

---

### Post by fubared259 on 2008-05-18
Oh I love VLC player use it all the time in XP but just looking for something a little different. I want to change everything over to Ubuntu eventually but for now I use it to surf and some work. I use xp for all my gaming.

---

### Post by hyper_ch on 2008-05-18
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

