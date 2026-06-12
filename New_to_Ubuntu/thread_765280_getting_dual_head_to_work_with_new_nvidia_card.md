---
title: "getting dual head to work with new nvidia card"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by precision on 2008-04-24
I just installed Kubuntu 8.04 and I am having trouble getting my dual head set up. Right now the monitors are just mirrored. Does anyone have any suggestions on how to get this working with the default setup of the new Kubuntu?

When I try using display properties, all of the buttons are greyed out so I cannot apply any changes when I drag the green monitors around. 

Please let me know any information you need. I am very new to Kubuntu.

---

### Post by precision on 2008-04-24
OK I got it working. Here is what I did after a fresh install of Kubuntu KDE4:


1. apt-get update
2. apt-get install nvidia-kernel-common
3. apt-get install build-essential
4. download the newest drivers from the nvidia site
4. sh NVIDIA-Linux-x86_64-169.12-pkg2.run
5. run nvidia-settings and enable second monitor
6. click "save configuration file"

And it's working! Only took me the whole afternoon.

---

### Post by Hooya on 2008-04-24
To elaborate on what precision has said, I answered nearly this exact question yesterday.  Here is my post:

[http://ubuntuforums.org/showpost.php?p=4776215&postcount=2](http://ubuntuforums.org/showpost.php?p=4776215&postcount=2)

It covers more specifically the stuff you'd do after the steps in precision's post above.

---

