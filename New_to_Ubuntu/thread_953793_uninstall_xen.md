---
title: "uninstall xen"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by happytechie on 2008-10-20
Hi all,

I installed xen to try and get a bootable version of windows installed to do some .NET development.  It's changed the boot loader (grub ?) to add a load of other options.

It's going to be more hassle than I can deal with to get it all working so can anyone help with removing xen and leaving my machine in a bootable state?

at the moment I have to hit esc during boot and select the local install from the numerous options, the xen ones leave me with a blank screen.

I know that I've been stupid and dived in installing stuff without researcing it propperly :(

---

### Post by Hexagoon on 2008-10-20
Just some questions to make the answering a bit easier; did you install it by synaptic, add/remove software or did u compile it by hand? And if you installed it with synaptic or add/remove software, have you tried just to uncheck it there and then pressing ok or apply?

---

### Post by happytechie on 2008-10-20
I think I used an apt-get command but I can't find the instructions I followed on the web now :( I was surprised when it got into by grub config and I thought I'd bricked my laptop until I pressed esc during the grub load messages.

I definitely didn't compile it by hand if that helps.

sorry for the lack of information

---

### Post by aeiah on 2008-10-20
xen is a bit special and advanced. what it did was turn your ubuntu installation into the hypervisor by compiling an optimised kernel, and it enabled this kernel to boot from grub. dont panic :p

you can uninstall xen through synaptic the normal way buy before you do this you'll want to edit your menu.lst file. this is the config file that grub looks at to decide whats available, and what to boot to by default. its pretty self explanatory. so, in a terminal:

```

sudo gedit /boot/grub/menu.lst

```
right, reading the menu.lst file, remember that anything starting with a # is just a comment, and isnt read by grub.

you'll see it says something like "defaut 0" somewhere near the top. except yours probably wont say 0, it'll probably be another number. further down you'll be able to see your boot entries. if you cast your mind back to the boot screen you'll be able to recognise that they correspond to your boot options. you want to change that number to the one you want to boot to by default. its probably 0, the first option.

there are plenty of posts on this forum about the grub menu if ive been too brief with my explanation

---

### Post by aeiah on 2008-10-20
oh, and you might find a virtualisation program like virtualbox more up your street, or perhaps kvm. xen is brilliant, but is probably overkill for accessing windows to do some development. its real strength lies in servers, live migration across physical machines, clustering etc.

---

### Post by happytechie on 2008-10-20
Thanks guys, I changed the defaut to be the same thing that I'm using now (3) and I've rebooted and it seems OK.  How do I go about removing all the stuff and optomised kernels that xen left behind?

---

### Post by matey3 on 2008-11-04
Hello;

I wonder if anyone can help me uninstall xen from my machines. I tried it on 2 machines but even though I took every step the instructions told me (and the steps they forgot to tell me) there is still No Go on either machines!

I manually installed one and the other one was semi-auto setup.
Reading the stuff above I rebooted in generic kernel and I know how to take xen off my menu.lst file but there are xen folders all over...and I wondered if I can manually delete them to make room.
there is /etc/.xen , /home/xen,(??)  /usr/local/src, usr/lib/xen/
oh and I dont know where else?
these are the ones I remember seeing..

I am just little worried that all the changes may harm the system if I manually delete the xen? like the tls thingy that I had to disable and God knows what else?

thanks for any help!

---

