---
title: "First time used can't start"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by krc369 on 2008-07-12
I installed the Ubuntu Linux and then logged in with my username (non root) and password

Now i see this

user@computer: $                 (the ampersand before the $)

How do i go past this one...it's my first time...so any help will be appreciated.

---

### Post by Hendrixski on 2008-07-12
Did you install the server version?  Because that doesn't have a visual interface (and why would it... so that you can play solitaire on your expensive server?)

If that's the case then just try "sudo apt-get install ubuntu-desktop" and it'll install the GNOME desktop

If you installed the regular version... then... umm, did you log in in "safe mode"?  typing in startx should start the xserver

---

### Post by krc369 on 2008-07-12
> **Hendrixski said:**
> Did you install the server version?  Because that doesn't have a visual interface (and why would it... so that you can play solitaire on your expensive server?)

If that's the case then just try "sudo apt-get install ubuntu-desktop" and it'll install the GNOME desktop

If you installed the regular version... then... umm, did you log in in "safe mode"?  typing in startx should start the xserver

THANKS. I did enter the "sudo apt-get install ubuntu-desktop" command...and now it's loading the various parts and drivers. it's been over an hour. How long should it take? Thanks.

---

### Post by TSS on 2008-07-12
It will probably take a long time because it has to download a lot of files.
Do you know what type of CD you downloaded?

Since "sudo apt-get install ubuntu-desktop" is downloading so much, I would have to guess that you downloaded the server version.  If that's the case, I personally would recomend downloading the desktop version and reinstalling it.  It'll make your life easier in the long run.

---

### Post by krc369 on 2008-07-12
> **TSS said:**
> It will probably take a long time because it has to download a lot of files.
Do you know what type of CD you downloaded?

Since "sudo apt-get install ubuntu-desktop" is downloading so much, I would have to guess that you downloaded the server version.  If that's the case, I personally would recomend downloading the desktop version and reinstalling it.  It'll make your life easier in the long run.



I'm back to the same screen as earlier [ username@computername: ampersand $ ]. What do I enter now? 

BTW, where do I get the non-server version. Any recommendations? Thanks.

---

### Post by TSS on 2008-07-12
Look here for the non-server version: 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

As for what you should do now, if everything installed correctly, just type:
```
startx
```

---

### Post by krc369 on 2008-07-12
> **Hendrixski said:**
> Did you install the server version?  Because that doesn't have a visual interface (and why would it... so that you can play solitaire on your expensive server?)

If that's the case then just try "sudo apt-get install ubuntu-desktop" and it'll install the GNOME desktop

If you installed the regular version... then... umm, did you log in in "safe mode"?  typing in startx should start the xserver

I'm back to the same screen as earlier [ username@computername: ampersand $ ]. What do I enter now?

---

### Post by TSS on 2008-07-12
Can you tell us what happened when you typed startx?

---

### Post by avtolle on 2008-07-12
Yes, please give us any error messages when you did the startx command.

One thought: if indeed the server edition was installed, does installation of ubuntu-desktop install xorg? Try this from the command line```
sudo aptitude update && sudo aptitude install xorg
``` if there's no evidence of x being present.

---

### Post by krc369 on 2008-07-13
> **TSS said:**
> Can you tell us what happened when you typed startx?

It worked. I was able to login and had a great first time experience with Linux. In fact I'm thinking of putting ubuntu on my Dell Inspiron 700m laptop. I hope that is the right choice I'm making as I'm not sure how to activate the wireless option.

Thanks for the help.

---

