---
title: "Need a macro program like autohotkey to simulate a key being HELD down."
date: 2013-10-12
forum: New to Ubuntu
---

### Post by Crinkle on 2013-10-12
Need an autohotkey substitute for linux.

AHK doesnt run even through wine.

Autokey doesnt seem to have any INDIVIDUAL key press simulation. Or indeed, any list of commands you can put in it.

Really need this ASAP please help!

---

### Post by whitesmith on 2013-10-12
Have you tried xbindkeys? And why use a Windows program in the first place?

---

### Post by Crinkle on 2013-10-12
well because something like it would be a good idea because im used to using that. xbindkeys doesnt work at all tho, i did

sudo apt-get install xbindkeys

and it did the usual install thing, but when i type it in the launcher, its doesnt find a program for it.

---

### Post by Vaphell on 2013-10-12
[http://www.semicomplete.com/projects/xdotool/xdotool.xhtml](http://www.semicomplete.com/projects/xdotool/xdotool.xhtml)

```
xdotool type abc  # type abc
xdotool key a     # single press
xdotool keydown a # hold a
xdotool keyup a   # release a
xdotool click 1   # mouse (lmb)
```

---

### Post by Crinkle on 2013-10-12
Ahh no thats no good, it needs to have some sort of GUI i cant be doing with the command line, i get stressed every time i have to open the terminal as it is.

I'll probably still with AutoKey as i've been able to get it to do MOST stuff i need it to do. However if anyone knows how to make it move the mouse slightly or do loops that would be fantastic. I made a loop but it doesnt error and doesnt wrk:

# Enter script code
loop = 0
if loop < 15:
    keyboard.press_key("W")
    time.sleep(2.00)
    keyboard.release_key("W")
    time.sleep(1.00)
    #rturn debuggery
    keyboard.send_key("<return>",1)
    loop = loop + 1

---

