---
title: "Cannot install new hardware support"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by annika2 on 2014-07-19
Hello there,  
today I saw in my Update Manager that new hardware support for my Ubuntu 12.04. When I tried to install, i got the following error message 

 "Die folgenden Pakete haben nicht erfüllte Abhängigkeiten:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) aber 10.1.3-0ubuntu0.1~precise1 soll installiert werden
                            Depends: libx11-6 (>= 2:1.4.99.1) aber 2:1.4.99.1-0ubuntu2.2 soll installiert werden
                            Depends: libxdamage1 (>= 1:1.1) aber 1:1.1.3-2build1 soll installiert werden
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) aber 2:1.15.1-0ubuntu2~precise1 soll installiert werden"  

(sorry for the german, hope you understand it anyway) 
Since I have pretty much zero knowledge about Ubuntu (and to be honest computers in general) 
I don't know what to do with this message... Would be great if someone could help me.  

Cheers,
Annika

---

### Post by grahammechanical on 2014-07-19
Is your installation of Ubuntu still working? Be thankful. Over the last couple days many have come to this forum asking for help because they accepted that upgrade offer and it broke the OS. Here are two threads

[http://ubuntuforums.org/showthread.php?t=2234815](http://ubuntuforums.org/showthread.php?t=2234815)

[http://ubuntuforums.org/showthread.php?t=2234830](http://ubuntuforums.org/showthread.php?t=2234830)

I am of the opinion that it is necessary for Ubuntu 12.04 to have newer ISO images with the latest Hardware Enablement Stack (HWE) so that Ubuntu can install on newer hardware, but in my ignorance, I cannot see any benefit to pushing this out to existing users as the existing HWE is suitable for the hardware that the user has. Especially, if it breaks things. But who listens to me?

Is there a specific problem that we can try to help you with? Are you still able to load to a desktop user interface? Can you still update/upgrade? Does Update Manager work without errors? 

Regards.

---

### Post by annika2 on 2014-07-19
Hi grahammechanical,

thanks for the quick answer. Kinda relieved I couldn't updatenow... I am still able to load everything and I could update other things without problems, so I am fine.

The only thing that does not work though I unrelated to the topic here. When I plug in external speakers/headphones, the sound is still audible through the laptop speakers. Since I do not quite know how to describe the problems in "technical" terms my search for solutions was not succesful. Maybe you have an idea where to look for a solution / in which part of the forum to post?

Thanks,
Annika

---

### Post by kansasnoob on 2014-07-19
I think it's best to just wait for the devs to straighten this out :)

Full info here:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

But the key date to remember is Aug 8, 2014. Hopefully they'll have the packaging issue worked out by then.

---

