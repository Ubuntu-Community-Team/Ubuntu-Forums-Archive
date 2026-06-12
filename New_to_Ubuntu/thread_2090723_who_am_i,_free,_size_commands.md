---
title: "who am i, free, size commands"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by pras8421 on 2012-12-03
Hi, . . 

I am quite new to UNIX/LINUX and I got stuck in doing my project to implement who am i, free and size commands. 

I am unable to get the required information in the web.
Can anybody suggest me simple codes(preferably in C or C++) for the above commands(the options such as -a, -f, -r are unnecessary). I am sorry as it's not so relevant to Ubuntu. .

---

### Post by Tony Flury on 2012-12-03
No-one on the forums will help you do your homework, but If you can provide an attempt at a solution in which you can states a specific problem then people will help with that.

It is best to post programming questions to the Programming Talk forum.

---

### Post by MG&amp;TL on 2012-12-03
While I understand it's not foolproof, one easy way of implementing whoami is to use the $USER environment variable.

---

### Post by drmrgd on 2012-12-03
Don't know why you need such commands in C.  Looks like some are in the C library already, and if you need more control, you can do it with 'popen' or 'system()':

[http://www.unix.com/programming/35027-bash-c.html](http://www.unix.com/programming/35027-bash-c.html)

---

