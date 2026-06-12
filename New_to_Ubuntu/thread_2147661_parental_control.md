---
title: "parental control"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by ksenija on 2013-05-22
can anyone help
I have installed parental control on my ubuntu 12.04 from ubuntu software center, but When I double click on it nothing happens.
thank you!

---

### Post by lykwydchykyn on 2013-05-22
I believe it's broken, and has been for some time.  AFAIK there really aren't many viable parental control options in Ubuntu right now.

What specifically do you want to accomplish with parental controls?  There may be a workaround.

---

### Post by monkeybrain2012 on 2013-05-22
If I was still a kid I would love to find ways to work around parental control. :)  I am actually happy that this option is broken in Ubuntu.

---

### Post by ksenija on 2013-05-23
> **ksenija said:**
> can anyone help
I have installed parental control on my ubuntu 12.04 from ubuntu software center, but When I double click on it nothing happens.
thank you!
I would like to set timelimit for my children.

---

### Post by newb85 on 2013-05-23
If I remember right, the biggest problem with gnome-nanny is that its dependency list is incomplete.  There's a package (sorry, I don't know which one) that gnome-nanny needs to run which is automatically included in Gnome, but is not in Unity.  When I was running Precise, I got Nanny to work by installing the Gnome DE and then installing Nanny.

Well, there were a few caveats.  Scheduling for browser, email, and chat clients were all in GMT for some reason.  And scheduling for login in didn't work at all, for some reason.  (Probably, that was because I was still using LightDM instead of GDM.)

---

### Post by lykwydchykyn on 2013-05-23
> **ksenija said:**
> I would like to set timelimit for my children.

Offhand I don't know of a way to limit the *amount* of time the child can be logged in -- there used to be a program called timekpr that could do this, but it too is no longer functional -- but there is a way to limit *when* they can log in.  It's slightly "under the hood" and cryptic, unfortunately, but it's doable.

Someone did a good writeup on how to to this here:  [http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time](http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time)

Scroll down to the second answer or so that involves PAM.

Like I said, it's not simple, unfortunately; but if you really need to do this, it works.

---

### Post by grover66 on 2013-10-17
I had this issue to... So I wrote this kidtimer script, which lets you define usage times and totals for local user accounts.
[https://github.com/grover66/kidtimer](https://github.com/grover66/kidtimer)

---

### Post by mastablasta on 2013-10-18
looks like a nice little script. does it consume a lot of resources?

---

### Post by jeehyun on 2013-10-18
Canonical should make this program as bundle app for ubuntu.

---

