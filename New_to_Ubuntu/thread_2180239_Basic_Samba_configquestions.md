---
title: "Basic Samba config/questions"
date: 2013-10-12
forum: New to Ubuntu
---

### Post by geohei on 2013-10-12
Hi.

Forums are full of examples, howtos and tutorials, but most of them deal with ADs and other stuff exceeding my desired setup.

I use Ubuntu 12.04 server and would like to access its share (for testing I have only one) from a windows network (initially only Windows 7) in such a way, that ...
a. guests can browse the share (no W access)
b. Windows "Administrator" can RW the share

I use ...
```
[global]
...
workgroup = myhomenetwork
security = user
...
[myshare]
    comment = test share
    path = /media/test-share
    browsable = yes
    public = yes
    writable = yes
    create mask = 0755
...
```
Like this, I can see the Ubuntu server in Network, see its share and RW this share.

Some questions:

1. When I create a file or folder, I get permissions 0777 instead of the shown 0755. How come?

2. I created a user "administrator" for the Ubuntu server (adduser administrator). I read that a system user is required before a Samba user can be created (smbpasswd -a administrator). Is this correct?

3. Is the Ubuntu/Samba username case sensitive against Windows username? The Windows administrator is called "Administrator", not "administrator".

4. How should my [myshare] look like to accept guest R and administrator RW access?

Thanks,

---

