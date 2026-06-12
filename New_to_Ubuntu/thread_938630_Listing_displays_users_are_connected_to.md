---
title: "Listing displays users are connected to"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by pooppoop on 2008-10-05
How can i list all the displays(like this :0) that are active on my box?

---

### Post by pooppoop on 2008-10-05
-bump-

---

### Post by cjv8888 on 2008-10-05
cannot understand your question.

---

### Post by pooppoop on 2008-10-05
I want to view all available displays, when i connect with nxserver for example i have the :0 display(the monitor) and 5342: display which is the nxserver x11 display window, how can i list all those displays(echo $DISPALY doesn't help because it only return the current display i am on)

---

### Post by bodhi.zazen on 2008-10-05
I am not sure what you are asking exactly. 

X sessions are numbered starting with 0 (:0) and goin up to I believe 99 (:99)

When you start an X server you can either assign a number to the session or the system will default to then next number ( 0 ... 1 ... 2 ... ).

You start an X session by starting a X server, X (startx, GDM, etc) or a VNC server or *Xephyr*/Xnest.

In your case you are connecting directly to the FreeNX server and as you connect to each server you are connected to the X session associated with that server.

That I know of you do not choose X sessions when you connect.

---

### Post by pooppoop on 2008-10-05
What i am asking is a way to list all open display on the current machine

---

### Post by bodhi.zazen on 2008-10-05
try the command who :

```
who
```

---

### Post by pooppoop on 2008-10-05
the who command gives me what i want only if there is a console window open on the other display.
still doesn't solve my problem

---

### Post by pooppoop on 2008-10-06
-bump-

---

### Post by pooppoop on 2008-10-06
-bump-

---

### Post by pooppoop on 2008-10-12
Help please

---

### Post by earthpigg on 2008-10-12
i know that, if you have it, the nvidia settings thing has a little 'refresh displays' button that will show you all the displays you have plugged in....

---

### Post by bodhi.zazen on 2008-10-12
I hate to sound like a broken record, but who lists all the displays on my system.

Can you give an example of who not working ?

Ie start a few X sessions and post the output of who.

---

### Post by pooppoop on 2008-10-13
An example of this not working is me connecting localhost using nxserver, it starts a new display the $DISPLAY variable is infact a different $display, i can use xdw to screencapture it, but if i use who or w i can't see the new display unless i run a terminal window on the display. If i do, it shows up on the w or who output

---

