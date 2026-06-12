---
title: "Nice command in Hardy"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Faud on 2008-05-02
I am unable to use the nice command in Hardy. I used to be able to get into my system monitor and then right click on a application and change the priority. As soon as the bar comes up that I can move to -20 - +20 and I choose a "nice" level a bar pops up that says "starting administration" and then just closes, changing nothing.
Any ideas ?

---

### Post by freebeer on 2008-05-02
My guess (and that's what it is) is that the app you're using to change the level requires the correct permissions.  Maybe try launching that app with sudo or gksudo might help.

---

### Post by mivo on 2008-05-02
It seems to be a bug -- same happens on my box, even if I have the proper permissions (changing an app I just started). (And the system monitor is "my" process as well.)

---

