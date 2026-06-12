---
title: "Cannot access secure folder"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by nato85 on 2014-02-20
Hi guys, please be patient with me, i know this is a dumb question lol.

Ok situation is this


A long time ago I set up samba in Linux

I created a share that everyone can access - which still works

Inside that share, i created a folder called Secure


drwxrwx---  17 root         root              4096 Feb  3 16:08 secure

I then added a user to the root group and gave the user a password

I then was able to log into the secured share on Windows using the username and password I had set up.

The computer I was accessing the share on has died on me, and when I try to access the share on another computer that can see the server, I access that secured folder, but instead of being able to type in a username and password, it just says access denied.

Any ideas please?

---

### Post by bab1 on 2014-02-20
> **nato85 said:**
> Hi guys, please be patient with me, i know this is a dumb question lol.

Ok situation is this


A long time ago I set up samba in Linux

I created a share that everyone can access - which still works

Inside that share, i created a folder called Secure


drwxrwx---  17 root         root              4096 Feb  3 16:08 secure

I then added a user to the root group and gave the user a password

I then was able to log into the secured share on Windows using the username and password I had set up.

The computer I was accessing the share on has died on me, and when I try to access the share on another computer that can see the server, I access that secured folder, but instead of being able to type in a username and password, it just says access denied.

Any ideas please?
The user on the 2nd machine is not considered the same user as on the first machine.  You might consider changing the ownership and permissions temporarily to access the files.

Two best practices you should follow.  Never add a mortal user to the root group account.  Add the mortal user to another user group and change the group ownership (chgrp).

It's messy to have a secured share BELOW a public share (inside of).  If you want to have private shares create a new share outside of the public share.  The user will still access the private share the same way (//SERVERNAME/SHARENAME)

---

### Post by nato85 on 2014-02-20
does the username and the password on the PC have the be the same of what the username and password is for the share?

how do I find out what users have access to that share?

---

### Post by bab1 on 2014-02-20
> **nato85 said:**
> does the username and the password on the PC have the be the same of what the username and password is for the share?

Samba authenticates the user to the share.  Linux authorizes the file and directory use.  So the user has to be both a Linux user and a Samba user.  Having the same name and password would be very helpful.
> 

how do I find out what users have access to that share?
Didn't you create the share?  If not you need the system administrator fix this.

---

### Post by nato85 on 2014-02-20
I did not create the share itself, all i can tell you is that the folder was created by root, i assume it is in the root group, and the username that is in the root group should have no problem accessing it, but it does not bring up a username and password field when I try to access it, just says access is denied on Windows

I know root password if that helps?

Also the only thing that has changed is the customer has purchased a new PC, the old PC that could access it is now dead

---

### Post by bab1 on 2014-02-20
> **nato85 said:**
> I did not create the share itself, all i can tell you is that the folder was created by root, i assume it is in the root group, and the username that is in the root group should have no problem accessing it, but it does not bring up a username and password field when I try to access it, just says access is denied on Windows

I know root password if that helps?

Then you are capable of setting all of this up.  You need root access to configure the shares via the smb.conf file and root access to change ownership and permissions.  Is this network yours or are you the system administrator for this network?
> 

Also the only thing that has changed is the customer has purchased a new PC, the old PC that could access it is now dead
So the user (account) on the new host (computer) is new.  The person is the same.  We are dealing with user accounts not the human using the machine.

In this conversation "you"and "who" are a human and "the user" is an account on the Ubuntu or Windows host.  The root user is the account that create the directory that is shared.  The access problem is twofold.  You seem to have trouble accessing the share.  Even if you did access the share you would not be able to read or write to the files in the share as your account would not have any permissions to do that.  So I'll ask again *who *created the share?  How was it created?  By editing the smb.conf file? 

There is also the concept of local and remote.  If you have the root password (either by su or sudo) then you have local access to the directory and can change the ownership of the files in that directory on that host (computer).  You have remote access to the share via SMB if you have a Linux and Samba account on the Samba server and the directories and file ownership and permissions are set correctly.  Are you the administrator for these various hosts (Ubuntu and Windows)?

---

### Post by nato85 on 2014-02-20
The network is mine, and i am considered system administrator for the network.

I looked at the smb.conf file, and found the setup for the share /var/data/share however i could not find anything for /var/data/share/secure. this is the folder that i am having problems getting into

Yes, new computer, new username and password on new computer. Person is the same person.

I created the share for /var/data/share, someone else setup the secure folder inside that share. I set up my share using smb.conf, but i cannot see anything set up for the secure folder in smb.conf. I am the administrator of the Ubu machine, but not the windows machine

Sorry if I come across as a little vague with this. I can tell you nothing was changed with the ubu server, it was only when the computer was replaced that I lost access to this directory

---

### Post by bab1 on 2014-02-20
> **nato85 said:**
> The network is mine, and i am considered system administrator for the network.

I looked at the smb.conf file, and found the setup for the share /var/data/share however i could not find anything for /var/data/share/secure. this is the folder that i am having problems getting into

Yes, new computer, new username and password on new computer. Person is the same person.

I created the share for /var/data/share, someone else setup the secure folder inside that share. I set up my share using smb.conf, but i cannot see anything set up for the secure folder in smb.conf. I am the administrator of the Ubu machine, but not the windows machine

Sorry if I come across as a little vague with this. I can tell you nothing was changed with the ubu server, it was only when the computer was replaced that I lost access to this directory

The secure directory has changed (added) and a new share was added.  If you can su to the root user, you have access to the data,  You can move it to where ever you want and create a new share.

The person with the new computer needs to have an account on this host with the same login as the user on the old machine. Does that user have a Samba account?  If not then that user is an anonymous user and by default is the user "nobody" on Ubuntu.

I guess at this point you might as well post the output of this```
cat /etc/samba/smb.conf
```

---

