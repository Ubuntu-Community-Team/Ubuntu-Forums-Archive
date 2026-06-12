---
title: "No backups or updates"
date: 2024-03-16
forum: New to Ubuntu
---

### Post by commonleftie on 2024-03-16
I'm fairly new to Linux/Ubuntu. I have provided two screenshots one for the issue I'm having with updating the Snap Store and the other for what I get when trying to save a backup.
Also I can't update to Ubuntu 23.10 from 22.04.

Please and thank you.

---

### Post by Rubi1200 on 2024-03-16
Hi and welcome to the forums :-)

To try and fix the snap store issue run this in a terminal:
```
sudo snap refresh snap-store

```

Do not recognize the error for the backup; what software are you using for backups?

---

### Post by deadflowr on 2024-03-16
For the backup it should only need to install python3-pydrive package.
```
sudo apt install python3-pydrive
```
The google api stuff should install along with that.

> Also I can't update to Ubuntu 23.10 from 22.04.
Check what the settings are in Software and Updates > updates.
For updating from 22.04 to 23.10 it needs to be set for check for any new version.
I'm not sure but it might default to check only for Long Terms Support version, which 23.10 is not.

---

### Post by paulparker2 on 2024-03-16
Am NON Technical, as a user found using terminal commands to update, install, unininstall and more, taught me how to easily do things.



There are various archive methods. 


Read terminal command:  [B]man tar 
[/B]


For backups self created a folder named Archive/    then used command:  **tar**   

examples: 

To create an [archivename].tar.zip  

read then try commands with a few small packages to create archives: 
  
  **tar  -zcvf   Archive/Public20240302.tar.gz     Public**  
  **tar  -zcvf   Archive/Music20240302.tar.gz      Music**   
  **tar  -zcvf   Archive/Pictures20240302.tar.gz   Pictures** 
  **tar  -zcvf   Archive/bin20240302.tar.gz            bin**    


***BTW***  read articles about **tar**  [linux only?] to learn more and solve problems. 

 


.

---

### Post by commonleftie on 2024-03-17
This is the message it gave me when trying that line.

---

### Post by deadflowr on 2024-03-17
Try running
```
sudo add-apt-repository universe
sudo apt update
sudo apt install python3-pydrive
```

I assumed you had the universe repository enabled already since you prefixed this thread for the Xubuntu flavor, which has it enabled by default.
The Ubuntu desktop does not have the universe repository enabled by default, so...

---

### Post by geezuslvr on 2024-03-21
I've the same problem.  After installing  python3-pydrive, Deja Dupe still cannot find my backup files even though they are staring me in my face and I cannot seem to find a solution for this

---

