---
title: "Mouse pointer size"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Johnny3 on 2012-01-04
Is there and easy way to make the pointer a little bigger? I have look in System setting, Advanced setting and Myunity. Am I just not see it?. I have Ubuntu 11.10 just about like I want it and don't want to take a chance on messing it up. So if it not to easy just say no. No big deal.
Thanks and God Bless Johnny3 65+++
PS hope this is OK to post here.

---

### Post by hhh on 2012-01-04
You could install chameleon-cursor-theme, either through Synaptic or by running the following in a terminal...```
sudo apt-get install chameleon-cursor-theme
```

That will install a cursor theme in several different colors and 3 different sizes (small, regular, large). Check in Settings>Mouse to change ther cursor theme, or if that setting doesn't exist (I don't run Ubuntu these days) in a terminal run...```
update-alternatives --config x-cursor-theme
```
That will present you with a list of your installed cursors, choose the number of a theme and press Enter. I believe you'll have to logout/login to activate the theme, whichever method you use.

If you decide you don't like any of them, run the update-alternatives command again, I believe choosing 1 will restore the default theme. If not, you could always run...```
sudo apt-get purge chameleon-cursor-theme
```... and logout/login again.

---

### Post by bluexrider on 2012-01-04
> **hhh said:**
> I believe you'll have to logout/login to activate the theme, whichever method you use.



not needed

---

