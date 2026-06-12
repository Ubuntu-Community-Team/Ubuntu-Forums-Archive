---
title: "ftp folder setup"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by r3bol on 2012-01-15
Hi, Ok, bare with me :P

I have forwarded port 21 from my router and created an account on dyndns.org to keep tabs on my ip address and set up a ftp server (vsftpd). I can login via ftp with filezilla using my user credentials and get access to my home directory. 

So this is good so far, but I also want to create another folder in /home (outside my user folder) called ftp for my friend to be able to download from -- while I can read/write to it. What would be a good way to only give him ftp download access to this folder while keeping him out of my user folder?

Thanks :)

---

### Post by r3bol on 2012-01-16
Bump and update:

I tried this, but it didn't work...

* Create a folder called 'share' in /home
* Make myself the owner and make the group 'share'
* Create a new user, but not allocate a home directory to the user and add him to the group 'share' -- like # useradd -M john -g share
* Give the user john a login and password and activate the user account.

So, after setting this up, I couldn't access 'share' via ftp login using john's credentials.

---

### Post by Cheesemill on 2012-01-16
I know this doesn't answer your question but I just thought I'd point out what a bad idea it is to use FTP in this situation.

FTP is incredibley unsecure, all of the data and the username/password are sent in plain text with no encryption, you're making it very easy for someone to hack your machine.

I'd look into SSH instead if I were you.

---

### Post by nhasian on 2012-01-16
as Cheesemill suggested, rather than using ftp, use sftp and you will want to forward port 22 instead of port 21 from your router.  You will want to create a new login for your friend so you dont give out your personal info.  Then when you create your /home/share folder make sure that both of you have permission to read/write to it and you should be all set.

---

### Post by r3bol on 2012-01-16
Hi, thanks for the replies.

So to do sftp, I open port 22 and when connecting with filezilla, use the sftp protocol? 

Is it possible to create a user without a home directory of their own?

Thanks.

---

### Post by r3bol on 2012-01-16
Ok solved. 

The shtp over SSH was very easy to setup. The problem was the shell access I gave the user. It seems if I don't give him bash, it won't let him connect. 

With bash, he has access to folders in root which I don't want. So I'll look at solving that problem -- which shouldn't be too hard with googl ;)

---

### Post by Derek Karpinski on 2012-01-16
set his shell to /bin/false.
 
You need to make sure '/bin/false' is included in your '/etc/shells' file.

---

