---
title: "Easy Quesion of the Day (I think)"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by nosmadar on 2008-11-08
Is there a way to determine which version of Ubuntu is running.  "uname" will tell me about the underlying Linux kernel.  And I'm actually running Kubuntu - so of course I can find the KDE version as well. But I want to experiment with several different versions (Ubuntu / Kubuntu... ) and it would be nice, while in the midst of doing something, to confirm which version I'm actually running - before I do something I will regret later.

Thanks...

---

### Post by Steve1961 on 2008-11-08
cat /etc/lsb-release

---

### Post by gpsmikey on 2008-11-08
You could always put whatever you want in /etc/motd and cat that anytime you wanted to -- and it would show when you logged in too.  That's the easiest way that comes to mind off hand for me.

mikey

---

### Post by nosmadar on 2008-11-08
Thanks! 
And just to clarify for any one else who stumbles on this:
cat /etc/lsb-release
is what worked because lsb-release lives in /etc

---

### Post by nosmadar on 2008-11-08
Thanks...great Idea.

---

### Post by phidia on 2008-11-08
> lsb_release -a entered in a terminal-of course-does it too.

---

