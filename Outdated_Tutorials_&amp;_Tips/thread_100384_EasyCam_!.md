---
title: "EasyCam !"
date: 2005-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Anbreizh on 2005-12-07
Hi, 
To start, please excuses me for my English of low level.  I wanted to make you by script which I dev on the forum of the French-speaking community.  This script makes it possible to install the drivers for webcam thanks to a graphic interface.  It is compatible for the moment with the drivers according to:  Spca, Ov511, Pwc, Qce and drivers for Eyes Toys.  It functions thanks to the autodetection of good the drivers has to use thanks to the ID of the webcam.  The EasyCam project is rather recent and by consequance the list of the webcam autodetec is rather weak but it does not hold that the list by fournisant me your ID of webcam has you to increase it if it is not autodetec.  

News ! 

I have to develop a new software, EasyCam 2 which is for the moment in phase of test but I have good return on the Francophone forum.  Installation:  
            - To add the following deposit: 

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

- To install the EasyCam2 Package 
- The notifications of setting has days are automatic


Installation:  
- To add the following deposit: 

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

- To install the EasyCam Package 
- The notifications of setting has days are automatic


If you have any problem, please contact me has the following address:  jbtheou At gmail dot com because I am only seldom on the english forum :D


 I awaits your returns

---

### Post by Anbreizh on 2006-03-03
If you have any problems with EasyCam2, please contact me with this post ;) 
I can totally try my program because a haven't one webcam for all drivers ;) 
I try resolve any problem who is send me in French Forum. I often update this program with patch.
I available for you am helped when you have problems with EasyCam2 ;)

---

### Post by haomomo on 2006-03-05
First of all, I would like to thank you for your great job. It will really save me off the horrible work to make my cam work. 

My cam is Mustek Wcam300A. It works now, but only with gnomemeeting, because gnomemeeting has such setting of changing cams and I can set my cam over another option of "Unknown/Generic". Unluckily, Camorama or gqcam or whatever doesnt have such setting and whenever I start these apps, the default cam is always that "Unknown/Generic", which surely doesnt work! Do you or somebody know how to do some configurations in camorama or somewhere in Ubuntu to set my cam as the default cam whenever the apps get started?

Thans in advance!

---

### Post by Anbreizh on 2006-03-05
Hi,

Can you try in terminal : "camorama -d /dev/video1" ?

---

### Post by stanz on 2006-03-09
Hi All,
I've got the same problem, or hassle- with ever. I've imput your code:
"**Could not connect to video device**(/dev/video1). **Please Check connection**.
I'm looking right at the connection~ it's good.
My cam is listed in my 'Device Manager'- with it name too! It's **intel Pro Share WebCam**, and in the 'Advanced' tab, all is filled in.
Any help would be a great help!!

# camorama -d /dev/video1
(camorama:10941): GnomeUI-WARNING **: While connecting to session mana ger:
Authentication Rejected, reason : None of the authentication protocols  specified are supported and host-based authentication failed.

---

### Post by lxstoian on 2007-08-11
I installed easycam2 but when i run the driver installation it gives me an error that it can't run the make install.
I have a Vimicro web cam.

---

### Post by vishnu_sresht on 2009-03-23
Is there a way to install Easycam in Intrepid ?

---

### Post by executorvs on 2009-04-12
easycam works fine in intrepid using the hardy packages. this is not true for jaunty though :-(
the sources are:
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
  deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main

---

### Post by krivosh on 2009-05-10
> **executorvs said:**
> easycam works fine in intrepid using the hardy packages. this is not true for jaunty though :-(
the sources are:
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
  deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main

check [http://ubuntuforums.org/showthread.php?p=7252801#post7252801](http://ubuntuforums.org/showthread.php?p=7252801#post7252801) for Jaunty solution(s)

---

