---
title: "How to :Auto + secure Mount remote SSH  filesys with AUTOFS and SSHFS + samba )"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by gaupe on 2007-10-19
At home i  have a unix (unslung) based router with an usb harddisk mounted on it  wich supports ssh and scp 
My goal is to have access to that remote file system as it was a local file system from the folder /RemoteDiskSSH on my Laptop running Ubuntu 7.10 
I want it to be a secure connection because i allso want to be able to have access to the remote file system over the internet.

For me automaticly mounting and dismounting the remote drive with sshfs is the solution for me.

As I justinstalled gutsy Ubuntu 7.10 I wrote along this howto in order to document it for my self but allso for others to use. .
**First the package sshfs is needed.**
This can be installed with the synaptics package manager. Search for sshfs, mark it and have it installed.
After installed sshfs installed, test if you can mount a ssh/scp accessable remote file system.
create a directory where you want to mount it on

```
 sudo mkdir /RemoteDiskSSH
``` 


Mount the desired remote directory on your local file system.

```
sudo sshfs remoteuser@remote.machine.address:/Remote/Directory/to/mount /RemoteDiskSSH
```

If all went oke you can now access the remote file system as it was a local file system from the local folder /RemoteDiskSSH

```
sudo ls /RemoteDiskSSH
```

Want to be able to use the local rights system on that folder? (just if you dont want to go on but want to be able to mount a remote filesystem and have the 
local rights translated to it.) 

```

sudo sshfs -o allow_other,default_permissions remoteuser@remote.machine.address:/Remote/Directory/to/mount /RemoteDiskSSH

```
now the local rights system will work for this mount

to unmount it just give the command

```
sudo fusermount -u /RemoteDiskSSH
```

As i want the remote directory mount automaticly (with autofs described later on)
**i need a passwordless ssh login. This can be done with help of generating public keys. **
A public key for the local system is generated with the command:

```
ssh-keygen -t rsa
```

