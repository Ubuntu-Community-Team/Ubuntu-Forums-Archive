---
title: "Automatic login and theme problem"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by Mark de J on 2014-05-27
Hi,

I got an theme on my Ubuntu 14.04 LTS what isn't working, now I want get back to the default theme but I can't log off. The system is logged in automatic, I can only use the console, but I have no idea how to log off then to change the theme to default and login again.

Someone who can post a fix?

Thank you.

---

### Post by gijs2 on 2014-05-27
> **Mark de J said:**
> Hi,

I got an theme on my Ubuntu 14.04 LTS what isn't working, now I want get back to the default theme but I can't log off. The system is logged in automatic, I can only use the console, but I have no idea how to log off then to change the theme to default and login again.

Someone who can post a fix?

Thank you.

Try
```
pkill -u username
```
Put your username instead of the username

---

### Post by Mark de J on 2014-05-27
Is that also working in the console, because that is the only thing that works.

---

### Post by gijs2 on 2014-05-27
> **Mark de J said:**
> Is that also working in the console, because that is the only thing that works.

That is what you put in your terminal to log off

---

### Post by Mark de J on 2014-05-27
> **gijs2 said:**
> That is what you put in your terminal to log off
If I said in my first post, I can only use the console: cntrl+alt+F1

> **Mark de J said:**
> The system is logged in automatic, I can only use the console, but I have no idea how to log off then to change the theme to default and login again.

---

### Post by gijs2 on 2014-05-27
> **Mark de J said:**
> If I said in my first post, I can only use the console: cntrl+alt+F1

That should also work there

---

### Post by Mark de J on 2014-05-27
It worked, thanks!

---

### Post by deadflowr on 2014-05-27
ctrl +alt+del is the default keyboard shortcuts to log you out.

---

### Post by Mark de J on 2014-05-27
> **deadflowr said:**
> ctrl +alt+del is the default keyboard shortcuts to log you out.
I know, but that wasn't working. :$

---

### Post by deadflowr on 2014-05-27
> **Mark de J said:**
> I know, but that wasn't working. :$

Being this was a theme debacle, it most likely was working, but invisible to you.
A simple left arrow key + enter might've initiated the log out sequence.
another thing to try would have been
```
sudo restart lightdm
```
that restarts the Xserver, which would auto logout all users from xsessions.

---

