---
title: "synaptic error help"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by janne5011 on 2008-06-25
I tried to install 2 apps when things wntwrong and only way was a reboot under the time installation procdeed.
now when I try to start synpatic I got this msg:
dpkg was interuppted run dpkg --configure -a to correct the problem.
so that was I did but it dont helps.
So I cant start synpatuc becuse of this and apt-get dont works.
anyone got a solution?

thanks in advance
/J

---

### Post by avtolle on 2008-06-25
When you ran```
sudo dpkg --configure -a
```what error messages did you get, if any?

---

### Post by arochester on 2008-06-25
Just open a terminal and input > sudo dpkg --configure -a 

---

### Post by janne5011 on 2008-06-25
> **avtolle said:**
> When you ran```
sudo dpkg --configure -a
```what error messages did you get, if any?

not any errormsg. But motion and a another program starts after one more file  is installed  application:"webcam". At the same time the application "motion-demon" is started which make webcam crach.
Its a mess. should I reinstall ubuntu its a fresh install so I didnt do much work on it yet?

---

### Post by janne5011 on 2008-06-25
> **arochester said:**
> Just open a terminal and input

as said it dont works.

---

### Post by taavikko on 2008-06-25
Also use ```
sudo apt-get -f install
```
in conjuction with dpkg --configure
both commands one at a time.

---

### Post by janne5011 on 2008-06-25
> **taavikko said:**
> Also use ```
sudo apt-get -f install
```
in conjuction with dpkg --configure
both commands one at a time.

when I do "sudo apt-get -f instal" it says
dpkg was interuppted run dpkg --configure -a

...

---

### Post by Elfy on 2008-06-25
So what error messages are you actually getting because there'll be a bit more detail than that

---

### Post by janne5011 on 2008-06-25
> **forestpixie2 said:**
> So what error messages are you actually getting because there'll be a bit more detail than that
As I told in the last post: "dpkg was..."and thats it.
If there was some more errormsg:s I should appreciate it,and I should have putte them here of course.
 but there is no more. 

Anyway I give up and reinstall.it will be faster.
thanks to thoose who tried to help

---

### Post by Elfy on 2008-06-25
If you run an apt-get command it should give you an error message which would say what package was causing the problem, then perhaps we can get it sorted without resorting to a reinstall.

That said after 20 minutes if you've started it'll be nearly finished now :)

---

