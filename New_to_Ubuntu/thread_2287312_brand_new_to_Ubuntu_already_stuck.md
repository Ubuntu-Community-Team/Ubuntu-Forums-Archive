---
title: "brand new to Ubuntu already stuck"
date: 2015-07-18
forum: New to Ubuntu
---

### Post by jerry50 on 2015-07-18
I decided to install Ubuntu 14.04 on a Win.7 64 bit home pc, with dual boot options.  As I was playing around in Ubuntu there came a point when it asked me for my password.  I hadn't even put one in yet!  I also bought the "Getting Started with Ubuntu 14.04" manual, and it tells how to reset the password: get to recovery menu, at terminal prompt enter ** passwd username** (replacing username with mine), then when prompted for a password enter it, then again because Ubuntu asks for it twice.

I do all that and I get this message:  **passwd: Authentication token manipulation error    passwd: password unchanged**

So...what am I doing wrong?

---

### Post by Geoffrey_Arndt on 2015-07-18
How in the world is it possible to install Ubuntu without assigning a password right after providing a user name?   Did you just skip through that screen (and why does the installer allow that?)   Wow, live and learn I guess . . . 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://askubuntu.com/questions/294946/how-to-change-root-password-in-ubuntu](http://askubuntu.com/questions/294946/how-to-change-root-password-in-ubuntu)

---

### Post by slickymaster on 2015-07-18
See this thorough thread in askubuntu: [Getting an “Authentication token manipulation” error when trying to change my user password]("http://askubuntu.com/questions/57620/getting-an-authentication-token-manipulation-error-when-trying-to-change-my-us")

---

### Post by jerry50 on 2015-07-18
I didn't install it.  I had a tech from a store do it.  He was setting up a dual boot with Win 7.  He never gave me the password.  I tried variations of things he could have used, to no avail.  So, I followed the directions from the link you gave (psychocats) and it worked like a charm.  The problem was the file system is in read only, so once I used "mount -o rw,remount /" I was. able to continue with setting up my password.

Thanks so much, Geoffrey!  This noob is very appreciative.

---

### Post by sandyd on 2015-07-18
Hi, if you have found a solution, please mark this thread as Solved via Thread Tools -> Mark Thread as Solved.

Thanks!

---

### Post by Buntu Bunny on 2015-07-21
> **jerry50 said:**
> I didn't install it.  I had a tech from a store do it.  He was setting up a dual boot with Win 7.  He never gave me the password.

Seems like the simplest thing to do would have been to call the tech guy and ask what password he used. Still, you learned a lot and so did I from reading this post. Have to love the Ubuntu Forums for that.

---

