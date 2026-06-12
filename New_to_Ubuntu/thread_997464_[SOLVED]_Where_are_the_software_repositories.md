---
title: "[SOLVED] Where are the software repositories?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gshockxc on 2008-11-29
I was reading the Documentation, and I'm not quite sure that I understand exactly "where" the software repositories are.  I take it that I need internet access to get to them, and they are available through my Ubuntu distribution.  

Unfortunately, I'm still waiting for my internet to get connected so I was looking to install OOov3, and play around a bit while I'm waiting for that to happen.  I got the right file (something, something.tar.gz), which I'll have to figure out how to install later.

But for future reference, once I do have internet access, how to I connect to the repositories and install other software?

-Thanks, 
gshock

p.s. what are tags for, and how do I use them?

---

### Post by Xiong Chiamiov on 2008-11-29
[This]("http://www.psychocats.net/ubuntu/installingsoftware") will give you a good overview of installing software in Ubuntu.  The repositories themselves are hosted on Canonical's servers, and you can browse them at packages.ubuntu.com.

Tags are used by the forum to help you find other questions similar to yours when searching.

---

### Post by gshockxc on 2008-11-29
> **Xiong Chiamiov said:**
> [This]("http://www.psychocats.net/ubuntu/installingsoftware") will give you a good overview of installing software in Ubuntu.  The repositories themselves are hosted on Canonical's servers, and you can browse them at packages.ubuntu.com.

Tags are used by the forum to help you find other questions similar to yours when searching.

I couldn't find anything that gave me the location of the repositories, but I could have missed it.  I'm on my work laptop now, on XP, but when I get internet on my Ubuntu machine, do I just connect to the repositories from the OS, or do I browse them like a webpage?

So do I use tags in my post, or do the forum moderators put those in?  

Thanks, 
-gshockxc

---

### Post by Xiong Chiamiov on 2008-11-29
> **gshockxc said:**
> I couldn't find anything that gave me the location of the repositories, but I could have missed it.  I'm on my work laptop now, on XP, but when I get internet on my Ubuntu machine, do I just connect to the repositories from the OS, or do I browse them like a webpage?

The actual location depends on which version of Ubuntu you have, and I don't know any of them offhand.  When accessing them, you'll just use one of the tools that runs on-top of APT.  The most commond are Add/Remove and Synaptic for graphical interfaces, and apt-get and aptitude for terminal-based.

> **gshockxc said:**
> 
So do I use tags in my post, or do the forum moderators put those in?  

It's something you do, but I'm not sure how often they actually get used.

---

### Post by adult swim on 2008-11-29
on your ubuntu machine go to system>administration>synaptic package manager
or go to applications>add/remove
both of these are graphical tools to let you download and install things from the repositories.  they are basically  big software databases and whenever you choose to install something all you have to do is select it and it will be downloaded and installed.

---

### Post by Xiong Chiamiov on 2008-11-29
> **adult swim said:**
> whenever you choose to install something all you have to do is select it and it will be downloaded and installed.

...along with anything else required to make them work.  Welcome to package management.

---

### Post by OrangeCrate on 2008-11-29
Here's another good read on repositories...

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The proper use of tags on the forums is spotty at best. Searching for specific terms either here, or on the engine of your choice, will probably serve you best.

---

### Post by Sealbhach on 2008-11-30
If you go into System/Adminstration/Software Sources you will see a "Download From" button, click on that and then click on "Select Best Server".

This will make your computer ping all the available servers and select the quickest one for you. Well worth doing, will make downloads a lot faster.


.

---

