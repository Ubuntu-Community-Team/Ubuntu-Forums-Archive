---
title: "Wobbly windows in unity"
date: 2018-11-04
forum: New to Ubuntu
---

### Post by doux91 on 2018-11-04
I Installed Ubuntu 18.04 in my laptop and I want to activate that efect with compiz config but I want to use it with unity desktop, can I do that?

---

### Post by deadflowr on 2018-11-04
Yes
install ubuntu-unity-desktop
```
sudo apt install ubuntu-unity-desktop compizconfig-settings-manager compiz-plugins
```

Pick lightdm when prompted,
this will switch the display server to lightdm which works better with unity.
Reboot
Choose unity from the icon that shows in the username/password box.
Just click on the icon box in the right corner, it'll allow you to toggle various desktop sessions you have installed.


FTR, Ubuntu 18.04 does not (and cannot) use compiz in any way for the default desktop, so you wouldn't be able to use it for that anyway.
Some alternate desktops you can run it with are
unity
gnome-flashback
ubuntu mate
xfce (xubuntu)
though I'm not sure how well xfce/xubuntu do with compiz these days.

---

### Post by 23dornot23d on 2018-11-04
This is Ubuntu 18.10 .......... wobbly windows works in mate ......... but so far have not been able to get the cube working in it ...... not sure about 18,04 or unity ?

[https://youtu.be/yyxukkB5-Ao](https://youtu.be/yyxukkB5-Ao)

---

### Post by doux91 on 2018-11-04
> **deadflowr said:**
> Yes
install ubuntu-unity-desktop
```
sudo apt install ubuntu-unity-desktop compizconfig-settings-manager compiz-plugins
```

Pick lightdm when prompted,
this will switch the display server to lightdm which works better with unity.
Reboot
Choose unity from the icon that shows in the username/password box.
Just click on the icon box in the right corner, it'll allow you to toggle various desktop sessions you have installed.


FTR, Ubuntu 18.04 does not (and cannot) use compiz in any way for the default desktop, so you wouldn't be able to use it for that anyway.
Some alternate desktops you can run it with are
unity
gnome-flashback
ubuntu mate
xfce (xubuntu)
though I'm not sure how well xfce/xubuntu do with compiz these days.
[COLOR=#000000]I Made it but it change my theme and It seems gnome desktop only with the dock and it Installed a lot of apps that was installed, I understand I cannot use compiz with my desktop but for me all are awfull desktops, gnome, and this new one unity, I dont none of them, so I will stop looking for enable wobbly windows, thank you for the answer, I will uninstall unity desktop I install cuz always request me password for start the ubuntu [/COLOR]:sad:[COLOR=#000000] [/COLOR]
[https://mega.nz/#!NsQBUILb!x2SLsNg2Q...4bNLA4doAG5w6U]("https://mega.nz/#!NsQBUILb!x2SLsNg2QpaalmVU7Ylee_uGrSOvS4bNLA4doAG5w6U")

---

