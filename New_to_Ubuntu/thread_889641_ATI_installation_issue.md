---
title: "ATI installation issue"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by ExSuSEusr on 2008-08-14
Downloaded the prop drivers from ATI for a Radeon 9600. Followed the instructions on ATI's page and am running into a problem.
 
When I click on the driver file, it brings up terminal and begins the install process but then stops and says "You must be logged in as super-user" to do this. 
 
I have tried starting the file under sudo and it doesn't work.
 
*[SIZE=2]ati-driver-installer-8-7-x86.x86_64.run[/SIZE]*
 
 
[SIZE=2]Any ideas?[/SIZE]

---

### Post by renzokuken on 2008-08-14
could run ```
sudo su
``` and enter your password, then try again. this will give you a full root permission terminal.....

....just be a bit careful what you do though, remembering everything you do in the terminal will be run as superuser

---

