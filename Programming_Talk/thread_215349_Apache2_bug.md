---
title: "Apache2 bug"
date: 2006-07-13
forum: Programming Talk
---

### Post by quedigg on 2006-07-13
Hello ,
when i run Apache2 server from the terminal ,i get this :```
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

when i point my browser to 127.0.1.1 it works but why it's not assigned to the localhost (127.0.0.1),and what's that issue message .

Many thanks in advance !

---

### Post by thumper on 2006-07-14
Running apache2 from the terminal as a normal user will not work.

You'll not be able to user a port below 1024, nor write to the logs, which is the errors you are seeing.

---

### Post by quedigg on 2006-07-14
Thanks, so i simply run ```
sudo apache2
```?

---

### Post by thumper on 2006-07-14
```
sudo /etc/init.d/apache2 start
```

---

### Post by nagilum on 2006-07-14
> **quedigg said:**
> Thanks, so i simply run 'sudo apache2'?
No, you start/stop Apache with the init-script in /etc/init.d/, e.g. '/etc/init.d/apache2 start'. Anyway, this is done by default during boot, you won't have to start it manually.

---

### Post by quedigg on 2006-07-15
Thanks alot mates!
one more question ,the apache2 server is using 127.0.1.1 instead of 127.0.0.1 ,why?

and how can i know what is reserving the 127.0.0.1 loop-back ip ...

Thanks agian

---

### Post by Daniel15 on 2006-07-15
Well, actually, the whole Class C range is the loopback address (that means from 127.0.0.1 all the way to 127.255.255.254)

Anyways, for your error:
> apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
That means that the hostname of your computer couldn't be determined. Firstly, run ```
sudo nano /etc/hostname
``` and make sure that a hostname is listed there (for example, on my testing server, the hostname is server1.dan-network.local. You can make it anything). Run ```
 sudo hostname --file /etc/hostname
``` to set the hostname.

Next, run ```
sudo nano /etc/hosts
``` and make sure that there's a line like this:
```

192.168.0.1     server1.dan-network.local

```
(replace 192.168.0.1 with the server's IP address, and server1.dan-network.local with the host name you're using).

Finally, restart networking: ```
/etc/init.d/networking restart
```. Then, restart Apache2: ```
/etc/init.d/apache2 restart
```. Check the error log for any errors: ```
tail --lines=30 /var/log/apache2/error.log
```.

Hope this helps you :D
--Daniel15

---

### Post by eulipion2 on 2006-07-20
Hello, I just tried doing this, running ```
sudo nano /etc/hostname
```, changed the address to rick-desktop.local, then tried running the next step, but got this message:
```
sudo: unable to lookup rick-desktop.local via gethostbyname()
```  In fact, I can't do anything.  I tried removing /etc/hostname in order to make a new one, but I can't even do that, getting the same above stated error.  Help, please!

---

### Post by eulipion2 on 2006-07-20
And I just found out, apt doesn't work now either.  Help!

---

### Post by ifokkema on 2006-07-21
> **eulipion2 said:**
> And I just found out, apt doesn't work now either.  Help!
Sudo can't match your username with the current hostname, so it doesn't allow you to do anything. Can you log in as root? If you reboot in recovery mode, can you then edit the /etc/hosts file to include your hostname? Otherwise, you may need to pop in the Live CD.

---

### Post by eulipion2 on 2006-07-21
Well, I kinda cheated and reinstalled the OS.  So far all of the errors I had experienced with my first install are now fixed, including this one.  But just for future reference how do I boot in recovery mode?

Thanks!

---

### Post by eulipion2 on 2006-07-21
And I tried again and get the same error, so yeah, need to boot in recovery mode.

EDIT: I figured out how to login and change the /etc/hostname file back to the original (used Login: Failsafe Terminal -> su root)

Now, my question is this:  do I need to do ```
sudo /etc/init.d/apache2 stop 
``` before doing the above steps?  Even doing this gives me the error, but will that make the process work without seizing up on me?

Thanks!

---

### Post by ifokkema on 2006-07-22
The problem is not so much with apache as it is with sudo trying to identify you.

If you want to change your hostname, FIRST change /etc/hosts and add your new hostname (link it to 127.0.0.1). DON'T remove the current hostname from that file yet. After that, you can change your hostname in /etc/hostname. This way, your hostname will always be linked to your internal loopback IP address.

You don't need to restart Apache at all (unless you changed the configuration to use hostnames in stead of IP addresses). If you type in your hostname in the browser, it will connect to 127.0.0.1 (using /etc/hosts) and just connect to Apache the same way it did with the previous hostname.

---

### Post by tomservo291 on 2007-04-01
Easy solution.. give Apache what it wants:  FQND (fully qualified domain name.)

What fixed it for me:

Original /etc/hosts entry:
127.0.1.1 themoon

New /etc/hosts entry:
127.0.1.1 themoon themoon.local

restart Apache2, problem solved.

---

