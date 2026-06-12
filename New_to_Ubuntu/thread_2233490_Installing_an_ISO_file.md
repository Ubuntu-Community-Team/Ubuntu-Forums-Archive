---
title: "Installing an ISO file"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by deezdrama on 2014-07-08
Long story short...

Im new to ubuntu and linux.

My mother Came from Germany and can speak German,
She told me if I learned German she would take me on a trip there.

My nephew has a copy of a german learning program from school he burned to a cd for me.

It is an iso file meant to run on windows. On windows I would just mount it on a virtual drive and install.

What do I do on ubuntu?
Can I install it from Play on Linux.

Do i have to mount a virtual drive?

---

### Post by Bucky Ball on 2014-07-08
You'd probably need to create a Windows virtual machine and run it in that. For Wine, you can check here to see if it will work:

[https://appdb.winehq.org/](https://appdb.winehq.org/)

For PlayOnLinux see here:

[http://www.playonlinux.com/en/supported_apps.html](http://www.playonlinux.com/en/supported_apps.html)

You don't have access to a Windows machine?

---

### Post by deezdrama on 2014-07-08
I have my gaming rig I built but the kids kept getting on websites that installed malware and viruses and got tired of it and installed ubuntu on the rig.

My other pc is a junk gateway that barely runs netflix.

Im thinking about installing windows again on this pc as a dual boot option, would that be easier than trying to get it to run in ubuntu?

---

### Post by Bucky Ball on 2014-07-08
Did you check those links? If no joy, I'd say yes, or install Virtualbox and Windows in that as a virtual machine. You need decent specs to run a virtual machine (solid processor and _at least_ 2Gb of RAM as the RAM is split between the two OSs). Virtualbox is in the repositories.

As for the dual-boot, make sure you install Windows to a primary partition and not on a logical one inside an extended partition. Create a new thread with a descriptive title if you go that way and need help with a dual-boot. Cheers and good luck. ;)

---

### Post by hbutt875 on 2014-07-09
Go to this link.
[http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/](http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/)

---

### Post by Bucky Ball on 2014-07-09
> **hbutt875 said:**
> Go to this link.
[http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/](http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/)

You might be able to mount the ISO but if this is for Windows, that's about it. The setup file will be an .exe file. Case closed then.

---

### Post by ibjsb4 on 2014-07-09
Maybe you can find something that is built for linux.

[https://www.google.com/search?client=ubuntu&channel=fs&q=german+language+softwarw+linux&ie=utf-8&oe=utf-8#channel=fs&q=learn+german+language+software+linux](https://www.google.com/search?client=ubuntu&channel=fs&q=german+language+softwarw+linux&ie=utf-8&oe=utf-8#channel=fs&q=learn+german+language+software+linux)

---

### Post by yancek on 2014-07-09
> It is an iso file meant to run on windows. 

What happens when you put the CD in the drive on Ubuntu?  Do you see the files (should show under the /media directory) and is this something that is interactive and does have a setup file?

---

### Post by hbutt875 on 2014-07-09
Thank you for your answer. Can he open that exe file with wine?

---

### Post by Bucky Ball on 2014-07-09
> **hbutt875 said:**
> Can he open that exe file with wine?

See post #2. Previously discussed.

---

### Post by hbutt875 on 2014-07-09
thanks

---

### Post by deezdrama on 2014-07-09
I didnt get a whole lot of time to mess with a solution as my nephew was here and bugging me.

Im still undecided on which route to try.

Wine lists some versions of this program with platinum, most gold, but the version I have says silver rating with no mic support.


I thought about dual booting (I have a junk laptop thats dual boot.... I might just install on it.

When I installed ubuntu on this system I did fresh reformat with no extra partitions so dont know if its possible now.
Besides that my rig is ancient but think its up to the task.

Modded socket ep45 mobo running xeon quadcore at 4.6 ghz per core on slight vcore bump/air cooling
8gb ddr2 800
650ti video.

Ill just try on my craptop ... if it doesnt work out ill post back about dual OS booting unless anyone has suggesstions about this.

thanks

---

### Post by deezdrama on 2014-07-09
wont be able to install on my craptop, its screen is broke so I use an external monitor... this works fine when I boot into ubuntu but when I boot into windows on the laptop it only shows a background on the external monitor and ive tried all keyboard commands ive found online to swap to ext monitor and nothing works :(

---

### Post by Bucky Ball on 2014-07-09
> **deezdrama said:**
>  if it doesnt work out ill post back about dual OS booting unless anyone has suggesstions about this.

thanks

All good. Post about any dual-boot questions/issues in a new thread with a descriptive title. Cheers and good luck. ;)

---

