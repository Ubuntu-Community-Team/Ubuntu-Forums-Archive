---
title: "show all running processes"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-13
Hi. is there a keyboard shortcut to show list of all running processess. ie what ctrl alt delete does in windows xp.
M

---

### Post by handydan918 on 2008-11-13
> **irish66 said:**
> Hi. is there a keyboard shortcut to show list of all running processess. ie what ctrl alt delete does in windows xp.
M

In a terminal window, you can enter ```
top
``` or ```
ps aux
```

Just idle curiosity, or is there a reason for your query?

---

### Post by bswilson on 2008-11-13
> **irish66 said:**
> Hi. is there a keyboard shortcut to show list of all running processess. ie what ctrl alt delete does in windows xp.
M

See the other replies about **top** and **ps**, but I believe you could assign a keyboard combination to launch the System Monitor application, which is somewhat similar to the Windows Task Manager.

Here are two good articles ([1]("http://www.cyberciti.biz/faq/howto-create-keyboard-shortcuts-in-gnome/"),[2]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")) on how to do that.

---

### Post by irish66 on 2008-11-13
Wow. talk about quick responses. Yep, it was related to ldc++ running. but not showing on screen. I wanted to use an "end task" option.
Those commands you gave me seem to be to show running processess in text form. I guess what i really want is to be able to stop a program running. 
M

---

### Post by binbash on 2008-11-13
ps aux | grep programname
kill pidnumber

---

### Post by irish66 on 2008-11-13
Thanks everybody
so bin, if i wanted to kill firefox, would it be
ps aux | grep firefox
kill pidnumber

---

### Post by binbash on 2008-11-13
> **irish66 said:**
> Thanks everybody
so bin, if i wanted to kill firefox, would it be
ps aux | grep firefox
kill pidnumber

Sample : 

xxxx@ubuntu:~/compiz/stackswitch$ ps aux | grep firefox
xxxx     18215 11.5  5.2 277244 108540 ?       Sl   03:20   2:38 /usr/lib/firefox-3.1b2pre/firefox-3.1

kill 18215 or sudo kill 18215

you may need sudo at some programs

---

### Post by irish66 on 2008-11-13
Thank you. That seems like a lot of writing though.
M

---

### Post by irish66 on 2008-11-13
actually system moniter is fine. Thank you.Mr wilson.
M

---

### Post by bswilson on 2008-11-13
> **irish66 said:**
> actually system moniter is fine. Thank you.Mr wilson.
M

My pleasure!  We're here to help you as best we can.  :)

---

### Post by uiberto on 2008-11-18
Thanks, those gconf-editor links did just the trick.

---

### Post by Kinetic Being on 2008-11-18
also you could use 

```
killall
```

instead of 

```
kill
```

to kill a program by its name instead of the processid.

Like this:

```
sudo killall firefox
```

would kill firefox.

---

### Post by gettinoriginal on 2008-11-18
CLI is fine, but why not just >System >Admin >Sytem Monitor >Processes >End Process ??

---

### Post by Kinetic Being on 2008-11-18
> **gettinoriginal said:**
> CLI is fine, but why not just >System >Admin >Sytem Monitor >Processes >End Process ??


I agree.

Every fix anyone says is for the CLI, which is very new-user unfriendly.

I understand how its a lot easier to just give a command than guide someone through a GUI, which is why I did just give advice in commands...

but,

It scares people, makes them think that this is the only way to do things, and they think they need to know any of it. It doesn't matter if its faster, or easier (in a way), they don't know that, its just scary to them.

But really, it doesn't matter too much...If they want to learn it they will, if not they can just copy/paste and be done with it...

---

### Post by irish66 on 2008-11-19
Ta, Kb. I might ty that kill command sometime.
M

---

