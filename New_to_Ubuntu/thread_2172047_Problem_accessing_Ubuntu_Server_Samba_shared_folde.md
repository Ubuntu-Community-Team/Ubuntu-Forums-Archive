---
title: "Problem accessing Ubuntu Server Samba shared folder from Windows 8"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by matt27 on 2013-09-03
Hi all, I have a question about accessing my shared folder on an Ubuntu Server 12.04 box from Windows 8.  If I am posting in the wrong place let me know, because I'm new to this forum.  I know a little about Linux and am not a total newbie, so I understand permissions, but I think they are giving me issues when I'm using Samba to share a folder.

Here's what I'm trying to do.  I have an Ubuntu Server 12.04 box with a couple of HDDs.  One I installed the system onto, and the other, I've used Logical Volume Management to make a 1GB logical volume for document storage, mounted in /mnt/docs.  I plan to make more volumes for other stuff once I get this working right.  I've converted my users to Samba users and aim to have different logical volumes available as shared folders on my home network, where users can login with a particular username and password to store their files on the server.  I successfully shared the mounted folder, and I can see my server in Windows 8 on my laptop.  The initial username/password combo I picked works, and after I fiddled with permissions for the folder on the server, I was able to read/write to it.  However, I cannot get it to work with any other users!

My ultimate question is, how do I set up the permissions for this folder on the server so that different users (part of the same group maybe?) can all read/write to this share?  And how do I correctly manage their usernames/passwords so that they can all access this folder without a hitch?  Some bits and pieces I've read say that the Samba user passwords must be the same as the admin's password on the server?  Which makes no sense to me.  I don't really understand the relation between the two.  Any help here would be greatly appreciated.  Thanks!

fyi, I've been loosely following this guide:  [http://linuxhomeserverguide.com/server-config/Samba.php](http://linuxhomeserverguide.com/server-config/Samba.php)

---

### Post by mikewhatever on 2013-09-03
The guide you've followed has the permissions topic covered in the paragraph before last. I can only assume that's how it wors - not familiar with Webmin.
Usernames and passwords aren't relevant for permissions, and no, samba users' passwords definitely should not be the same as the admin's.
A user that connects remotely must exist on the server, and is usually assigned to the 'samashare' group in Ubuntu.

For example, let's say I want to create a user named 'test' just to connect to Samba.

```

useradd -N -M -g sambashare test

smbpasswd -a test
New SMB password:
Retype new SMB password:
Added user test.

id test
uid=1001(test) gid=109(sambashare) groups=109(sambashare)

```

Now, that 'test' is a valid samba user on the server, you could try connecting as 'test' from a Windows 8 machine.

---

### Post by Morbius1 on 2013-09-03
It may be that I too am unfamiliar with Webmin and how it works but the procedure outlined in that HowTo won't work.

He has you create a folder with owner:group = root:users. Then he has you set permissions to 755. Then he has you create a writeable share.

The only user that can write to the share at this point is root. The folder that is being shared should have permissions of 775 and all of the samba client users need to be added to the "users" group or an addition to the share definition needs to be added that forces the group to be "users" ( force group = users ).

Why not post the output of the following command so we can all see how you are currently set up:
```
testparm -s
```

[COLOR=#0000cd]*Side note: the sambashare group allows it's members to create a Samba share of anything they own - usually implemented through the file manager. It's really not applicable to this topic since it has nothing to do with the samba client..*[/COLOR]

---

### Post by capscrew on 2013-09-03
> **Morbius1 said:**
> 
[COLOR=#0000cd]*Side note: the sambashare group allows it's members to create a Samba share of anything they own - usually implemented through the file manager. It's really not applicable to this topic since it has nothing to do with the samba client..*[/COLOR]

Too much BBQ and beer.  ;-) I think you have misspoken here.  The group *sambashare *is not related directly to **Samba usershares**.  The *sambashare *group is just a Linux user group like any other user group.

Or am I missing something here?

---

### Post by Morbius1 on 2013-09-03
> **capscrew said:**
> Too much BBQ and beer.  ;-) I think you have misspoken here.  The group *sambashare *is not related directly to **Samba usershares**.  The *sambashare *group is just a Linux user group like any other user group.

Or am I missing something here?
OK, I'll respond to that. Yes you are missing something here. Membership in the sambashare group is most certainly related to the ability of a user to create a samba usershare since share creation is limited to root and members of that group:
> ls -dl /var/lib/samba/usershares
drwxrwx--T 2 root sambashare 4096 Sep  2 11:02 /var/lib/samba/usershares

Take away membership to that group and the user will get this error message when he attempts to create a share:
> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
You are free of course to use the sambashare or any other group for whatever purposes you desire as long as you understand the consequences but it certainly is not a requirement for samba clients to be members of that group as this statement suggested:
> A user that connects remotely must exist on the server, and must be assigned to the 'samashare' group in Ubuntu.

