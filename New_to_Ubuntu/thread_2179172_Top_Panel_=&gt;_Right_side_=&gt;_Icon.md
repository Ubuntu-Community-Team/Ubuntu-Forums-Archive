---
title: "Top Panel =&gt; Right side =&gt; Icon"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by czgirb on 2013-10-06
Are we allowed to customized, which icons are desirable to be shown in Top Panel's Right side without having a problem?
* The default is **Power, Account, Time, Sound, Networking, Messages, Networking, etc.**
If YES, please guide me ...
**Thanx**

---

### Post by stinkeye on 2013-10-07
In dconf-editor look in **com.canonical.indicator**

---

### Post by czgirb on 2013-10-09
> **stinkeye said:**
> In dconf-editor look in **com.canonical.indicator**

SORRY! I'm a newbie ... I don't know what it is?
Wouldyou mind to describe it briefly?

---

### Post by heir4c on 2013-10-09
First, you must install dconf-editor via UbuntuSoftwareCenter.
When you open USC than typ in the search bar: dconf-editor
On the right you can click on install.

---

### Post by Frogs Hair on 2013-10-09
Some of the indicators are located in dconf editor > apps > indicator session. The network manager show applet is under org > gnome > nm applet . Others I find under com> canonical> indicator. Locations may vary depending on release.

---

### Post by stinkeye on 2013-10-09
In raring(13.04) dconf-editor should be installed.
May have to install in earlier releases.
Search in dash.
It is included in the package **dconf-tools**.
Check you have dconf-tools installed then run **dconf-editor**

You will just have to find them from previous suggestions.
With **dconf-editor** open, press ctrl+f to seach.

---

### Post by czgirb on 2013-10-11
> **Frogs Hair said:**
> Some of the indicators are located in dconf editor > apps > indicator session. The network manager show applet is under org > gnome > nm applet . Others I find under com> canonical> indicator. Locations may vary depending on release.

Now, I am able to hide **Bluetooth** and **Battery** icon.
But I do not know how to hide **Keyboard** and **User Account** icon.
Would you mind to guide me ...
Thank you

---

