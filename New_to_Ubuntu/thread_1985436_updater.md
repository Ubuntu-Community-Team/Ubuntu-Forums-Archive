---
title: "updater"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Nadarasan on 2012-05-23
IS there any automatic updater available for ubuntu or software updater to update software in UBUNTU12?

---

### Post by Paqman on 2012-05-23
Yes, open Update Manager, click refresh and all the available updates will be shown to you.

---

### Post by ~!geek!~ on 2012-05-23
> **Nadarasan said:**
> IS there any automatic updater available for ubuntu or software updater to update software in UBUNTU12?

I am unable to get what exactly are you saying here, but I think you are asking whether ubuntu updates the softwares installed itself. 
Ans- Yes, Ubuntu updates the list of available softwares itself after a certain duration of time (can be set by the admininstrator). 
You can use the update-manager to explicitly update the lists or from command line type: > sudo apt-get update ; apt-get upgrade; 
The above command will first check for any updates and if found, second part of the command will install them for you. 
You can change the automatic update checking duration and stuff by ubuntu update-manager too. To do this: 
1) Start the update-manager 
2) Click on the Setttings at the bottom left of the window 
3) Select update tab in the new window 
4) Make changes to the configurations from there.

---

