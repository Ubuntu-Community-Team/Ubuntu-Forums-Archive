---
title: "Great uses for SSH you probably DONT KNOW!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by neurostu on 2008-05-16
Seeing as how this forum is mostly "Beginner Talk" I thought I would share some of the great things you can do with SSH!

SSH - is a secure shell program that lets you create secure connections to other computers. Most people use it to get CLI access on another machine but using SSH you can accomplish a lot of different things.
[B][U]
1 - Windows Forwarding[/U][/B]
Using the -X or -Y option on SSH you can run programs on a remote machine but have the window opened on your local machine.
```

ssh user@remoteMachine -X

```
Then if you type ./firefox in the prompt of the remote machine, firefox will open but it will be running on the remote machine. This is great if you have a intra-office (school) website you want to access but can only do it locally. 

**_2 - SSH Keys_**
SSH Keys allow you to create SSH connections WITHOUT using a password. It is really easy to do and makes logging into other machine  really slick!

I'm not going to post how to do it but here is a great link:[COLOR="Blue"][http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html](http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html)[/COLOR]

**_3 - SSHFS_**
SSH File system, is a great program that will let you mount a remote directory locally using SSH, its super easy to use, first install it with aptitude or synaptic then to use it type:
```

sshfs user@remoteHost:remoteDir localMountPoint

```
Thats it, now you can work with a remote directory as if it were local.

I will try to post more uses of SSH here later on as i remember them.

If you can come up with anymore great uses feel free to post them below!

good luck and enjoy SSH!

---

### Post by dizee on 2008-05-16
> **neurostu said:**
> **_2 - SSH Keys_**
SSH Keys allow you to create SSH connections WITHOUT using a password. It is really easy to do and makes logging into other machine  really slick!

I'm not going to post how to do it but here is a great link:[COLOR="Blue"][http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html](http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html)[/COLOR]

Nice post but, just so you know there is a security vulnerability with ssh keys: [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by PinkFloyd102489 on 2008-05-16
You have to authenticate to the remote machine first, so security is still foremost.

---

### Post by seetho on 2008-05-16
> **dizee said:**
> Nice post but, just so you know there is a security vulnerability with ssh keys: [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

Problem has been solved with latest update of libssl according to the announcement.

---

### Post by neurostu on 2008-05-17
>  Nice post but, just so you know there is a security vulnerability with ssh keys: [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326) 
So within a day the vulnerability was announced it was patched. Your post is good in that it reminds people to always keep security in mind.

---

