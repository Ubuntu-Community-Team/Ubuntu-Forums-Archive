---
title: "question what is better to do"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by moekernel on 2008-07-02
Hi:
I have a question.

I will like to work on learning more about lamp by installing a lamp system on my laptop so I can play with it by writing little applications in a non-web environment.

Should I 

1) Install LAMP on my ubuntu desktop   or
2) Install  the ubuntu server and delete the ubuntu desktop?

I would like to still be able to use my laptop as a regular computer for regular web surfing.  But I also want to have learning environment for lamp.

What is the best thing to do?

Please advice.

Thank you.

Moe

---

### Post by mcduck on 2008-07-02
If you still want to use them machine as desktop computer, keep the install you have now and install the LAMP stack from Synaptic.

Uninstalling the desktop, installin ubuntu-server and then installing the desktop would bring you back to where you are now. Doesn't really make much sense.. ;)

---

### Post by hyper_ch on 2008-07-02
if you want to run that box as pure server, install the server version...

however if you want to also use it as desktop, make a desktop install and then install the services that you want to run.

---

### Post by .nedberg on 2008-07-02
The best solution would be to get a separate computer. You could probably pick one up for free or very little money.

I run one server at home for testing and it is only a 300MHz with 192MB RAM.

This way you will not need to have services running on your desktop when you don't need them and the webpages will be available from every computer on your LAN.

---

### Post by mevets on 2008-07-02
ubuntu-server is completely non gui, at least last time I used it, so you wont be able to use it as a desktop without installing additional packages after the initial install. You also probably want to run the desktop so you can run the various gui server tools like gproftpd, etc.

---

### Post by watsbe on 2008-07-02
If you only have the one computer, then just use Synaptic to install the LAMP components you want.  One at a time is probably a good thing.
... but ... I agree with .nedberg.  Try and pick up some cheap second-hand gear to build a "toy" computer.  It is simple.  It is great fun.  It is satisfying.  If it breaks, it doesn't matter.
You also learn a great deal more about real-world computing by running things on a different box across a network.

---

### Post by fatality_uk on 2008-07-02
> **moekernel said:**
> Hi:
I have a question.

I will like to work on learning more about lamp by installing a lamp system on my laptop so I can play with it by writing little applications in a non-web environment.

Should I 

1) Install LAMP on my ubuntu desktop   or
2) Install  the ubuntu server and delete the ubuntu desktop?

I would like to still be able to use my laptop as a regular computer for regular web surfing.  But I also want to have learning environment for lamp.

What is the best thing to do?

Please advice.

Thank you.

Moe

I suggest using the environment you have. Your laptop would only have a comman line if you install the server version of Ubuntu, plus it's not really required. If all you are doing is testing an developing, then your current desktop will be more than fine.

Best way to install LAMP is to go to Synaptic Package Manager and it the edit menu, select "Mark packages by task..." This will install a LAMP stack for you automatically including MySQL. Then, from Synaptic again, install phpmyadmin.

Once those two are up and running, you will have a LAMP server in two easy clicks.

---

### Post by moekernel on 2008-07-10
:popcorn:
Thanks everybody for your help.
I did install lamp.

---

