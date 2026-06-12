---
title: "Disable caps lock"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by szaqlon on 2008-06-22
I found that "xmodmap -e “clear Lock”" will disable the caps lock key. However once you log out and back in it's enabled again. Is there a way to disable it so it stays that way until you manually re-enable it?

---

### Post by angryfirelord on 2008-06-22
Here you go: [http://www.peterbe.com/Disable-Caps-Lock-in-Linux]("http://www.peterbe.com/Disable-Caps-Lock-in-Linux")

First, open up a terminal and open the file:
```
gedit .bashrc
```
Then, copy-paste this at the end:
```
if [ "$PS1" ]; then
    # Disables the bloody CapsLock button
    xmodmap -e "remove lock = Caps_Lock"
 fi

```

---

### Post by szaqlon on 2008-06-22
Tried that, doesn't seem to work. Once I log out and back in it's enabled again. I looked at the link and that was posted in 2004, is it possible that something has changed?

---

### Post by iaculallad on 2008-06-22
You can modify your keymap by creating your own xmodmap file to activate Caps Lock key:

-First step is to create your own xmodmap-file

```
xmodmap -pke > ~/.xmodmap.mapkey
```

-Open and edit ~/.xmodmap.mapkey. Look for the capslock line (keycode should be = 66) and replace it with key combination that you prefer to activate your Caps Lock.

```
gksudo gedit ~/.xmodmap.mapkey
```

> keycode 66 = slash slash

-You need to press slash key twice to activate your Caps Lock.

-On your terminal, make an autostart entry for your xmodmap.

```
xmodmap -e “clear Lock”
xmodmap ~/.xmodmap.mapkey
```

---

### Post by angryfirelord on 2008-06-22
Do the previous one again, but put in /etc/bash.bashrc instead.

If that doesn't work, try this:
```
gedit ~/.Xmodmap
```
Add:
```
clear Lock
```

---

### Post by szaqlon on 2008-06-23
> **iaculallad said:**
> You can modify your keymap by creating your own xmodmap file to activate Caps Lock key:

-First step is to create your own xmodmap-file

```
xmodmap -pke > ~/.xmodmap.mapkey
```

-Open and edit ~/.xmodmap.mapkey. Look for the capslock line (keycode should be = 66) and replace it with key combination that you prefer to activate your Caps Lock.

```
gksudo gedit ~/.xmodmap.mapkey
```



-You need to press slash key twice to activate your Caps Lock.

-On your terminal, make an autostart entry for your xmodmap.

```
xmodmap -e “clear Lock”
xmodmap ~/.xmodmap.mapkey
```

Tried this, when I do "xmodmap ~/xmodmap.mapkey" I get: 
xmodmap: unable to open file '~/xmodmap.mapkey' for reading
xmodmap: 1 error encountered, aborting.

---

### Post by szaqlon on 2008-06-23
> **angryfirelord said:**
> Do the previous one again, but put in /etc/bash.bashrc instead.

If that doesn't work, try this:
```
gedit ~/.Xmodmap
```
Add:
```
clear Lock
```

"gedit ~/.xmodmap" opens a blank page. Is it supposed to be blank and add clear Lock, or is it not supposed to be blank?

---

### Post by ukripper on 2008-06-23
> **szaqlon said:**
> "gedit ~/.xmodmap" opens a blank page. Is it supposed to be blank and add clear Lock, or is it not supposed to be blank?

It is blank if you don't have anything in there mapped.

it is very normal to be blank. it should be capital X as **~/.Xmodmap**

---

### Post by szaqlon on 2008-06-23
well it seems something has worked. Just logging out and back in didn't disable the caps lock. I had some updates that required a restart and when everything was back up and running caps lock did not work. So, not sure exactly what it was, but thank you for the help.

---

### Post by kwacka on 2009-05-19
> **angryfirelord said:**
> 
```
clear Lock
```

Worked for me, thanks.

---

### Post by rwigle on 2010-08-20
I hope I am not missing something, BUT how about a way for the non-hackers. (There are some in the Ubuntu community!)

Under Lucid (and I think since Hardy something similar)

System => Preferences => Keyboard => Layouts => Options => CapsLock key behaviour => disabled (or other nifty possibilities).

I know it isn't very cryptic (and again apologies if this doesn't do quite what people want).

---

### Post by mike555 on 2010-08-20
I just install "xkeycaps" , it lets you map any key , like the caps lock to a shift ........

---

