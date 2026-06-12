---
title: "Permissions on a External USB Drive for Backup"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by OZFive on 2008-10-09
I have a Maxtor 160bg One Touch 4Mini USB Hard Drive I bought  awhile back for data backup.  I had an issue and installed a full Ubuntu System on there but now am ready to use it for general backup purposes now.  I used Gparted to get the system off of it and formatted it to ext3 but now I cannot place anything on there as the entire drive is owned by root.  

So how do I change the permissions on the drive and make them stick so I can perform routine back up and transfer of large files to the external?

---

### Post by Idefix82 on 2008-10-09
Firstly, the fact that the drive is owned by root shouldn't stop you from using it, it just means that you have start each command which modifies the content of the drive with sudo:
```
sudo cp /home/Music /media/driveName
```

If that bothers you then you can change the ownership by
```
sudo chown -R username:username media/driveName
```
where of course username is your user name and driveName is the folder under which the HD is mounted.

---

### Post by OZFive on 2008-10-09
> **Idefix82 said:**
> 
```
sudo chown -R username:username media/driveName
```
where of course username is your user name and driveName is the folder under which the HD is mounted.

That did it, thanks!

---

### Post by mexicanbob on 2008-10-09
Please bear with this newbie to Ubuntu :)
I have just followed this thread as I too have just added a maxtor 120gb external hard drive which I want added.
opened the terminal and typed sudo chown -R username:bob media/wine but the terminal keeps coming back with "invalid username" I have set up my current profiles etc ... starting to get a bit angry :lolflag:

Can you plse help?

mexicanbob

---

### Post by jerome1232 on 2008-10-09
```
sudo chown -R $USER:$USER /media/wine
```

---

### Post by mexicanbob on 2008-10-10
Hi Jerome
Thank you for your reply and the only request is sudo chown -R $USER:$USER can you please suggest what to put after it ( embarassed) what folder ??

Ubuntu is great.  Although a bit of a challenge after using the OTHER op.

Bob

---

### Post by Idefix82 on 2008-10-10
If you plug in your hard drive, make sure it is mounted (an icon should appear on your desktop) then go to the terminal and type
```
ls -l /media
```
and give us the output then we will be able to tell you exactly what to type in.

Just to explain what was going on with your first command: you should have typed "bob:bob" instead of "username:bob". The first "bob" is the user and the second "bob" is the group. By default each group only consists of one user and has the name of the user. But on larger systems you may have less groups than users. With hundreds or thousands of users on one system, the group provides a convenient way of managing permissions and privileges. This will probably never concern you, just to explain why you have to type the same thing twice.

Jerome's solution was to use the environment variable $USER so you could actually copy his command without changing anything. I hope this makes sense.

Oh, and welcome to the free world :)

---

### Post by mexicanbob on 2008-10-10
Hi Guys

Thank you  Jerome & Idefix

No matter what I tried it wasn't successful ( uumm but still I try :) )
Your instructions were clear.  So I went back to windows and suddenly got a message after I disconnected the Maxtor ' run "chkdsk /f" which i did and then I had to reboot windows TWICE after that.

Ok then I got back to Ubuntu and lo and behold there in "Places" is the 120GB drive.

So keeping my fingers crossed it stays there.
Thank You both for your time and advice

Bob

---

### Post by Idefix82 on 2008-10-10
Oh, when dual booting you have to remember one thing: when you mount a device like an external HD, there is a flag on the HD which is set by the OS to say that it is mounted. When Windows mounts a HD but you don't use the "securely remove hardware" option or whatever it's called, to unmount it at the end then Ubuntu will read the flag and tell you that the device is still mounted by another OS and refuse to mount it.

Summary: Under Windows, always "remove" the hardware via the corresponding button in the lower right corner at the end of your session. Under Ubuntu, always unmount the device by right clicking on its icon on the desktop and saying "unmount". Then you won't have any trouble.

Your problem had nothing to do with permissions, unlike that of the original poster, it was just two OSs fighting for one device.

---

