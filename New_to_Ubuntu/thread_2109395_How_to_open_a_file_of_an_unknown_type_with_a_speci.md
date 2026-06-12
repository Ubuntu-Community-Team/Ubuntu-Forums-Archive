---
title: "How to open a file of an unknown type with a specific application?"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by brallan on 2013-01-27
I am trying to associate all ".tc" files with a program called truecrypt. The problem is, if I choose **open with** and try to select is as an application, it neither shows up, nor permits me to choose a terminal command:

[IMG]https://dl.dropbox.com/u/53208596/screenshorts%20for%20use%20in%20ubuntuforums%2C%20etc%20%28don%27t%20move%20or%20erase%29/select_app.png[/IMG]
Nor does **find applications online** find anything useful. Is there another GUI or a command from the terminal which will associate all files of type .tc with truecrypt? I already have it installed.

---

### Post by dolphin194 on 2013-01-28
Yes, you can do this through the terminal easily.

Fire up the terminal and drag the application you want to use into it, then drag the file into the window and hit enter. 

The application should then open the truecrypt file.

---

### Post by Vaphell on 2013-01-28
find truecrypt's .desktop file in /usr/share/applications and see if the 'Exec=...' line has a placeholder for opened file, something like %u. For some reason programs lacking that placeholder don't show up in 'open with' dialogs.

---

### Post by brallan on 2013-01-29
hi dolphin,

thanks for the answer. couldn't drag the application into the terminal window, either from the launcher or the window itself. It just puts one window on top another. I notice you are using Xubuntu..... which terminal does it use?

> **dolphin194 said:**
> Yes, you can do this through the terminal easily.

Fire up the terminal and drag the application you want to use into it, then drag the file into the window and hit enter. 

The application should then open the truecrypt file.

---

### Post by stinkeye on 2013-01-29
I did what **Vaphell** suggested.

```
gksudo gedit /usr/share/applications/truecrypt.desktop
```
and changed the line...
```
Exec=/usr/bin/truecrypt
```
to
```
Exec=/usr/bin/truecrypt %u
```

Truecrypt then appeared in the open with menu.

Clicking on  a **.tc** file and choosing to open with truecrypt
then brings up a password window.

---

### Post by brallan on 2013-01-30
Yes! Thanks, **Vaphell**! Thanks, **stinkeye**! I didn't get it at first (nautilus didn't show me the .desktop file extension, which was annoying, making me think the applications folder only contained binaries), but figured it out just now! Thanks to both of you!

> **stinkeye said:**
> I did what **Vaphell** suggested.

```
gksudo gedit /usr/share/applications/truecrypt.desktop
```and changed the line...
```
Exec=/usr/bin/truecrypt
```to
```
Exec=/usr/bin/truecrypt %u
```Truecrypt then appeared in the open with menu.

Clicking on  a **.tc** file and choosing to open with truecrypt
then brings up a password window.

---

