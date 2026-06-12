---
title: "Password for su?"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by topdog2009 on 2012-03-02
Downloaded & installed 11.10.

Downloaded XAMPP & installed.

Now trying to run XAMPP - needs to start from su BUT su (sudo) asks for password, ???

I have my own password which I used when I installed 11.10 (this does not work) but I did not give sudo a password,. Is there a default password that I can use, if not, how do I run programs using su?

Brian

---

### Post by audiomick on 2012-03-02
> **topdog2009 said:**
> 
I have my own password which I used when I installed 11.10 

The password you use to log on, right? This _***is ***_the password it is looking for. If it is truly not working, then something is amiss.

When you say it doesn't work, what happens exactly to make you think it is not working?

If you are working in a terminal, are you aware that you do not see what you type when you are asked to enter your password in the terminal?

---

### Post by Double.J on 2012-03-02
Hi Brian, 

Afraid forums policy dicatates that we can't share information on enableing the root account - su is actually Switch User, and su followed by a blank space switches to the root user account from your own - this means that you would keep on running with root privilages until you manually switched out. Obviously this increases the chances that you accidentally do something bad, as you won't be prompted for a password again.

As a safty measure, ubuntu uses sudo - this gives you temporarily root privileges whilst that command runs. try running it from the terminal with 
```
sudo xampp
``` or ```
gksudo xampp
``` if it's a graphical program (not used it sorry)

Hope it helps!

---

### Post by audiomick on 2012-03-02
> **topdog2009 said:**
>  needs to start from su BUT su (sudo) asks for password, 

The above leads me to believe you were actually trying to use "sudo", not "su".

Just checked: "su" does in fact not work.
The advice from gnu/mirow applies. Sorry if I confused you.

A quick search indicates that xampp is an Apache package. My guess is you should be using "sudo" rather than "gksudo".

---

### Post by topdog2009 on 2012-03-02
sudo xampp would work but there is now another problem. I will start a new thread,

Thanks

Brian

---

