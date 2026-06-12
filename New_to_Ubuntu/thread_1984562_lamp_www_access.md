---
title: "lamp www access"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by GregD001 on 2012-05-21
Hello,
I am running ubuntu 10.10.
I have installed lamp.
the server works fine going to local host.
However, trying to create files in www I get access denied.
I only have 1 user.  Administrator.
I have also tried
sudo chmod 755 /var/www -R

any ideas?
thanks

---

### Post by ubudog on 2012-05-21
Hi there, could you post the output of:
```
ls -ld /var/www
```

---

### Post by Paqman on 2012-05-22
> **GregD001 said:**
> 
sudo chmod 755 /var/www -R


That should be:
```
sudo chmod -R 755 /var/www
```

Obviously doing this will give world+dog pretty free reign in your sites, so make sure you change it back to something a bit more restrictive when you're done tinkering.

Alternatives that would have allowed you to work without changing permissions:[LIST=1]
[*]Use a root session of the file manager. Hit Alt-F2 and:
```
gksudo nautilus
```
[*]Work on the command line with sudo. Use:
 ```
sudo -i
``` if you want to avoid having to type sudo all the time.
[/LIST]

---

### Post by Derek Karpinski on 2012-05-22
```
sudo usermod -a -G www-data GregD001
```

Assuming GregD001 is your username. Log out, log in and you should have access.

---

### Post by Nick_Kats on 2012-05-22
Also, If you want your web server to be seen from other pcs in the network, I think you need to forward the port that the web server is using.

---

### Post by GregD001 on 2012-05-22
thanks for the responses.

the output from ls -ld /var/www is
drwxr-xr-x 2 root root 4096 2012-05-21 22:47 /var/www

the gksudo nautilus worked, by popping up a file explorer.

neither of these worked
sudo chmod -R 755 /var/www
sudo usermod -a -G www-data user

---

### Post by Derek Karpinski on 2012-05-23
> **GregD001 said:**
> thanks for the responses.

the output from ls -ld /var/www is
drwxr-xr-x 2 root root 4096 2012-05-21 22:47 /var/www

the gksudo nautilus worked, by popping up a file explorer.

neither of these worked
sudo chmod -R 755 /var/www
sudo usermod -a -G www-data user

I'm not sure what user apache runs as, or if this is the safest way to keep your webserver safe, but this should work.  Someone more knowledgeable with webservers will correct me if I'm wrong.  But this has worked for me.  But if apache runs as www-data, there might be a security risk?

First confirm you are a member of 'www-data' group.

```
groups
```You should see www-data as one of the entries.

```
sudo chown -R www-data:www-data /var/www/
``````
sudo chmod -R 775 /var/www/
```Like someone said above, change 775 to something more restrictive when you're done messing around.

EDIT: forget everything i wrote above.  The first answer at this link is the best:

[http://askubuntu.com/questions/46331/how-to-avoid-using-sudo-when-working-in-var-www](http://askubuntu.com/questions/46331/how-to-avoid-using-sudo-when-working-in-var-www)

---