(hit enter so its saved in your home directory under .ssh/id_rsa

(hit enter for no passphrase)  

you have now a .ssh directory with two files
 id_rsa  and id_rsa.pub 

id_rsa is your private key ! protect it well let only YOU have rights on it (default) as if this gets compromised 
anyone can gain access to your remote host

id_rsa.pub is the public key it is readable by others and this is what you have to send to the remote host so it can have it in its authorized_keys file


Copy now the public key to the remote machine 

```

scp ~/.ssh/id_rsa.pub remoteuser@remote.machine.address:~/.

```


logon with an ssh client to the remote machine the id_rsa.pub file content must be added to the authorized_keys file in the .ssh directory of the homedir of the user you want to connect as.

In this example the remote users home directory  

```

ssh remoteuser@remote.machine.address
cat ~/id_*.pub >> ~/.ssh/authorized_keys

```

A alternative simpeler way to get your public key in the authorized_keys file of your remote host is with ssh-copy-id 
from your local machine type

```
 ssh-copy-id -i ~/.ssh/id_rsa.pub remoteuser@remote.machine.address
```

this does the whole process of copying your public key to the remote machnes users homedir in .ssh in authorized_keys
and sets the rights oke



As later on the mount is done by the local root user you need the public key of root too.

so give command

```
sudo gnome-terminal
```

to open a command terminal as user root and repeat the above procedure.

after this the file authorized_keys at the remote station has both the public key of the local user and the local root so it works in test and in production later when root does the mounwork....

Set the right rights for the file authorized_keys or the ssh deamon ( in my case dropbear) might not want to process  the authorize_keys file

```

ssh remoteuser@remote.machine.address
chmod 0600 ~/.ssh/authorized_keys

```

logout from the remote machine and test. 

```

ssh remoteuser@remote.machine.address

```

You should now be able to login without giving a password.

If it does not work debug with  ssh -v option .

(same for the sudo gnome-terminal )

If it works you can see if the mount works passwordless too

```
sudo sshfs remoteuser@remote.machine.address:/Directory/to/mount /RemoteDiskSSH
```

So ! thats done!!! you can now mount the remote filesystem without using a password.

unmount again with: ```
sudo fusermount -u /RemoteDiskSSH
```

**As i said i want the remote filesystem to be mounted automaticly as soon as i try to access it. This can be done with autofs.**

First install autofs by starting the synaptics package manager search for autofs, mark for install and have it installed.

theres now a auto.master configuration file in /etc
add the line

/etc/auto.master
```

RemoteDiskSSH /etc/auto.ssh uid=1000 gid=1000 -v --ghost --timeout=3600

```
uid and gid are the local user and group id you want the mount to belong to.

--ghost is the directory will be ghost mounted so you see it with an ls but the actual mount is done when you access it

--timeout gives the maximum inactivity time for the mount. After that it is auto dismounted again.

One more config file is needed and that is /etc/auto,ssh
create the file and put in the following line:

/etc/auto.ssh
```
RemoteDiskSSH -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#remoteuser@remote.machine.address\:/Directory/to/mount
```

You can now test the autofs mounting by starting and stopping the automount service

```

sudo /etc/init.d/autofs restart

```

in /var/log/syslog are the loggings
start a separate command terminal and give this command to follow it all.
```
tail -f /var/log/syslog
```

check if it worked

```
ls /RemoteDiskSSH
``` if all is oke you see the content of the remote file system.
[B]
The same you can actually do for a windows or samba share [/B]

The question is if you want this as in Ubuntu 7.10 gutsy if you goto menu Places and then browse network locations, you can easily get to the windows shares in your network. (I prefer doing the above)

Nevertheless ill describe here how it can be done using smbfs and autofs. 

first you have to install smbfs

Start the synaptics package manager, search for smbfs, mark and install it.

the line for the /etc/auto.master file is

```
/ /etc/auto.Samba --ghost -v --timeout=300
```

Create the file /etc/auto.samba

and fil it with the following line:

/etc/auto.samba
```
RemoteDiskSamba -fstype=smbfs,workgroup=WORKGROUPNAME,credentials=/etc/samba.credentials,uid=remoteuser,gid=users ://remote.server.address/ShareName
```

Then create the credentials file in /etc/samba.credentials

fill this file with the following lines:
/etc/samnba.credentials
```

username = remoteusername

password = remotepassword

```
take care only root can see this file ```
sudo chmod 600 /etc/samba.credentials
```
If this is done just restart the autofs

```

sudo /etc/init.d/autofs restart

```
(tail -f /var/log/syslog in a seperate terminal to see the loggings)

and see if it works.

Good luck!

---

### Post by hyper_ch on 2007-10-19
nice howto... just one suggestion. Code you run in the shell, plz put it into

[ code] [ /code] brackets. That will make it a lot simpler to read :)

---

### Post by gaupe on 2007-10-19
Thnx for the advice. i didn't know how to do that [ code] [ /code] stuff but edited the post
also saw it automaticly put in [ email] tags where they shouldn't be.... there out now too.
If anythings else pls let me kno so i can make it better again.

---

### Post by hyper_ch on 2007-10-19
much better... but in the /etc/auto.samba shouldn't it be:

```

workgroup=WORKGROUPNAME

```

instead of

```

workgroupWORKGROUPNAME

```

in this section:  in /var/log/syslog are the loggings --> you have added a comment to the command... (just the [ /code] is a bit late)

P.S.: Maybe ask a mod to move this to the HowTo section :)

---

### Post by bodhi.zazen on 2007-10-19
hyper_ch : use [noparse][noparse]<code>[/noparse][/noparse]

