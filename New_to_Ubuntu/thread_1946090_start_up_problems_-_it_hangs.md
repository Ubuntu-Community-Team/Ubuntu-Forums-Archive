---
title: "start up problems - it hangs"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by 007casper on 2012-03-24
After the new kernel update, I am having start up problems.  After I shot the computer down, and when I restart it.  I get...

> 
*skipping profile in /etc/apparmor.d
/disable:usr.bin.firefox [ok]
*setting sensors limits [ok]
*Not starting jetty-edit etc/default/jetty and change NO_START to be 0 (or comment it out)
*starting common unix printing system:cupsd


Hard shut down, then turn it on.  Same message.  

I had to cycle the 'puter 8 times to start.  When I got into safe mode, I just couldnt make out what was on screen.

Finally, after 8 tries it works.  

Why does it hang?

I wonder how crucial jetty is on start up, and consequences of commenting out, or 0 out.

---

### Post by 007casper on 2012-03-24
bump

---

### Post by Kevin McCready on 2012-03-24
Advanced title search on jetty gives 12 hits. Let us know if none of them solve the problem.

[http://ubuntuforums.org/search.php?searchid=85915335]("http://ubuntuforums.org/search.php?searchid=85915335")

---

### Post by 007casper on 2012-03-24
advanced search didnt help out.

I wonder why it hangs.
> 
*Not starting jetty-edit etc/default/jetty and change NO_START to be 0 (or comment it out)

is that the problem???

---

### Post by 007casper on 2012-03-25
I am seriously having this problem... nobody is here to help out

---

### Post by 007casper on 2012-03-27
bump

---

### Post by kevdog on 2012-03-27
Not starting jetty-edit etc/default/jetty and change NO_START to be 0 (or comment it out)

So why don't you try what it states -- edit the /etc/default/jetty and file and put a #sign in front of the line with NO_START or set NO_START to 0

---

### Post by 007casper on 2012-03-28
yes, I could do that... however, I want to know why it hangs after the kernel update.
And why it happens sometimes, and not other times.  Because of that I really dont think thats the real problem.
 
If thats the real problem, how come it doesnt happen all the time.

In addition to that mouse stops working occasionally, then it works again.  It is weird.

---

### Post by 007casper on 2012-03-28
so, I comment it out.  It still hangs

> 
*starting jetty servlet engine. jetty
*jetty servlet engine started, reachable on [http://puter:8080](http://puter:8080). jetty


so reboot and made it 0.  It hangs again
> 
*setting sensors limits [ok]
*starting jetty servlet engine. jetty [ok]
*jetty servlet engine started, reachable on [http://puter:8080/.jetty](http://puter:8080/.jetty)


it still hangs.  It has nothing to do with commenting out jetty.

???

---

