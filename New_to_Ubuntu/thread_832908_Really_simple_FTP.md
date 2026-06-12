---
title: "Really simple FTP"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-18
OK, I am getting a bit lost and frustrated...everyone has a different opinion to the best way to FTP.

Can someone recommend a very simple way to set up FTP on my home server, that I will then be able to access over the internet.

My thinking is that I would like to be able to FTP my shared directory on the server, so I can access all my data in that folder from anywhere. This same folder is the one I share on my LAN for users to use as storage space on the server.

For example, I am away from home and want to give someone a copy of a photo I know I have at home on the server. Is this the best way to do this? 

If so, I would like to be able to just enter the address (what address) in either a web browser or ftp client, have a single username and password that allows only that one name to be able to log on and access the files on the server.

Perhaps there is a better way to do this? if not FTP it is. 

I have tried proftpd and had a look at vsftpd with not very successful results, even just in the LAN.



Just a thought, I have remote access set up and (nearly) working. Obviously when I am remote controlling I can browse to the files on the server, but I guess there is no way of then extracting those files through the remote interface onto the machine I am using?

Thanks in advance!

---

### Post by hyper_ch on 2008-06-18
well, I'd use SFTP/SCP

(1) install ssh server
```

sudo apt-get install openssh-server

```

(2) install denyhosts
```

sudo apt-get install denyhosts

```
--> that will auto-ban ip addresses that try to brute-froce your ssh-server... you should maybe have a read on how to use/configure

(3) Forward port 22
If your computer is behind a router, you need to forward the port 22 TCP from your router to your computer (best to give your computer a static IP in your land)

(4) Connect to it:
- Windows: Use [http://www.winscp.com](http://www.winscp.com) --> Login with your username and password
- Linux: There are a few programs for it... I normally use konqueror as it is a multi-pane filemanager -->  enter  fish://USER@YOUR_IP  wher USER is your username and YOUR_IP is your ip address or no-ip/dyndns name.
That is for file management - ftp style

of course you can also login with a terminal:
- Windows: Download putty --> [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
- Linux: Open a termina and run:  ssh USER@YOUR_IP
---> you will then have a full terminal shell open where you can, sort of, completely administer yuor computer

---

### Post by jcr1 on 2008-06-18
ok... so I install those two packages, forward that port and thats it?

Where do I tell it what users can connect, passwords, what directory to access?

Can I just use filezilla from any machine? If so, what would the address and user be? The external IP of my router? Which user though? The admin of my server? or another user set up just for ftp access with his home directory set to the folder I would like to access?

Thanks for your quick response

---

### Post by hyper_ch on 2008-06-18
sorry, I thought only you want to have access to it (reading too fast and skipping half of it ^^^)

You need to clarify a bit:

- You and other shall have access to it
- Shall the others also be able to connect to it from outside your lan?
- If the others shall also be able to connect from outside your lan, shall they have only read or also write permission?

---

### Post by jcr1 on 2008-06-18
> **hyper_ch said:**
> sorry, I thought only you want to have access to it (reading too fast and skipping half of it ^^^)

You need to clarify a bit:

- You and other shall have access to it
[COLOR="Red"]Just me (one user) for now[/COLOR]
- Shall the others also be able to connect to it from outside your lan?
[COLOR="red"]I would like this one user to be able to connect from the outside. Inside, I can access files through a share.[/COLOR]- If the others shall also be able to connect from outside your lan, shall they have only read or also write permission?
[COLOR="red"]the one user that can connect from outside, read and write[/COLOR]

Thanks!

---

### Post by hyper_ch on 2008-06-18
that is achieved with ssh server install... you can login using your credentials... if you want others to connect, you might want to go an alternate route (or know what you're doing)

---

### Post by jcr1 on 2008-06-18
ok, so when I install ssh, do I need to configure it, or is the default setting to allow the admin of the server to be the only user that can access it?

Do I then just go to the external ip of my router in an ftp client and use my login details like i would use to log in to the server itself?

What is the default directory it allows you to see?

I think I may be getting confused as to what ssh is actually allowing me to do. The way I picture it, I just simply want to access a certain directory on my server, from outside my LAN and be able to extract files and upload files... with a username and password for security.

Can ssh allow me to do more?

When you log in from a terminal on another linux machine, what do you see..what can you do?

---

### Post by hyper_ch on 2008-06-18
> **jcr1 said:**
> ok, so when I install ssh, do I need to configure it, or is the default setting to allow the admin of the server to be the only user that can access it?
All system users can login that do not have certain restrictions... the root account can login as it is not enabled by default. So if you setup jcr1 and first user during install and then made another user "tom" then either of you can login.
However if you want to give other people access you might want to consider using "mysecureshell" to limit those people.

> **jcr1 said:**
> Do I then just go to the external ip of my router in an ftp client and use my login details like i would use to log in to the server itself?
You need a sftp/scp capable client... I liked WinSCP very much on windows and use konqueror on linux. But basically you will connect to the external IP and the router should then forward it to yur server. Hence forwarding of port 22 is needed. You use your normal username/password that yuo also use to login normally.

> **jcr1 said:**
> What is the default directory it allows you to see?
You'll be logged into your home folder. However you can transverse through any directory - as your normal user can when you are on the machien itself. With mysecureshell you can restrict other users then...

> **jcr1 said:**
> I think I may be getting confused as to what ssh is actually allowing me to do. The way I picture it, I just simply want to access a certain directory on my server, from outside my LAN and be able to extract files and upload files... with a username and password for security.
SSH allows you that... and a few thigns more... plus all the traffic is encrypted...

> **jcr1 said:**
> Can ssh allow me to do more?
By default you'll have also a normal ssh login which allows you to run commands on your computer. E.g. you have a theme... you can then upload the tar.gz file to your computer and then issue a command to unpack it there...

> **jcr1 said:**
> When you log in from a terminal on another linux machine, what do you see..what can you do?
The same as when you open a terminal on the computer directly.

---

### Post by jcr1 on 2008-06-18
Fantastic answers!

Thank you ever so much for all your help. I will have fun setting this up!

---

### Post by jcr1 on 2008-06-20
Just top say thanks again! This was really so simple to get working, seems too good to be true. Cheers!

Just trying to find ways of using the ssh login to use files remotely as per this thread now:
[http://ubuntuforums.org/showthread.php?t=834607](http://ubuntuforums.org/showthread.php?t=834607)

---

### Post by hyper_ch on 2008-06-20
If you use Konqueror it should be able to open it (I think)

or you use 

[http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856)

---

### Post by jcr1 on 2008-06-20
Thank you very much. You have been very helpful!

---

