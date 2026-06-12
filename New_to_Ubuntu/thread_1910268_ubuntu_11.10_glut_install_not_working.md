---
title: "ubuntu 11.10 glut install not working"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by sealsix on 2012-01-16
Hey guys, I tried posting this to askUbuntu and it didn't seem like the right place and was told to try it here. So here is what I posted and hope someone could help me out.  

I currently installed ubuntu 11.10 on my acer netbook overwriting my previous windows starter OS and am having a problem getting some packages I need for an upcoming class. I am using the most updated version and have a wifi connection on my campus. This is what my instructor wishes for us to do:

1. select Applications/Accessories/Terminal on the Ubuntu desktop
2. type ls /usr/include/GL if glut.h gl.h etc are there, great if not, if you are root (prompt #)type apt-get install libglut3-dev if asked, answer yes if you are a user login, type sudo apt-get install libglut3-dev
3. I then copied program1.c to the desktop IF needed you can e-mail files to yourself and use Ubuntu web browser to retrieve
4. cd desktop
5. gcc -lglut -lGLU program1.c note l is a lower-case L, which means library in UNIX
.6. /a.out to execute

I complete step 2, in which returns:

ls: cannot access /usr/include/GL: No such file or directory

so from here I do the apt-get and try to install it but returns me with this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libglut3-dev

Does this have to do with my connection or is there something I need to be doing on my system for it to find the package and install it. I'm really new to ubuntu and could use some help just getting started.

---

### Post by grahammechanical on 2012-01-16
Hi and welcome to the forums. I am glad you took my advice. The fact that you are using Ubuntu is immaterial. This is a Linux question and I think that it is very bad that the so-called professional and enthusiastic programmers on Stackoverflow passed you over to Askubuntu.

So, we have worked out that you do not have Glut installed on your system. I think that the other problem is that the Glut libraries like libglut3-dev are not in the Ubuntu repositories. So, where can you get them from? And I am trying to find the answer to that.

Perhaps someone else will know for sure.

Regards.

---

### Post by sealsix on 2012-01-16
Thanks for the welcome, and I'll try looking for  the repositories but from what my instructor stated, i don't get why it would be a problem.  I almost wonder if it is because I am running it on a netbook, but that's just a guess.

---

### Post by grahammechanical on 2012-01-16
Hi again. I found this link

[http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=285994]("http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=285994")

Note the first post. You could try running that command again but instead of libglut3-dev try sudo apt-get freeglut3-dev. This library I know is in the Ubuntu repositories.

Also if you search in your web browser for linux glut tutorial you will find at least two sites that have a downloadable PDF tutorial for Glut which you may find useful to have. One tutorial says this:


> Precompiled binaries available in most GNU/Linux distributions, for
example on debian &#8220;apt-get install freeglut3-dev&#8221;, suffices to install it.

By the way Ubuntu is based upon Debian.

Regards.

P.S. If your tutor wonders about freeglut instead of glut you can direct him to this page:

[http://freeglut.sourceforge.net/]("http://freeglut.sourceforge.net/")

---

### Post by sealsix on 2012-01-16
Thank you so much, works nicely and I will definitely be looking into those tutorials. Thanks again for your help.

---

### Post by sandeep25292192 on 2013-02-14
hey there, i am facing a similar problem as stated above. I have tried both your suggestions but i am still facing this error message:


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Hoping you have a solution.....

Awaiting your reply.

---

### Post by grahammechanical on 2013-02-14
Have you accepted the advice from the error message to run?

```
sudo dpkg --configure -a
```

What messages do you get? What were you trying to do?

Regards.

---

### Post by sandeep25292192 on 2013-02-15
I was trying to install glut.

Thank you very much for your response. :P  I figured it out!

---

