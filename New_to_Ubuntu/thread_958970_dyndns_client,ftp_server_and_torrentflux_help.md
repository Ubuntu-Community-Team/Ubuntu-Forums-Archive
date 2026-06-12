---
title: "dyndns client,ftp server and torrentflux help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by fate_ on 2008-10-25
How to set up dyndns to start when the computer reboots? also I have torrentflux installed and everything is fine but I cant seem to change the save path,any help? also whats the best ftp server program I should use?

---

### Post by cariboo on 2008-10-26
Did you download a file when you registered with Dyndns if you did, the open a Application-->Accessories-->Terminal and type:

```
sudo update-rc.d programname defaults
```

Where programname is the name of the program you downloaded. Make sure the program is somewhere in yout path, normally it would be located in /usr/loca/bin.

Jim

---

### Post by fate_ on 2008-10-26
no I installed from a guide. I used this guide here [http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html](http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html)

actually I found the solution, I added the command sudo /etc/init.d/ddclient start here System \ Preferences\ Sessions, will that be ok? ill test in a minute, I just restarted my pc and used /etc/init.d/ddclient status and it said it was running, so everything is fine then?

---

### Post by fate_ on 2008-10-26
bump

---

