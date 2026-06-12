---
title: "Server?? Sharing/accessing files over the internet"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by jmiller87 on 2008-10-14
I am a week old Ubuntu user now and have been searching the forums looking for any way to share files anywhere I have an internet connection.

My situation is this....

I have an old desktop that I am now happily using the latest Ubuntu on and a laptop that I am still running windows Vista on.
I am sharing a 500GB hard drive that is on the Ubuntu computer and everything is great as long as I am at home and connected to my router. 

What I am looking to do is be able to access that same hard drive or at least some of the files on that hard drive when I am not at home ie: at school or at work.

I have read alot about samba, SSH, ftp, sftp, ebox and many other things and I am frankly very lost right now!
Any help that someone can give me would be greatly appriciated!! 

-Joshua

---

### Post by Nxion on 2008-10-14
How much data do you have all together that you access on the hard drive?

---

### Post by jmiller87 on 2008-10-14
well right now only about 10GB, but this is growing to become my pet project for music and video. So the plan is to fill up this drive with music and video and add more when needed.
But I also have a lot of office docs, spreadsheets and such that I access weekly for work and such.

---

### Post by bodhi.zazen on 2008-10-14
Well, you have a few options as you can see. I think one of the primary concerns should be security and as such I think ssh (scp) and sshfs are your best options.

Second would be apache (http) , but that is one way.

Third would be ftp (vsftp or proftp).

I would not advise NFS or Samba over the internet.

---

### Post by jmiller87 on 2008-10-14
Does it matter at all that I would be accessing the hard drive primarly from windows computers?

And out of the options you listed which is the easiest/most secure to set up.....remember that I am very new to ubuntu and also the idea/goal I am trying to accomplish.

---

### Post by bodhi.zazen on 2008-10-14
As I said, ssh if by far the most secure.

You can use putty and winscp from windows.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Winscp looks like this (what could be easier ???)

[IMG]http://winscp.net/eng/data/media/screenshots/commander.png[/IMG]

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

---

### Post by jmiller87 on 2008-10-14
Thanks I will check these out and let ya now how it goes!

---

### Post by AndyCooll on 2008-10-14
You'll need to be looking at using ssh, and in turn setting it up so that you can connect using it remotely (i.e. if you have a router port forwarding the ssh connection to your Ubuntu pc. 

At it's most basic ssh works by creating an encrypted secure "tunnel" between the computer in front of you and the remote computer. For it to work you'll need ssh-server runner on the remote pc, and a client (e.g. PuTTY) on the computer in front of you.

ssh is initially a command line tool (not sure if there is a gui front end for it). However once the "tunnel" has been created, i.e once you've connected to the remote pc it's possible to run gui apps through the tunnel etc etc.

:cool:

---

### Post by Nxion on 2008-10-14
> **bodhi.zazen said:**
> As I said, ssh if by far the most secure.

You can use putty and winscp from windows.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Winscp looks like this (what could be easier ???)

[IMG]http://winscp.net/eng/data/media/screenshots/commander.png[/IMG]

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

I agree ssh(SCP) is the way to go. It is the most secure to use, and is not that difficult to setup.

---

### Post by taqkavar on 2008-10-14
While people above are right about ssh being more secure, From a newb point of view, I would suggest using gproftpd. Its quite easy to setup, and you can access it with any browser without the need of any extra programs on the client.

Yes, the data can be intercepted in a ftp connection, but so can your day to day http browsing and downloads on the very same computers. Just make sure you choose a good long password.

sudo apt-get install grpoftpd
then
System > Administration > gproftpd
Don't forget to forward port 21 and the passive mode ports range on your router.

---

### Post by bodhi.zazen on 2008-10-14
> **taqkavar said:**
> While people above are right about ssh being more secure, From a newb point of view, I would suggest using gproftpd. Its quite easy to setup, and you can access it with any browser without the need of any extra programs on the client.

Yes, the data can be intercepted in a ftp connection, but so can your day to day http browsing and downloads on the very same computers. Just make sure you choose a good long password.

sudo apt-get install grpoftpd
then
System > Administration > gproftpd
Don't forget to forward port 21 and the passive mode ports range on your router.

I have to disagree with that advice (sorry). It is no harder to set up ssh then ftp (how is apt-get install openssh-server harder or easier then apt-get install gproftpd ???).

The "difficulty" is in securing your server, and IMO all servers should be secured.

Also, again IMO, FTP servers are notoriously insecure, not just during data transmission (which is what you are referring to) but by the nature of the ftp protocol. I agree they can be secured, but IMO installing FTP servers is not such good advice for new users (and reading through the FTP config files is a real pain for new users, and small mistakes in your ftp config can render your system (server) wide open).

---

### Post by taqkavar on 2008-10-14
I'll keep it short
1- Any modern browser supports ftp:// urls, while you need a client program for ssh
2- gproftpd is a GUI frontend for proftpd and is quite simple. No thinkering with config files there too.

Its security or accessibility here. I would choose the former for non work related stuff.

---

### Post by JoshuaRL on 2008-10-14
> **taqkavar said:**
> I'll keep it short
1- Any modern browser supports ftp:// urls, while you need a client program for ssh
2- gproftpd is a GUI frontend for proftpd and is quite simple. No thinkering with config files there too.

Its security or accessibility here. I would choose the former for non work related stuff.

Well, I think that he's talking about config files for FTP server side.  Sure, it can be easy to set up non secure, but SSH is well known to be easy and secure too.  Really, the difference between the two is insignificant as far as difficulty.  Have you read that wiki page on SSH?  I have rarely read one that concise and understandable.  SSH is really the way to go, especially for the OP who wants to use his files at work.

To the OP:  If you don't have the admin rights to install on your work machine, go to [www.portableapps.com](www.portableapps.com).  They have apps you can install to a USB drive and use on other windows machines without installing.  Look into Putty for what you want.

---

### Post by jamesrfla on 2008-10-14
I use SSH(SCP) and it is just what I wanted. Just put winscp on a flash drive and go anywhere and get all the files you need securely.

---

### Post by hwheeler43 on 2008-10-14
:)You people make it easy to learn things.  Can I use SSH on my Ubuntu server and WinSCP client on my windows machine to update my Web server?  I think this would be the best procedure for doing this.  However,  I am a bit of a Linux newby and would like a professional opinion.

---

### Post by jamesrfla on 2008-10-14
> **hwheeler43 said:**
> :)You people make it easy to learn things.  Can I use SSH on my Ubuntu server and WinSCP client on my windows machine to update my Web server?  I think this would be the best procedure for doing this.  However,  I am a bit of a Linux newby and would like a professional opinion.

Yes except when you put in the new web page you need to SSH into the server and run one command. You can use putty to do that. After you change the web page SSH into your server and run this command ```
sudo /etc/init.d/apache2 restart
```

---

### Post by hwheeler43 on 2008-10-14
Thank you. I will install putty as well if needed.  Do you know if a command can be run using WinSCP?  Just curious as it would be nice to just use one client.

---

### Post by jamesrfla on 2008-10-14
Unfortunately you have to have two. WinSCP is just used for transferring files. Their might be a way but I don't know it or think their is.

---

### Post by hwheeler43 on 2008-10-14
Thank you very very much.  I will install both.  It will be a good learning experience.

---

