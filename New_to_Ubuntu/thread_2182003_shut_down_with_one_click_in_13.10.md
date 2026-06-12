---
title: "shut down with one click in 13.10"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by bbrazie on 2013-10-19
I was using the command:

 dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop

for an easy one click shut down in previous versions but it doesn’t seem to work after upgrading to 13.10.

What can I use in Ubuntu 13.10?

---

### Post by VMC on 2013-10-19
Maybe this:
```
gsettings set org.gnome.SessionManager logout-prompt 'false'
```
I'n not quite sure what your looking for, but the above will immediately turn off computer when shutdown is applied of power-off pushed.

---

### Post by bbrazie on 2013-10-20
I am looking for a command I can assign to an icon on my desktop that when clicked on the computer just shuts down and doesn’t ask me if I want to switch users or restart or... Just turn off the computer.

---

### Post by bbrazie on 2013-10-20
gsettings set org.gnome.SessionManager logout-prompt 'false'

I tried that code in both a terminal and my jumper and it does not shut the machine down.

Any other thoughts?

---

### Post by Frogs Hair on 2013-10-20
Open the dconf editor and try org > gnome > gnome session > logout prompt. I have never tested this though.

---

### Post by bbrazie on 2013-10-20
I is already un-checked so I don't think that will make a difference.

---

### Post by Hadaka on 2013-10-21
Hi, if you are not password paranoid this works.
```
#!/bin/bash
echo 'YOUR PASSWORD' | sudo -S shutdown -h now

```
chmod +x
then have your .desktop exec file call this. (icon file)

---

### Post by bbrazie on 2013-10-21
Sorry. Tried that in a terminal and it didn't work either.

---

### Post by Hadaka on 2013-10-21
ok, try it this way in a terminal then.
please do..
```
sudo -S shutdown -h now
```
this will indeed work.

---

### Post by sammiev on 2013-10-21
> **Hadaka said:**
> Hi, if you are not password paranoid this works.
```
#!/bin/bash
echo 'YOUR PASSWORD' | sudo -S shutdown -h now

```
chmod +x
then have your .desktop exec file call this. (icon file)

This works great on 13.10 Tried and tested.

---

### Post by sammiev on 2013-10-21
> **VMC said:**
> Maybe this:
```
gsettings set org.gnome.SessionManager logout-prompt 'false'
```
I'n not quite sure what your looking for, but the above will immediately turn off computer when shutdown is applied of power-off pushed.

This works great and no password required on 13.10 :)

---

### Post by bbrazie on 2013-10-22
Not sure why these are not working in a jumper on my desktop. I get the message "there was and error when launching the application".

---

### Post by bob brazie on 2013-10-26
Still not working in a jumper.

---

### Post by sammiev on 2013-10-26
```
sudo gsettings set org.gnome.SessionManager logout-prompt 'false'
```

Open up "Terminal" and copy and paste that line. Hit enter and close the "Terminal" and shut down the OS from the menu. :)

---

### Post by bob brazie on 2013-10-26
That will make the shut down option not ask for restart or change users? Just shut down?

---

### Post by sammiev on 2013-10-26
> **bob brazie said:**
> That will make the shut down option not ask for restart or change users? Just shut down?

It will shut down without ask for restart but I can still use the Log Out option and select a New User or another flavor.

---

### Post by bob brazie on 2013-10-26
Sorry but it still comes with two options to select from.

---

