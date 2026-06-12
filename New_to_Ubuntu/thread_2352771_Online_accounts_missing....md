---
title: "Online accounts missing..."
date: 2017-02-15
forum: New to Ubuntu
---

### Post by jaytt on 2017-02-15
Hi 
Running 16.10 and fairly new to Linux.
Got it running perfectly with lots of apps/wine etc and really happy...

then I started playing.. :(
I tried installing KDE Desktop and Kubuntu (I think), then tried removing.
I thought I removed but when I reboot it still shows the blue xubuntu screen? is this normal?

All seems ok now - however....

If I click the cog in the right hand corner .. under System Settings it says "Online Accounts"
When I click that it just launches "System Settings" (as does system settings)

Under the Personal Tab,  There used to be an Icon called "Online Accounts"
Its now not there.

If I search in the Unity? for online accounts - No apps come up?

Any ideas please

Thanks

---

### Post by howefield on 2017-02-15
There is an system settings Online Accounts

[ATTACH=CONFIG]273737[/ATTACH]

But I believe this is from a bygone age when the messenger Empathy was included in the default Ubuntu installation, could be wrong but I don't think the Online Accounts "feature" will do anything for you.

It isn't uncommon for desktop environments to "bleed" over each other so your remnant of the xubuntu desktop wouldn't be a surprise. Nothing wrong with installing multiple desktops, my preference is for multiple partitions/installs for each desktop environment of choice.

---

### Post by jaytt on 2017-02-16
Hi, thanks - the System Settings Online Accounts is whats missing.
I wanted it for my Google Drive integration etc

This is all I have (attached)

---

### Post by Perfect Storm on 2017-02-16
Try:
```
sudo apt-get install --reinstall gnome-control-center unity-control-center-signon
```

---

### Post by howefield on 2017-02-16
If the packages that Artificial Intelligence don't sort it, have a look at this one : ubuntu-system-settings-online-accounts

---

### Post by jaytt on 2017-02-17
Cheers, Artifical Intelligence post sorted it.

Much appreciated

---

### Post by jaytt on 2017-02-17
Just checked and as much as its now back ...as screenshots show..it looks different to what it was - also files is not working for my Google Drive Nautilus integration.
[ATTACH=CONFIG]273760[/ATTACH][ATTACH=CONFIG]273761[/ATTACH]

My Evolution auto imported gmail details so I know its working to an extent but I want to be able to see my Google Drive in Nautilus/gnome file manager.

Cheers

---

