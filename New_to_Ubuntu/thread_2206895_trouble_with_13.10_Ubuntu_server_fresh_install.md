---
title: "trouble with 13.10 Ubuntu server fresh install"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by aaron27 on 2014-02-21
Good afternoon, this is my first post here so please bare with me. Please also note I am a dreaded 15 year Windows user who has just installed first Linux based system so if anything doesn't make sense I apologise.

So here goes. I have just installed Ubuntu server version 13.10. I do not currently have a GUI so everything is being done in command line. I do however want a gui - but will come to that later.

It would appear that I currently do not have any network access. (I have set this up using a virtual machine on VMWare). I am trying to use a static ip configuration.

Running route -n gives the following:

Kernel IP Routing table
destination   gateway        genmask
0.0.0.0        172.16.12.1    0.0.0.0 
172.16.0.0    0.0.0.0         255.255.0.0

I cannot ping opendns servers.


I can run an ifconfig -a if it would help at all?

Can anyone help this lost newbie? The end result is I want to get out of command line and use a GUI.

KR

Aaron

---

### Post by varunendra on 2014-02-21
Welcome to the forums Aaron ! :)

What kind of networking have you selected for the Virtual Machine? NAT? Bridged? Something else?

And how have you configured the networking INSIDE your VM, in Ubuntu? Using /etc/network/interfaces file I guess. If so, could you please post its contents? Commands to get that, and some other information that I'd like to see -
```
cat /etc/network/interfaces
ifconfig -a
sudo lshw -C network
```

You should be able to copy the outputs from the terminal in the VM (using your mouse cursor) to a text file or directly into the browser (into your next post here) on the host (outside the VM). But for that you must have VMware tools installed first. Have you installed it yet?

Please note that I need to see the full outputs, so if you had to write it down by hand (if copy-paste between host and guest doesn't work), you'll need to be extra careful. Maybe you could use a pendrive inside the VM without installing VMware tools, I'm not sure about that.

And please use 'Code' tags for posting the outputs. It preserves the formatting and makes it more readable. Please follow the "Using Code Tags" link in my signature to see how to use it.

---

### Post by aaron27 on 2014-02-24
Hi Varun,

I have got the network working, I was using NAT on the the virtual machine and have changed this to bridged :) I have now installed Gnome GUI and things are progresssing :) 

Thank you for the advice.

Aaron

---

### Post by varunendra on 2014-02-24
Glad you got it sorted by yourself. :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. It helps others by indicating that the thread contains a possible solution to the problem in the title.

---

