---
title: "File sharing with linux and windows comps on wireless network help"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-08-07
ok so i have a few computers throughout the house and all of them are connected to the net using a wireless router. a couple of the computers i have i just installed ubuntu 8.04 and have everything wrking very well! i am very pleased with ubuntu i just am not very familiar with it i've used windows all my life.... anyways back the point. i want to setup a network where i would be able to share files between all of my computers. i was thinking i could possibly set up a file server or something to store most of my files on but i guess as of now i just want to become more familiar with doing that kind of stuff (networking/file sharing) with ubuntu. as of now i don't know how to view other computers connected to the router or even map the drives or folders so i could access them with the other computers in the house so i guess that's where we should start. looking forward to the help. thnx in advance

---

### Post by RobHK on 2008-08-07
> **steve joe bob said:**
> ok so i have a few computers throughout the house and all of them are connected to the net using a wireless router. a couple of the computers i have i just installed ubuntu 8.04 and have everything wrking very well! i am very pleased with ubuntu i just am not very familiar with it i've used windows all my life.... anyways back the point. i want to setup a network where i would be able to share files between all of my computers. i was thinking i could possibly set up a file server or something to store most of my files on but i guess as of now i just want to become more familiar with doing that kind of stuff (networking/file sharing) with ubuntu. as of now i don't know how to view other computers connected to the router or even map the drives or folders so i could access them with the other computers in the house so i guess that's where we should start. looking forward to the help. thnx in advanceI'm only a beginner here myself, but do you have samba installed from the Synaptic Package Manager?
I have it and my Windows network appears automatically under System/Administration/Network.

---

### Post by hyper_ch on 2008-08-07
you want to install samba

---

### Post by steve joe bob on 2008-08-07
i checked it out and it looks like i have samba-common installed but not samba. so i'll go ahead and give that a shot and report back with any problems

---

### Post by hyper_ch on 2008-08-07
[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by steve joe bob on 2008-08-07
ok cool! so installed samba on both ubuntu machines and now i can go to places, network and see the computers. my next question is how would i map a drive? i know that u can right click on a folder and set it to share and i could see it on the network but i don't know how to do an entire drive. also is there a way to password protect a folder or drive to restrict access to it across the network?

---

### Post by JoshuaRL on 2008-08-07
Go to Tools->Map Network Drive.

Also, I think you can add a password in the Samba settings on Ubuntu.  Haven't messed a ton with that, but just look around for it.  It should be there.

---

