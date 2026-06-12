---
title: "Question about Firestarter"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by coldfire204 on 2008-06-22
Just wondering if this is normal behavior for Firestarter... I found this and decided to install it just to see how it works.   Seems pretty good, it doesn't lag my computer down at all, but anyways, the question I have is this:  Is it normal to be getting hits from incoming IP addresses literally every second?  Firestarter has been running for about 30 minutes, and so far has found 1 threat that it classified as 'Serious'.  

Also, does Firestarter block trojans, or should I get something like AVG for that?  I was reading about anti virus measures used in Linux, and it seems like the general view is that you don't even need any anti virus programs since most threats are directed towards Windows machines.  Is it really ok to not use anti virus software on a Linux machine?

Thanks for reading, sorry if it's already been asked a thousand times lol.

---

### Post by Ripfox on 2008-06-22
My experience is that you do NOT need anti virus for Ubuntu or any Linux OS. If you have a windows partition and you want to scan once in a while try ClamAV it's free and works on Linux. As far as Firestarter goes, yes it is normal to get a lot of innocuous hits (or at least thats how it seems to me)

Firestarter runs in the background, and does not depend on the GUI thing in your task bar. If you don't start the GUI, it is still running so if it bugs you like it bugs me, let it run in the background and just check it once in a while :)

---

### Post by PinkFloyd102489 on 2008-06-22
Firestarter is just the frontend application editor to iptables.

---

### Post by cariboo on 2008-06-23
> Just wondering if this is normal behavior for Firestarter... I found this and decided to install it just to see how it works. Seems pretty good, it doesn't lag my computer down at all, but anyways, the question I have is this: Is it normal to be getting hits from incoming IP addresses literally every second? Firestarter has been running for about 30 minutes, and so far has found 1 threat that it classified as 'Serious'.


Yes it is normal it is probably coming from infected or zombied windows computers in your net block

> Also, does Firestarter block trojans, or should I get something like AVG for that? I was reading about anti virus measures used in Linux, and it seems like the general view is that you don't even need any anti virus programs since most threats are directed towards Windows machines. Is it really ok to not use anti virus software on a Linux machine?


Again yes it is true, as of right now the only viruses and trojans are proofs of concept, there is nothing in the wild that will effect your computer.

I've been running several different distributions as my main system since 1999. The only viruses I ever see are attached to emails. I ususally run something like strings on them just to see what they are. Since changing ISP's about 5 years ago. I don't see any viruses at all.

Jim

---

### Post by bumanie on 2008-06-23
Firestarter is a graphical front end for iptables which is basically a firewall initiated at kernel level and is on by default. As for the need for antivirus - it is not necessary unless you want to scan for windows viruses to protect A) another computer/partition of yours that you will share files with or B) are going to be sending files to someone else who runs windows. All the anti-virus scanners, look for windows viruses as there are no viruses in the wild that affect linux. Even if there were, it takes the user to install them in 'super user' mode, they can't infect the system files purely by going to a malicious website or whatever, unlike some other OSes.

---

### Post by hyper_ch on 2008-06-23
(1) antivirus is not necessary in general - there might be specific need for usage on AV on linux

(2) altering iptables / installing a firewall is not necessary in general - there might be specific need for usage of running customized iptables rules.

---

### Post by gn2 on 2008-06-23
You might want to read this: [http://ph.ubuntuforums.com/showthread.php?t=694198](http://ph.ubuntuforums.com/showthread.php?t=694198)

Running Firestarter constantly is completely unecessary and it has been suggested it could even be a potential security risk as it runs with root permissions = bad.

---