"[noparse][noparse]```
like this
```[/noparse][/noparse]"

looks like this:

[noparse]```
like this
```[/noparse]

@gaupe : Nice how-to. I suggest you post in the how-to section ([http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100))

---

### Post by gaupe on 2007-10-19
Howto made better again. And i learn howto use the forum editor. :)

---

### Post by hyper_ch on 2007-10-19
didn't know about the [noparse] thing :) thx ;)

---

### Post by KubuntuKilledMe on 2007-10-19
I present to you the glory of ssh installkeys!

[http://www.catb.org/~esr/ssh-installkeys/](http://www.catb.org/~esr/ssh-installkeys/)

---

### Post by htoerrin on 2007-10-22
I've been fiddeling around with the same setup without any great success. Maybe someone here can help.

I have been able to setup public key authentification to my nslu box, and are able to log in without password. scp does also work without password. I generated a key with the -t dsa option and added it to authorized_keys2.

Whenever I try to mount the box with sshfs, I get the followin error message:

read: Connection reset by peer

I still get this message after following the above procedure. -So any information on how ssh and sshfs handles the various keys would be appreciated.

---

### Post by Scotty562 on 2007-11-08
I've been looking for something like this for a while now. The way I usually do it is just run a script called sshfs.sh and it runs this command:

sshfs [email]xxx@xxx.no-ip.org[/email]:/hda1 /home/zach/hda1_xbox

This works just like it should and according to the howto this is the only prerequisite. I did my best, but I still missed something.

Now in the guide here I think this is the area I'm having problems with:

```
RemoteDiskSSH -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#remoteuser@remote.machine.address\:/Directory/to/mount
```

This is what I'm using:

RemoteDiskSSH -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#xxx.no-ip.org\:/hda1

My auto.master looks like this:

/ /etc/auto.SSH uid=1000 gid=1000 -v --/home/zach/hda1_xbox --timeout=32400

I obviously have something wrong, I'm guessing it's the syntax but I could be wrong. Anyone see what I'm doing wrong here?

---

### Post by gaupe on 2007-11-08
probably just a typo in your posting but i do see a space between allo and w 
now what does syslog say ?

---

### Post by Scotty562 on 2007-11-08
Copy and paste messed up the allo w for some reason, that space isn't in the actual file. Although that would have been embarrassing had that been the problem :).

All I get is this:

Nov  8 17:30:55 aries kernel: [12817.044000] wlan0: CTS protection disabled (BSSID=00:17:3f:c0:28:f9)
Nov  8 17:30:56 aries kernel: [12818.068000] wlan0: CTS protection enabled (BSSID=00:17:3f:c0:28:f9)

It doesn't seem to be related to what I'm trying to do hear though.

---

### Post by gaupe on 2007-11-08
if you do 

sudo /etc/rc6.d/K19autofs restart  your syslog should show some more

like in my case 

Nov  8 23:51:22 Wultftop-Ubuntu automount[4820]: prep_shutdown: state = 1 
Nov  8 23:51:22 Wultftop-Ubuntu automount[4820]: signal_children: send 12 to process group 4820
Nov  8 23:51:22 Wultftop-Ubuntu automount[4820]: umount_multi: no mounts found under /WulfSSH
Nov  8 23:51:22 Wultftop-Ubuntu automount[4820]: shut down, path = /WulfSSH
Nov  8 23:51:22 Wultftop-Ubuntu automount[5914]: starting automounter version 4.1.4, path = /WulfSSH, maptype = file, mapname = /etc/auto.ssh
Nov  8 23:51:22 Wultftop-Ubuntu automount[5914]: using kernel protocol version 4.00
Nov  8 23:51:22 Wultftop-Ubuntu automount[5914]: using timeout 3600 seconds; freq 900 secs
Nov  8 23:51:22 Wultftop-Ubuntu automount[5914]: ghosting enabled

---

### Post by Scotty562 on 2007-11-08
I don't get any of that information... how frustrating.

---

### Post by gaupe on 2007-11-08
Furthermore what does the --/home/zach/hda1_xbox do there


i think your auto.master it should say

home/zach/hda1_xbox /etc/auto.ssh uid=1000 gid=1000 -v --ghost --timeout=3600

assuming you want the xbox folder mounted on /home&zach/hda1_xbox

and then leave away the --/home/zach/hda1_xbox  furtheron 

(i hope i have it right now :-)

---

### Post by Scotty562 on 2007-11-08
Ahh, that was what I didn't understand. Works great :).
Will this automatically dismount and mount when I change wireless networks?

---

### Post by gaupe on 2007-11-08
AH nice i see now that the howto is not oke i forgot to put the mountingdirectory  in the auto.master instead i put put  / there 
while my explanation goes from having it inRemoteDiskSSH .... ill change it.
(and allso auto.SSH gets auto.ssh 

hope the next one will have a flawless howto now. 
it will dismount after the given time you put it on and it will mount even over the internet if your at someone elses place (assuming yoyu have th ip address right i use dyndns to track my outside ip and open it up when i need it.

---

### Post by gaupe on 2007-11-08
> **htoerrin said:**
> I've been fiddeling around with the same setup without any great success. Maybe someone here can help.

I have been able to setup public key authentification to my nslu box, and are able to log in without password. scp does also work without password. I generated a key with the -t dsa option and added it to authorized_keys2.

Whenever I try to mount the box with sshfs, I get the followin error message:

read: Connection reset by peer

I still get this message after following the above procedure. -So any information on how ssh and sshfs handles the various keys would be appreciated.

You do realise that while testing you need the public key of the user you are loged in as and while having it in the config files root does the work for you so then it should be in the root keys 
look at my examples maybe you forgot something 
allso i use rsa keys dunno if the dsa worsk tought i read something about it does not work for dropbear .

---

### Post by Scotty562 on 2007-11-08
One other consideration, I move from network to network throughout the day. I use sleep mode on my laptop so I don't like to shutdown. Is there a way I can have this automatically unmounted when I switch wireless networks? Maybe stop this service when the network is switched and then started back up next time I access a share?

Glad you caught the .SSH :) I forgot to mention that.

---

### Post by gaupe on 2007-11-09
I have no experience with sleep > ( is that suspend or hibernate mode ? )
mode i would think since its an automounter it would mount by itself again... but havent tried.

I think  its possible to run a script after wakeup (would be if i look quickly but again i have no experience with this, in /etc/acpi/resume.sh ) , then if it wouldnt work automaticly,  you could restart the automounter probably from there ....

couldnt test it here as is use the ATI proprietary drivers with wisch suspend or hibernate doesnt work in gutsy

in the auto.master there is a timeout which automaticly dismounts allready if no activity.

(this means allso if you have a fle browser open on it but not actively browsing it will dismount and your filebrowser is falling back to the rootdir (ncie if you drag files to it afterwards thinking it is still on the automount) I havent yet found out how to prevent that....

---

### Post by gaupe on 2008-01-04
Got some more knowledge of the whole thing
and adjusted the howto a litte bit for , hopefully, a better understanding
of ssh or samba automount

---

### Post by hyper_ch on 2008-01-04
Small typo:

> 
Want to be able to use the local rights system on that folder? (just if you dont want to go on but want to be able to mount a remote filesystem and have the
local rights translated to it.)

Code:

]sudo sshfs -o allow_other,

You have that closing bracket just before the sudo command.

---

### Post by gaupe on 2008-01-04
fixed that thanks

---

### Post by Jawfish on 2008-01-10
On Gutsy connecting to a remote CentOS5.1 box I got the same "connection reset by peer" error.

In my case the problem was resolved after I **deleted both the keys for the CentOS box ( ip and hostname) from my known-hosts file, and let the sshfs command get a key and write it to the known-hosts file.**

Oddly, Dolphin was able to make a fish:  ssh share to the same location all along. ( but my editor has a bug that makes this very convenient Dolphin technique unusable ) And I had ssh sessions also connected to the CentOS box.

Conclusion: using both the IP and hostname to connect may have confused sshfs ( should behave like ssh, but....) or maybe Dolphin created an extra key.

---

### Post by snobel on 2008-01-31
I am using ssh with RSA keys. When I tried sshfs I also got the "connection reset by peer". In my case It was solved like this:
```

