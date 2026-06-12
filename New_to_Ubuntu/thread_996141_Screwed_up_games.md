---
title: "Screwed up games"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by MasterSander on 2008-11-28
Whenever I launch a fullscreen game I get all sorts of crap that's not really visible. I believe this has to do with my fonts, is there any way to fix this?

---

### Post by Bölvaður on 2008-11-28
System &#8594; Preferences &#8594; Appearance
Chose the tab named Fonts and pick some new fonts like Petra or something you like and works for you.

Also try disabling compiz before starting the game up.

---

### Post by MasterSander on 2008-11-29
Changing fonts didn't work, disabling compiz did work. What can I do about that?

I mean is there something in my settings that I should change cause I can't find it.

---

### Post by MasterSander on 2008-11-30
bump

---

### Post by Bölvaður on 2008-11-30
Try running compiz without any effects enabled at all. And then check if it works. You can do that by installing ccsm and take all the tics off from there.

If you can play games with that you should be able to isolate the problem by activating one effect at a time. Please post your findings as I sometimes have this problem.
I know others are having similar troubles but they make some sort of quick way to disable and enable compiz. (perhaps the easiest way would be making customized lunchers that disable compiz, load up the game, when the game has finished, enable compiz.

---

### Post by Perfect Storm on 2008-11-30
Other options;

1.
install compizconfig-settings-manager.
```
sudo apt-get install compizconfig-settings-manager
ccsm

```

You can now find compizconfig-settings-manager somewhere in the system tabs (properly in Systems ---> preferences --->)
Execute it.
Go to **Generel Options** and unselect **Unredirect Fullscreen Windows**

2. 
Install fusion-icon
```
sudo apt-get install fusion-icon
fusion-icon -n
```

It should now be in Applications tab ---> Accessories
With this one you can switch compiz on/off as pleased.

---

