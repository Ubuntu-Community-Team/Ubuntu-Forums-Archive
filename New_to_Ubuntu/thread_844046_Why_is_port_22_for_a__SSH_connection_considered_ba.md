---
title: "Why is port 22 for a  SSH connection considered bad?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-06-29
Hi,
I've been trying to update my website that's currently being hosted on 1&1 and I've been poking around the ubuntu forum and the 1&1 faq's on how to do that.
My understanding is that FTP is considered old school and SSH is the way to go since supposedly its more secure. (I'm not claiming to know what I'm what I'm talking about here, I'm just summarizing my understanding of about 50 posts.

So I went to  Places->Connect to Server changed it to SSH and filled in the info that's in the 1&1 site under FTP.
It was very cool how easy that was and how the connection shows up in the file browser....  
Anyway, 1&1 documentation talks about using port 22 and I read a ubuntu forum posts talking about you shouldn't use port 22.  :confused:  Could someone who knows more about this stuff elaborate?  
Thanks,
JT

---

### Post by fahadsadah on 2008-06-29
Because port 22 is the default, and it is well known.
If you use key authing (rather than username/password) then you have no problem.

---

### Post by twright on 2008-06-29
> **Jonas thomas said:**
> Hi,
I've been trying to update my website that's currently being hosted on 1&1 and I've been poking around the ubuntu forum and the 1&1 faq's on how to do that.
My understanding is that FTP is considered old school and SSH is the way to go since supposedly its more secure. (I'm not claiming to know what I'm what I'm talking about here, I'm just summarizing my understanding of about 50 posts.

So I went to  Places->Connect to Server changed it to SSH and filled in the info that's in the 1&1 site under FTP.
It was very cool how easy that was and how the connection shows up in the file browser....  
Anyway, 1&1 documentation talks about using port 22 and I read a ubuntu forum posts talking about you shouldn't use port 22.  :confused:  Could someone who knows more about this stuff elaborate?  
Thanks,
JT
there is nothing special about port 22, it is just convention

when people say not to use port 22 that is just to be none conventional, if you use port 22 then someone can guess which port you are using for ssh which could potentially be a security risk

i wouldn't bother changing it

---

### Post by prshah on 2008-06-29
> **Jonas thomas said:**
> 
 I read a ubuntu forum posts talking about you shouldn't use port 22.  :confused:  Could someone who knows more about this stuff elaborate?  


Everyone knows that port 22 is standard for SSH. So anyone (human or bot) trying to hack a box will first attempt port 22. If you change your SSH port to something else, port 22 becomes inactive (unlistened, closed, orphaned) and thus hack attempts on port 22 will fail. Further, only someone who _knows_ your new port number for SSH will be able to make SSH hack attempts. (Though actually, it will still be relatively easy to find out, but at least it will deter newbie hackers and bots)

Just changing the port number is not enough for security. AllowedUsers, Client KeyAuthentication, DisallowRoot all are important security settings that you must check. Look at "/etc/ssh/sshd_config"
 for a full set of options and explanations.

---

### Post by Jonas thomas on 2008-06-29
I poked around /etc/ssh/sshd_config and it started to make my brain ache... I suppose I should go through the man pages on this... Can anyone point me to some recommended reading on how to limit my security risk on inadvertenly doing something I'll regret latter on. Moderate to light technobabble prefered.. ;)
JT

---

### Post by NovaAesa on 2008-06-29
Be aware that security via obscurity is really a form of false security, which is inevitably a bad thing.

---

### Post by prshah on 2008-06-29
> **Jonas thomas said:**
> I poked around /etc/ssh/sshd_config and it started to make my brain ache... I suppose I should go through the man pages on this... Can anyone point me to some recommended reading on how to limit my security risk on inadvertenly doing something I'll regret latter on. Moderate to light technobabble prefered.. ;)
JT

When reviewing your post, I realise you're talking about connecting as an ssh _client_. Nothing of what I said is applicable to you. It's applicable to 1&1, and I assume that they will have all relevant security in place.

In fact, if you are not using sshd (secure shell _server_) on your local machine, you should disable it. If you disable sshd then you can still continue to make connections to other ssh servers, and use ssh, but other computers (hackers, bots, etc) cannot connect and control your computer. 

To disable secure shell _server_ (ie, disallow others to initiate connections to your computer), use ```
sudo /etc/init.d/ssh stop
``` Note that though the command says ssh, it actually refers to sshd.

an additional tip: ```
man scp 
``` will open up a whole new world of wonders. (scp = secure copy)

---

### Post by hyper_ch on 2008-06-29
using port 22 is not considered bad... just use an auto-ban service like denyhosts

---

### Post by brian_p on 2008-06-29
> **Jonas thomas said:**
> 
Anyway, 1&1 documentation talks about using port 22 and I read a ubuntu forum posts talking about you shouldn't use port 22.  :confused:  Could someone who knows more about this stuff elaborate?  

1&1 offer a ssh service on port 22. Only they can change that. The posts you have read are about running a ssh service on one of your own machines. It's daft advice anyway and 1&1 agree.

You use the ssh client. It is set up to connect to port 22 at 1&1.

---

### Post by Jonas thomas on 2008-06-30
Thank you for the info. 
Would sudo /etc/init.d/ssh stop only affect inbound only??  I suppose I should experiment a little bit with this when I'm a little less tired.

 I was talking a friend of mine earlier today (who uses Windows exclusively) to tell him about all the cool free stuff I'm finding in Ubuntu to maintain my website.  He had mentioned he has when he adjusts the local copies of his website that they automatically update on the server.  I wish I remember the name of the application he said he uses.... I wonder if there is something similar to that in Ubuntu. I skimmed the man scp.  It didn't seem like scp  could do that sort of type of update.  I suppose I should ask him the name of application and then search of the open source equivalent.

---

### Post by Jonas thomas on 2008-06-30
re:Be aware that security via obscurity is really a form of false security, which is inevitably a bad thing.
This may be true, but the best place to hide a tree is in a forest.

---

### Post by bodhi.zazen on 2008-06-30
Here is a nice wiki page re: ssh security :

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by Cadmus on 2008-06-30
> **Jonas thomas said:**
>  I was talking a friend of mine earlier today (who uses Windows exclusively) to tell him about all the cool free stuff I'm finding in Ubuntu to maintain my website.  He had mentioned he has when he adjusts the local copies of his website that they automatically update on the server.  I wish I remember the name of the application he said he uses.... I wonder if there is something similar to that in Ubuntu. I skimmed the man scp.  It didn't seem like scp  could do that sort of type of update.  I suppose I should ask him the name of application and then search of the open source equivalent.

You're looking for that most versatile of programs, rysnc. Rsync uses ssh to update files so you can use it on any machine you cn ssh to. As always take a look at the man page, and ask us about any problems.

Basically rsync examines the modification dates on the source and destination files (and checksums too, but that's very cpu intensive) and only copies those which have changed.

---

### Post by nowshining on 2008-06-30
/etc/init.d/ssh is the startup service for ssh, anything in /etc/init.d are services and can use the stop start and restart commands.

---

### Post by twright on 2008-06-30
> **nowshining said:**
> /etc/init.d/ssh is the startup service for ssh, anything in /etc/init.d are services and can use the stop start and restart commands.
eg to stop ssh you would use
```
sudo /etc/init.d/ssh stop
```

---

### Post by prshah on 2008-06-30
> **nowshining said:**
> /etc/init.d/ssh is the startup service for ssh, 


> **twright said:**
> eg to stop ssh you would use
```
sudo /etc/init.d/ssh stop
```

As I mentioned, /etc/init.d/ssh refers to **sshd** or the ssh _server_ daemon. Starting, stopping or restarting this only affects SSH _server_ functions on the _local_ machine, it has no effect on ssh client operations, eg, connecting to another server using SSH, using scp/rcp, using rsync, etc.

---

