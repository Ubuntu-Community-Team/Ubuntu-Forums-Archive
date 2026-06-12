---
title: "Xubuntu loading over Ubuntu."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by steelisreal on 2008-04-27
I have an HP2133 Mini-Note and was noticing that Ubuntu was hogging a lot of my cpu, so I decided to put on Xubuntu.

I followed this method

```
sudo apt-get install xubuntu-desktop
```

Reboot

```
sudo apt-get remove ubuntu-desktop
```

Now when I boot up the ubuntu screen comes up and starts to load and then the screens goes blurry and for a quick instance I see the ubuntu desktop, then I get the xubuntu login screen.  It is almost like Xubuntu is running over Xubuntu.

Also on the system monitor screen it says ubuntu and gnome.

Is this normal?  Did I miss a step? How can I fix this if in fact I did mess up?  Should I just do a fresh install with Xubuntu?

---

### Post by overdrank on 2008-04-27
> **steelisreal said:**
> I have an HP2133 Mini-Note and was noticing that Ubuntu was hogging a lot of my cpu, so I decided to put on Xubuntu.

I followed this method

```
sudo apt-get install xubuntu-desktop
```

Reboot

```
sudo apt-get remove ubuntu-desktop
```

Now when I boot up the ubuntu screen comes up and starts to load and then the screens goes blurry and for a quick instance I see the ubuntu desktop, then I get the xubuntu login screen.  It is almost like Xubuntu is running over Xubuntu.

Also on the system monitor screen it says ubuntu and gnome.

Is this normal?  Did I miss a step? How can I fix this if in fact I did mess up?  Should I just do a fresh install with Xubuntu?

HI and this link may help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Apparently some difference between apt-get and aptitude

---

### Post by rubicon on 2008-04-27
First: sudo apt-get remove ubuntu-desktop *doesn't* remove ubuntu packages, it only removes the given meta-package. So it is &#8212;imho&#8212; useless.

Then: if you think that ubuntu runs simultaneously, try switching to another VT: alt-ctrl-F7/F8/F9 (that's where usually X starts). I guess you should disable auto-logging-in feature in System/Admin'/Login Screen. Then at boot it will load gdm and wait for username+password. If so, you can choose another session (Xfce) from menu in gdm.

---

### Post by martrn on 2008-04-27
Its your desktop manager that is causing this problem, you could :-

```
sudo apt-get remove --purge  gdm
sudo apt-get remove --prge kdm
sudo apt-get -remove --purge xdm
```

and then put (1 of back)

```
sudo apt-get install gdm
sudo apt-get install kdm
sudo apt-get install xdm
```

> Is this normal? Did I miss a step? How can I fix this if in fact I did mess up? Should I just do a fresh install with Xubuntu?

Its normal when switching desktops, for this to happen.  There are sites on the internet telling you how to put pure gnome back on the desktop but not the other way around, ie not get a pure xfce or kde desktop, a bit annoying really.

---

