---
title: "Can't write to Samba share after switch to security = user"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by mconley3 on 2014-05-02
After more than 10 years of not changing my smb.conf, security = share was deprecated.  I have several home shares for both Linux and Windows clients that don't need security.  I got past the “map to guest = bad user” problem.  I've been unable to figure out why clients don't have permission to create  files or folders on the shares.  I've tried various combinations with “only guest”, “guest ok”, “writable”, and “readonly”.   

To toubleshoot, I created a test directory with 777.
drwxrwxrwx  2 mconley3 mconley3 4096 May  2 20:23 test

Then from the client I can create a directory inside of test.
mconley3@hansolo:/usr02/music/test$ pwd
/usr02/music/test
mconley3@hansolo:/usr02/music/test$ ls -l
total 4
drwxr-xr-x 2 mconley3 mconley3 4096 May  2 20:47 testlevel2

Then I try to create a directory or file inside of testlevel2, but get permission denied. 

Here is the global and share config from the smb.conf.
[global]
   workgroup = tatooine
   server string = Samba
   security = user
   map to guest = Bad User
   guest account = mconley3
   log file = /var/log/samba/%m.log
   max log size = 50
   interfaces = 192.168.0.100/24
   dns proxy = no

[music]
   path = /usr02/music
   only guest = yes
   guest ok = yes
   writable = yes
   readonly = no

Has anyone gotten a basic share, with out security, to work with Samba 4 that would be willing to share their smb.conf file?  I'm to the point of rolling back to a version that still supports security = share.

Samba version 4.1.6-Ubuntu
Ubuntu 14.04

Thanks,
Mark

---

### Post by bab1 on 2014-05-02
> **mconley3 said:**
> After more than 10 years of not changing my smb.conf, security = share was deprecated.  I have several home shares for both Linux and Windows clients that don't need security.  I got past the &#8220;map to guest = bad user&#8221; problem.  I've been unable to figure out why clients don't have permission to create  files or folders on the shares.  I've tried various combinations with &#8220;only guest&#8221;, &#8220;guest ok&#8221;, &#8220;writable&#8221;, and &#8220;readonly&#8221;.   

To toubleshoot, I created a test directory with 777.
drwxrwxrwx  2 mconley3 mconley3 4096 May  2 20:23 test

Then from the client I can create a directory inside of test.
mconley3@hansolo:/usr02/music/test$ pwd
/usr02/music/test
mconley3@hansolo:/usr02/music/test$ ls -l
total 4
drwxr-xr-x 2 mconley3 mconley3 4096 May  2 20:47 testlevel2

Then I try to create a directory or file inside of testlevel2, but get permission denied. 

Here is the global and share config from the smb.conf.
[global]
   workgroup = tatooine
   server string = Samba
   security = user
   map to guest = Bad User
   guest account = mconley3
   log file = /var/log/samba/%m.log
   max log size = 50
   interfaces = 192.168.0.100/24
   dns proxy = no

[music]
   path = /usr02/music
   only guest = yes
   guest ok = yes
   writable = yes
   readonly = no

Has anyone gotten a basic share, with out security, to work with Samba 4 that would be willing to share their smb.conf file?  I'm to the point of rolling back to a version that still supports security = share.

Samba version 4.1.6-Ubuntu
Ubuntu 14.04

Thanks,
Mark
When you use *security = user* Samba will either authenticate (who are you) the user or use the guest user (in your case mconley3).   Here is what I use for a public share on a machine that uses *security = user*```

[public]
        comment = Shared Data
        path = /srv/public
        browseable = yes
        guest ok = yes

        force group = users
        writeable = yes

        create mask = 0664
        directory mode = 2775


```

The group *users* is how I control who has read and write permissions.  The owner(creator) is not relevant.

[COLOR="#0000FF"]Edit: Just saw the Samba v4 bit.  I can tell you that the smbd daemon is the same in both Samba3 and Samba4.  For a stand alone server the smb.conf file should be the same.  Have you tried using s*ecurity = share* ? [/COLOR]

I have used the share definition that I provided on others Samba4 install, but I run Samba3 at the moment.

---

### Post by mconley3 on 2014-05-03
Switch to using group is a good idea, however I don't thing that will help.  If I ever get this working right, I will make that change.   If you look at my test, when I create a folder from my client in a 777 directory, the folder is created as the correct user and group, but I still can't write in the directory I created from my client.  Only in the 777 directory.

