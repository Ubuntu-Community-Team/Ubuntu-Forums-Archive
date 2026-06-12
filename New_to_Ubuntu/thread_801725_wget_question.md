---
title: "wget question"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-20
Hey guys. I'm trying to download music off a server. the problem is, there are several songs, and downloading them individually would be a pain in the butt. I tried 

```
wget http://site.com/*.mp3
``` and it didin't work. Is there a way to get all of a certain file type off a site? btw, I am running Ubuntu SE, so command line only. thanks!

~Dan

---

### Post by peitschie on 2008-05-20
Update:  My initial posting was incorrect... it is indeed possible

Nope.  wget (and all other utilities similar to this) can only get a specific url.  Though I understand you only have a command-line on that computer, if you have access to a browser somewhere you might try this firefox plugin: DownThemAll - [https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by Monicker on 2008-05-20
Actually, you can make wget retrieve all of files it finds with a certain extension.  I do have reservations about the link in question though, so will not give any details about to accomplish it in this case.

---

### Post by iaculallad on 2008-05-20
Try relating wget on this [page]("http://www.linux.com/articles/59457"). Maybe, you could get an idea on how to solve your problem.

---

### Post by Thirtysixway on 2008-05-20
You could get Lynx, the textbased browser and just "click" on each of the files, maybe that will prompt a download.

sudo apt-get install lynx

---

### Post by Monicker on 2008-05-20
Now the link looks better.  ;)


```
wget -r -A mp3 http://site.com/directory
```

---

### Post by DBrocks on 2008-05-20
Thanks! Lol i had a forum staff member come chasing after me. I didn't know that wasnt allowed. But thanks alot!

---

