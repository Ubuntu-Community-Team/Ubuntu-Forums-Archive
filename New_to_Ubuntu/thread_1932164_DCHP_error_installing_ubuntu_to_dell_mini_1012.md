---
title: "DCHP error installing ubuntu to dell mini 1012"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by treyberry on 2012-02-26
I know this is a dumb question....but this is absolute beginner talk. I am trying to install ubuntu to a dell mini 1012 that had a previous version of ubuntu 10.04 on it. Well, I got the wild idea that it wasn't good enough...plus my daughters needed the netbook for school. So I figured since I was giving the netbook to them I would totally reformat the hard drive and install ubuntu 11.10. I found several texts on the net stating that this was possibe (I am not 100% sure however) Which is another question I have: Will 11.10 run on a dell mini 1012? 
However, my main question is this. Everytime I try to install ubuntu(any version) I get the the screen stating that network configuration failedI! It then gives me the option to:
1) retry network autoconfiguration
2) retry network autoconfiguration with a DHCP hostname
3) configure network manually
4) do not configure the network at this time.
What am I doing wrong? 
If I choose the 4th option it takes me to another screen asking me which file to use as a root file system:
1) /dev/sda1
2)/dev/sda2
3)/dev sda5
4)/dev/sdb1
5)Assembe raid array
6)do not use a root file system
Help me please figue out what I am doing wrong.
I have run a winmd5sum on all the versions of ubuntu that I have tried...but everytime it states my file is correct.

---

### Post by Ir0nMa1deN on 2012-02-29
To me it looks like the installation failed to automatically configure the network settings. You could choose **4) Do not configure the network at this time **to continue the installation and manually configure it later. For your second question, I'm not sure why it's asking you that but I'd try 1)
There's nothing wrong with the actual ubuntu image/cd you're just having some issues setting it up.

---

