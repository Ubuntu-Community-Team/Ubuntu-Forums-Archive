---
title: "samba sharing"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by creepwood on 2013-05-23
I have an ubuntu workstation running 13.04 as a server. I have one large LVM-volume spanning over four drives that contains a lot of data.
I mount this into my home folder of the user that the server is running under. I also share this as samba since most of my other computers are running windows. I have no problem accessing this data from another computer which is running the same username and password as the user on the ubuntu machine. we can call this user userA. I also have a second user, userB which wants to access these files as well. running from the same machines. The rights on the folder and subfolders are drwxrwsr-x  and the group name is group1, both userA and userB are part of group1.

In the sharing options I tried setting both "allow others to create and delete files in this folder" and "guest access", and it doesn't seem to matter. I just can access the share from userB

I have some subfolders in the shared folder that should not be accessable to userB, therefor I have  drwx------ (owner userA) on these folders.

What should I do. I'm not fluent in linux.

---

### Post by dino99 on 2013-05-23
no needs for dupe : [http://ubuntuforums.org/showthread.php?t=2147891](http://ubuntuforums.org/showthread.php?t=2147891)

---

### Post by HermanAB on 2013-05-23
Howdy,

The best way to debug Samba is with a program called 'smbclient'.  Read the man page.  The advantage is that it will give error messages, so then you can see exactly what is going on.  Start by testing things out on the server machine.  If it doesn't work right on the server, then it isn't going to work anywhere else either.

---

### Post by creepwood on 2013-05-23
> **dino99 said:**
> no needs for dupe : [http://ubuntuforums.org/showthread.php?t=2147891](http://ubuntuforums.org/showthread.php?t=2147891)

I'm sorry, I got "proxy error" on the first two so I just reloaded the page not wanting to lose the text I written.

---

### Post by creepwood on 2013-05-23
> **HermanAB said:**
> Howdy,

The best way to debug Samba is with a program called 'smbclient'.  Read the man page.  The advantage is that it will give error messages, so then you can see exactly what is going on.  Start by testing things out on the server machine.  If it doesn't work right on the server, then it isn't going to work anywhere else either.

Thank you for the tip, I'm trying out some basic things, but I'm clearly not savvy enough to deal with this. I'm getting no errors when I try;
```
smbclient -U userB -L \\192.168.242.13 -D thefolder
```

---

### Post by Morbius1 on 2013-05-23
>  In the sharing options I tried setting both "allow others to create and  delete files in this folder" and "guest access", and it doesn't seem to  matter. I just can access the share from userB
That's a Samba Usershare. Please post the output of this command so we can see how it's set up:
```
net usershare info --long
```
Just to make sure there is no conflict with this and a Classic Samba share you might have created you might want to post the output of this one as well:
```
testparm -s
```

---

### Post by creepwood on 2013-05-23
This is what net usershare info --long outputs

```
[Downloads]
path=/home/creepwood/Downloads
comment=
usershare_acl=Everyone:R,Unix User\creepwood:F,
guest_ok=n

[home]
path=/home/creepwood
comment=
usershare_acl=Everyone:R,BABEL\creepwood:F,
guest_ok=n

[media]
path=/home/creepwood/media
comment=
usershare_acl=Everyone:F,
guest_ok=y

[test]
path=/home/creepwood/test
comment=
usershare_acl=Everyone:F,
guest_ok=y
```


and for testpar -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
```

---

### Post by Morbius1 on 2013-05-24
Methinks this is all Linux permissions issues rather than a Samba issue and how and where you are accessing each share.

You have to different types of shares:

This one allows only credentialed users to gain access to read and only creepwood to write:
> [Downloads]
path=/home/creepwood/Downloads
comment=
usershare_acl=Everyone:R,Unix User\creepwood:F,
guest_ok=n

This one allows anyone to read and write:
> [media]
path=/home/creepwood/media
comment=
usershare_acl=Everyone:F,
guest_ok=y

So the things to check out are:

** Did you encrypt your home directory? If you did then only creepwood is gaining access and UserB or anyone else is out of luck.

** Assuming you did not encrypt did you add UserB to the samba password database so he can access the [Downloads] share:
```
sudo smbpasswd -a UserB
```

** Assumming no one can access the [media] share look at the permissions along the entire path to the target folder to see if anything is getting in the way of a guest user:
ls -dl /home/creepwood
ls -dl /home/creepwood/media

---

### Post by creepwood on 2013-05-24
the folders are not encrypted. the download folder is only for the creepwood user so that's not a problem. it's the media folder that should be accessible to userB I know the rights on the media folder are too generous right now, I want I want full rights for the owners in media, I want full rights for people in group1 in media and I want others to only be able to read and access folders.


ls -ld /home/creepwood

drwxr-xr-x 41 creepwood creepwood 4096 May 23 18:27 /home/creepwood



ls -ld /home/creepwood/media

drwxrwxrwx 15 creepwood media 4096 May  3 00:17 /home/creepwood/media

---

### Post by Morbius1 on 2013-05-24
How is UserB trying to access the contents of /home/creepwood/media?

If he is trying to do that through the [home] share he needs a samba password to do that. And even when he has one he will only be allowed to read.

If he is trying to do that through the [media] share there should be nothing stopping him or any one else from doing so.

---

### Post by creepwood on 2013-05-24
Alright, this is odd. I haven't changed anything, the only thing I've done is restart the server, maybe you need to restart the machine if you meddle with the sharing over samba?

Now, Question is. is "others" having access to write or tamper with anything or is it just group1 that has rights to do so?

And wow, thank you for your so thourough help

---

### Post by Morbius1 on 2013-05-24
If we are still talking about /home/creepwood/media then everyone and your Aunt Tilly can pretty much do whatever they want if they go through the [media] share. 

But no one can get to /home/creepwood/media unless they have a samba password if they go through [home]. And even if they did have a password Samba not Linux will prevent them from writing to the media folder regardless of it's Linux permissions - unless they are creepwood.

---

### Post by creepwood on 2013-05-24
Alright, the [home] share is all good then but I'm concerned about the [media] share. What do I need to do to not make that possible?

---

### Post by Morbius1 on 2013-05-24
If this is still true you can reverse the roles Samba and Linux usually play in these cases:
> drwxrwxrwx 15 creepwood media 4096 May  3 00:17 /home/creepwood/media

Do not allow guest access but do "Allow others to create and delete files in this folder". This will cause everyone to have to provide credentials to gain access but it also allows Samba to know who everyone is.

Now change the permissions to 775:
```
sudo chmod 775 /home/creepwood/media
```
Now the "ls -dl" command for tht folder should read:
> drwxrwxr-x 15 creepwood media 4096 May  3 00:17 /home/creepwood/media
Creepwood and members of the "media" group will be allowed write access.
Everyone else can only read.

---

### Post by creepwood on 2013-05-28
Thank you for your support, it really seem that i'm learning from this.

However, I removed the guest access and I can't get gain access to media (the share) when using userB. I did try making a trial folder named test so that I don't have to mess with the live data of media. What I did was make a folder named "test" and  I changed the group to media and I changed the rights for it to 775. Then I added a share for it, only with "allow others to create...", it asked me a question about controlling the share. I said yes (and it changed the rights for the folder to 777). When I tried to access it from windows it's asking for credentials, I supply my userB credentials, but it won't accept.  

the net usershare info --long gives

[test]
path=/home/creepwood/test
comment=
usershare_acl=Everyone:F,
guest_ok=n



I'm not haxxor but I get a feel that it has something to do with the folder being in creepwoods home folder.

---

### Post by Morbius1 on 2013-05-29
Then you didn't add UserB to the samba password database:
```
sudo smbpasswd -a UserB
```
And you didn't add UserB to the "media "group":
```
sudo gpasswd -a UserB media
```

---

### Post by creepwood on 2013-06-02
Alright I tried this, and it seems to work, I haven't tried as an "other" user yet, but when I enter as userB (group member of media) I can enter media folder, when I try to enter a folder in media where rights are set to 700 userB can't enter, which is what I wanted. I'll try as other further on.

I can't thank you enough for helping me with this issue. I tried Linux several times before as my workstation but gotten so annoyed that I can't get everything to work right away, I do alot of different things I didn't have pation enough to deal with it. So five months ago I moved in with a friend of mine that's really good with this and I gave it a try, as a server, not workstation and he helped me immensly, but I moved to my own place a month ago so I'm on my own again :P

That last part, with the smbpasswd, can you explain that i little bit in laymans terms. You added the user xbmc to a samba database, is that of users that should be able to connect with a samba password? If that's so, how come it has worked for my user creepwood right of the bat from my windows computer?

---

### Post by Morbius1 on 2013-06-02
> **creepwood said:**
> That last part, with the smbpasswd, can you explain that i little bit in laymans terms. You added the user xbmc to a samba database, is that of users that should be able to connect with a samba password? If that's so, how come it has worked for my user creepwood right of the bat from my windows computer?
It's really just like Windows except Linux differentiates between a local user and a network user whereas in Windows there is only THE user.

If you want user: morbius to provide credentials to gain access to a samba service you need to:

** Create a local user called morbius on the Linux server itself.
** Then you need to tell Samba that the local user morbius is a samba user. You do that with the smbpasswd command.

As far as the user creepwood working without you doing the smbpasswd , one explanation is that you have the following package installed: **libpam-smbpass**

It's an absolutely insane little utility that has only one function: At every boot it makes sure the local user is added to the samba user database and makes the samba password match the local user's login password automatically. I usually remove the package if it got installed somehow since it has no place in a home network.

---

### Post by creepwood on 2013-06-16
Thank you immensly for all the help.

Everything has worked for what I've been doing until today, when I tried to connect as "other". It asked for username and password. What kind of options do I have to be able to connect as "other"?

---

### Post by Morbius1 on 2013-06-16
None. You've created a share the requires credentials to gain access.

---

### Post by creepwood on 2013-06-16
Aah, I guess making a "guest" user is the best way to fix this?

---

### Post by creepwood on 2013-06-20
Aah, I guess making a "guest" user is the best way to fix this?

---

