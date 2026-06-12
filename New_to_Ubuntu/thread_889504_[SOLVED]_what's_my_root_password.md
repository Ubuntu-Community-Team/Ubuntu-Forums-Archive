---
title: "[SOLVED] what's my root password?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-14
I'm trying to install POV-Ray onto Linux using their step-by-step instructions here: [http://povray.org/download/linux.php]("http://povray.org/download/linux.php"). I've reached step 8 and I tried my user password but it didn't work, at least 20 times now, it's not a caps lock thing either. What's my root password? How do I find it? Or what's its default value?

---

### Post by Rolcol on 2008-08-14
The root account is automatically disabled on Ubuntu.  Use sudo before the command to run it with "root powers" without being root.  If you actually want to become root without adding a password for root, use this command:```
sudo su
``` input your usual password.

---

### Post by Aalnius on 2008-08-14
you don't have a root password you have to use sudo. you can however unlock your root like i did but its not recommended by ubuntu expert ppeople and they say sudo is easier.
Also i don't think i'm allowed to tell you how to unlock root.

---

### Post by Bradtek on 2008-08-14
root account is disabled in Ubuntu
To run / install things in Ubuntu as root
you type
```
sudo
```
before each command that requires root privileges
eg.
```
sudo ./install
```

---

### Post by Rolcol on 2008-08-14
> **Aalnius said:**
> you don't have a root password you have to use sudo. you can however unlock your root like i did but its not recommended by ubuntu expert ppeople and they say sudo is easier.
Also i don't think i'm allowed to tell you how to unlock root.

I think it'd be fine to at least explain.  The root account is actually there but with a randomized password.  If hackers attack your computer, they will usually attempt to attack root since there's always a root user.  Brute force attacks usually try different dictionary patterns which is what typical passwords created by humans are.

---

### Post by zzzonked on 2008-08-14
But that's what it says on the instructions:
#

8. become root:

user@machine:~/povray/povray-3.6> su
Password: <enter root password>

#

9. run the install script:

root@machine:/home/user/povray/povray-3.6> ./install

Check if the install script reports any problems. At the end you will be asked if you want to do a test render. This test render will be without display when run as root.
#

10. leave the root environment:

root@machine:/home/user/povray/povray-3.6> exit

So how do I make my way around this and still get my software to work normally?

---

### Post by Bradtek on 2008-08-14
The instructions obviously were not written for Ubuntu

---

### Post by Rolcol on 2008-08-14
> **zzzonked said:**
> But that's what it says on the instructions:
#

8. become root:

user@machine:~/povray/povray-3.6> su
Password: <enter root password>

#

9. run the install script:

root@machine:/home/user/povray/povray-3.6> ./install

Check if the install script reports any problems. At the end you will be asked if you want to do a test render. This test render will be without display when run as root.
#

10. leave the root environment:

root@machine:/home/user/povray/povray-3.6> exit

So how do I make my way around this and still get my software to work normally?
You can either use "sudo" before every command, for example: ```
sudo ./install
``` or, become sudo this way (instead of step [noparse]8):[/noparse] ```
sudo su
```  It will prompt you for your user password.

---

### Post by spec-chum on 2008-08-14
> **zzzonked said:**
> But that's what it says on the instructions:
#

8. become root:

user@machine:~/povray/povray-3.6> su
Password: <enter root password>

#

9. run the install script:

root@machine:/home/user/povray/povray-3.6> ./install

Check if the install script reports any problems. At the end you will be asked if you want to do a test render. This test render will be without display when run as root.
#

10. leave the root environment:

root@machine:/home/user/povray/povray-3.6> exit

So how do I make my way around this and still get my software to work normally?

Ignore step 8.

For step 9 instead of running ./install run
```

sudo ./install

```
and enter your password.

That will run the install script with root priviledges.

You don't need to type exit afterwards, so step 10 is unnecessary too.

---

