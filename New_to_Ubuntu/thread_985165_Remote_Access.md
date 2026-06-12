---
title: "Remote Access"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Angry Dog on 2008-11-17
I want to be able to dial into my pc at home from my windows pc at work.

I do not have a fixed IP at home.

How can i go about doing this please?

---

### Post by prshah on 2008-11-17
> **Angry Dog said:**
> I want to be able to dial into my pc at home from my windows pc at work.
I do not have a fixed IP at home.


If your home router supports dyndns.org (most do) then you can create a free account at dyndns.org and enter the details into your router. Now on, whenever your modem connects to the net, it will update your account name at dyndns.org with the current ip address, so you can access your computer with the account name you've created (Example: forexample.dyndns.org)

You will also need to "forward" ports from your router to your computer, which will depend on the type of applications you want to use, for ex. port 22 for ssh, port 5900 for vnc, etc.

---

### Post by sirjoebob on 2008-11-17
I have used no-ip before with much success. Check [www.no-ip.org](www.no-ip.org) for info. It allows your computer to automatically update it's IP on their server and you can access it by typing YOURUSERNAME.no-ip.org... It works wonderfully for this type of app. You  will still have to port-forward on your router to forward the appropriate ports to your computer. I have done this with SSH, VNC, apache, gnump3d, among others and it works great if you have it setup right.

---

### Post by Angry Dog on 2008-11-18
Thanks guys, I really appreciate that information!!

---

### Post by sirjoebob on 2008-11-18
If this solved your question, remember to mark as solved.

---

