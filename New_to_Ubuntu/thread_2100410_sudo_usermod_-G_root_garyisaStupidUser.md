---
title: "sudo usermod -G root garyisaStupidUser"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by gmgj on 2013-01-01
Objective:  make it easy for username to edit LAMP system files
Approach : sudo usermod -G root username

in an attemp to give username root priveleges
instead, 

I can't sudo, becasue its says authentication failure
not in sudoers file
I can't SU for the same reason

my passwd shows this 
username:x:1000:1000:username,,,:/home/username:/bin/bash

I can't figure out how to login as root

Anyway out of this?

my swag is 
usermod -G root username
changed my group?
but did not give me ownership of files, so i still can't edit what I want

---

### Post by sisco311 on 2013-01-01
Boot into recovery mode and add your user to the admin or sudo group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by PinkFloyd102489 on 2013-01-01
Shouldn't be trying to add yourself to the root group.

/var/www should be chowned to www-data:www-data. Anything under that will be writable by the user/group that created it, while still being displayed by the Apache server.

If you're needing to gain ownership of files, use the chown command. Use the -R switch to recurse into a directory, if you want to change ownership of a directory and all files contained within it.

---

### Post by gmgj on 2013-01-01
I was able to use Recovery mode to add username to the sudo and admin groups and I got back sudo access. (adduser username sudo and adduser username admin).  

If I try and view syslogs etc with logviewer, it says I don't have permissions.  

if I do grops I see username root sudo admin.  My swag was that something in the root group is mucking this up.  Thats my silly waild *** guess, but what do I really need to do?

also for this /var/www should be chowned to www-data:www-data. How does this give me write access to files like /etc/apache2/httpd.conf

---

