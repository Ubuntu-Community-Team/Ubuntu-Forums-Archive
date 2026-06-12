---
title: "After installing Anydesk, when I click the top right region, Anydesk pops up"
date: 2023-06-22
forum: New to Ubuntu
---

### Post by Cristatus on 2023-06-22
I have installed Anydesk for personal use, but whenever it is running in the system tray, ready to run, and I click in the top right 1/8th region, it pops up.

I have a webm screencast of this that I would like to upload somewhere for a better explanation.

Even when I was trying to search the forums, I could not, because the search box was in exactly that area, so when I tried to click it, Anydesk popped up.

I can also not use the X button to close any of the windows that are in full screen, such as my browser.

Running Ubuntu 23.04 and Anydesk version 6.2

:shrug:

---

### Post by #&amp;thj^% on 2023-06-22
kind of a hardlainer but I know of no other way to date:
```
sudo plutil -replace RunAtLoad -bool false /Library/LaunchAgents/com.philandro.anydesk.Frontend.plist
```
Basically this will set the auto start boolean value in the *.plist file from true to false which as a result would disable the autostart function.  I know this still works on vers:6.2

---

### Post by Cristatus on 2023-06-22
Would this mean that Anydesk would not start up automatically?

If so, that is not what I am trying to do.

I need Anydesk.  Also when I am remoted in, clicking in that region in the remote session still pops up the Anydesk window on my local computer.

---

### Post by #&amp;thj^% on 2023-06-22
It will always be in your app menu... Or even through the terminal via:
```
/usr/bin/anydesk %u
```
My suggested code on Mine:
```
sudo plutil -replace RunAtLoad -bool false /Library/LaunchAgents/com.philandro.anydesk.Frontend.plist
Loading '/Library/LaunchAgents/com.philandro.anydesk.Frontend.plist' - nil data argument passed to method

```
And it is still setting in my tray.
Now My DE is XFCE4 and I can click the top right corner with out Anydesk hogging my screen.

---

### Post by Cristatus on 2023-06-22
Gotcha.

When I try to run the code you pasted, I get > plutil: command not found

---

### Post by #&amp;thj^% on 2023-06-22
No big deal
```
sudo apt-get install libplist-utils
```

---

### Post by Cristatus on 2023-06-22
Now I get>  sudo: plutil: command not found

---

### Post by #&amp;thj^% on 2023-06-22
Easiest method is to simply remove Anydesk from auto start preferences.
I still don't have a clue why your code comes back not found?
I'm going to guess i won't be of help if your using Gnome Shell, I haven't used it since Gnome2 and was the best desktop I ever used.(IMHO)

---

### Post by Cristatus on 2023-06-22
Running > echo $0 shows that I'm using bash

---

### Post by #&amp;thj^% on 2023-06-22
bash here as well, but that's got nothing to do with the differences between yours and mine 
```
 echo $0 
/bin/bash

```
Here might show something:
```
apt show anydesk
Package: anydesk
Version: 6.2.1
Status: install ok installed
Priority: optional
Section: net
Maintainer: AnyDesk Software GmbH <linux-support@anydesk.com>
Installed-Size: 16.3 MB
Depends: libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.20.1), libstdc++6 (>= 4.1.1), libx11-6, libxcb-shm0, libxcb1, libpango-1.0-0, libcairo2, libxrandr2 (>= 1.3), libx11-xcb1, libxtst6, libxfixes3, libxdamage1, libxkbfile1, libgtkglext1
Recommends: libglx-mesa0, xdg-utils
Homepage: https://anydesk.com/
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: The fastest remote desktop software on the market.
  It allows for new usage scenarios and applications that have not been possible with current remote desktop software.

```

---

### Post by Cristatus on 2023-06-22
I'm using whatever the default downloaded Ubuntu version is, which I guess is GNOME.

So I guess someone else will have to help me?

---

### Post by Cristatus on 2023-06-22
Exactly the same as mine

```
pt show anydesk
Package: anydesk
Version: 6.2.1
Status: install ok installed
Priority: optional
Section: net
Maintainer: AnyDesk Software GmbH <linux-support@anydesk.com>
Installed-Size: 16.3 MB
Depends: libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.20.1), libstdc++6 (>= 4.1.1), libx11-6, libxcb-shm0, libxcb1, libpango-1.0-0, libcairo2, libxrandr2 (>= 1.3), libx11-xcb1, libxtst6, libxfixes3, libxdamage1, libxkbfile1, libgtkglext1
Recommends: libglx-mesa0, xdg-utils
Homepage: https://anydesk.com/
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: The fastest remote desktop software on the market.
  It allows for new usage scenarios and applications that have not been possible with current remote desktop software.

```

---

### Post by Cristatus on 2023-06-22
If I installed Ubuntu MATE, would this problem become solvable?

Alternatively, what shell are you using, and could I potentially get it running on my current install?

---

### Post by #&amp;thj^% on 2023-06-22
Now this may blow your mind:
Note the absence of both:
```
apt policy libplist-utils plutil
libplist-utils:
  Installed: (none)
  Candidate: 2.2.0-6+b2
  Version table:
     2.2.0-6+b2 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        500 https://deb.debian.org/debian bookworm/main amd64 Packages
N: Unable to locate package plutil

```
Yet again my code runs just fine, and has the desired results:
```
sudo plutil -replace RunAtLoad -bool false /Library/LaunchAgents/com.philandro.anydesk.Frontend.plist
[sudo] password for me: 
Loading '/Library/LaunchAgents/com.philandro.anydesk.Frontend.plist' - nil data argument passed to method

```
So again our Desktops have a difference with that command.

---

### Post by #&amp;thj^% on 2023-06-22
> **Cristatus said:**
> If I installed Ubuntu MATE, would this problem become solvable?
I would have to guess that it would.
> **Cristatus said:**
> 
Alternatively, what shell are you using, and could I potentially get it running on my current install?

We had this in post # 10
```
echo $0 
/bin/bash
##Shell: bash 5.2.15

```
If your asking my Terminal in use it is "Terminal: terminator"
EDIT1:
This is off 
```
inxi -S
System:
  Host: voyager-zfs Kernel: 6.2.0-20-generic arch: x86_64 bits: 64
    Desktop: Xfce v: 4.18.1 Distro: Ubuntu 23.04 (Lunar Lobster)

```
and again:
```
sudo plutil -replace RunAtLoad -bool false /Library/LaunchAgents/com.philandro.anydesk.Frontend.plist
Loading '/Library/LaunchAgents/com.philandro.anydesk.Frontend.plist' - nil data argument passed to method

```

---

### Post by jabenn79 on 2024-04-18
Same. Quite annoying.

---