$ sudo chgrp fuse <mountpoint>
$ sudo chmod g+w <mountpoint>
$ sudo adduser <user> fuse

```
After logging out/in I can use the sshfs command without sudo.

---

### Post by Balachmar on 2008-09-29
Hi,

I want to mount an sshfs fs to /home/user/share instead of /share
However putting /home/user in the master file and share in the ssh file
Makes all directories in /home/user disappear!
They return after a reboot without the automounting.

I have it currently mounted to /home/user/share/share
with /home/user/share in the master and share in the ssh config file. However that is not as I really would like it.
What should do configuration files look like if I want it like described above?

---

### Post by bodhi.zazen on 2008-09-29
> **Balachmar said:**
> Hi,

I want to mount an sshfs fs to /home/user/share instead of /share
However putting /home/user in the master file and share in the ssh file
Makes all directories in /home/user disappear!
They return after a reboot without the automounting.

I have it currently mounted to /home/user/share/share
with /home/user/share in the master and share in the ssh config file. However that is not as I really would like it.
What should do configuration files look like if I want it like described above?

I am not sure if I am understanding you correctly, but you can not have two things mounted at the same place at the same time.

If you have a directory /foo and you put a file into it :

```
touch /foo/test_file
```

now you see your test_file when you ls /foo

Now mount a hard drive in /foo

sudo mount /dev/sda1 /foo

no more test test_file as /foo now holds the contents of /dev/sda1

Now unmount /dev/sda1

sudo umount /foo

and test_file is back ;)

With sshfs, you unmount not with umount but by killing the ssh connection.

```
pkill ssh
```

So, yes, you need a unique directory to mount your sshfs share or mount it at /home (and move the contents of /home/user to the sshfs share).

---

### Post by Balachmar on 2008-09-29
I just want to mount it to /home/user/share
This directory is currently there but empty.
But I don't know how to do it using autofs. It works fine when I do it manually.
I did, however, succeed in mounting it on /home/user/share/share.
But that is not what I want.
So my question is, what should the auto.master and auto.ssh look like, to do just that?

---

### Post by mfleonhardt on 2008-10-05
Hello, I'm also having a problem here.  I've tried to /etc/rc6.d/K19autofs, but I still get nothing in /var/log/syslog when I restart autofs.

Anyway, maybe someone can check my syntax here and tell me what I'm doing wrong.

```
root@hp:/# cat /etc/auto.master | grep home
export  /etc/auto.home  -v --ghost --timeout=3600

