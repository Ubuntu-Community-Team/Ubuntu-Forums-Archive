---
title: "Preview Enlightenment with Klik (No install require)"
date: 2005-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by KillerKiwi on 2005-11-01
Want to try Enlightenment with out any hassles?

Use Klik

install the client 
1) Press Alt-F2 and paste **wget klik.atekon.de/client/install -O -|sh**
2) Restart your browser

Click this link
[klik://enlightenment]("klik://enlightenment") (18.9 MB)

easy ;)

How does it work
[http://klik.atekon.de/blog/?p=5](http://klik.atekon.de/blog/?p=5)

---

### Post by kashms on 2005-11-01
How do you then start it? Can you login from GDM?

---

### Post by jobezone on 2005-12-14
I got the error "Unable to mount /tmp/app/1". Do you do this in Kubuntu or Ubuntu (I use Ubuntu)?

---

### Post by Interblaze on 2005-12-15
[QUOTE=jobezone]I got the error "Unable to mount /tmp/app/1". Do you do this in Kubuntu or Ubuntu (I use Ubuntu)?[/QUOTE]

getting the same error :confused:

---

### Post by TimmyJ on 2005-12-15
try making a symlink between /usr/X11R6/lib/X11/fonts/ -> /usr/share/X11/fonts/ and see if that does the trick for you. Taken from [http://klik.atekon.de/blog/?p=5](http://klik.atekon.de/blog/?p=5)

---

### Post by Rob2687 on 2005-12-15
Yeah, i get the same error that Arrr guy posted in the blog. There is already a fonts folder so how are you supposed to make a symlink?

---

### Post by jobezone on 2005-12-15
I managed to make the symlink:
```

eduardo@compEdu:/usr/X11R6/lib/X11$ sudo ln -s /usr/share/X11/fonts/ fonts
```
I'm now going to try enlightenment... Wish me good luck!

---

### Post by jobezone on 2005-12-15
Nope, have the same error.

---

### Post by One Quick Question on 2005-12-16
Jobezone, you might want to look at your command a bit more closely.

With the symlink, I got the Enlightenment running....  Although for some reason its graphics weren't being displayed properly.  Shrug.

---

### Post by jobezone on 2005-12-16
How many MB's is the enlightenment klik download?
I've since switched to kubuntu, and it seems to me that it's better supported, but now I'm wanting to know if it's too much a download just for trying it out.

---

### Post by Rob2687 on 2005-12-16
[QUOTE=One Quick Question]Jobezone, you might want to look at your command a bit more closely.

With the symlink, I got the Enlightenment running....  Although for some reason its graphics weren't being displayed properly.  Shrug.[/QUOTE]

So what's the correct way to symlink it?

---

### Post by One Quick Question on 2005-12-16
It's 20.1 megs.  
And I fixed the weird graphical issue by removing some  misconfigured e settings I had laying around from the last time I played with it.

> /usr/X11R6/lib/X11/fonts/ -> /usr/share/X11/fonts/
To symlink it, since I also had the /usr/X11R6/lib/X11/fonts/ folder on my system, I first moved all the useful files from the subdirectories of the one to the other, so that the .../lib/... folder had no useful data.  Then I deleted it and symlinked it.  The command would be *ln -s /usr/share/X11/fonts /usr/X11R6/lib/X11/fonts*, but I just used a root-powered Konqueror for all the dragging and dropping. *kdesu konqueror*, you know, much easier.

---

