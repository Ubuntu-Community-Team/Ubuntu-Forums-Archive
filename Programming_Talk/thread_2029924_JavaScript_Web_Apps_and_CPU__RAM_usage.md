---
title: "JavaScript Web Apps and CPU / RAM usage"
date: 2012-07-20
forum: Programming Talk
---

### Post by snowz on 2012-07-20
[FONT=Verdana]There was this **Ubuntu** **App** **Showdown**, and there were applications posted that were made with **JavaScript** + **HTML** + **CSS**, so web apps, which were put into a WebKit window made with Python.
In the discussion about the applications I saw some people complaining that the apps can have a pretty big **CPU** and **RAM** usage if I remember right(even the small lightweight applications).

**[COLOR=DarkOrange]Is this true and what can be done to possibly prevent or lower those two?[/COLOR]**
[/FONT]

---

### Post by Dimarchi on 2012-07-21
I would guess that the CPU usage is due to single thread Javascript stuff. Multi threading is something new in that environment, and probably not widely used. RAM usage is due to all three (Javascript, HTML, CSS) in an engine - Webkit in this case - plus whatever Python wrapper might use. No small things, those, I would say. :) I doubt much can be done to lessen their demands when it comes to web app kind of stuff.

---

### Post by snowz on 2012-07-21
Thanks for your response :)

---

### Post by ofnuts on 2012-07-21
> **Dimarchi said:**
> I would guess that the CPU usage is due to single thread Javascript stuff. Multi threading is something new in that environment, and probably not widely used. RAM usage is due to all three (Javascript, HTML, CSS) in an engine - Webkit in this case - plus whatever Python wrapper might use. No small things, those, I would say. :) I doubt much can be done to lessen their demands when it comes to web app kind of stuff.
Event driven apps, multithread or not, don't use CPU between events. These days any app that needlessly burns CPU has very little future, because is draws on batteries...

---

### Post by snowz on 2012-07-21
If being portable is the key, then it might represent a battery problem yeah. If portability isn't that much the main goal then it's the applications performance for sure.

Lets compare, if an application is written in JavaScript, does it use more CPU as if it would be done in Python + GTK because of its HTML + CSS interface?

---

### Post by MadCow108 on 2012-07-22
it depends what the application does
javascript is probably faster than python because its VM's are so very optimized.
on the other hand its easier in python to offload heavy workload into optimized C code.

and as mentioned gui's are normally event driven applications which don't use any cpu at all unless you actually do something, no matter if written in javascript or python/C.

---

### Post by snowz on 2012-07-22
@MadCow108 Thanks for the reply :)

---

### Post by ofnuts on 2012-07-22
> **snowz said:**
> If being portable is the key, then it might represent a battery problem yeah. If portability isn't that much the main goal then it's the applications performance for sure.

Lets compare, if an application is written in JavaScript, does it use more CPU as if it would be done in Python + GTK because of its HTML + CSS interface?
All applications are portable these days... they all run on laptops, and laptops are becoming a vast majority of end-users computers. An app can burn CPU cycles, but for good purpose... 

From a battery point of view, I doubt there is much difference between two well written apps in either language.

---

### Post by snowz on 2012-07-22
> **ofnuts said:**
> From a battery point of view, I doubt there is much difference between two well written apps in either language.

Oh ok, thanks.

---