```

```
root@hp:/# cat /etc/auto.home
alison  -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,reconnect,uid=1000,gid=1000,maxread=65536 :sshfs\#alison@family\:/home/alison
matt  -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,reconnect,uid=1001,gid=1001,maxread=65536 :sshfs\#matt@family\:/home/matt

```

Here's what the /export directory looks like before automount and after
```
root@hp:/# ls -al /export/*
/export/alison:
total 8
drwxr-xr-x 2 alison alison 4096 Oct  5 10:21 .
drwxr-xr-x 4 root   root   4096 Oct  5 10:56 ..

/export/matt:
total 8
drwr-xr-x 2 matt matt 4096 Oct  5 10:21 .
drwr-xr-x 4 root root 4096 Oct 5 10:56 ..
root@hp:/# /etc/init.d/autofs start
Starting automounter: done.
root@hp:/# ls -al /export/*
ls: cannot open directory /export/alison: No such file or directory
ls: cannot open directory /export/matt: No such file or directory

```

It seems that autofs is reserving /export but the individual sshfs mounts in auto.home are failing.  Of course, I'm not getting an error message, so I don't know why.

I think the RSA keys are set up okay, because I can do the following with no password prompt:
```
root@hp:/# /etc/init.d/autofs stop
Stopping automounter: done.
root@hp:/# sshfs matt@family:/home/matt /export/matt
root@hp:/# ls -l /export/matt
total 32
drwxr-xr-x 1 matt matt 4096 Oct  4 20:17 Desktop

[snip]

root@hp:/# fusermount -u /export/matt
root@hp:/# su matt
matt@hp:/$ sshfs matt@family:/home/matt /export/matt
matt@hp:/$ ls -l /export/matt
total 32
drwxr-xr-x 1 matt matt 4096 Oct  4 20:17 Desktop

