---
title: "How do I stop Dolphin from creating those &quot;.d3lphinview&quot; in every single folder?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by vvvladut on 2008-09-13
...it's especially annoying on SD cards and USB drives!

---

### Post by forger on 2008-09-13
Are you sure it's **dolphin** and not **d[COLOR="Red"]3[/COLOR]lphin** that creates those files, .d3lphinview ?

[https://marrat.homelinux.org/D3lphin](https://marrat.homelinux.org/D3lphin)
> 
D3lphin 0.9.1
- Added option to turn off .d3lphinview files for every folder. 

Even if it's dolphin, there must be an option in its preferences windows (?)

---

### Post by vvvladut on 2008-09-13
I don't know what D3lphin is, I'm talking about the file manager in my Kubuntu, which is clearly labeled "Dolphin". I could not find anything about creating hidden files in every folder in the configuration menu...

---

### Post by xebian on 2008-09-13
> **vvvladut said:**
> I don't know what D3lphin is, I'm talking about the file manager in my Kubuntu, which is clearly labeled "Dolphin". I could not find anything about creating hidden files in every folder in the configuration menu...

If you are using Kubuntu hardy 8.0.4  then it's d3lphin where the 3 indicates KDE3.xx.  It's still dolphin but the package name is d3lphin to differentiate from the KDE4 package dolphin. But the features/configuration should be pretty much the same.

---

### Post by vvvladut on 2008-09-13
> **xebian said:**
> If you are using Kubuntu hardy 8.0.4  then it's d3lphin where the 3 indicates KDE3.xx.  It's still dolphin but the package name is d3lphin to differentiate from the KDE4 package dolphin. But the features/configuration should be pretty much the same.

The top menu bar, and the about menu all say "Dolphin", although I am using KDE3.5.10.

Anyway, does anyone have any idea how to stop it from creating .d3lphinview files?

---

### Post by Denestria on 2008-09-13
Do you have save view properties for each folder checked in the general tab of the config window?  I've never had it turned on so I'm not certain that is causing your .d3lphinview file, but it sounds like the perpetrator.

---

### Post by vvvladut on 2008-09-14
> **Denestria said:**
> Do you have save view properties for each folder checked in the general tab of the config window?  I've never had it turned on so I'm not certain that is causing your .d3lphinview file, but it sounds like the perpetrator.

It looks like you identified the perpetrator correctly! But I liked that feature, because if I don't turn that on, Dolphin (or whatever it's spelled) will not remember that I want to see my hidden files, and I will have to turn on viewing hidden files for every folder every time I open one of them, now...

How come Windows can remember folder view settings without creating those obnoxious files all over the place?...

---

### Post by Denestria on 2008-09-14
> It looks like you identified the perpetrator correctly! But I liked that feature, because if I don't turn that on, Dolphin (or whatever it's spelled) will not remember that I want to see my hidden files, and I will have to turn on viewing hidden files for every folder every time I open one of them, now...

Professor Plum in the library with the candlestick!

View > Adjust View Properties, Show Hidden Files = All Folders is broken, but is supposed to be fixed for Intrepid so you should soon be able to view hidden files without wearing out your fingers on the Alt+. keys.

I don't know why there isn't a simple "always view hidden files" checkbox in the config to begin with.

---

