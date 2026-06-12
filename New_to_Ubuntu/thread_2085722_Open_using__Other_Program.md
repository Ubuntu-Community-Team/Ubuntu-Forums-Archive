---
title: "Open using  Other Program"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by gbrowning on 2012-11-18
I should know how to do this but I cannot seem to come up with an answer.
  If I try to click on an email link inside Opera I get this error message
*You have not specified an external helper application. Do you want to modify the configuration now?*
  I get to a point where Nautilus is opened and the Opera is waiting for me to find a program to specify.
  How do I find the program to specify?  I want to use Thunderbird.

---

### Post by aliddell on 2012-11-18
Thunderbird, by default, lives in /usr/bin:

```
/usr/bin/thunderbird
```In the future, you can find this via the [FONT=Fixedsys]which[/FONT] command:
```
which thunderbird
```

---

### Post by stinkeye on 2012-11-19
In opera prefences, set the mailto protocol to use /usr/bin/thunderbird.

---

### Post by gbrowning on 2012-11-19
thank you. the *which* command is the simple OMG I can't believe I didn't do this before answer.

---

### Post by aliddell on 2012-11-19
No problem. I forget that kind of stuff all the time.

---

### Post by SantaFe on 2012-11-21
There's also 'whereis' I.E.
> s******@s******-Studio-1745:~$ whereis thunderbird
thunderbird: /usr/bin/thunderbird /etc/thunderbird /usr/lib/thunderbird /usr/bin/X11/thunderbird /usr/share/man/man1/thunderbird.1.gz
s******@s******-Studio-1745:~$ 


Useful if you want to see every occurrence of Thunderbird. ;)

And yes I know, I should have used the Code tags, but it was very small example. :D

---