Would love to switch back to security=share, but it is deprecated.

I'm begining to think the only way I can get this to work is a global change to 777 and set the  mask so everything that is created is 777.

---

### Post by bab1 on 2014-05-03
> **mconley3 said:**
> Switch to using group is a good idea, however I don't thing that will help.  If I ever get this working right, I will make that change.   If you look at my test, when I create a folder from my client in a 777 directory, the folder is created as the correct user and group, but I still can't write in the directory I created from my client.  Only in the 777 directory.

I would have to assume that you are not using the user mconley3.  Only the user mconley3 has permissions to write i the new directory.  The umask should already be set to 0002 which gives you 775 for directories and 664 for files.  Both make the user (creator) and group have rw and directory traversal.  Just what you need with a common group and read, write and eXecute permissions on all directories in the path from root.  You can use 777 but that allows for world writable conditions along the path.  A much better solution is to limit that to the user and user group that you control.  
> 

Would love to switch back to security=share, but it is deprecated.

I'm begining to think the only way I can get this to work is a global change to 777 and set the  mask so everything that is created is 777.
How global is global?  If you set the entire file system to 777 the OS will stop working.  Setting the permissions on existing directories and files will not do anything for newly created files and directories.

[COLOR="#0000FF"]EDIT: I would remove this[/COLOR]```
only guest = yes
```[COLOR="#0000CD"]from the share definition.[/COLOR]

---

### Post by mconley3 on 2014-05-03
Yeah, it works!!  Thanks for hanging in there with me.  Now hopefully I don't have to touch it for another 10 years.

The final global and 1 of the shares.

[global]
   workgroup = tatooine
   server string = Samba
   security = user
   map to guest = Bad User
   guest account = mconley3
   log file = /var/log/samba/%m.log
   max log size = 50
   interfaces = 192.168.0.100/24
   dns proxy = no

[music]
   path = /usr02/music
   guest ok = yes
   browsable = yes
   force group = mconley3
   writeable = yes
   create mask = 0664
   directory mode = 2775


I went through all my shares and chmod -R 775 them, now they all work as expected.  New folders get created as below.  Still not sure why it wasn't working as only user level security but it is now working at group level security.

drwxrwxr-x  2 mconley3 mconley3     4096 May  3 11:46 Untitled Folder

---

### Post by bab1 on 2014-05-03
> **mconley3 said:**
> Yeah, it works!!  Thanks for hanging in there with me.  Now hopefully I don't have to touch it for another 10 years.

The final global and 1 of the shares.

[global]
   workgroup = tatooine
   server string = Samba
   security = user
   map to guest = Bad User
   guest account = mconley3
   log file = /var/log/samba/%m.log
   max log size = 50
   interfaces = 192.168.0.100/24
   dns proxy = no

[music]
   path = /usr02/music
   guest ok = yes
   browsable = yes
   force group = mconley3
   writeable = yes
   create mask = 0664
   directory mode = 2775


I went through all my shares and chmod -R 775, now they all work as expected.  New folders get created as below.  Still not sure why it wasn't working as only user level security but is it now working at group level security.

drwxrwxr-x  2 mconley3 mconley3     4096 May  3 11:46 Untitled Folder
Are you the only user?  If there are multiple users then you will have more problems down the road.  Consider what will happen if you had a user jsmith using that share along with you.  His creations would be owned by jsmith:jsmith under your set up.

If you want the group user to be the same for everyone (e.g. *mconley3 ***:users** for you and *jsmith ***:users** for your buddy) then you need to complete a few more steps.  Did you wonder what permissions 2775 is for?

---

### Post by mconley3 on 2014-05-03
Only one user, it's a home share.  There will never be another user on the server.

Nope, I've always left directory and file creation at the default for samba.  I did know there was a way to control the filesystem permissions on what was created but never had a reason to look at it.

---

### Post by bab1 on 2014-05-03
> **mconley3 said:**
> Only one user, it's a home share.  There will never be another user on the server.

Nope, I've always left directory and file creation at the default for samba.  I did know there was a way to control the filesystem permissions on what was created but never had a reason to look at it.

Then I would change the last line of the share definition to this ```
directory mode = 0775

```

The leading 2 in my original setup turns on group ownership inheritance.

---

### Post by mconley3 on 2014-05-03
Will do.  Thanks again.

---

### Post by bab1 on 2014-05-03
> **mconley3 said:**
> Will do.  Thanks again.
Glad it all worked out for you.

---

