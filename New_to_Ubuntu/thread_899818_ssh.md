---
title: "ssh"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by anderskitson on 2008-08-24
I am trying to ssh into a openssh device. I get this error
I was able to do it yesterday no problem, in nautilus. I can do it in putty but i want the gui interface
> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!

Someone could be eavesdropping on you right now (man-in-the-middle attack)!

It is also possible that the RSA host key has just been changed.

The fingerprint for the RSA key sent by the remote host is
5a:e8:06:f3:8c:1e:d5:f2:d4:9d:99:eb:d4:04:c3:fa.

Please contact your system administrator.

Add correct host key in /home/anders/.ssh/known_hosts to get rid of this message.

Offending key in /home/anders/.ssh/known_hosts:3

RSA host key for 192.168.75.185 has changed and you have requested strict checking.

Host key verification failed.

---

### Post by Joeb454 on 2008-08-24
Edit your known hosts file, the remote device has likely been updated :)

---

### Post by nothingspecial on 2008-08-24
Have a look at this.
Make sure you read the whole page (including all the comments at the bottom before deciding what to do)
As for me I used the original method but if you have any security worries at all look further into it.

[http://tombuntu.com/index.php/2008/01/29/fix-the-ssh-remote-host-identification-has-changed-error/](http://tombuntu.com/index.php/2008/01/29/fix-the-ssh-remote-host-identification-has-changed-error/)

I`m serious - don`t just delete your ~/.ssh/know_hosts file unless you are completely happy with your security.

---

### Post by bodhi.zazen on 2008-08-24
As indicated by nothingspecial, you need to check the integrity of the server.

---

