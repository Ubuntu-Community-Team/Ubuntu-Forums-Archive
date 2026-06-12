---
title: "I reset the root password"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by fyreme on 2008-06-03
Im a little concerned but please keep in mind i'm new to ubuntu.

I forgot my root/admin password. I found help on resetting it here, in an archive in ubuntu forums.

The post was:

sudo passwd root

then I entered the new pass twice and it worked.

What has me concerned is that I was logged on in an ordinary account. 

Am I wrong.. is this not possible?

tia

---

### Post by chronographer on 2008-06-03
I understand that usually there is no root password set with Ubuntu. THis is different to many other Linux distributions where root is an important part of the system. Ubuntu does have root, but uses 'sudo' more. So the root password is your password, in a way. If you change the root password with 'sudo passwd root' it does, sudo=superuser do (root) change password, 'root' which is like changing to root, then changing its password.... if that makes sense. SO if you didn't have sudo privelages, you couldn't change root password, so no there is no problem with you doing this!

I just checked and if you type passwd root, you are not allowed to change the password, as you haven't changed users to root!

---

### Post by SunnyRabbiera on 2008-06-03
in a way having sudo as opposed to su is more secure.
For one root access can be compromised much faster and it makes the user unable to mess around with root and mess up with the system.

---

### Post by spiderbatdad on 2008-06-04
Creating a root password in Ubuntu is an added security risk. As is, publicizing your username. A brute-force-attack hacker, for example would know root exists...if there is no shell available except through the user account, then the hacker would need to know username and password. If root has a password...the first piece is filled in...then just the password to crack.

To disable root login:```
 sudo passwd -l root
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2008-06-04
Just to see how secure your passwords are check out this link:

[http://www.cyberciti.biz/faq/unix-linux-password-cracking-john-the-ripper/](http://www.cyberciti.biz/faq/unix-linux-password-cracking-john-the-ripper/)

Jim

---

### Post by fyreme on 2008-06-04
Thank you, 

I am surprised how quickly my post was answered, and, again, thank you. :)

I didn't understand that there was essentially no root pass in ubuntu.

I was trying use the update feature.. to add security update.. and it asked for an administrative password. I forgot this password and thought I had to change root. I had set root to the same pass as the account I was logged onto, which, I had thought was an ordinary account,, ie,, without admin privileges. I am guessing that the account that I was logged in with had admin privileges and that I should disable the root as instructed above.

Again, thank you, you guys rock. :guitar:

---

### Post by fyreme on 2008-06-04
> **spiderbatdad said:**
> Creating a root password in Ubuntu is an added security risk. As is, publicizing your username. A brute-force-attack hacker, for example would know root exists...if there is no shell available except through the user account, then the hacker would need to know username and password. If root has a password...the first piece is filled in...then just the password to crack.

To disable root login:```
 sudo passwd -l root
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

when I was asked for a password after entering this command I left it blank. Is this how to disable or did I need to enter the root password?

---

### Post by todb on 2008-06-04
> **fyreme said:**
> when I was asked for a password after entering this command I left it blank. Is this how to disable or did I need to enter the root password?

The password you're asked for is the current logged-on account's password. using "passwd -l" locks the root account (that's what the "l" (letter el, not numeral one) stands for).

You will not be asked for the usual new password / retype password exchange.

sudo: Requires the password of the currently logged-on user.
su: Requires the password of the account you're su'ing to.

It can be confusing to keep them straight at first.

---

### Post by aysiu on 2008-06-04
To reset your user password, follow these instructions: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Once you do that, be sure to ```
sudo passwd -l root
``` to lock the account again.

---

### Post by ByteJuggler on 2008-06-04
> **fyreme said:**
> 
I didn't understand that there was essentially no root pass in ubuntu.

I was trying use the update feature.. 

Just to reiterate what was said:  

1.) The root account on Ubuntu is locked by default, meaning you cannot "log in" directly on it.  No password will work as the password field contains a *,which locks it.

2.) The way to perform admin tasks (under the root security context), is via "sudo".  "sudo" will perform a command as root, but, asking *your* password, to verify *you* are who you say you are.  You are allowed this priviled because your user is in the Amin group.  If you add anoter user that is not in the Admin group, then trying to use "sudo" will fail.

I hope that clarifies it.

---

### Post by aysiu on 2008-06-04
If you did somehow remove yourself from the *admin* group, try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by fyreme on 2008-06-04
Thanks again for your help. I entered the command as posted. Here is a copy and past of my terminal session:

 sudo passwd -l root
Password:
Password changed.


Is it locked now? Sorry I'm such a noob, but better safe then sorry.

:guitar:

---

### Post by todb on 2008-06-09
Yep.

---

