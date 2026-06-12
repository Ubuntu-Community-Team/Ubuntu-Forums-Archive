---
title: "synaptic doesnt start on Ubuntu 18.04 LTS"
date: 2019-07-25
forum: New to Ubuntu
---

### Post by amitjatin on 2019-07-25
Hi All

To lessen boot time i had installed synaptic as suggested on ubuntu forums in my previous post, but now when i run synaptic it simply ask password for authentication but after that nothing happens, i tried to run it from terminal i get " Gtk-Message: 11:57:17.324: GtkDialog mapped without a transient parent. This is discouraged." in terminal and a dialogue box saying " Starting synaptic manager without administrative privileges".

---

### Post by tea for one on 2019-07-25
Are you running a **Ubuntu on Wayland** session.

Log out > Select the gear wheel near the **sign in** > Select Ubuntu.

Does synaptic function OK now?

Synaptic won't reduce your boot time, it is simply an efficient package (software) manager.

Good luck

---

### Post by cruzer001 on 2019-07-25
Is your system up to date?
```
sudo apt update && sudo apt-get upgrade -y
```
Try reinstalling synaptic
```
sudo apt purge synaptic && sudo apt autoclean
```
then install
```
sudo apt install synaptic
```

---

### Post by amitjatin on 2019-07-26
thanx a ton " Tea for one" problem solved, can u pls suggest how to remove wayland completely ??

---

### Post by uRock on 2019-07-26
> **amitjatin said:**
> thanx a ton " Tea for one" problem solved, can u pls suggest how to remove wayland completely ??

[https://linuxconfig.org/how-to-disable-wayland-and-enable-xorg-display-server-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-wayland-and-enable-xorg-display-server-on-ubuntu-18-04-bionic-beaver-linux)

Wayland is the path many distros are already going with. It's very annoying.

---

### Post by tea for one on 2019-07-26
> **amitjatin said:**
> thanx a ton " Tea for one" problem solved, can u pls suggest how to remove wayland completely ??

I don't think that you can completely remove Wayland but you can disable it as mentioned in the link from **uRock**.

Anyway, Ubuntu remembers your last session and will automagically log you in to a non-Wayland session each time.

I simply ignore Wayland for the time being until all the little potholes are fixed.

p.s. Can you mark your thread as solved to help other forum users with the same problem

---

### Post by ramskilo on 2019-08-14
Hello, 
I'm just writing from a fresh installation with native wayland environment. It works like a charm, splendid looking, very poor resources consumption... I suggest you to use synaptic in this way: 
-make your selections 
-save them in a file (say "sel")
-run this command from terminal: [B]sudo apt install $(cat sel| sed 's/\<install\>//g')
[/B](install previously selected packages removing automatically the word "install" from the file created)

Let me know if it works for you if you want

---

### Post by cruzer001 on 2019-08-14
I tried just last week to get synaptic to work in wayland.  I created a applications (.desktop) file in /.local/share/applications and that let it display when using the ShowApplications launcher.
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=SynapticPM
Comment=
Exec=synaptic
Icon=synaptic3
Terminal=false
Type=Application
StartupNotify=true
```
However I could not get either sudo -H or pkexec to work, as noted in the above Exec= entry.

---

### Post by ramskilo on 2019-08-21
Hello cruzer001,
Did you tried to launch from a terminal? My bult-in command (synaptic-pkexec) is a script:


```
#!/bin/sh

USING_WAYLAND=0
if [ ! "x${WAYLAND_DISPLAY}" = "x" ]; then
    USING_WAYLAND=1
fi
if [ "x${XDG_SESSION_TYPE}" = "xwayland" ]; then
    USING_WAYLAND=1
fi

if [ "x${USING_WAYLAND}" = "x1" ]; then
    # Running wayland; start synaptic without pkexec
    zenity --warning --width=500 --text \
        "You are using Wayland environment, Synaptic will continue without administrative privileges.\\n\
To make Synaptic fully functional, please restart your session without Wayland."
    exec "/usr/sbin/synaptic" "$@"
else
    pkexec "/usr/sbin/synaptic" "$@"
fi


```

I cannot help at the moment with .desktop commands because I don't use them.

---

