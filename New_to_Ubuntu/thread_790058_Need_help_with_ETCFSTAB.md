---
title: "Need help with /ETC/FSTAB"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ejpyle on 2008-05-11
OK...Here we go...I need to know what to put in FSTAB for a 2nd drive which is my web server with an ext3 file system....i have just discovered this is the reason my site is not accessible....Here is what I have an FTSAB for this file:

/dev/sda1 /media/disk ext3 defaults 0 0

I am assuming that leaving it "defaults 0 0" is creating a permissions issue to the drive with HTTP requests....making my web server inaccessible to other PC's in my LAN as well as outside it.

What do the permissions need to be so that my web server is accessible on this 2nd drive?

---

### Post by Rocket2DMn on 2008-05-11
Any files that you want apache to be able to access need to have read (and possibly execute) permissions on the files for World (the third octal in XYZ permissions).  Scripts require executable permissions, but normal files just require read permissions.  Say say you have some html files - they should be owned by the user running apache and have permissions 644.  If the file is executable (like a script), permissions should be 755.

---

### Post by ejpyle on 2008-05-11
> **Rocket2DMn said:**
> Any files that you want apache to be able to access need to have read (and possibly execute) permissions on the files for World (the third octal in XYZ permissions).  Scripts require executable permissions, but normal files just require read permissions.  Say say you have some html files - they should be owned by the user running apache and have permissions 644.  If the file is executable (like a script), permissions should be 755.

So should my fstab look like this

/dev/sda1/ /media/disk ext3 rw users 0

I am a little unclear on what I put in there.

---

### Post by Rocket2DMn on 2008-05-11
No, your fstab is fine as it is.  What you need to change is the ownership and permissions on the files that are being shared on your webserver by using the chown and chmod commands.
Can you tell me what directory you are sharing on the drive?  Are you sure the disk access is setup correctly in apache?  Normally you store all the accessible files under  apache's htdocs and cgi-bin directories (I think).

---

### Post by ejpyle on 2008-05-11
> **Rocket2DMn said:**
> No, your fstab is fine as it is.  What you need to change is the ownership and permissions on the files that are being shared on your webserver by using the chown and chmod commands.
Can you tell me what directory you are sharing on the drive?  Are you sure the disk access is setup correctly in apache?  Normally you store all the accessible files under  apache's htdocs and cgi-bin directories (I think).

yes i think u are right....this worked for me a few weeks ago so i think it is the permissins on the folder...

Basically the folder with the website is /media/disk/www/

I need this accessible via website users.

---

### Post by Rocket2DMn on 2008-05-11
OK, so you are supposed to run apache using a regular user (not root), so we will call that user "user1".  The /media/disk/www/ should be owned recursively by user1 and all files should have permissions 644, unless they are executables, in which case the permissions would be 755.  So,
```
sudo chown -R user1 /media/disk/www/
sudo chmod 644 -R /media/disk/www/
```
I would run those commands if you think that the current permissions are wrong (substituting user1 with the correct username), then you can go and change executables to have 755 permissions.  You should NOT be changing apache files with these permissions, just the stuff that is available on the website.

---

### Post by ejpyle on 2008-05-11
> **Rocket2DMn said:**
> OK, so you are supposed to run apache using a regular user (not root), so we will call that user "user1".  The /media/disk/www/ should be owned recursively by user1 and all files should have permissions 644, unless they are executables, in which case the permissions would be 755.  So,
```
sudo chown -R user1 /media/disk/www/
sudo chmod 644 -R /media/disk/www/
```
I would run those commands if you think that the current permissions are wrong (substituting user1 with the correct username), then you can go and change executables to have 755 permissions.  You should NOT be changing apache files with these permissions, just the stuff that is available on the website.

OK I understand except for one small detail....

where does apache verify user1 at?

If i want to change the ownership from root what name am i using? do i make this name under "users and groups"?

---

### Post by Nepherte on 2008-05-11
[quote="ejpyle"]where does apache verify user1 at?[/quote]
Linux itself and not apache will check that. Linux will enforce the ownership and user rights of that map to everyone.

[quote="ejpyle"]If i want to change the ownership from root what name am i using? do i make this name under "users and groups"?[/quote]
I wouldn't put it under the users group. I'd rather create a new group 'www' for example and add the necessary users to it.

---

### Post by Rocket2DMn on 2008-05-11
It depends on who is running the apache daemon.  You can check with
```
ps aux | grep httpd
```
If it is being run as root, then you should change it.  I don't have an apache install myself, so I can't walk you through that, but if you google, I'm sure you can find out very quickly how that is done.  Perhaps start here - [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html) (it's for Dapper, but apache hasn't changed much if at all, so it still applies).
You can also use apache's website - [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)
I'm going to go to bed now, so I will check up on you in the morning.  I guess I would suggest doing a little research/googling, then if you have more questions, post them back and I will answer them in the morning.  Good luck!

---

### Post by ejpyle on 2008-05-11
> **Nepherte said:**
> Linux itself and not apache will check that. Linux will enforce the ownership and user rights of that map to everyone.


I wouldn't put it under the users group. I'd rather create a new group 'www' for example and add the necessary users to it.

i am to the point of giving up on it and going back to paid hosting... LOL

I don't understand the permission when it comes to www users...
i know how it works within network sharing and local user accounts, just dont grasp it with apache

---

### Post by Rocket2DMn on 2008-05-11
> **ejpyle said:**
> i am to the point of giving up on it and going back to paid hosting... LOL

I don't understand the permission when it comes to www users...
i know how it works within network sharing and local user accounts, just dont grasp it with apache

Whatever works best for you is fine.  The whole idea is that running apache as root can be a security risk because if somebody is able to hack it, they have root privileges on the system.  Therefore, you run apache as a regular user that doesn't have root privileges, but that user has to have correct access to the files so apache can share them with the world.  Then the world has to have permissions to read them (and execute them if it is a script).  In this case, the world is people using the website.

---

### Post by ejpyle on 2008-05-13
> **Rocket2DMn said:**
> Whatever works best for you is fine.  The whole idea is that running apache as root can be a security risk because if somebody is able to hack it, they have root privileges on the system.  Therefore, you run apache as a regular user that doesn't have root privileges, but that user has to have correct access to the files so apache can share them with the world.  Then the world has to have permissions to read them (and execute them if it is a script).  In this case, the world is people using the website.

well I applied your discussion to hands on....and guess what?

the darn thing is working......so thx for the guidance. :)

on another note I have to do it all over again because I tried to install CGI and screwed it up....

oh well....this is all a really fun learning process.

---

### Post by Rocket2DMn on 2008-05-13
+1 for hands on fun.  Enjoy yourself, and remember, if you break it, you get to keep the pieces!

---

