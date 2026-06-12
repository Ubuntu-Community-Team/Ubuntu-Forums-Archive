---
title: "Unable to use my wireless data card on Ubuntu 9.10"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Azeem Jafri on 2012-07-26
Hello friends,
 
I am a beginner in the Linux field.I have recently installed Ubuntu 9.10 in my system and want to use my wireless data card over it.Somewhere over the net i read that i need the wvdial package in order to do so.So,I downloaded the wvdial.deb package but it showed lots of dependencies over the other packages.Now .deb packages are the best option for me as they can be executed by simply making a double click on them.But the problem is that i am not able to find any place over the net where i can get all the desired .deb packages.Please guide me and suggest a link from where i can download any .deb package that i need.If this is not the best way then please guide me how can i become expert in handling this installation of packages in the ubuntu system.

---

### Post by 2F4U on 2012-07-26
That is because Ubuntu 9.10 is no longer supported. What is the reason to use such an outdated version? The current version is 12.04, which is also a long-term support release.

---

### Post by Azeem Jafri on 2012-07-26
Thanks for your reply.
 
I know that i am usnig an obsolete version and i should upgrade to 12.04 but due to some reasons i will be upgrading after few months.But i want my data card to get enabled on my existing ubuntu system.
 
Please guide me on the basis of my first comment.

---

### Post by mastablasta on 2012-07-26
> **Azeem Jafri said:**
> I know that i am usnig an obsolete version and i should upgrade to 12.04 but due to some reasons i will be upgrading after few months.But i want my data card to get enabled on my existing ubuntu system.
 
Please guide me on the basis of my first comment.
 
 
i don't think you understand what they are telling you. 12.04 has newer kernel. since drivers in linux are part of kernel this also means that 12.04 has newer drivers included. and sinc eit has newer drivers it has a chance thta your card would work out of the box (i.e. on system install).
additonally since 9.10 is not supported anymore the pakcages you seek could be a bit harder to find. or they were replaced by newer ones. in short you could face a dependency hell. it is better to install latest version and then troubleshoot from there.
 
is it the problem because you do not have an internet connection at home? if so and if computer is portable you could take it to somewhere where you can connect it and then install the package via synaptic or software center. that should pull all dependencies down as well. 
 
another option is to use synaptic for offline download.
 
if however you have the internet connection at home then connect via wire and use the package management tools that are provided by the OS (synaptic and software center for GUI and apt-get for command line) to install the package you need.
 
it is the safest and easiest way. 
 
use deb and source files only as a last resort.

---

