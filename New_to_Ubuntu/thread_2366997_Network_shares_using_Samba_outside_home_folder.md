---
title: "Network shares using Samba outside home folder"
date: 2017-07-24
forum: New to Ubuntu
---

### Post by curtash on 2017-07-24
Hi All,


I'm a new to Ubuntu but understand a bit of Linux. I'm using version 16.04LTS


I'm really struggling to create a network share. I can create a folder in my home folder and get it working but when I try on my mounted internal RAID I cannot. 


I assume that there is a permissions error as I can log in via OSX and Windows using //smb:192.168.0.29 and I can see my folders but I cannot open them. I get a permission denied.


I've spent countless hours on this and I've tried all sorts so I'm hoping someone can point me in the right direction here. Many thanks in advance.


The following is what I did:

**Installed Samba**
```
sudo apt-get samba
```

**Added a Linux user**
```
sudo adduser nic
```

**Added an smb password**
```
sudo smbpasswd -a nic
```

[B]Added nic to the group users
[/B]```
sudo usermod -a -G users nic
```

**Edited the config**
```
sudo nano /etc/samba/smb.conf
```

```
[Test]
        comment = Test Share
        path = /media/ns/storage/test
        browseable = yes
        only guest = no
        force group = users
        writeable = yes
        create mask = 0777
        directory mask =0777
        force directory mode = 2777
```


**restarted the smbd service**
```
service smbd restart
```

---

### Post by curtash on 2017-07-25
Still working on a solution. Here is some more info.

I've checked the permissions of my RAID drive and checked that the group owner is **users**

```
**server:/media/ns$** ls -l
```

```
total 4 
drwxrwxrwx+ 13 ns users 4096 Jul 24 19:18 storage



```

The folder I'm trying to share sits within the **storage** folder. Oh and the **storage** folder is the root of my RAID.

---

### Post by curtash on 2017-07-25
Problem solved. As with any linux related issue the solution to my specific issue was spread across many many forums and for a noob it is difficult to understand what is the best method and advice!

Anyway as I've said **I'M NO EXPERT** so if you follow my solution and it does not work or worse then tough :p. Also if there are any experts that want to put me right then please feel free.

"My" Solution

Navigate to the folder that your RAID or drive is mounted to and modify the permissions. I used 777, I'm aware this is bad practice but I then locked the Samba users to their own folders in the /etc/samba/smb.conf file. My server sits in my home. I'm sure people may say I'm crazy but I'm hoping that an expert will post a better solution here.

I used:
```
sudo chmod 777 /media/ns
```

---

### Post by Morbius1 on 2017-07-25
> drwxrwxrwx[COLOR=#0000cd]**+**[/COLOR] 13 ns users 4096 Jul 24 19:18 storage
It's a little late at this point but do you see that little "+" sign at the end of the permissions? You will see the same thing with /media/ns.

That indicates there are extended permissions being applied to that folder - an access control list ( acl ) to be specific. 

As an example on my own system I can look at these acl permissions of my /media/tester1 folder this way:
> tester1@vu17:~$ getfacl /media/tester1
getfacl: Removing leading '/' from absolute path names
# file: media/tester1
# owner: root
# group: root
user::rwx
user:tester1:r-x
group::---
mask::r-x
other::---
The owner and group of the folder is root but tester1 - [COLOR=#0000cd]**and only tester1**[/COLOR] - has the ability to traverse the folder to get to what is under it. This is by design.

Your share definition is forcing the group to be users because the shared folder is set to the group users but none of these users will be able to get past the /media/ns folder since they are not ns.

Had your share specified "force user = ns" this would have all worked. Or just mount the partition one level up at /media/storage which avoids the /media/ns acl.

---

### Post by curtash on 2017-07-25
Never too late I'm still refining (well, messing about). Yeah I did notice the + but had no idea what it meant. As part of my experimenting process someone advised using ACL so I installed it. I would like to get this right if you have time to help out? I'm a beginner though so will need a bit of hand holding.

---

### Post by Morbius1 on 2017-07-25
The acl I'm talking about is built into the system itself when it creates the /media/$USER folder. THe system will create a folder under /media for ever local user named for that user then apply an acl to it.

I suspect it was a security or perhaps privacy thing. If userA plugs a usb device into the system it will be accessible only to userA. If userB logs in at the same time and tries to access /media/userA/xyz he will get a permission denied error not because of the permissions on xyz but becuause of the permissions on /media/userA since he is not userA.

What happens locally happens across the network.

---

### Post by curtash on 2017-07-25
That makes sense thanks. 

I'll try and do your suggestion below:

 "[COLOR=#000000]Or just mount the partition one level up at /media/storage which avoids the /media/ns acl."[/COLOR]

---

