---
title: "gnome vs. enlightenment"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bmann11 on 2008-06-25
A couple of questions.  I've been using ubuntu for several months now, and I'm beginning to feel settled with the basics.  I don't see myself ever going back to the dark side, so I'm wondering about ckecking out enlightenment.  By the way, I tried kubuntu, and it didn't do it for me.

1.  Will enlightenment work with ubuntu 8.04?

2.  What are the disadvantages/ advantages of one versus the other?

3.  Is it relatively painless to install and try, then uninstall if I find it doesn't work for me?

4.  Will all programs I'm currenlty using (i.e. evolution) play nicely with enlightenment?

Any feedback is appreciated.

---

### Post by billgoldberg on 2008-06-25
> **bmann11 said:**
> A couple of questions.  I've been using ubuntu for several months now, and I'm beginning to feel settled with the basics.  I don't see myself ever going back to the dark side, so I'm wondering about ckecking out enlightenment.  By the way, I tried kubuntu, and it didn't do it for me.

1.  Will enlightenment work with ubuntu 8.04?

2.  What are the disadvantages/ advantages of one versus the other?

3.  Is it relatively painless to install and try, then uninstall if I find it doesn't work for me?

4.  Will all programs I'm currenlty using (i.e. evolution) play nicely with enlightenment?

Any feedback is appreciated.

1. yes

2. Installing e16 from the repo's (or e17 not in the standard repo's) will install it for you, and all apps should work. But most of them will look horrible. 

Enlightements file manager is useless (on ubuntu).

There is an special version of ubuntu that comes with elightenment called [opengue]("http://opengeu.intilinux.com/Home.html"). That will work better than just adding enlightement to ubuntu.

Enlightenment is faster than gnome, but if you are an any pc not older than 3 years, you won't really feel the difference.

And it must be noted that compiz fusion will not work with enlightenment.

3. yes

4. they will work, but chances are it won't be pretty (visually).

---

### Post by atomkarinca on 2008-06-25
[This howto]("http://ubuntuforums.org/showthread.php?t=546746") explains how to install it in very easy steps, so it shouldn't be a problem. All your applications should work with it quite well, I only had problems with VLC (I'm a Mplayer guy anyways).

Enlightenment is more lightweight than Gnome but it lacks a decent file manager and some configuration tools. You can use Thunar or PCManFM for a file manager. As for configuration tools I recommend installing [openGEU]("http://opengeu.intilinux.com/") as a metapackage instead of just E17. It has best of both worlds: Gnome tools with Enlightenment's beauty and speed.

---

### Post by Inxsible on 2008-06-25
Yet another option is to try out [Ozos]("http://cafelinux.org/OzOs/"). Its a distribution based on xubuntu with E17 (the latest) as the Window Manager.

it also gives you the option of installing programs using their apt:foo method. 

although I think, you can use that repo with any ubuntu based distro as well.

---

### Post by dracayr on 2008-06-25
> **billgoldberg said:**
> 
4. they will work, but chances are it won't be pretty (visually).

I disagree. I run e17, and my apps are as pretty as ever. It is possible to apply a gtk2 theme in e17.

dracayr

---

### Post by Rui Pais on 2008-06-26
> **billgoldberg said:**
> 1. yes

2. Installing e16 from the repo's (or e17 not in the standard repo's) will install it for you, and all apps should work. But most of them will look horrible. 

Enlightements file manager is useless (on ubuntu).

There is an special version of ubuntu that comes with elightenment called [opengue]("http://opengeu.intilinux.com/Home.html"). That will work better than just adding enlightement to ubuntu.

Enlightenment is faster than gnome, but if you are an any pc not older than 3 years, you won't really feel the difference.

And it must be noted that compiz fusion will not work with enlightenment.

3. yes

4. they will work, but chances are it won't be pretty (visually).

Just create a .gtkrc-2.0 file with :
```
gtk-theme-name = "Wanted_GtkTheme_Name"
gtk-icon-theme-name = "Wanted_IconThem_Name"
gtk-font-name = "Wanted_Font_Name"
```
And apps will look the same as in gnome.

e17 File Manager can (should) be disabled and any other FM used instead (pretty much the same as any light WM)


On Gnome vs Enlightenment question:
I doubt that gnome apps would be faster running inside e17... but e17 session starts faster and users usually like the level of eye-candy/usability of e17: 
big nice very interactive pager, menus everywhere, very configurable "panels" till full transparency, easy "desklets", much less memory used.

---