---

### Post by mikewhatever on 2013-09-03
> **Morbius1 said:**
> OK, I'll respond to that. Yes you are missing something here. Membership in the sambashare group is most certainly related to the ability of a user to create a samba usershare since share creation is limited to root and members of that group:

Take away membership to that group and the user will get this error message when he attempts to create a share:

You are free of course to use the sambashare or any other group for whatever purposes you desire as long as you understand the consequences but it certainly is not a requirement for samba clients to be members of that group as this statement suggested:

That sounds about right, and thanks for correcting. It should have read something like ..."and is usually assigned to the 'samashare' group in Ubuntu. ".
Not sure why I've used the must word twice, I'll go edit it.

---

### Post by capscrew on 2013-09-03
> **Morbius1 said:**
> OK, I'll respond to that. Yes you are missing something here. Membership in the sambashare group is most certainly related to the ability of a user to create a samba usershare since share creation is limited to root and members of that group:

Take away membership to that group and the user will get this error message when he attempts to create a share:

You are free of course to use the sambashare or any other group for whatever purposes you desire as long as you understand the consequences but it certainly is not a requirement for samba clients to be members of that group as this statement suggested:
Ah..., but I didn't say who had the BBQ and beer.  :D

Seriously, that is something I didn't know.  All of the shares on my network we created by me in the smb.conf of the various servers I administrate.  The users on my network are members of a group I created (e.g. smbusers) as well as in the group sambashare.  

I can see now to administratively control users from sharing folders on an ad hoc basis.  You just delete the user from the sambashare group.  Thanks for elucidating on the subject.

---

### Post by matt27 on 2013-09-03
Thanks for all the replies everyone!  I'm going to see where I get with what you have given me so far and get back to you in a little while.  I've been busy today haha.  I think I'll try just working with the command line instead of using Webmin for now, since that just adds confusion.

---

### Post by matt27 on 2013-09-03
I'm having success with getting my various users to log into the share, which is good.  I think part of my issue there may have been that Webmin wasn't properly changing the samba passwords.  Like I said I'm sticking to command line now, and that's working well.  

My next question is, how do I set up my users so that they can all read/write to the share?  Currently as Morbius said, the permissions for the folder look like this:

```
drwxrwxr-x  3 root root 4096 Sep  2 01:02 docs/
```

And I made all of my users part of the users group.


Morbius, here's the output of testparm -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[DOCS]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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


[printers]\
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[DOCS]
        path = /mnt/docs
        read only = No
        create mask = 0775
        directory mask = 0775

```

---

### Post by Morbius1 on 2013-09-04
> how do I set up my users so that they can all read/write to the share?  

First of all I hope you can see that the problem with the current permissions is that only root has write access:
> drwxrwxr-x  3 root root 4096 Sep  2 01:02 docs/

Second, It all depends on your definition of "write":

If by "write" you mean the ability for your users to add or remove files from the shared folder then there are a couple of ways to do this:

[1] Change permissions on the shared folder to allow everyone write access to the folder then use the share definition as a gatekeeper to limit access to only credentialed users:
```
sudo chmod 777 /mnt/docs
```
[2] OR, Since all the samba users are members of the "users" group you can leave permissions as they are and change the group of the shared folder:
```
sudo chown root:users /mnt/docs
```
[COLOR=#0000cd]* Just make sure all your samba users are members of the "users" group.*[/COLOR]

If by "write" you mean the ability not only to add/delete files but edit the content of files things get more complicated. Again there are many ways to pull this off:

Perhaps the easiest is just to make everyone appear to be the same user:
> [DOCS]
        path = /mnt/docs
        read only = No
**[COLOR=#0000cd]force user = morbius[/COLOR]**

Change morbius to some user - perhaps your own user name. If the folder has permissions set to 777 it doesn't matter who the force user is but if permissions/group ownership have changed to 775/users then make sure this user is a member of the users group. The samba client will be forced to provide username and password to access the share but once Samba let's him in his identity changes to morbius when he adds a file or edits a file. The same thing will happen to all samba users.

If you want to keep track of who is doing things but still want the ability to edit everything in sight then it will take multiple steps, something like this:

Change permissions on the shared folder:
```
sudo chmod 2775 /mnt/docs
```
Change your share definition to this:
> [DOCS]
        path = /mnt/docs
        read only = No
        force group = users
        create mask = 0664
        force directory mode = 2775
        

---

### Post by matt27 on 2013-09-05
> **Morbius1 said:**
> First of all I hope you can see that the problem with the current permissions is that only root has write access:

Yeah, I understand that for sure ;)

Thanks to your help I think I have it working the way I want!  I used the option of forcing the user, and things are going well.  As for the other knowledge you imparted, I had no idea and now I do!  Thanks everyone, greatly appreciated!! :D

---

