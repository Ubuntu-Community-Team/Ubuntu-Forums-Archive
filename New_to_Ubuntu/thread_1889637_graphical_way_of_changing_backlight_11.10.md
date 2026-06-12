---
title: "graphical way of changing backlight? 11.10"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by JazzPotato on 2011-12-01
I have tried messing with my xorg.conf. I have tried xbacklight. I have tried using dodgy bash scripts i found on the tubes of the internet. I have not yet found a way to turn my goddamn laptop's screen brightness down!!! Its stuck on max and i have 30 mins battery life!

I have heard tales of a mythical "slider" in display settings but i have found no such "slider". 
It is probably obvious, but i'm sure theres a solution!

Thanks in advance.

---

### Post by roger_1960 on 2011-12-01
Hi

Have you looked in "system settings" (top right icon) then "screen"?  If not, there is normally a key set FN+F? to adjust brightness on laptops....

---

### Post by DapperMe17 on 2011-12-01
Should be easy...use your laptop's "F" keys.

Mine are "f2" for less, "f3" for more light!

:popcorn:

---

### Post by dave0109 on 2011-12-02
There seem to be a number of us with issues regarding screen brightness.  Check out the following threads to see if they help you.

[http://ubuntuforums.org/showthread.php?p=11505626](http://ubuntuforums.org/showthread.php?p=11505626)
[http://ubuntuforums.org/showthread.php?t=1882469](http://ubuntuforums.org/showthread.php?t=1882469)

---

### Post by OrangeCrate on 2011-12-02
> **JazzPotato said:**
> I have tried messing with my xorg.conf. I have tried xbacklight. I have tried using dodgy bash scripts i found on the tubes of the internet. I have not yet found a way to turn my goddamn laptop's screen brightness down!!! Its stuck on max and i have 30 mins battery life!

I have heard tales of a mythical "slider" in display settings but i have found no such "slider". 
It is probably obvious, but i'm sure theres a solution!

Thanks in advance.

Install the Compiz Configuration Settings Manager package from the Software Center. Then open the Compiz dialog through Dash, and scroll down to the Ubuntu Unity Plugin. Then, find - Behaviour > Experimental > Backlight Mode, and you find the available backlight options.

---

### Post by OrangeCrate on 2011-12-02
<removed duplicate post>

---

### Post by roger_1960 on 2011-12-03
Hi,

OrangeCrate, I think thats just the backlighting for the launcher icons...

---

### Post by OrangeCrate on 2011-12-04
> **roger_1960 said:**
> Hi,

OrangeCrate, I think thats just the backlighting for the launcher icons...

Oops, you're absolutely right. Sorry for any confusion...

---

### Post by andrew.46 on 2011-12-24
And xbacklight did not work for you? I use xbacklight under fluxbox, bound to some keys, and it works very well. Simple dimming:

```
xbacklight -set 75
```

and restore to maximum:

```
xbacklight -set 100
```

Should be able to bind something like this to keys under your window manager too?

---