```

Ideally, I'd like to set the two user's home directory to /export/username so that we have identical sessions and "local" files regardless of which computer we're on.

Any clues?

Thanks,
Matt

---

### Post by lxcypp on 2008-10-11
You must ensure your /etc/auto.home has 644 (none x) attribute.
Otherwise autofs will not work!

> **mfleonhardt said:**
> Hello, I'm also having a problem here.  I've tried to /etc/rc6.d/K19autofs, but I still get nothing in /var/log/syslog when I restart autofs.

Anyway, maybe someone can check my syntax here and tell me what I'm doing wrong.

```
root@hp:/# cat /etc/auto.master | grep home
export  /etc/auto.home  -v --ghost --timeout=3600

```

```
root@hp:/# cat /etc/auto.home
alison  -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,reconnect,uid=1000,gid=1000,maxread=65536 :sshfs\#alison@family\:/home/alison
matt  -fstype=fuse,port=22,rw,nodev,nonempty,noatime,allow_other,reconnect,uid=1001,gid=1001,maxread=65536 :sshfs\#matt@family\:/home/matt

```

Here's what the /export directory looks like before automount and after
```
root@hp:/# ls -al /export/*
/export/alison:
total 8
drwxr-xr-x 2 alison alison 4096 Oct  5 10:21 .
drwxr-xr-x 4 root   root   4096 Oct  5 10:56 ..

/export/matt:
total 8
drwr-xr-x 2 matt matt 4096 Oct  5 10:21 .
drwr-xr-x 4 root root 4096 Oct 5 10:56 ..
root@hp:/# /etc/init.d/autofs start
Starting automounter: done.
root@hp:/# ls -al /export/*
ls: cannot open directory /export/alison: No such file or directory
ls: cannot open directory /export/matt: No such file or directory

```

It seems that autofs is reserving /export but the individual sshfs mounts in auto.home are failing.  Of course, I'm not getting an error message, so I don't know why.

I think the RSA keys are set up okay, because I can do the following with no password prompt:
```
root@hp:/# /etc/init.d/autofs stop
Stopping automounter: done.
root@hp:/# sshfs matt@family:/home/matt /export/matt
root@hp:/# ls -l /export/matt
total 32
drwxr-xr-x 1 matt matt 4096 Oct  4 20:17 Desktop

[snip]

root@hp:/# fusermount -u /export/matt
root@hp:/# su matt
matt@hp:/$ sshfs matt@family:/home/matt /export/matt
matt@hp:/$ ls -l /export/matt
total 32
drwxr-xr-x 1 matt matt 4096 Oct  4 20:17 Desktop

