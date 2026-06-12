---
title: "ktechlab  problem"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by cosine352 on 2008-11-06
Hi friends, 
I was using this "ktechlab" application to simulate some circuit elements. When I try to use it is crashing. Here is what terminal is saying
> ktechlab 
kbuildsycoca running...
KCrash: Application 'ktechlab' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.


I am using ubuntu 8.10 
any help will be greatly appreciated. 

Thanks

---

### Post by Daveth on 2008-11-06
where did you get it from? It should not crash if from the repositories....

---

### Post by cosine352 on 2008-11-07
I did install it from repositories of Ubuntu 8.10. 
> sudo apt-get install ktechlab

I also reinstalled it.

> sudo aptitude reinstall ktechlab

It opens up and when I try to drag some circuit element to drop it on the board, it crashes.

---

### Post by Martin von Wittich on 2008-11-08
Same problem here. It's definitely a bug in this program version that unfortunately made it into the repository. I will try to compile it from source...

---

### Post by fatihsola on 2008-11-09
hello, i have been using ktechlab recently; it is very well as i see.

about the executing problem;

when a friend of mine mentioned the program, i downloaded 

ktechlab_0.3-6_i386.deb from [www.ktechlab.org](www.ktechlab.org). it worked with bugs. so i 

had to back-up often. after a while, i have been notified that there was a 

newer version of ktechlab. i accepted to update. after updating the 

program, i could not execute the program any more. 

i uninstalled it on command line; 


sudo apt-get remove ktechlab


then installed ktechlab_0.3-6_i386.deb from ktechlab.org again. i advice you to do same.

---

### Post by arunkumar413 on 2008-12-26
iam using ubuntu8.04 and installed ktechlab.There is not problem with ktechlab

---

### Post by magusjonny42 on 2009-07-19
im new to linux, installed it to use this program, only problem now is...how do I run it? Is there any way I can get installers to put a shortcut on my desktop?

---

### Post by cosine352 on 2009-07-19
'Alt+F2' and type 'ktechlab'

---

### Post by magusjonny42 on 2009-07-22
> **cosine352 said:**
> 'Alt+F2' and type 'ktechlab'

Thanks, it runs now. Although it seems to crash when I try and place a component on the breadboard. Im guessing thats just a bug.

---

### Post by cosine352 on 2009-07-22
> **magusjonny42 said:**
> Thanks, it runs now. Although it seems to crash when I try and place a component on the breadboard. Im guessing thats just a bug.

that is right

---

### Post by robertrej on 2009-12-12
I had a problem with ktechlab crashing and found out  that it runs fine
as long as you do not allow and automatic Updates which seem to pop
up along with regular system updates. I just uncheck ktechlab updates
and allow all others to go though.I installed ktechlab 0.3-6_i386
and no problems at all. Its a neat little program ( flashing LED's )!


                                   Happy holidays
                                   Bob

---

### Post by jmcgovern on 2009-12-12
i notice the name is *k*techlab. Is everyone trying to run this under GNOME?  Has anyone tried it in KDE?  some gnome apps dont work wel in KDE even though most do, and vice versa, (I've had a problem with Kompozer before).

---

