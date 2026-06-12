---
title: "transfering files from a terminal"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by jacewa on 2012-01-13
hello! i just started a new apache 2 server, and i was wondering how to transfer files from home to my html link

---

### Post by drdos2006 on 2012-01-13
The terminal command to copy is : cp
So to copy from your /home directory to /var/www would be :

cp /home/user_name/Documents/my_files.html     /var/www

regards

---

### Post by d4m1r on 2012-01-13
You are gonna have to provide more info...Is your home PC connected to the internet on a static ip? Is it running a HTTP server?

To download things from command line, you can use "wget http://example.com/example.exe", for example ;)

---

