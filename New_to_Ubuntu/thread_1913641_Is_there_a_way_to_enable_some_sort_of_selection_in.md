---
title: "Is there a way to enable some sort of selection in the login screen?"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by Fabyfakid on 2012-01-22
1. Is there a way to enable some sort of selection in the login screen?

I'm using Lubuntu 11.10, and it's working amazing, but I want to know if I can make the login screen function similar to what other distros like ubuntu and mint have: a selection list for the different users so that I just have to click on the username I want to login as, instead of manually typing my choice. 

2. How can I change the way time is shown on the desktop?

Right now, it's in "military time" I'd like to have it in 12 hour format.

Thanks in advanced for your help!!!!

---

### Post by SteveDee on 2012-01-24
> **Fabyfakid said:**
> 
2. How can I change the way time is shown on the desktop?



Open LXterminal and type:-
```

man strftime

```
This will give you a list of format codes like this:-
```

       The  characters  of  ordinary  character sequences (including the null
       byte) are copied verbatim from format to s. However, the characters of
       conversion specifications are replaced as follows:

       %a     The abbreviated weekday name according to the current locale.

       %A     The full weekday name according to the current locale.

       %b     The abbreviated month name according to the current locale.

       %B     The full month name according to the current locale.

       %c     The  preferred  date  and  time  representation for the current
              locale.

```
While keeping this screen open, right-click on the clock on desktop panel and select "Digital Clock" Settings.
Enter the required code in Clock Format string.
e.g. to display a 12hr clock plus my name I use:-
```

%I:%M steve

```

I hope this makes sense, but ask if you need clarification.

---

### Post by mastablasta on 2012-01-24
> **Fabyfakid said:**
> 1. Is there a way to enable some sort of selection in the login screen?
 
I'm using Lubuntu 11.10, and it's working amazing, but I want to know if I can make the login screen function similar to what other distros like ubuntu and mint have: a selection list for the different users so that I just have to click on the username I want to login as, instead of manually typing my choice. 
 

 
you need to install a different login manager probably. i thing Ubuntu uses gdm or something like that.: [http://projects.gnome.org/gdm/](http://projects.gnome.org/gdm/)

---

