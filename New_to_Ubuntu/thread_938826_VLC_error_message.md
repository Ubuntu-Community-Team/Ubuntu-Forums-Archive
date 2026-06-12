---
title: "VLC error message"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by eddie_reid on 2008-10-05
I have just installed Ubuntu (hardy heron) I am trying to install VLC movie player but I get an error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am sorry I am a Novice user only just installed to get some experiance 2 days ago. Please Help :)

---

### Post by echo314 on 2008-10-05
Go into the terminal and type in ```
sudo dpkg --configure -a
```

ps: Hi! Welcome to our forums!

---

### Post by eddie_reid on 2008-10-05
echo314 You are the man/woman :) Now is all good

Thank you for your quick response

---

### Post by billgoldberg on 2008-10-05
It wasn't a vlc error, lol.

Could you mark this thread as solved?

---

### Post by eddie_reid on 2008-10-05
Hi Again I am sorry but I have encountered a new problem with VLC. I am trying to play an encrypted DVD one that I have recently purchased from the video shop and it will not play. A:confused:lthough it will play my "back up" dvd's  Do I need to install any plug ins for this or will it just not play real DVD's

Thanks

---

### Post by billgoldberg on 2008-10-05
> **eddie_reid said:**
> Hi Again I am sorry but I have encountered a new problem with VLC. I am trying to play an encrypted DVD one that I have recently purchased from the video shop and it will not play. A:confused:lthough it will play my "back up" dvd's  Do I need to install any plug ins for this or will it just not play real DVD's

Thanks

First completely remove vlc player.

You can do this using synaptic or by using this command in a terminal.

```
sudo apt-get autoremove vlc --purge
```

Then follow instructions here:

[http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/](http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/)

Afterwards reinstall vlc.

---

