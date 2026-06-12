---
title: "Noob trying to get elan1200 touchpad to work"
date: 2018-10-20
forum: New to Ubuntu
---

### Post by hokoden on 2018-10-20
Hello everyone,my apolligies if this has been posted somewhere else i looked in the search feature and couldnt find anything.
My problem is basically this I have an asus fx504ge laptop with a non-functioning touchpad basically doa,i have to use a mouse if 
i need a cursor functionality. I found a solution on the rog forums here [URL="https://rog.asus.com/forum/showthread.php?103220-Is-your-ELAN1200-touchpad-not-working-on-Linux-D"]https://rog.asus.com/forum/showthread.php?103220-Is-your-ELAN1200-touchpad-not-working-on-Linux-D
[/URL]
i just need to figure out how to implement it i guess, i extracted the tar folder linux-4.18.16 kernel from kernel.org to the downloads section cause i was trying it out then wrote the cp /boot/ code exactly as it shows in terminal, then i did make menuconfig and i got an error 2 make menuconfig saying bison not found in the description,so i went and downloaded configured and installed bison,as well as the recommended m4 both of them to the download directory,not the kernel directory which i think might be the problem,thing is i dont know how to uninstall bison or m4,i tried looking it up and theres only directions to install, if im going about this all wrong feel free to tell me as again im completely new to all this. Any help is appreciated,thanks.

UPDATE: Ok,so it looks like where i installed it (bison,m4) isnt the problem,and all i had to do in the rog forum post was update the mainline kernel. Which i did,but still no touchpad. I still dont know how to uninstall bison, but i did find a ?driver? on github, here [https://github.com/mishurov/linux_elan1200_touchpad](https://github.com/mishurov/linux_elan1200_touchpad) i just dont know how to use it as theres no config file to help install,just a makefile and some extras,this is rather annoying as ive heard of other people getting the driver to work (though a bit sketchy with how it functions) just no instructions anywhere on how to install the driver. I'll keep looking and try to keep this posted until i find a solution. Thanks in the meantime.

UPDATE TO UPDATE: Hooray,I got it working,turns out all i needed was help from this article [URL="https://opensource.com/article/18/5/how-load-or-unload-linux-kernel-module"]https://opensource.com/article/18/5/how-load-or-unload-linux-kernel-module 

[/URL] and the right search terms,i didnt know drivers were called kernel modules,learn something new everyday. It seems i got no replies,i hope i posted right. Oh well. till next time mean beans!

---

