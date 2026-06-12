---
title: "what does the gnome taskbar clock applet use to get its time info?"
date: 2010-09-02
forum: Programming Talk
---

### Post by pythonscript on 2010-09-02
I'm trying to write a python script that will give me the times in various cities, plus the time zone, GMT/EAT offset, etc, and I really like the information that the Gnome taskbar clock applet uses. Where does it get this information? Is this some sort of api that I could get with GET/POST, or elsewhere?

Thank you!

EDIT:  Or if someone knows of a better, free service that has an api that could give me all that information, of course that would be appreciate as well!

---

### Post by ssam on 2010-09-02
have a look at tzdata and python-tz

---

### Post by Joeb454 on 2010-09-02
Moved to Programming Talk - I imagine somebody here will be able to help you out :)

---

### Post by wojox on 2010-09-02
Nevermind

---

### Post by hakermania on 2010-09-02
There are plenty of command to get current system time/hour etc. Have a look at command **date**

---

### Post by pythonscript on 2010-09-03
I'm not so much interested in the current system time/date in my location; it's the functionality that the applet uses where it displays information about various cities/locations based on time zone. I think tzdata might be what I'm looking for; is this what the applet uses?

---

### Post by hakermania on 2010-09-03
Maybe the applet have a source which says it from where the our is set and with simple mathematic can calculate the hour in other places on earth

---

### Post by pbrane on 2010-09-03
gnome-panel applets - clock source:
[http://git.gnome.org/browse/gnome-panel/tree/applets/clock]("http://git.gnome.org/browse/gnome-panel/tree/applets/clock")

---

