---
title: "Where are the splash screens?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by bwhite82 on 2008-11-02
Hi, I'm not very familiar with XFCE. Where exactly are the login splash screens kept?

/usr/share/what?

I know there is a graphical tool to change them. Thats not what I need. I need to know where the splash screens are kept, the exact directory.



-Thanks

EDIT: Not the "login manager" theme, nor the "boot splash" screen. The "login splash" screen.

---

### Post by cardinals_fan on 2008-11-02
This could be useful: [http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html](http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html)

---

### Post by bwhite82 on 2008-11-03
> **cardinals_fan said:**
> This could be useful: [http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html](http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html)

I've been there, its showing you how to create a "newer-style" splash. Basically, from what I've discovered is:

-XFCE used to use an older type of splash screen which were "hard-coded" into libraries (.so's). They were kept in /usr/lib/xfce4/splash/engines

-XFCE has a newer tool to install and create splash screens called "balou"
These are kept in /usr/share/themes/NameOfTheme/balou

Unfortunately, the splash I am trying to extract from another distro (KateOS) is of the "hard-coded" variety. I have no idea if the artwork is in the library or the splash graphics are actually completely coded.

I want to actually convert that splash to Gnome but it seems impossible. I've also attempted to copy the library to my Xubuntu installation but its not working either. Its a lost cause.

---

### Post by philinux on 2008-11-03
In ubuntu they are here. 

/usr/lib/usplash

I use startupmanager to do the splash set up but the code required would be similar to this.
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
 sudo update-alternatives --config usplash-artwork.so
 sudo update-initramfs -u

```

---

### Post by bwhite82 on 2008-11-03
> **philinux said:**
> In ubuntu they are here. 

/usr/lib/usplash

I use startupmanager to do the splash set up but the code required would be similar to this.
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
 sudo update-alternatives --config usplash-artwork.so
 sudo update-initramfs -u

```
Hmm..I'll have to give this a try though that is for bootsplash.

---

