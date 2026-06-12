---
title: "Ubuntu in virtualbox"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by conure on 2013-02-17
Hey all,

I have recently began a degree in software development here in the UK and one of my modules is a completely based around Ubuntu. At first I though this module would be dull (my other two are engineering mathematics and introductory programming) but have found that, actually, Linux is my favourite area of study.

I have really 'fallen in love' with the principles of open source software and the idea of the FSF, and cant wait to be experienced enough to begin contributing to open source projects.

My first question is...I am currently running Ubuntu LTS 12.04 through virtual box on windows 7. I have good hardware, an i5 at 4 ghz, gtx 660ti and 8gb of ram with an SSD however even with guest additions Ubuntu feels sluggish at times. Would a native install fix this? If so i will probably just get rid of windows alltogether! I must apologise for grammar, I am on a mobile device.

Thanks

---

### Post by DuckHook on 2013-02-17
Welcome to Ubuntu and the forums.

Good to see enthusiastic new users.

A dual boot install on bare metal will definitely give you great performance, but unless your module requires you to do stuff like compiling, etc, I would actually recommend that you stick with the VM and explore some more first. Be mindful that you are not getting anything remotely close to real-world performance, but other than that, you have the best of both worlds right now. A VM is the ideal way to explore, in my opinion. Just take a snapshot of your currently perfectly running Ubuntu, and no matter what you do to break it later, you can always roll back to the snapshot and you are as good as new. With the security of a snapshot, you can hack, burn and slash the OS with confidence. Can't think of a better way to learn Linux, quite frankly.

---

### Post by snowpine on 2013-02-17
Try choosing "Unity 2D" from the login screen, as it's less graphics-intensive and therefore might give you less lag.

---

### Post by brusegadi on 2013-02-17
Hello,

You could also try Xubuntu, its less resource intensive so it should be a little smoother on a VM.  It is also very similar to ubuntu (the only difference should be the window manager) so you should be able to follow instructions for your projects as if you were on an ubuntu box (assuming everything is done from the shell.)  Thanks!

---

### Post by andrew.46 on 2013-02-18
A lot depends on what sort of resources in terms of cores and ram you have allocated to the guest system?

---

### Post by MoebusNet on 2013-02-18
I basically have half of my installed RAM, all of my cores and maximum allowable video RAM set in my VBox OS's. It hasn't caused me any trouble yet, but YMMV.

---

### Post by DuckHook on 2013-02-18
+1 to all above advice recommending allocation of more resources for your VM.

Also, don't know how it works in W7, but in a Linux host you can allocate more than the 128 MB VRAM that VirtualBox maxes out at in its GUI control panel app. Do:```
vboxmanage modifyvm name_of_your_ubntu_vm --vram 256
```You will have to google to find the equivalent instructions for Windows. VirtualBox maxes out at 256MB of VRAM, but this should be enough to get Ubuntu more responsive.

---

### Post by andrew.46 on 2013-02-19
Thanks for the great tip DuckHook!

---

### Post by Paqman on 2013-02-19
Yeah, Ubuntu does require decent graphics to run smoothly these days, which is why it'll always struggle in a VM compared to running on bare metal.

TBH, I would go ahead and install it on the machine. Nothing to lose really, you can always remove it if you change your mind.

Do a Windows backup first though. The installer is pretty bombproof, but it's always smart to back up before messing about with things like drive partitions.

---

