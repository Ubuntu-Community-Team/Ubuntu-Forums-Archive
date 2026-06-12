---
title: "[SOLVED] Cannot GetDeb"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by OldGrey on 2008-10-21
Hi I wonder if you wise people can help me? 

I dual boot Ubuntu 64bit with XP. I am not sure if this is a Linux issue, but Linux is what I use the most. I recently upgraded to Ubuntu 64bit to see if it was any faster, marginal but otherwise fine, but in the process I needed to get the 64bit version of Songbird from GetDeb. There lies the problem, I cannot get onto the site, it just times out. I've tried on lots of occasions, at all times of the day, and even using XP and IE, but always the same result. Now at work using an office XP pc I can get on no problem. I am beginning to wonder if this is down to my internet connection at home (Virgin Media / ntlworld cable 10mb Broadband), but other browsing / emailing works fine. 

Does anyone have any experience or advice they could share? 

Yours frustrated and bemused.

---

### Post by phidia on 2008-10-21
You can use 32 bit apps in 64 bit by installing the ia32libs package and sometimes a deb program called getlibs is useful too.

There might be alternative download sites for 64 bit songbird if you want the 64 bit package. There are some links [here]("https://help.ubuntu.com/community/Songbird") but maybe they are the same as you've already tried?

---

### Post by unutbu on 2008-10-21
Did you do an distro upgrade, or did you do a fresh install?
Sometimes when you do a distro upgrade, strange things start failing.
If you did do a distro upgrade, the best solution might be to backup your data and then do a fresh install. 

If that is not an option or you would like to experiment a bit with your current problem, try this:
```

wget -c http://www.getdeb.net/download/3117/0

```
This will attempt to download songbird_0.7.0-0~getdeb1_amd64.deb from the getdeb website.

If the connection times out, you might get an error message out of the wget output which could be useful. Also, try running the same command again. The -c flag means "Continue getting a partially-downloaded file" which means that wget will pick up where it left off.

---

### Post by OldGrey on 2008-10-21
It was a fresh install. I'll try your experiment, but I am away from the pc at the moment, so it will be a few hours before to try it out.

---

### Post by OldGrey on 2008-10-21
I have now had a chance to try it again and for the first time since Friday it now works. Thanks for your suggestions anyway.

---

