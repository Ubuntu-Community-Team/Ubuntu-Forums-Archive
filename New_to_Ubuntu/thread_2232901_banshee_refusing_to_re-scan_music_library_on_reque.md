---
title: "banshee refusing to re-scan music library on request"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by smokingates on 2014-07-04
Machine: Hp Pavilion
Model: 500-141ea
O.S : Ubuntu 14.04LTS

The scan tool pops up and is at 100% when i request a scan without even scanning anything. I've had problems with music data for years and it was one big reason for switching to Ubuntu from windows (which I no longer have available to me). everything is missing for 1 of my compilations which displayed fine when running Ubuntu in VirtualBox with windows as host. Please help, I am still very new to Ubuntu and finding my feet, I am learning with every passing day and night (when my wi-fi connection is stable) however, I feel like I have mountains upon mountains to climb and it's very daunting. 

Thank you in advance! :p

---

### Post by cariboo on 2014-07-05
Make sure all the files are owned by your user. Open a terminal and type the following command:

```
chown -R user:user *
```

Where user:user is your user name. This also assumes that the files are located in your home directory.

---

### Post by smokingates on 2014-07-05
I don't think that's the problem because before you replied I deleted the compilation cd in question have since rebooted, run the terminal command you posted and tried re-importing the audio CD but still nothing.. it says "Could not fetch track information" and I don't think it even tried to check. Thank you for your reply.

---

### Post by ajgreeny on 2014-07-05
Are these files on your hard disk or are we talking about physical CDs with the files still on them and not yet ripped to file?

---

