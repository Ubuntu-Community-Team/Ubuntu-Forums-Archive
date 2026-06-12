---
title: "[SOLVED] Fstab Question"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by stuart264 on 2008-10-30
For the last 2 days i have been battling to mount a few directories on my Windows machine containing multimedia so I can add them to Mediatomb and avoid me having to run Linksys PC-Link software so my Linksys KISS1600 media player will run them

When I issue the command below at the console it works perfectly and mounts the file where I want it

> sudo smbmount //192.168.250.102/NewsDown /home/stuart/Desktop/Windows/NewsDown -o smbfs  auto username=XXX,password=XXX,uid=1000,mask=000, user

But when I add the line 

> //192.168.250.102/NewsDown /home/stuart/Desktop/Windows/NewsDown smbfs auto username=XXX,password=XXX,uid=1000,mask=000,umask=000,user   0 0

To my fstab file it still doesn't work even if I include the "sudo smbmount" command can any smart person look at the code above and tell me where I have "flamingo-ed up", secondly can I change the ip address in that code for the "Network Name" as I run my router as a DHCP server as I have an Internet radio and a laptop (that I am trying and failing to get networked with ubuntu but thats another issue for another post if I cant solve it)

Stuart

P.S. Windows Box is Windows XP x64  and yes I know the passwords are insecure at the moment but I want to get it working first before I go back in and secure the passwords.

---

### Post by Het Irv on 2008-10-30
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Here is a walkthough that I have used successfully in the past, It handles the login a little different than what you are doing, so you might have more success.

---

### Post by amak79 on 2008-11-01
stuart264,

It appears that you have a space preceding the umask: **umask= 000**. Try removing it.

---

### Post by stuart264 on 2008-11-06
Thanks, I will give it a try once I get a spare minute to myself sorry for the late thanks but my personal life has been totally hectic the last few days

---

