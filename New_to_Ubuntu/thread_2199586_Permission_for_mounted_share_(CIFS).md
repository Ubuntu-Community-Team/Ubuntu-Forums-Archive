---
title: "Permission for mounted share (CIFS)"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by tkalowsky on 2014-01-14
So here is the deal.
I have Linux box with Plex installed. On the Linux box I'm mounting share from my synology RS212, below are my fstab entries.```

//Rackstation/video /mnt/video cifs username=myuser,password=mypassword,sec=ntlm 0 0  
//Rackstation/music /mnt/music cifs username=myuser,password=mypassword,sec=ntlm 0 0 
//Rackstation/photo /mnt/photo cifs username=myuser,password=mypassword,sec=ntlm 0 0 

```
RS212 has all permissions setup for myuser.
Outcome:
No access for video folder permission denied
No problem with access to music and photo folder.
I want to clraify that both Linux box and Plex dont have access to mounted video folder.
Permission on folders
drwxrwxrwx 4  1026 users      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek users     0 Jan  5 18:21 Movies
drwxrwxrwx 3  1026 users      0 Jan 12 20:38 Temp

Permission on file inside Movies folder
```

------------rwx 4  tomek tomek      10300000 Dec 30 14:36 xxx.mv4
```

I know its permission issue. But tried chmod and it didn't work if someone can please help I'm still a NOOB :)

---

### Post by bab1 on 2014-01-14
> **tkalowsky said:**
> So here is the deal.
I have Linux box with Plex installed. On the Linux box I'm mounting share from my synology RS212, below are my fstab entries.
```
//Rackstation/video /mnt/video cifs username=myuser,password=mypassword,sec=ntlm 0 0  
//Rackstation/music /mnt/music cifs username=myuser,password=mypassword,sec=ntlm 0 0 
//Rackstation/photo /mnt/photo cifs username=myuser,password=mypassword,sec=ntlm 0 0 
```

RS212 has all permissions setup for myuser.

Outcome:
No access for video folder permission denied
No problem with access to music and photo folder.
I want to clraify that both Linux box and Plex dont have access to mounted video folder.
Permission on folders
drwxrwxrwx 4  1026 users      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek users     0 Jan  5 18:21 Movies
drwxrwxrwx 3  1026 users      0 Jan 12 20:38 Temp

Permission on file inside Movies folder

------------rwx 4  tomek tomek      10300000 Dec 30 14:36 xxx.mv4

I know its permission issue. But tried chmod and it didn't work if someone can please help I'm still a NOOB :)

The permissions are determined on the local machine (i.e. "Linux box" in your case) upon mounting the remote file system from the NAS.

The "Linux box" itself has no access to files or directories.  Only users have access.  You should have a user and a user group *plex*.  How did you get the user group *users* set on the directories below /mnt/video?

It is important to make sure that the permissions are correct from /mnt on down to the last file in the file system.  Did you modify anything in /mnt  what are the permissions on /mnt/video.  Post the output of ```
ls -ld /mnt/video
```

---

### Post by maestrobwh1 on 2014-01-14
I have struggled with this as well: this opens you up to potential security issues but I just use files on my home server and it is behind a fairly robust firewall and I don't really have much to hide.  If someone finds my pictures of me in Spain or the fact that I listen to Lady Gaga intriguing, well more power to them:

I have tried to use the graphical means in nautilus and dolphin (KDE) but I often run into permissions issues.  They sometimes work but more often than not, only the creator can modifu files so if I drip files from a guest, then another guest or the host can't modify them and all guests and hosts are me.  Here is a sample share I have set up in /etc/samba/smb.conf

```
[BRIAN_STUFF]
path = /home/ubuntu/Documents
guest ok = yes
read only = no
wide links = yes
create mask = 0775
force create mask = 0775
force directory mode = 775
directory mask = 0775
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by bab1 on 2014-01-14
> **maestrobwh1 said:**
> I have struggled with this as well:
What's your problem?> 
 this opens you up to potential security issues 

What potential security issues?
> 
but I just use files on my home server and it is behind a fairly robust firewall and I don't really have much to hide.  If someone finds my pictures of me in Spain or the fact that I listen to Lady Gaga intriguing, well more power to them:

