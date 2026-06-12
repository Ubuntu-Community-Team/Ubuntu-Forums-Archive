---
title: "[SOLVED] Limpus Lite Query"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by s.fox on 2008-10-03
Hello everyone,

Would someone please be able to help me with a slight problem i am experiencing in limpus lite?  Basically i have bought an Acer Aspire One and have been working on opening up the OS after Acer had effectively hidden many of its features.

My question is this:  How would i get the OS to run a terminal command upon bootup?  I know how this is done in Ubuntu,  but its a little different in this linux distrobution.

P.S  I have enabled the right click on the desktop menu,  so have full access to the system.

Thanks for any help,  its greatly appreciated.

-Ash R

---

### Post by s.fox on 2008-10-05
Good news!  I figured it out and all is well when I boot up.

Normally in XFCE its under Setting -> Autostarted Applications.

I don't know why but it doesn't show on the Acer Aspire One.  I got round this by entering  

```
xfce4-autostart-editor
``` 

This brought up a nice simple GUI where I was able to add an item to the autostarted applications.  In my case ```
compiz-manager
```

Hope this saves someone some time!

-Ash R

---

### Post by barbedsaber on 2008-10-05
Just a quick suggestion, why don't you install linpus yourself, or at least try it from a live cd, maybe less things will be hidden that way.

---

### Post by s.fox on 2008-10-05
The Acer came with it installed so I thought i would give it a go.  If i were to install an OS from scratch i would probably install Xubuntu or similar.  

This distro is not that bad once you get used to it and more importantly get the desktop  switcher to work.  I don't know if I will remove Linpus or not.  I have heard a few people have had trouble with the wifi drivers so it might not be such a good idea.

---

### Post by barbedsaber on 2008-10-05
what I am suggesting is that you install linpus again (optimized for small screen) but you do it yourself, so you don't have the restrictions that acer (or was it asus, I forget) put on it for the benifet of n00bs. at the end of the day, its your computer, and what you choose to install is up to you.

---

