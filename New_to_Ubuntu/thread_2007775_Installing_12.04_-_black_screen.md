---
title: "Installing 12.04 - black screen"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by SammyM on 2012-06-21
Hi there,

I'm trying to install Ubuntu 12.04 on my Dell XPS 15z using a Live CD, but it gets stuck on a black screen with a white slash, after choosing the installation language etc.

In this first screen I choose 'nomodeset', but it doesn't change anything.

What should I do?

---

### Post by NikTh on 2012-06-21
Hi , 
you can try from a LiveUsb . I think its better 
or 
give this command in terminal 
```
sudo apt-get remove ubiquity
``` **before **the installation start.

---

### Post by SammyM on 2012-06-21
Booting from USB won't work, since my keyboard and trackpad drivers don't work, so I need both my USB ports for external mouse and keyboard.

How do I access my terminal? I read some things about selecting 'nosplash', 'noquiet' and 'nomodeset', but the only thing I can set is the 'nomodeset'. The installer won't let me change the other settings.

---

### Post by NikTh on 2012-06-21
> **SammyM said:**
> 

How do I access my terminal?.

Select "Try Ubuntu" and then click on dash ( Ubuntu icon up left) and write **terminal** , open it , remove ubiquity with the command i gave you above and then proceed to installation .

---

