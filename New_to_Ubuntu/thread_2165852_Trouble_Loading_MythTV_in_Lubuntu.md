---
title: "Trouble Loading MythTV in Lubuntu"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by jerry4 on 2013-08-06
Hello,  I am a new user and would like some help.

I am trying to get Lubuntu working with MythTV and can’t seem to get it to work properly.   I tried both Mythbuntu and Lubuntu.   Mythbuntu loads perfectly with no issues with MythTV.   In Lubuntu I do a fresh load, and then do the apt-get update and apt-get upgrade.   Then I open the synaptic package manager and select MythTV which should load all the dependencies and apply. I then exit the package manager and perform the following test.
```
sudo netstat -tap | grep myth
```
This lists about 10 or more lines showing that the backend is up and running.   From here I can stop the back end,  restart it and repeat the above netstat command and see that it is still working.
```
sudo stop mythtv-backend
# wait 10 seconds
sudo netstat -tap | grep myth
sudo start mythtv-backend
sudo netstat -tap | grep myth
```
 At this point the backend is running, but I do not know the mythtv password. So I open up mysql as root and change the password.   Myslq1.txt does not yet exist because I have not yet launched the MythTV gui backend or frontend.  Once I change the mysql mythv password, I can never stop and start the backend using the sudo stop/start commands.  When I run the sudo start mythtv-backend, I do get a process ID returned, but the netstat command returns only one row for logging.   The only way I seem to be able to get MythTV to work is by opening a terminal and executing the command
 
```
mythbackend
```
 
I would like to know the difference between running mythbackend and sudo start mythtv-backend.
 
After loading MythTV the backend is up and running, but once the mysql mythtv password is changed, sudo start mythtv-backend stops working properly.
I can get MythTV up and running using the mythbackend command from a dedicated terminal session, but I have issues stopping it.

What am I missing with this load procedure?

---

### Post by jerry4 on 2013-08-08
Since it's been more than 24 hours and I have had no response as a first time user, I'm replying to my own thread.
It appears that Lubuntu is broken or at least not ready for MythTV.   At least that has been my experience.
MythBuntu on the other had works great.   My problem with Mythbuntu, is that I do not like the desktop.
Since I prefer the Lubuntu desktop, what I did was load Mythbuntu and after all was set up, I removed the Mythbuntu desktop and installed the Lubuntu desktop.
```
sudo apt-get remove mythbuntu-desktop
sudo apt get install lubuntu-desktop
```

---

