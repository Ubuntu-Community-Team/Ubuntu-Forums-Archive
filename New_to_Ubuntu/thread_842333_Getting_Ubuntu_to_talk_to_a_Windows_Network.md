---
title: "Getting Ubuntu to talk to a Windows Network"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by DaltonAdair on 2008-06-27
Hey guys, if you could help a former Windows guy out with this I would appreciate it. 

I am doing testing with Ubuntu to see if it is a good alternative to XP Pro for our offices, (save money and headaches).

I need to get Ubuntu to talk to the network we have setup here. It is a full-fledged Windows network, with a domain controller, exchange servers and the whole shebang. 

Basically, what processes should I go through so I can get my Ubuntu machine and the network to play nice?

My goal here is to be able to access all the shared folders and resources that are available to my network permissions for my Windows login. 
I have already halfway done this by getting Evolution to talk to the Exchange server on the network and getting mail, but that's about it.

I am using Hardy Heron, FYI.

---

### Post by OldTimeTech on 2008-06-27
I think you should be asking this question in Networking and Wireless...

---

### Post by ukripper on 2008-06-27
> **DaltonAdair said:**
> Hey guys, if you could help a former Windows guy out with this I would appreciate it. 

I am doing testing with Ubuntu to see if it is a good alternative to XP Pro for our offices, (save money and headaches).

I need to get Ubuntu to talk to the network we have setup here. It is a full-fledged Windows network, with a domain controller, exchange servers and the whole shebang. 

Basically, what processes should I go through so I can get my Ubuntu machine and the network to play nice?

My goal here is to be able to access all the shared folders and resources that are available to my network permissions for my Windows login. 
I have already halfway done this by getting Evolution to talk to the Exchange server on the network and getting mail, but that's about it.

I am using Hardy Heron, FYI.

You will need samba to let your domain controller talk to ubuntu machines.

Here are some good guides-
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
For Active directory authentication - [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

---

### Post by DaltonAdair on 2008-06-27
Thank you ukripper! It's good to know we have some helpful people around. :D

---

### Post by prostar on 2008-06-27
As I just mentioned in another post, I would look at using "webmin".  If you aren't used to the config files, it can save you hours of pain (even if you are, actually).  Samba setup is found under services, and there are some things under network that you should fill in as well to integrate with a MS network.

---