```

Ideally, I'd like to set the two user's home directory to /export/username so that we have identical sessions and "local" files regardless of which computer we're on.

Any clues?

Thanks,
Matt

---

### Post by mfleonhardt on 2008-10-12
> **lxcypp said:**
> You must ensure your /etc/auto.home has 644 (none x) attribute.
Otherwise autofs will not work!

lxcypp,

Thanks for your reply.  Unfortunately, the screen on the laptop in question just died, so I gotta work that out first...but I'll check those permissions when I get my screen issue resolved and post back here.

Matt

---

### Post by mailforbiz on 2008-10-31
Hi

Nice guide, thanks for the how-to!

I am running into issues while setting up the passwordless mount to remote systgem. Here is my scenario:

Host A: my laptop with login userA (who is a sudoer)
Host B: remote ssh server with login userB which is to be mounted

After playing around a bit, I was able to do passwordless ssh login onto Host B as userA. For that to work, I had to make my home directory on Host B to have permission 700.

So this works passwordless:

```
ssh userB@HostB
```

But this doesn't:

```
sudo ssh userB@HostB
userB@HostB's password: 
```
Also, sshfs command doesn't work passwordless.

I don't have root permissions on HostB and I don't think its setup with sudo. 

Any pointers as to what's going on or what I should check?

Thanks in advance!
HT

---

### Post by acwojie on 2008-10-31
OK good go go [img]http://www.m516.cn/photo/q200762073753.jpg[/img]---------------------------------------------------------------------------------------------------------------[&#25490;&#27745;&#27893;](http://www.tpypump.com/pwb.html) [&#31163;&#24515;&#27893;](http://www.tpypump.com/lxb.html) [&#21270;&#24037;&#27893;](http://www.tpypump.com/huagongbeng.html) [&#33180;&#32467;&#26500;](http://www.lalamo.net)

---

### Post by mfleonhardt on 2008-10-31
> **mailforbiz said:**
> 
Any pointers as to what's going on or what I should check?

Thanks in advance!
HT

HT

You can see exactly how it's trying to authenticate by using ssh's verbose flag (-v)

Here's mine

```
[ matt:~ ] ssh -v family
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to family [192.168.0.10] port 22.
debug1: Connection established.
debug1: identity file /Users/matt/.ssh/identity type -1
debug1: identity file /Users/matt/.ssh/id_rsa type 1
debug1: identity file /Users/matt/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'family' is known and matches the RSA host key.
debug1: Found key in /Users/matt/.ssh/known_hosts:14
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/matt/.ssh/identity
debug1: Offering public key: /Users/matt/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
```

and with sudo:

```
[ matt:~ ] sudo ssh -v matt@family
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to family [192.168.0.10] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /var/root/.ssh/identity type -1
debug1: identity file /var/root/.ssh/id_rsa type -1
debug1: identity file /var/root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'family' is known and matches the RSA host key.
debug1: Found key in /var/root/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /var/root/.ssh/identity
debug1: Trying private key: /var/root/.ssh/id_rsa
debug1: Trying private key: /var/root/.ssh/id_dsa
debug1: Next authentication method: password
matt@family's password: 
```

As you can see, it's looking for public keys in root's home (local root, not the machine you're connecting to).   I tried a couple of variations...copying root's id_rsa to the host machine's authorized_keys, copying matt's id_rsa to root's .ssh/ dir...but I couldn't accomplish what you're trying to do.  Maybe someone out there has the answer.

Matt

---

### Post by mailforbiz on 2008-11-03
mfleonhardt,

Thanks for your response. For me the trace runs like this -
```

debug1: Trying private key: /home/met/.ssh/identity
debug1: Trying private key: /home/met/.ssh/id_dsa
debug1: Next authentication method: password

```

I am beginning to think this has something to do with how my account is setup on the server. I'll find out more and post.

HT

---

### Post by mailforbiz on 2008-11-03
Ok, so i was able to persuade the administrator to set me up as a sudoer. Afterwards, I was able to do both 
```
ssh userB@hostB

```

and 
```
sudo ssh userB@hostB

```

and no password was required. But now I have problems with the sshfs mount as sudo.

For one, the remote home directory shows up like this in ls
```

%ls
d?????????  ? ?    ?       ?                ? remote


```
And I can not cd to it. 

If I do just sshfs instead of sudo sshfs
```

% sshfs userB@hostB:/home/userB /home/userA/remote
fuse: invalid argument `userB@hostB:/home/userB'

```

At this point, I'm stuck. Any ideas?

Thanks in advance!

> **mailforbiz said:**
> mfleonhardt,

Thanks for your response. For me the trace runs like this -
```

debug1: Trying private key: /home/met/.ssh/identity
debug1: Trying private key: /home/met/.ssh/id_dsa
debug1: Next authentication method: password

```

I am beginning to think this has something to do with how my account is setup on the server. I'll find out more and post.

HT

> **mailforbiz said:**
> Hi

Nice guide, thanks for the how-to!

I am running into issues while setting up the passwordless mount to remote systgem. Here is my scenario:

Host A: my laptop with login userA (who is a sudoer)
Host B: remote ssh server with login userB which is to be mounted

After playing around a bit, I was able to do passwordless ssh login onto Host B as userA. For that to work, I had to make my home directory on Host B to have permission 700.

So this works passwordless:

```
ssh userB@HostB
```

But this doesn't:

```
sudo ssh userB@HostB
userB@HostB's password: 
```
Also, sshfs command doesn't work passwordless.

I don't have root permissions on HostB and I don't think its setup with sudo. 

Any pointers as to what's going on or what I should check?

Thanks in advance!
HT

---

