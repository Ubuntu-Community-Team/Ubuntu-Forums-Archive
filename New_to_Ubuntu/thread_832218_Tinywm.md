---
title: "Tinywm"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-17
How do I start this up?  I've installed it..

I figured it would be under the "Window Manager" selection in Fluxbox but it is not.

---

### Post by sdennie on 2008-06-17
You can get it running under gnome with:

```

pkill metacity && twm &

```

I would imagine you can do the same in fluxbox with:

```

pkill fluxbox && twm &

```

---

### Post by kerry_s on 2008-06-17
do you have a xinitrc?

if mot make 1:

editor ~/.xinitrc
put
xsetroot -solid black &
xterm &
timywm

than just startx and it will load.

xinitrc is where you can specify the things to load.

tinywm is very scarce, i usually use it for kiosks since there is nothing in it to mess with.

---

### Post by AnLGP on 2008-06-17
What's a kiosk?

---

### Post by kerry_s on 2008-06-17
it's like this->
[http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)

but i helped a friend do his own from a debian base.

make sure you read the man page for tinywm.

sorry, i been slow, i'm in the process of doing a win2k laptop for mom and on mine i been switching over to bitmap fonts and added a font server, i've lowered my resources by 75% using bitmap fonts instead of truetype. woohoo

---

### Post by Nythain on 2008-06-17
and if you use gdm/kdm im sure you could create a new session for tinywm... something like
```

[Desktop Entry]
Encoding=UTF-8
Name=TinyWM
Exec=<whatever the path to the binary to run tinywm is, probably something like /usr/bin/tinywm>
Type=Application

```

you will have to find out the path and or name of the binary for tinywm, as i've never used it i cant tell you what it is

ps... kerry_s, any bitmapped fonts you recommend, particularly that look good in urxvt??? and whats this font server you speak of???

---

### Post by AnLGP on 2008-06-17
I get this error:

X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  10
  Current serial number in output stream:  12

---

### Post by kerry_s on 2008-06-17
> **Nythain said:**
> and if you use gdm/kdm im sure you could create a new session for tinywm... something like
```

[Desktop Entry]
Encoding=UTF-8
Name=TinyWM
Exec=<whatever the path to the binary to run tinywm is, probably something like /usr/bin/tinywm>
Type=Application

```

you will have to find out the path and or name of the binary for tinywm, as i've never used it i cant tell you what it is

ps... kerry_s, any bitmapped fonts you recommend, particularly that look good in urxvt??? and whats this font server you speak of???

i'm using the linux fonts, the font server is xfs(x font server). it gives me a win2k look, so if your use to the clear type of xp or the truetype of dejavu you might not like the look.

---

### Post by kerry_s on 2008-06-17
> **AnLGP said:**
> I get this error:

X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  10
  Current serial number in output stream:  12


using which method?

---

### Post by AnLGP on 2008-06-17
"tinywm" in the terminal..  probably wrong.

do you know how I would put it in SLiM?  I know where to stick the logon option I just don't know the command.

---

### Post by kerry_s on 2008-06-17
> **AnLGP said:**
> "tinywm" in the terminal..  probably wrong.

do you know how I would put it in SLiM?  I know where to stick the logon option I just don't know the command.

lol, yeah that would be wrong.

the command is "tinywm" or the full path "/usr/bin/tinywm" but you should use a xinitrc or you won't be able to do anything, there's nothing in tinywm, no access to anything, you'll have to start a program to access the other programs, in this case xterm.

> ps... kerry_s, any bitmapped fonts you recommend, particularly that look good in urxvt?

sorry, wasn't concentrating i'm jumping back and fourth between 2 laptops. i use the simple 9x15. my xdefaults->

```
!! you need to run> xrdb -merge ~/.Xdefaults 

!*customization: -color
*Font: 9x15 
*fontSet: 9x15
*faceName: mono
*faceSize: 12
*saveLines: 10000
*scrollBar: false
*font: 9x15
*reverseVideo: true
*enableBackups: false
```

---

### Post by RedSquirrel on 2008-06-18
Ah, good ol' 9x15. One of my favourites for terminals on fresh installs until I get around to installing terminus. ;)

---

### Post by kerry_s on 2008-06-18
> **RedSquirrel said:**
> Ah, good ol' 9x15. One of my favourites for terminals on fresh installs until I get around to installing terminus. ;)

i don't really like terminus, i've tried it several times and it just, i don't know. :confused:

hey, how have you been you were missing for a while, is everything okay?

---

### Post by RedSquirrel on 2008-06-18
> **kerry_s said:**
> i don't really like terminus, i've tried it several times and it just, i don't know. 

I know what you mean. I didn't really see what all the fuss was about when I first tried it but I kept it anyway. My eyes eventually got used to it and now it's really hard for me to use anything else! I have it in terminals and on the console.


> **kerry_s said:**
> hey, how have you been you were missing for a while, is everything okay?

Yes, fine. Thanks for asking. I've just been a bit busy. I don't read through the whole of the Ubuntu forums as often as I once did. I don't post as often either. By the time I come around, many of the threads are already full of helpful responses so there's no need for my $0.02. :)

Hope all is well with you.

---