I have tried to use the graphical means in nautilus and dolphin (KDE) but I often run into permissions issues.  They sometimes work but more often than not, only the creator can modifu files so if I drip files from a guest, then another guest or the host can't modify them and all guests and hosts are me. 

This is a Linux (the local host) configuration problem, not a Samba problem.  Follow along and see if the OP's solution helps you.

---

### Post by tkalowsky on 2014-01-15
outpout for [COLOR=#000000][FONT=Ubuntu Mono]ls -ld /mnt/video is  drwxrwxrwx root root 0 

[/FONT][/COLOR]

---

### Post by bab1 on 2014-01-15
> **tkalowsky said:**
> outpout for [COLOR=#000000][FONT=Ubuntu Mono]ls -ld /mnt/video is [COLOR="#800080"] d[/COLOR][COLOR="#0000FF"]rwx[/COLOR][COLOR="#008000"]rwx[/COLOR][COLOR="#FF0000"]rwx[/COLOR] root root 0 

[/FONT][/COLOR]

This shows that every user has read, write and execute (traversal) rights (see red above).  The first bit is the directory listing ( purple ).  The next three bits are the owner permissions (blue) and the next three bits are the group permissions (green).  The fact the root is the owner and group is not important in with these settings.  Any user should be able to create or modify or delete a file or directory in /mnt/media.

I saw previously that this is also true of the sub-directory Movies```

drwxrwxrwx 4 1026 users 0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek users 0 Jan 5 18:21 Movies
drwxrwxrwx 3 1026 users 0 Jan 12 20:38 Temp
```

The only thing unusual is the user ID (1026).  There is no user name attached to this user ID.  Post the output of ```
getent passwd 1026
```
What did you do to get the user group to be *users*?

Are you the user tomek?  See if you can create a test file in /mnt/video.  Try this```
touch /mnt/video/test.file
```...is the file there?  Post the output of```
ls -l /mnt/video
```
If that works try it again in the /mnt/video/Movies directory.  Where you successful?

---

### Post by tkalowsky on 2014-01-16
i was able to create test.file however got message cannot touch permission denied
ls - give me: ----rwx--- 1  1026 users 0  Jan 16 20:07 test.file

it behave exactly the same way on both directories /mnt/video and /mnt/video/movies
Thanks

---

### Post by bab1 on 2014-01-16
> **tkalowsky said:**
> i was able to create test.file 

The idea wasn't to create a file with any means.  It was to see if you could create the file using touch.   :-(
> 
however got message cannot touch permission denied.

I assume this means that you could NOT create the file using touch.  is this true?
> 
ls - give me: ----rwx--- 1  1026 users 0  Jan 16 20:07 test.file
it behave exactly the same way on both directories /mnt/video and /mnt/video/movies
Thanks
I asked a few other questions too.  One of them was in reference to the user 1026.  Who is that user? Post the output of
```
getent passwd 1026
```
What did you do to get the user group to be users?  Are you the user tomek?  Post the output of
```
getent passwd tomek
```

I can't diagnose the problem if you don't provide me feedback.

The touch command is just an easy way for me to see if the logged in user can create a 0 byte file and show who the owner/group is.  The other commands I asked you to post is to see who these users are (uid/gid).

If you have a directory that is available to read and write in then you should be able to do just that.  If this is not happening then either the directory is misconfigured or you are not using touch properly (unlikely).  Are you using the using the Linux host CLI to execute the commands directly or are you using ssh to login to the Linux host?  None of this is clear to me.  This output is confusing to me```
ls -l
----rwx--- 1  1026 users 0  Jan 16 20:07 test.file
```...Explain how you created the group *user*.  Is this Linux host a Debian type distro?

---

### Post by tkalowsky on 2014-01-17
[QUOTE=bab1;12902432]The idea wasn't to create a file with any means.  It was to see if you could create the file using touch.   :-(

I assume this means that you could NOT create the file using touch.  is this true?

No it's not true i was able to create file see below:


tomek@server:/mnt/video$ touch /mnt/video text.txt
touch: cannot touch `text.txt': Permission denied
tomek@server:/mnt/video$ dir
Clips  Movies  movies1    Temp text.txt  Thumbs.db  < it has been created
tomek@server:/mnt/video$ 

[COLOR=#000000][I][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **tkalowsky** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12902401#post12902401")
i was able to create test.file

[/I]
[/COLOR]
[COLOR=#000000]The idea wasn't to create a file with any means. It was to see if you could create the file using touch. [/COLOR]:sad:
[COLOR=#000000][I]however got message cannot touch permission denied.
[/I]
[/COLOR]
[COLOR=#000000]I assume this means that you could NOT create the file using touch. is this true?[/COLOR]
[COLOR=#000000][I]ls - give me: ----rwx--- 1 1026 users 0 Jan 16 20:07 test.file
it behave exactly the same way on both directories /mnt/video and /mnt/video/movies
Thanks
[/I]
[/COLOR]
[COLOR=#000000]I asked a few other questions too. One of them was in reference to the user 1026. Who is that user? Post the output of[/COLOR]
[COLOR=#000000]Code:
getent passwd 1026[/COLOR]

tomek@server:/mnt/video$ getent passwd 1026
tomek@server:/mnt/video$ 


[COLOR=#000000]What did you do to get the user group to be users? Are you the user tomek? Post the output of[/COLOR]
[COLOR=#000000]Code:
getent passwd tomek[/COLOR]
[COLOR=#000000]I can't diagnose the problem if you don't provide me feedback.[/COLOR]

I'm sorry 

tomek@server:/mnt/video$ getent passwd tomek
tomek:x:1000:1000:tomek,,,:/home/tomek:/bin/bash
tomek@server:/mnt/video$ 


[COLOR=#000000]The touch command is just an easy way for me to see if the logged in user can create a 0 byte file and show who the owner/group is. The other commands I asked you to post is to see who these users are (uid/gid).[/COLOR]

I understant yorur intentions with touch.

[COLOR=#000000]If you have a directory that is available to read and write in then you should be able to do just that. If this is not happening then either the directory is misconfigured or you are not using touch properly (unlikely). Are you using the using the Linux host CLI to execute the commands directly or are you using ssh to login to the Linux host? None of this is clear to me. This output is confusing to me[/COLOR][COLOR=#000000]Code:

I use directly terminal on my host

ls -l
tomek@server:/mnt/video$ ls -l
total 124
drwxrwxrwx 4  1026 users      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek tomek      0 Jan 16 20:13 Movies
drwxrwxr-x 2  1026 users      0 Jan 14 19:06 movies1
drwxrwxrwx 3  1026 users      0 Jan 14 20:03 Temp
----rwx--- 1  1026 users      0 Jan 16 19:55 test.file
----rwx--- 1  1024 users 126976 Nov  1  2012 Thumbs.db





[/COLOR][COLOR=#000000]...Explain how you created the group [/COLOR]*user. Is this Linux host a Debian type distro?*

I don't know how I've created it (possible messed up something) not its not Debian it is Ubuntu 12.04 Home

---

### Post by bab1 on 2014-01-17
> **tkalowsky said:**
> 
[QUOTE=bab1;12902432]The idea wasn't to create a file with any means.  It was to see if you could create the file using touch.   :-( 
I assume this means that you could NOT create the file using touch.  is this true?

No it's not true i was able to create file see below:


```
tomek@server:/mnt/video$ touch /mnt/video text.txt
touch: cannot touch `text.txt': Permission denied
tomek@server:/mnt/video$ dir   [COLOR="#FF0000"]<-- dir???  :-) [/COLOR]
Clips  Movies  movies1    Temp text.txt  Thumbs.db  < it has been created
tomek@server:/mnt/video$ 
```
i was able to create test.file
[/QUOTE]How about we use the the long form (ls -l) so we can see the permissions and ownership> 

I asked a few other questions too. One of them was in reference to the user 1026. Who is that user? Post the output of:
getent passwd 1026

tomek@server:/mnt/video$ getent passwd 1026
tomek@server:/mnt/video$ 

Hmmmm, not good at all.
> 

What did you do to get the user group to be users? Are you the user tomek? Post the output of:
getent passwd tomek
I can't diagnose the problem if you don't provide me feedback.

I'm sorry 

tomek@server:/mnt/video$ getent passwd tomek
tomek:x:1000:1000:tomek,,,:/home/tomek:/bin/bash
tomek@server:/mnt/video$ 


Are you using the using the Linux host CLI to execute the commands directly or are you using ssh to login to the Linux host? None of this is clear to me. This output is confusing to me[/COLOR][COLOR=#000000]Code:

I use directly terminal on my host

ls -l
tomek@server:/mnt/video$ ls -l
total 124
drwxrwxrwx 4  1026 users      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek tomek      0 Jan 16 20:13 Movies
drwxrwxr-x 2  1026 users      0 Jan 14 19:06 movies1
drwxrwxrwx 3  1026 users      0 Jan 14 20:03 Temp
----rwx--- 1  1026 users      0 Jan 16 19:55 test.file
----rwx--- 1  1024 users 126976 Nov  1  2012 Thumbs.db


Explain how you created the group *user*. Is this Linux host a Debian type distro?
I don't know how I've created it (possible messed up something) not its not Debian it is Ubuntu 12.04 Home

Ubuntu is a Debian type distro.  There is no *Ubuntu 12.04 Home *.  It's either a Server Edition or a Desktop.  But I get your meaning.

Let's try something completely different.  Post the output of ```
df -h
```...This will tell me how many disks you are using.

Then post the output of these 2 commands```

ls -ld /srv

ls -l /srv
```This will tell me the ownership and permissions of the /srv directory and list the contents of the /srv directory.  By default that directory should be empty.

Finally (because I can't let it go), post the output of these 2 commands```
getent group users

getent passwd | grep 100
```...neither the user 1026 or the group **users **are used by default in Ubuntu.

[COLOR="#0000FF"]**Edit: **I think I know the answer to your problem.  The Synology NAS is the source of the user 1026 ( and the user 1027) and the group *users*.   What I don't know is what the smb.conf file looks like on the Synology NAS and whether it is modifiable in any way.  Here is a [link]("http://askubuntu.com/questions/269643/how-do-i-map-users-with-a-samba-share") to what I am talking about.  Is there a terminal available on the Synology NAS? [/COLOR]

---

### Post by tkalowsky on 2014-01-17
Hey thanks for your support appreciate it.

df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  9.5G   91G  10% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  952K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  228K  3.9G   1% /run/shm
//Rackstation/video   3.6T  1.5T  2.2T  40% /mnt/video
//Rackstation/music   3.6T  1.5T  2.2T  40% /mnt/music
//Rackstation/photo   3.6T  1.5T  2.2T  40% /mnt/photo



tomek@server://mnt/video$ ls -ld /srv

drwxr-xr-x 2 root root 4096 Aug 23  2012 /srv

tomek@server://mnt/video$ ls -l /srv
total 0
tomek@server://mnt/video$ 


tomek@server://mnt/video$ getent group users
users:x:100:

tomek@server://mnt/video$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
tomek:x:1000:1000:tomek,,,:/home/tomek:/bin/bash





Synology Samba conf:

[global]
    printcap name=cups
    winbind enum groups=yes
    security=user
    local master=no
    realm=*
    passdb backend=smbpasswd
    printing=cups
    winbind enum users=yes
    load printers=yes
    workgroup=WORKGROUP
[Video]
    invalid users=nobody,nobody
    valid users=nobody,tomek,marzenka,admin,nobody
    comment="Storage Location For PlexMediaServer"
    path=/volume1/Video
    guest ok=yes
    browseable=no
    fileindex=no
    mediaindex=no
    edit synoacl=no
    enable recycle bin=no
    recycle bin admin only=no
    hide unreadable=no
    ftp disable list=no
    ftp disable modify=no
    ftp disable download=no
    read list=nobody,nobody
    write list=nobody,admin,marzenka,tomek,nobody
    writeable=yes

---

### Post by bab1 on 2014-01-18
> **tkalowsky said:**
> Hey thanks for your support appreciate it.

```
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  9.5G   91G  10% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  952K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  228K  3.9G   1% /run/shm
//Rackstation/video   3.6T  1.5T  2.2T  40% /mnt/video
//Rackstation/music   3.6T  1.5T  2.2T  40% /mnt/music
//Rackstation/photo   3.6T  1.5T  2.2T  40% /mnt/photo
```

These Synology shares are mounted.  Think about what you are doing here.  You are mounting one NAS's shares to a second NAS (the file server) only to reshare them to their ultimate clients.  Is there a reason to do this? 
> 



```
tomek@server://mnt/video$ ls -ld /srv

drwxr-xr-x 2 root root 4096 Aug 23  2012 /srv

```

```
tomek@server://mnt/video$ ls -l /srv
total 0
tomek@server://mnt/video$ 
```
This is usually where I mount remote shares.  I think we should temporary use this directory to test manual mounts. > 


```
tomek@server://mnt/video$ getent group users
users:x:100:
```
```

tomek@server://mnt/video$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
tomek:x:1000:1000:tomek,,,:/home/tomek:/bin/bash

```
I think that we should add the user tomek to the users group.  This user is the only mortal user on the server.

```
Synology Samba conf:

[global]
    printcap name=cups
    winbind enum groups=yes
    security=user
    local master=no
    realm=*
    passdb backend=smbpasswd
    printing=cups
    winbind enum users=yes
    load printers=yes
    workgroup=WORKGROUP
[Video]
    invalid users=nobody,nobody
    valid users=nobody,tomek,marzenka,admin,nobody
    comment="Storage Location For PlexMediaServer"
    path=/volume1/Video
    guest ok=yes
    browseable=no
    fileindex=no
    mediaindex=no
    edit synoacl=no
    enable recycle bin=no
    recycle bin admin only=no
    hide unreadable=no
    ftp disable list=no
    ftp disable modify=no
    ftp disable download=no
    read list=nobody,nobody
    write list=nobody,admin,marzenka,tomek,nobody
    writeable=yes
```

It seems that you are a Samba valid user on the Synology NAS.  Does Synology have a method to add tomek as a user?  Did you add tomek to the Samba users (smbpasswd -a tomek) on Synology?

As an experiment I'd like you to unmount /mnt/video```
sudo umount /mnt/video
```...at this point you can check to see if it is unmounted by using ```
df -h 
```
This should be gone (NOT SHOWING) ```
//Rackstation/video   3.6T  1.5T  2.2T  40% /mnt/video
```

Now add a mount point at /srv like this ```
sudo mkdir /srv/video
```

Now let's see if you can remount it at a different location.  In addition we will make you the owner of the video file system.  Try this```
sudo mount -t cifs //Rackstation/video /srv/video -o username=myuser,password=mypassword,uid=1000,gid=1  000,sec=ntlm 0 0   
```

NOTE!  we are mounting this share at /srv/video and we have added the uid and gid for your user.  The uid and gid settings should provide ownership and permission.  THIS IS JUST A TEST.  You can always go back to the original settings rebooting if you can't remember how to unmount the new mount location of the video share.

If it is successful, post the output of ```

ls -l /srv/video

```

if not successful, what errors did you get?

---

### Post by tkalowsky on 2014-01-18
These Synology shares are mounted.  Think about what you are doing here.   You are mounting one NAS's shares to a second NAS (the file server)  only to reshare them to their ultimate clients.  Is there a reason to do  this?

Sorry i should have explained it.
Yes the reason is PLEX installed on my Ubuntu "server", I've done some reasearch but seems that PLEX can't access network share so that's why i need to reshare from ubuntu.
BTW when i browse my Windows workgoup from ubuntu there is no issue with access video folder on my Synology NAS. 


It seems that you are a Samba valid user on the Synology NAS.  Does  Synology have a method to add tomek as a user?  Did you add tomek to the  Samba users (smbpasswd -a tomek) on Synology?

I've tried smbpasswd -a tomek on Synology but it didn't work.

As an experiment I'd like you to unmount /mnt/video     Code:

     sudo umount /mnt/video
Unmounted it 




...at this point you can check to see if it is unmounted by using      Code:

     df -h
tomek@server:~$ df -h
df: `/var/lib/lightdm/.gvfs': Permission denied
Filesystem           Size  Used Avail Use% Mounted on
/dev/sda1            106G   12G   89G  12% /
udev                 3.9G  4.0K  3.9G   1% /dev
tmpfs                1.6G  944K  1.6G   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                 3.9G  224K  3.9G   1% /run/shm
//Rackstation/music  3.6T  1.5T  2.2T  40% /mnt/music
//Rackstation/photo  3.6T  1.5T  2.2T  40% /mnt/photo













This should be gone (NOT SHOWING)      Code:

     //Rackstation/video   3.6T  1.5T  2.2T  40% /mnt/video
It is gone!





done!





Now add a mount point at /srv like this      Code:

     sudo mkdir /srv/video 

Now let's see if you can remount it at a different location.  In  addition we will make you the owner of the video file system.  Try this     Code:

     sudo mount -t cifs //Rackstation/video /srv/video -o username=myuser,password=mypassword,uid=1000,gid=1  000,sec=ntlm 0 0
This command didn't work for me!
So I've tried:
sudo mount -t cifs //Rackstation/video /srv/video -o username=tomek,password=mypass,uid=1000,gid=1,sec=ntlm




it had mounted share  



NOTE!  we are mounting this share at /srv/video and we have added  the uid and gid for your user.  The uid and gid settings should provide  ownership and permission.  THIS IS JUST A TEST.  You can always go back  to the original settings rebooting if you can't remember how to unmount  the new mount location of the video share.

If it is successful, post the output of      Code:

     ls -l /srv/video
tomek@server:~$ ls -l /srv/video
total 124
drwxrwxrwx 4 tomek daemon      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek daemon      0 Jan 16 20:13 Movies
drwxrwxrwx 3 tomek daemon      0 Jan 18 15:46 Temp
----rwx--- 1 tomek daemon 126976 Nov  1  2012 Thumbs.db









if not successful, what errors did you get?

No problem still exists look at permission on files 
tomek@server:~$ ls -l /srv/video/movies
total 395699340
-------rwx 1 tomek daemon  2163089367 Mar 11  2013 101 Dalmatians 2.m4v
-------rwx 1 tomek daemon  3702778413 Mar 10  2013 12 Monkeys.m4v


Thanks

---

### Post by bab1 on 2014-01-19
> **tkalowsky said:**
> ...If it is successful, post the output ...
```
tomek@server:~$ ls -l /srv/video
total 124
drwxrwxrwx 4 tomek daemon      0 Dec 30 14:36 Clips
drwxrwxrwx 3 tomek daemon      0 Jan 16 20:13 Movies
drwxrwxrwx 3 tomek daemon      0 Jan 18 15:46 Temp
----rwx--- 1 tomek daemon 126976 Nov  1  2012 Thumbs.db
```
> 
if not successful, what errors did you get?

No problem still exists look at permission on files 

tomek@server:~$ ls -l /srv/video/movies
total 395699340
-------rwx 1 tomek daemon  2163089367 Mar 11  2013 101 Dalmatians 2.m4v
-------rwx 1 tomek daemon  3702778413 Mar 10  2013 12 Monkeys.m4v


Thanks

So now all you need to do is edit the fstab entries to add: ```
 uid=1000,gid=1000
```  The reboot and it should work.

Also you should know that plex will work on the Ubuntu server file system.  You just need to set the permissions correctly for it to work.

If we are done here please mark this thread as SOLVED!

---

### Post by tkalowsky on 2014-01-19
BAB1,
Thanks for help and time invested.
Actually I've put uid=1026,gid=1026 and it done the trick.
Now my PLEX is running good.
T.

---

### Post by Brad_Willman on 2014-11-24
> **tkalowsky said:**
> BAB1,
Thanks for help and time invested.
Actually I've put uid=1026,gid=1026 and it done the trick.
Now my PLEX is running good.
T.


I realize this posting is labeled as solved and all that. However I want to thank both of you for indirectly also helping me with a similar issue.

Ultimately my scenario was that root was able to mount, and view the mounted location, but no alternate user could change directory into /mnt/sharename

below is my resulting fstab entry:
//192.168.98.90/Media /mnt/share cifs username=cifsuser,password=cifspasword,rsize=8192,wsize=8192,atime,auto,ro,dev,exec,uid=1001,gid=1001,suid 0 0


Worked on Synology Disktation 1813+.  I believe I also used some synology resources to create an nfs share and user although only after searching the logs did i realize it looked like it was attempting a mount at cifs type instead so i persued that avenue..

Now to turn my poor old laptop into a minecraft server... muhahaha.
Thanks again...

---

