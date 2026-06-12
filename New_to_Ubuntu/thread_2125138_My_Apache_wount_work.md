---
title: "My Apache wount work"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Mardwan on 2013-03-13
Hi. I am using Xammp on ubuntu. When i installed it yesterday, apache  was running well but now i get this message whenever i do  sudo  /opt/lampp/lampp start

[FONT=courier new]XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
XAMPP: Another MySQL daemon is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.[/FONT]

Any help will be greatly apperciated. Thank you in advance.

---

### Post by TK999 on 2013-03-13
Hi, did you try uninstalling XAMPP and installing just the Apache server with:
```

sudo rm -rf /opt/lampp && sudo apt-get install apache2

```
Also, if you wish to run a server, it's often a better idea to equip a separate computer as the server if possible and installing on it a distro like Ubuntu Server.

---

### Post by Mardwan on 2013-03-14
Hi. I have already uninstalled xampp and i am now using it on windows. I just needed to know how the problem could be solved for future reference. Thank you for the server idea. I highly apperciate the help :)

---

### Post by paprin on 2013-03-24
I have face the same problem after installing XAMPP. But when I sign out from skype, it was running absolutely. 

Actually Apache server use port 80 and if your computer connected with skype then port 80 was busy for skype. Once you stop this program than Apache find its own way.

You may start skype again after connecting Apache. Then It's not causing any problem.

I am not a expert but I share this solution from my own experience!

---