### Post by geohei on 2013-10-13
No answer yet .... :(
Wasn't the question clearly asked?
Shall I rephrase?
Thanks,

---

### Post by carl4926 on 2013-10-13
nixie pixel did a video recently on samba
[http://www.youtube.com/watch?v=-wUfzdiE4m8&feature=c4-overview&list=UUBE-FO9JUOghSysV9gjTeHw](http://www.youtube.com/watch?v=-wUfzdiE4m8&feature=c4-overview&list=UUBE-FO9JUOghSysV9gjTeHw)

---

### Post by geohei on 2013-10-14
Very nice, but ...
1. It deals with Ubuntu Desktop (yes, should be the same), but I use the Ubuntu server version. So no funcky GUI.
2. It doesn't address my specific questions listed in OP.

---

### Post by bab1 on 2013-10-14
> **geohei said:**
> Hi.

Forums are full of examples, howtos and tutorials, but most of them deal with ADs and other stuff exceeding my desired setup.

I use Ubuntu 12.04 server and would like to access its share (for testing I have only one) from a windows network (initially only Windows 7) in such a way, that ...
a. guests can browse the share (no W access)
b. Windows "Administrator" can RW the share

The only *users* that access the share are Ubuntu local users (/etc/passwd)  that are also Samba users (smbpasswd -a).  The only exception to that is a user that is unknown to Samba that tries to gain access.  This anonymous user can be mapped to the system user named *nobody* or any other user of your choice.

What do you mean by the term guests? 
> 

I use ...
```
[global]
...
workgroup = myhomenetwork
security = user
...
[myshare]
    comment = test share
    path = /media/test-share
    browsable = yes
    public = yes
    writable = yes
    create mask = 0755
...
```
Like this, I can see the Ubuntu server in Network, see its share and RW this share.

What username is viewing the share (I'm not talking about you the human);?  What are the permissions and ownership with this user as shown via the CLI (terminal)? 
> 

Some questions:

1. When I create a file or folder, I get permissions 0777 instead of the shown 0755. How come?

What are the ownership and permissions of the root directory of the share?
> 

2. I created a user "administrator" for the Ubuntu server (adduser administrator). I read that a system user is required before a Samba user can be created (smbpasswd -a administrator). Is this correct?

No.  The user Ubuntu user *administrator *needs a Samba user created.  Samba maps the remote user to both the local user and  the Samba user.
> 
3. Is the Ubuntu/Samba username case sensitive against Windows username? The Windows administrator is called "Administrator", not "administrator".

I believe so.  I would create Ubuntu usernames exactly as they are in Windows.  All of my usernames are in lower case.  The users Bill, Bob or Jane are not the same as the usernames bill, bob or jane.  What ever your username is on the Windows machine is what the username should be on the Ubuntu machine unless you want to complicate your life with mapping one to the other.
> 
4. How should my [myshare] look like to accept guest R and administrator RW access?

Do you mean an user account named *guest*?  I assume you mean the user account named *administrator*.

While the access to the share is via Samba authentication, the authorization to manipulate the files and directories is via Ubuntu permissions.

You have 3 sets of permissions on each file or directory.  Each user group (owner/group/others) control usage.  If the owner of the file is the user (uid) bill and you have set the owner permissions to RW then that user has RW.  If the same file has the group ownership (gid) set to the user group (i.e. smbusers or somesuch) and you have set the group permissions to RW then all user in that  group have RW.  All other users have can be set to RO.  The permissions look like this for a file:  664.  

The user *administrator* can be the owner or in the group to have RW permissions.  The user *guest* would be others and would only have RO permissions.

The bottom line here is you need to set the permissions for the branch of the Ubuntu file system you intend to share.  Then configure the share using Samba to provide access (authentication of the user).

---

### Post by geohei on 2013-12-08
Thanks for the answers! Helped quite a lot ... !

I only answer some of your questions. The rest follows or were answered after further tests.

Q1:
> **bab1 said:**
> What are the ownership and permissions of the root directory of the share?
This problem is solved. The reason was, that my share on the Ubuntu fs was an NTFS partition (harddisk connected from a former Windows system). After I did some more tests with an ext4 fs, permissions were set as expected, but only if I used 'create mask = 0644' and 'directory mask = 0755' in the share definition of smb.conf.

Example:
```
root@vm-96:/media# ls -l test1
total 4
-rw-r--r-- 1 Administrator Administrator    0 Dec  8 16:13 file.txt
drwxr-xr-x 2 Administrator Administrator 4096 Dec  8 16:13 folder
root@vm-96:/media# ls -l test2
total 4
-rwxr--r-- 1 Administrator Administrator    0 Dec  8 16:13 file.txt
drwxr-xr-x 2 Administrator Administrator 4096 Dec  8 16:13 folder
```
The share for test1 has masks set to 0644 (file) and 755 (folder). Permissions are correctly shown on Ubuntu (0644 and 0755).
The share for test2 has no masks set. Permissions on Ubuntu are 0744 and 0755.

Why are files rwx for owner in directory test2?

Q2:
> **bab1 said:**
> No. The user Ubuntu user *administrator *needs a Samba user created. Samba maps the remote user to both the local user and the Samba user.
Hmmm .... ?!
Let's rephrase this. The remote user (on the Windows system) needs to be the same (including identical password) on the Ubuntu system [useradd --no-create-home -s /usr/sbin/nologin Administrator] and on Samba [smbpasswd -a Administrator]. Is that correct? Hence ... the same user needs to be configured three times.

Q3:
> **bab1 said:**
> I believe so. I would create Ubuntu usernames exactly as they are in Windows. All of my usernames are in lower case. The users Bill, Bob or Jane are not the same as the usernames bill, bob or jane. What ever your username is on the Windows machine is what the username should be on the Ubuntu machine unless you want to complicate your life with mapping one to the other.
ACK! To avoid unnecessary problems, I will use upper/lowercase just as for the Windows systems which have access to the defined shares.

---

### Post by bab1 on 2013-12-08
> **geohei said:**
> Thanks for the answers! Helped quite a lot ... !

Q1:

This problem is solved. The reason was, that my share on the Ubuntu fs was an NTFS partition (harddisk connected from a former Windows system). After I did some more tests with an ext4 fs, permissions were set as expected, but only if I used 'create mask = 0644' and 'directory mask = 0755' in the share definition of smb.conf.

Example:
```
root@vm-96:/media# ls -l test1
total 4
-rw-r--r-- 1 Administrator Administrator    0 Dec  8 16:13 file.txt
drwxr-xr-x 2 Administrator Administrator 4096 Dec  8 16:13 folder
root@vm-96:/media# ls -l test2
total 4
-rwxr--r-- 1 Administrator Administrator    0 Dec  8 16:13 file.txt
drwxr-xr-x 2 Administrator Administrator 4096 Dec  8 16:13 folder
```
The share for test1 has masks set to 0644 (file) and 755 (folder). Permissions are correctly shown on Ubuntu (0644 and 0755).
The share for test2 has no masks set. Permissions on Ubuntu are 0744 and 0755.

Why are files rwx for owner in directory test2?

There are lots of reasons that can cause these kinds of things.  There are differences between files create on the Samba server vs copied vs cut and patse.  It also depends upon what OS the client is running.  The Ubuntu default file and directory permissions are file=666 and directory=777.  The default umask is 002 for users and 022 for root.  The combination gives you dir/file permissions for a user of 775/644 and 755/644 for root.  As you  can see it depends on where the file was actually created and who created it.  The best bet if to see what you get and adjust the share parameters to get the outcome you want.
> 

Q2:
[QUOTE]Samba maps the remote user to both the local user and the Samba user.
Hmmm .... ?!
Let's rephrase this. The remote user (on the Windows system) needs to be the same (including identical password) on the Ubuntu system [useradd --no-create-home -s /usr/sbin/nologin Administrator] and on Samba [smbpasswd -a Administrator]. Is that correct? Hence ... the same user needs to be configured three times.
[/QUOTE]
They may be for the same human, but they are 3 different accounts.  In fact a Windows client passes the logged in username to Samba.  Samba will attempt to either allow non-password access or restrict access using the login name, depending upon how you have setup the share.  The basic share access is either anonymous or known user.  For this to work the Samba daemon checks the Samba user database and the Linux user database.  Samba can't control the Linux user database, but it can control its own user database.  On top of the you have the samba client user.  In short, yes, you need to coordinate 3 user accounts for each user.

---

### Post by geohei on 2013-12-09
Q4:

I experimented a bit on that one. I noticed that the share below fulfills my needs (R for guests and RW for Administrator):
```
[myshare]
    comment = test share
    path = /media/test-share
    writeable = no
    write list = Administrator
    public = yes
    writable = yes
    create mask = 0644
    directory mask = 0755
```
By "guest", I mean any user on a Windows system, which is unknown to the Samba system.
Above share accepts a guest (public = yes) but prohibits write access to him (writeable = no), except for the Administrator (write list = Administrator).

However ... a list of Samba users needs to be specified with "write list = ...". Is it not possible to allow write access to all Samba known users without specifying each user?

---

### Post by bab1 on 2013-12-09
> **geohei said:**
> Q4:

I experimented a bit on that one. I noticed that the share below fulfills my needs (R for guests and RW for Administrator):
```
[myshare]
    comment = test share
    path = /media/test-share
    writeable = no
    write list = Administrator
    public = yes
    writable = yes
    create mask = 0644
    directory mask = 0755
```
By "guest", I mean any user on a Windows system, which is unknown to the Samba system.
Above share accepts a guest (public = yes) but prohibits write access to him (writeable = no), except for the Administrator (write list = Administrator).

However ... a list of Samba users needs to be specified with "write list = ...". Is it not possible to allow write access to all Samba known users without specifying each user?
Certainly you can allow rw access " to all Samba known users without specifying each user".  But not if you first allow everyone access to the share with *public = yes* which is the same as *guest = ok* and then add * writeable = no*.  Those two parameters make the share _read only for all_. Then you are forced to make exceptions with *write list =*.  If  this is really needed you can use groups and add the users you want to have write access to that group.

Most of the time it is easier to allow all users read/write permissions and make the user with read only the exception.  The Samba guest user is the Linux ser:group  nobody:nogroup.  That anonymous user should normally only have read only permissions to a correctly setup directory.  There should be no need to add the parameters you have to the Samba share definition.

---

### Post by geohei on 2013-12-10
Ok ... understood. I'll change my configuration accordingly.

Something else. Is it possible to hide a share from all users accept the ones defined (somewhere)?

Example:
A Windows user (mike) sees a Samba machine ("RHODE") with 2 shares:
"Private files for Mike"
"Public directory"
User mike is known to Samba (and the Ubuntu system behind).

Now, I'd like to hide the share "Private files for Mike" when a user different than mike accesses RHODE.
So when Peter (configured in Samba & Ubuntu) accesses RHODE, he should only see:
"Public directory"
So when Paul (not configured in Samba & Ubuntu) accesses RHODE, he should only see:
"Public directory"

It's basically like a user configurable "browseable" option (e.g. browseable = mike).

Is this possible?

---

### Post by codenine75a on 2013-12-10
> **geohei said:**
> Hi.

Forums are full of examples, howtos and tutorials, but most of them deal with ADs and other stuff exceeding my desired setup.
.........................
Thanks,

You have the right direction of SMB and accounts, but AD usually stands for active directory.  It is just called an user account.

---

### Post by bab1 on 2013-12-10
> **geohei said:**
> Ok ... understood. I'll change my configuration accordingly.

Something else. Is it possible to hide a share from all users accept the ones defined (somewhere)?

Example:
A Windows user (mike) sees a Samba machine ("RHODE") with 2 shares:
"Private files for Mike"
"Public directory"
User mike is known to Samba (and the Ubuntu system behind).

Now, I'd like to hide the share "Private files for Mike" when a user different than mike accesses RHODE.
So when Peter (configured in Samba & Ubuntu) accesses RHODE, he should only see:
"Public directory"
So when Paul (not configured in Samba & Ubuntu) accesses RHODE, he should only see:
"Public directory"

It's basically like a user configurable "browseable" option (e.g. browseable = mike).

Is this possible?
You can use the [homes] share for that.  You only need to configure the [homes] share one time.  Then all Samba users are automatically added to the [homes] share.  Since you can't browse you need to know that the share is located at //SERVER/<your_login>.

---