### Post by scaine on 2008-11-13
> **gaupe said:**
> I have no experience with sleep > ( is that suspend or hibernate mode ? )
mode i would think since its an automounter it would mount by itself again... but havent tried.

I'm working on exactly that problem now.  I believe that there's an ACPI switch that you can add to specify modules that should unload before the suspend (they're automatically restarted on resume).  Once I fix this, I'll post here.  AutoFS is preventing my EEE from entering resume at all!

> **gaupe said:**
> in the auto.master there is a timeout which automaticly dismounts allready if no activity.

(this means allso if you have a fle browser open on it but not actively browsing it will dismount and your filebrowser is falling back to the rootdir (ncie if you drag files to it afterwards thinking it is still on the automount) I havent yet found out how to prevent that....

Set your timeout to zero in your auto.master file to prevent autofs from unmounting the shares specified.  This prevents it constantly (every 5 mins or whatever your timeout is) rebuilding the mount point.  I think my use of a zero timeout is what is preventing my laptop from sleeping though!

Like I say, I'll post back once I figure a solution.  Also worth noting that I'm using autofs5 from the Intrepid repos - there didn't seem to be any reason not to, since the autofs website claimed that it close to releasing the new version anyway.  However, again, I wonder if the v5 is what is causing my suspend issue...

---

### Post by scaine on 2008-11-14
Well, after lots of googling and searching bug trackers on Debian and Ubuntu, I found... nothing.

So I started to experiment with autofs and struck paydirt on the first try - a timeout of zero means that autofs will never unmount the volume.  So if you intend to use autofs on a laptop or PC that CAN suspend, make sure you use a --timeout=360 or --timeout=3600 value.

Side note - does it annoy you that the screen locks every time you resume from suspend?  There's a gconf-key that controls this - start gconf-editor, then choose apps/gnome-power-manager/lock.  In there, tick the boxes appropriately.  There's a nice option to use locking only when it's ticked in gnome-screensaver for instance.

---

### Post by gilrim on 2009-11-05
Thanks for the guide!

I've been trying to set this up so it would mount a ssh server to /home/gilrim/hostname, such that doing ls ~/hostname would list the contents of the server. following the instructions above, I'd have to do ls ~/hostname/hostname to see the contents.
So I tried setting up the /etc/auto.master to have /home/gilrim as the first parameter, expecting autofs to create the hostname directory in my homedir, per parameter in /etc/auto.ssh. but alas, this is what I got in my syslog:
```

Nov  5 21:08:12 stua automount[20942]: starting automounter version 4.1.4, path = /home/gilrim, maptype = file, mapname = /etc/auto.ssh
Nov  5 21:08:12 stua automount[20942]: mount_autofs: already mounted
Nov  5 21:08:12 stua automount[20942]: /home/gilrim: mount failed!

```

now, I didn't want to type the hostname twice when accessing it, so I changed auto.master to a single "r" as the parameter.. So now I've got it running, but I'm curious to what's preventing me from using my home directory as the first mountpoint?
could it be because I'm using the encrypted-homefolder-thingie? this is my mount:
```
gilrim@stua:~$ mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/gilrim/.Private on /home/gilrim type ecryptfs (ecryptfs_sig=ac395b4351361084,ecryptfs_fnek_sig=e97fbd44ef0f6537,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
automount(pid21455) on /home/gilrim/r type autofs (rw,fd=5,pgrp=21455,minproto=2,maxproto=4)
user@hostname:/mnt/HD_a2/ on /home/gilrim/r/hostname type fuse.sshfs (rw,nosuid,nodev,noatime,max_read=65536,allow_other)

```

---

### Post by scaine on 2009-11-06
Automount has to create the directory you specify in auto.master - there's no way round this, I think.  Basically, you're asking it to mount something that already exists, so it's not happy.

Just tell it to mount in /smb or /net like default, then symbolically link the server object from there to the directory you want in your home directory.  I personally would do this by dragging the object out of /smb to my home directory while holding down shift and control, but you can do with the command line too :
```
ln -s /smb/servername /home/yourname/servername

```Good luck.

---

