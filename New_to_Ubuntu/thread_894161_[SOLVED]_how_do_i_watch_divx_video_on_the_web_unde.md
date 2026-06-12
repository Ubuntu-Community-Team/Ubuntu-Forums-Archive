---
title: "[SOLVED] how do i watch divx video on the web under ubuntu ?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by marine63 on 2008-08-19
title

---

### Post by Perfect Storm on 2008-08-19
Install mplayer, mplayer mozilla and w32codecs (or w64codecs if you're using Ubuntu 64-bit)

---

### Post by marine63 on 2008-08-19
thx but when i use mplayer i keep getting a big fat green line running through the video any suggestions?

---

### Post by Perfect Storm on 2008-08-19
Try uninstall totem-mozilla (it may interfer).

---

### Post by marine63 on 2008-08-19
i alrdy have

---

### Post by Perfect Storm on 2008-08-19
Try with xine player then.

---

### Post by marine63 on 2008-08-19
it doesnt work either

---

### Post by Perfect Storm on 2008-08-19
Sorry, I can't help you further then (havn't that kind of problem(s)).

---

### Post by Vivaldi Gloria on 2008-08-19
The following worked for me. 

First add medibuntu repos (see their howto):

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Now open a terminal and use the commands: 

```
sudo apt-get remove --purge totem-mozilla
sudo apt-get install mozilla-mplayer
```

---

### Post by marine63 on 2008-08-19
im getting a green line running through the video im playing and there are color shadows coming off some imagines

---

### Post by Drakkor on 2008-08-19
Or use vlc, it's in the repos :)

---

### Post by marine63 on 2008-08-19
vlc and its plugin wont stream for me... probably because i dont know how to set it up... too many options >.< ( im a windows media player classic user)
and i got it to work with mplayer and right clicking on the video and click on configure and change the video output to gl

---

### Post by Vivaldi Gloria on 2008-08-19
> how do i watch divx video on the web under ubuntu ?

Can you give an example of a web site where you cannot watch the videos?

And why is there a [SOLVED] in the thread title? Have you solved it?

---

### Post by 3rdalbum on 2008-08-19
> **marine63 said:**
> 
and i got it to work with mplayer and right clicking on the video and click on configure and change the video output to gl

Out of interest, can you please PM me as to whether you have Nvidia or ATI graphics? (or something else?). I had similar problems with an Nvidia card and Nvidia drivers with a similar solution (I changed to X11 or something).

---

