---
title: "password on folders!?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by aut-omatic on 2008-11-30
Hi!,
Well, my brother and I have this constant warfare going and it basically includes looking at the other persons private stuff (that are on the computer).
So I was thinking (because linux has been so grate and has proved its self to be really good) if one could lock folders. But in a manner that when you click on the folder is asks for a password. I don't really like encrypting things, or having to store them somewhere. What I want is a fully accessible folder that requires a password every time you want to open it^^.

All help is appreciated ! :D

---

### Post by Norfeldt on 2008-11-30
I new at Ubuntu. But what about using 2 users? It's quick to change user in Ubuntu or you could access the other folder by the terminal instead of switching user.

Did you try to seach the Add/remove.. for "password to folder"?

---

### Post by starcannon on 2008-11-30
+1 to separate user accounts; this is the best way. However, if your brother has admin rights and can run as root/sudo, then there is very little that you will be able to do short of encryption.

---

### Post by oldos2er on 2008-11-30
ccrypt

---

### Post by aut-omatic on 2008-11-30
?? ccrypt? what's that?

---

### Post by drubin on 2008-11-30
> **aut-omatic said:**
> ?? ccrypt? what's that?

[http://ccrypt.sourceforge.net](http://ccrypt.sourceforge.net)

---

### Post by Ben Webber on 2008-11-30
There are other encryption methods out there, with similar functionality. See [**this thread**]("http://ubuntuforums.org/showthread.php?t=182715") for more details and some of the alternatives to ccrypt.

Really though, I suggest making a new user for your brother (as mentioned above).

---

### Post by binbash on 2008-11-30
I suggest you to use 2 different accounts, you can limit the access(reading writing etc).Or you can use truecrypt to encrypt a folder OR disk or File

---

### Post by aut-omatic on 2008-11-30
having another user is not the problem because he has his own computer. He often just sneaks into my room when i'm gone (and i forget to lock my screen) for a few mins and fools around with my computer. This is why i just want a very simple way of giving a folder a password. I'm not a fan of encrypting because you can't access the files easily and one also can't put more stuff in it.

---

### Post by nhasian on 2008-11-30
ubuntu 8.10 comes with the ability for each user to have their own private encrypted directory. from a terminal type:

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private
```

---

### Post by oldos2er on 2008-11-30
> **aut-omatic said:**
> ?? ccrypt? what's that?

 It's a simple little program that allows you to password-protect a file or a folder. To install it open a terminal and run "sudo apt-get install ccrypt".

---

