---
title: "Going back in time..."
date: 2011-11-12
forum: New to Ubuntu
---

### Post by palpullero on 2011-11-12
Ok, first of all, this is my first post, so "Hello world!".  Not a noob per-se, but I came across something that I think I already know the answer to ("nope, can't do that..."), but here it goes anyway (no, I haven't searched it, but I need an answer before I loose my mind).

Problem:
I want to use Zoneminder as an IP camera recorder.  Installed it back in 2009 under 9.04 Jaunty and it had bugs but I could see an image at the beginning.  Forward to 2011 and I've tried 10.04, 11.04, and 11.10 and Zonminder just gives me a blue screen (no BSOD here).  So what do I do?  I want to install 9.04 Jaunty again, and everything is great, except I can't find the Zoneminder package and it seems all the repositories are defunt!  So my guess is that once Ubuntu drops support for a specific version, even old packages and updates of those packages are gone too - Am I right?

Hey, thanks for looking, wondering, frowning, and laughing at my post/question.  

Running 11.10 with XFCE on my laptop - let the good times roll!

---

### Post by Chronon on 2011-11-12
```
chronon@tangata:~$ sudo apt-cache search zoneminder        
mythzoneminder - view status and display footage recorded with zoneminder
zoneminder - Linux video camera security and surveillance solution

```

It appears to be in the 11.10 repositories.

I don't see an entry for 9.04 but there is a listing for 8.04 here:
[https://launchpad.net/ubuntu/+source/zoneminder](https://launchpad.net/ubuntu/+source/zoneminder)

---

