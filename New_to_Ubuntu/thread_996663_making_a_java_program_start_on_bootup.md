---
title: "making a java program start on bootup"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-29
I have tried making a .sh script to run on startup (through gnome-session-properties  & the /init.d directory)...and I can't seem to get this java (.jar) program running automatically on bootup.

I can manually run the .sh script I made, and it starts up flawlessly....but it won't boot when I try to make it autoboot

---

### Post by linuxguymarshall on 2008-11-29
I don't have Ubuntu in front of me right now but I believe it is System > Administration Or Preferences (Not sure) > Sessions. Then choose the start up tab and add it in.

---

### Post by B34ST1Y on 2008-11-29
thats the same window as running ```
gnome-session-properties
``` in terminal

---

### Post by linuxguymarshall on 2008-11-29
Yeah just do that.

---

### Post by B34ST1Y on 2008-11-29
that doesn't solve my problem. Does anyone know what else I may do?

---

### Post by Xiong Chiamiov on 2008-11-29
Does it need to be at boot-time, when X starts, or when you login?

---

### Post by shafi on 2008-11-29
> **Xiong Chiamiov said:**
> Does it need to be at boot-time, when X starts, or when you login?
go to System -> preferences -> sessions
add your script their.

---

### Post by Xiong Chiamiov on 2008-11-29
I do not believe we are getting anywhere in this thread.

> **B34ST1Y said:**
> I have tried ... [using] gnome-session-properties ... and I can't seem to get this java (.jar) program running automatically on bootup.

> **linuxguymarshall said:**
> I believe it is System > Administration Or Preferences (Not sure) > Sessions.

> **B34ST1Y said:**
> thats the same window as running ```
gnome-session-properties
``` in terminal

> **linuxguymarshall said:**
> Yeah just do that.

> **shafi said:**
> go to System -> preferences -> sessions
add your script their.

---

### Post by jamesstansell on 2008-11-30
> **B34ST1Y said:**
> I have tried making a .sh script to run on startup (through gnome-session-properties  & the /init.d directory)...and I can't seem to get this java (.jar) program running automatically on bootup.

I can manually run the .sh script I made, and it starts up flawlessly....but it won't boot when I try to make it autoboot

How does it fail?  Do any log files capture what the error is?

---

