---
title: "avant window navigator"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-05-01
Hi, i can not get avn to start. could someone help please?

---

### Post by jcwmoore on 2008-05-01
go to System>Preferences>Sessions

make sure you have Avant window navigator selected, then it will start when you log in.

---

### Post by NightwishFan on 2008-05-01
Do you have a compositor enabled? (such as compiz-fusion)

---

### Post by KaliVoid on 2008-05-01
if your problem is "Awn Manager" crash then
u need to start "Avant Window Navigator" once after
install (Applications->Accessories->Avant Window Navigator)
and then "Awn Manager" (System->Preferences->Awn Manager)

---

### Post by pikabuntu on 2008-05-01
how would I go about enabling compiz?

---

### Post by pikabuntu on 2008-05-01
how do i get the actual dock to come up from awn manager?

---

### Post by NightwishFan on 2008-05-01
I am not on gnome but if you have decent card with drivers (should be automatic with hardware drivers under administration) The go to System -> Preferences -> Appearance and set effects to normal then run awn and it should come up.

---

### Post by Victormd on 2008-05-01
you might want to install the avant-window-navigator-bzr. I found it to be more stable than the version in the repos'. Just try this link:
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by pikabuntu on 2008-05-01
hope this is useful: if i go to applications>accessories>avant window manager   it does not do anything, but if i go to system>preference>awn manager i get some options about it.  i can not figure out how to make it show up anywhere though.

---

### Post by NightwishFan on 2008-05-01
run this command in terminal and post the output:
```
avant-window-navigator
```

---

### Post by Spoken on 2008-05-01
> **jcwmoore said:**
> go to System>Preferences>Sessions

make sure you have Avant window navigator selected, then it will start when you log in.

+1

---

### Post by pikabuntu on 2008-05-01
here's what i get:

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by pikabuntu on 2008-05-01
does this mean that compiz is not enabled?

---

### Post by pikabuntu on 2008-05-02
i will be back here tomorrow...
sorry for the dumb questions 
i am still *very*new to ubuntu: i only got it a week or two ago =)

---

### Post by NightwishFan on 2008-05-02
Just follow what I said in my previous posts to enable compiz then it should work fine. :KS

---

### Post by pikabuntu on 2008-05-02
it wont let me run system>preferences>appearance under normal. 
i can only run it under none

---

### Post by NightwishFan on 2008-05-02
Go to system -> administrator -> hardware drivers

Check any boxes in there and when they are finished downloading, reboot and try to enable effects again.

---

### Post by pikabuntu on 2008-05-03
the only thing that shows up there is my wireless card

---

### Post by Absorbed on 2008-05-03
What output do you receive when you type these two commands?

```
glxinfo | grep direct
lspci
```

---

### Post by Victormd on 2008-05-03
What graphics card do you have?
You have to enable the 3D support on your graphics card to get compiz working and only then will you get AWN to work...

---

