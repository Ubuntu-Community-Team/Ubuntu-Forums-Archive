---
title: "black box when opening menus"
date: 2020-09-09
forum: New to Ubuntu
---

### Post by olezcano on 2020-09-09
Hi, I'm new in Linux, but so far so good, I got most of the things I need, just found a problem with some applications, for some reason, the classic menu on top is not displaying the information, instead it shows a black box. See the screenshot below.
[ATTACH=CONFIG]286929[/ATTACH]

In this example I'm using wireshark ver 2.6.10 but I see the same behavior with other tools, like Kdenlive.
I'm currently running Lubuntu over Linux 4.15.0-115-generic, with intel Core i3-7020UQ2.30Ghz.
Any help will be appreciated!

---

### Post by CelticWarrior on 2020-09-09
Welcome.

Have you installed some theme and/or changed some settings?

---

### Post by GhX6GZMB on 2020-09-10
> **olezcano said:**
> 
I'm currently running Lubuntu over Linux 4.15.0-115-generic

What does this sentence mean? Current Lubuntu kernel is 5.4.

---

### Post by CelticWarrior on 2020-09-10
> **ml9104 said:**
> What does this sentence mean? Current Lubuntu kernel is 5.4.

It probably means Lubuntu 18.04.

---

### Post by olezcano on 2020-09-11
I haven't install anything regarding the setting. Actually I still have the default wallpaper

---

### Post by olezcano on 2020-09-11
> **ml9104 said:**
> What does this sentence mean? Current Lubuntu kernel is 5.4.

Sorry for the confusion, I grabbed that info from Wireshark>help>about.
I was actually referring to the ubuntu version.

NAME="Ubuntu"
VERSION="18.04.5 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.5 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

---

### Post by &amp;KyT$0P# on 2020-09-12
How do you have Qt 5 appearance configured?

(Sounds like a similar problem to [this thread]("https://ubuntuforums.org/showthread.php?t=2445307").)

---

### Post by olezcano on 2020-09-16
> **halogen2 said:**
> How do you have Qt 5 appearance configured?

(Sounds like a similar problem to [this thread]("https://ubuntuforums.org/showthread.php?t=2445307").)

Sorry for the late reply. I'm not sure what QT5 is neither but this is what I got from the file qt.conf on /usr/lib/x86_64-linux-gnu/qt5
[Paths]
Prefix=/usr
ArchData=lib/x86_64-linux-gnu/qt5
Binaries=lib/qt5/bin
Data=share/qt5
Documentation=share/qt5/doc
Examples=lib/x86_64-linux-gnu/qt5/examples
Headers=include/x86_64-linux-gnu/qt5
HostBinaries=lib/qt5/bin
HostData=lib/x86_64-linux-gnu/qt5
HostLibraries=lib/x86_64-linux-gnu
Imports=lib/x86_64-linux-gnu/qt5/imports
Libraries=lib/x86_64-linux-gnu
LibraryExecutables=lib/x86_64-linux-gnu/qt5/libexec
Plugins=lib/x86_64-linux-gnu/qt5/plugins
Qml2Imports=lib/x86_64-linux-gnu/qt5/qml
Settings=/etc/xdg
Translations=share/qt5/translations

In other hand, yes, that other thread you mentioned sounds like my problem, but looks like it was unresolved. Do you agree with one of the last post mentioning LXDE dektop vs LXQt desktop?

---

### Post by &amp;KyT$0P# on 2020-09-17
As a test, can you please try running Wireshark (because it's what you took screenshot of) from Terminal using this command? -
```
QT_QPA_PLATFORMTHEME= wireshark
```
Any difference?

---

### Post by olezcano on 2020-09-18
> **halogen2 said:**
> As a test, can you please try running Wireshark (because it's what you took screenshot of) from Terminal using this command? -
```
QT_QPA_PLATFORMTHEME= wireshark
```
Any difference?

Thank you for the advice, I ran that command and it worked properly. What may be the problem?

[ATTACH=CONFIG]286988[/ATTACH]

---

### Post by &amp;KyT$0P# on 2020-09-19
> **olezcano said:**
> Thank you for the advice, I ran that command and it worked properly. 

Great, now run this command to see what the bad value of [FONT=Courier New]QT_QPA_PLATFORMTHEME[/FONT] is -
```
env | grep -F QT
```

Next step is to find out where [FONT=Courier New]QT_QPA_PLATFORMTHEME[/FONT] is being set -
```
grep -r -F QT_QPA_PLATFORMTHEME /etc ~/.profile 2>/dev/null
```

Please post the output of both these commands.

---

### Post by olezcano on 2020-09-21
> **halogen2 said:**
> Great, now run this command to see what the bad value of [FONT=Courier New]QT_QPA_PLATFORMTHEME[/FONT] is -
```
env | grep -F QT
```

Next step is to find out where [FONT=Courier New]QT_QPA_PLATFORMTHEME[/FONT] is being set -
```
grep -r -F QT_QPA_PLATFORMTHEME /etc ~/.profile 2>/dev/null
```

Please post the output of both these commands.

Thank you, when I run the first command I get this:

QT_STYLE_OVERRIDE=gtk
QT_DEVICE_PIXEL_RATIO=auto
QT_QPA_PLATFORMTHEME=lxqt
QT_PLATFORM_PLUGIN=lxqt

Now, with the second command, nothing happens...

[ATTACH=CONFIG]287003[/ATTACH]

---

### Post by &amp;KyT$0P# on 2020-09-21
> **olezcano said:**
> Now, with the second command, nothing happens...

That's odd.  So odd that I got curious enough to try to reproduce this myself in my Xubuntu 18.04.  And I did.

The fix:

1) run this command in Terminal -
```
QT_QPA_PLATFORMTHEME= lxqt-config
```

2) In the window that comes up, open Appearance.

3) Select any theme that does NOT start with "bb10".

---

### Post by olezcano on 2020-09-22
> **halogen2 said:**
> That's odd.  So odd that I got curious enough to try to reproduce this myself in my Xubuntu 18.04.  And I did.

The fix:

1) run this command in Terminal -
```
QT_QPA_PLATFORMTHEME= lxqt-config
```

2) In the window that comes up, open Appearance.

3) Select any theme that does NOT start with "bb10".

Thank you so much, that worked.
Sorry for the inconvenient, I'm new in Linux and have been struggling with that.

---

