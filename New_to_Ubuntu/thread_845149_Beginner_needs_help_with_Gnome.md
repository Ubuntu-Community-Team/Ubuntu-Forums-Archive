---
title: "Beginner needs help with Gnome"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by kalypso418 on 2008-06-30
I just partitioned my laptop using windows xp and ubuntu (hardy heron).  I am completely new.  I want to install a new theme, and it said "drag theme to gdmsetup".  I go to gdmsetup and I need to be root?  Please help, i tried looking for a "theme install" guide in the newbie section but alas, could not really find it.

---

### Post by WRDN on 2008-06-30
If a password is requested, just enter the password you entered during installation and it should work. 

Alternatively, you could use the following command in the terminal:

```
sudo gdmsetup
```

Im not currently using Ubuntu so cant check the command works, but im guessing it will. The "sudo" prefix gives you super- user privileges (sudo stands for 'super user do').

---

### Post by raja on 2008-06-30
What theme are you trying to install? Assuming it is a compiz theme (If you have compiz running) or a metacity theme, you can install it from the System -> Preferences -> Appearance dialog. Read [here]("http://library.gnome.org/users/user-guide/stable/prefs-theme.html.en") for more details.

---

### Post by Inxsible on 2008-06-30
> **kalypso418 said:**
> I just partitioned my laptop using windows xp and ubuntu (hardy heron).  I am completely new.  I want to install a new theme, and it said "drag theme to gdmsetup".  I go to gdmsetup and I need to be root?  Please help, i tried looking for a "theme install" guide in the newbie section but alas, could not really find it.Assuming that you have downloaded a GDM theme and not a GTK theme, this is what you do

1) Go to System>>Administration>>Login Window
2) Click on the Login tab
3) Drag and drop the theme that you downloaded into the space where there are a number of themes listed.
4) Select your new theme and restart X. You can also select multiple themes and have them be randomly selected. There is a drop down up top for that option.

---

