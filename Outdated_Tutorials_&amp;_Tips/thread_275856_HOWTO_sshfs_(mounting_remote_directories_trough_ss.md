---
title: "HOWTO: sshfs (mounting remote directories trough ssh)"
date: 2006-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by crazymonkey on 2006-10-12
sshfs is a good way to easily mount folders from a remote host that you can access trough ssh. This tutorial assumes that you have openssh installed on the server. (Easy way: sudo apt-get install openssh-server)

On the client you will have to install sshfs and its dependencies (fuse-utils and libfuse2)
```
sudo apt-get install sshfs
```

Now load the fuse module :
```
sudo modprobe fuse
```

Create the directory where the share is to be mounted :
```
mkdir /home/user/local/mountpoint
```
*Of course change the path to fit your needs

You are now ready to mount the share :
```
sudo sshfs username@IPorHOSTNAME:/remote/folder/to/mount /home/user/local/mountpoint
Ex: sshfs bobbrown@bobserver.net:/home/bob /mnt/bobshome
```

Now you can use the remote directory as if it was local!

If you get an error saying : > fusermount: failed to open /dev/fuse: permission denied
adding your user to the fuse group should solve the issue.

```
sudo addgroup yourusername fuse
```

**Additional recommended step**
These steps are not required to make sshfs work but are recommended if you plan on using sshfs alot and will save you some time.

*Add the fuse module to /etc/modules*
```
sudo gedit /etc/modules
```
add fuse at the bottom of the list, this will load the fuse module each time you boot.

*Change permissions of fusermount*
```
sudo chmod +x /usr/bin/fusermount
```
Once this is done you wont need to use sudo to mount directories using sshfs.

There is also the possibility to mount the share when you boot using /etc/fstab but I'm not sure how to do it yet.

---

### Post by MighMoS on 2006-10-15
Is there a way to have this do port forwarding as well?

---

### Post by capitalistpiglet on 2006-10-25
It took me a while to work it out but finally i found a way to automount sshfs on startup so ill share it here.

first of all you need to create a public/private key pair for the server your logging into so you dont have to use a password. 
```

ssh-keygen -t rsa

```
Just keep hitting return you dont have to wory about any of the options.
then cd to the ssh directory
```

cd ~/.ssh

```
if there is authorized_keys file already in the .ssh directory back it up.
```

cp authorized_keys authorized_keys$

```
then 
```
cat *.pub >> authorized_keys
```
Then  copy the auhorized_keys to the ~/.ssh directory of the server and you can then ssh in without a password.
once that is done you can create a simple script in your ~/.kde/Autostart directory to mount it all when you login. (not sure where the autostart directory is in gnome)

```

!/bin/bash
 # mount sshfs drive
sshfs 192.168.1.101:/directory /mnt/to/whereever

```
then make the script executable
```

chmod a+x nameofscript

```
And your done.
I hope this helps someone.

---

### Post by rune_kg on 2006-11-03
Hey man

Great howto thx. Worked out of the box on both dapper and breezy for me. Did anyone compare speed and responsiveness with openvpn solutions???

CYA
Rune Kaagaard
[http://rune@runelyd.dk](http://rune@runelyd.dk)

---

### Post by jetpeach on 2006-11-05
Thanks for the howto.
One question: I'm trying to get write access to my sshfs fuse mounted directories. but even using -o uid=[group id e.g.1000] which mounts it with my user id, i still can't write to the shares *unless i am root*.

So I thought it might be a fuse permissions thing and added myself to the fuse group as you said, and then changed the permissions as you suggested.  But I still can't mount shared without sudo first, without sudo i still get
fuse: failed to exec fusermount: Permission denied
 - any thoughts on this? Were others able to mount all your shares without sudo and do they then get mounted with the correct permissions such that you can write to them?  I checked that I am in the fuse group in the control panels (I am) and that the group on /dev/fuse and /usr/bin/fusermount is fuse and is executable.

Thanks!
jet

EDIT: all that and it seems at least the problem with permissions simply required a reboot - probably to load the fuse modules with the new permissions....  But still I can't write to the directories - the permissions say they're all mine and writable but they aren't.

EDIT: more info, i found it interesting the difference I get now that I'm adding it under my account, it seems it's not a permissions but that it's not allowing the "operation???"
jet@ubuntu:~/rsync$ sudo mkdir asdf
mkdir: cannot create directory `asdf': Permission denied
jet@ubuntu:~/rsync$ mkdir asdf
mkdir: cannot create directory `asdf': Operation not permitted

---

### Post by ner0tic on 2006-11-21
i'm having a strange issue...

> ner0tic@blackhawk:/mnt$ rm vendetta 
rm: cannot remove `vendetta': Is a directory
ner0tic@blackhawk:/mnt$ rm -r vendetta
rm: cannot lstat `vendetta': Permission denied
ner0tic@blackhawk:/mnt$ sudo rm -r vendetta
rm: cannot lstat `vendetta': No such file or directory
ner0tic@blackhawk:/mnt$ mkdir vendetta
mkdir: cannot create directory `vendetta': File exists


this is my sshfs mount point. i followed the steps and it all looked good but i can't access it nor remove it. it acts as if it's not there when it is

---

### Post by jetpeach on 2006-11-22
i think the problem is even sudo doesn't have permission to remove your mountpoint until after it is unmounted (it is currently mounted when you tried to remove it?).  try 
sudo umount /mnt/vendetta 
after that you should be able to remove it with sudo rm etc...

---

### Post by jis on 2006-12-01
> **crazymonkey said:**
> 
*Change permissions of fusermount*
```
sudo chmod +x /usr/bin/fusermount
```
Once this is done you wont need to use sudo to mount directories using sshfs.


Now 
```
ls -l /usr/bin/fusermount
``` outputs 
> -rwsr-xr-x 1 root fuse 18328 2006-05-11 20:45 /usr/bin/fusermount


Then I try to mount using sshfs without sudo, and first it asks password, but after I return it, I get 
> fusermount: user has no write access to mountpoint /media/kielo


So it did not help. However, if I change permissions of my mountpoint like this ```
sudo chmod a+w /media/kielo
```, I can mount the directory by sshfs without using sudo.

---

### Post by jetpeach on 2006-12-04
jis, this behavior makes sense to me at least.  the normal user can't write to /media/kielo so a normal user can't mount something there either unless the permissions of it are changed.

your solutions of changing the permissions of /media/kielo is fine (though i wouldn't make it all writable, just change the ownership or something, all isn't good practice for security) or, as i do, just use a mount point in your users home directory, something like /home/yourUsername/kielo (make the directory first of course). then it's just like any other folder in your home directory and you'll be able to mount there.

of course, i haven't been able to fix the write problems after mounting that i've described above still.

---

### Post by jis on 2006-12-04
jetpeach, I had have the same permissions drwxr-xr-x for /media/floppy than for /media/kielo before and I can mount /media/floppy for writing but could not mount /media/kielo with sshfs. Mount program did change the ownership of /media/floppy from root to my current local user account. When I later changed permissions of /media/kielo as described before, and then mounted by sshfs, it changed ownership to some number and permissions to drwx--x--x .

I don't know if there is any advantage of using a mount point in /home. How could an attacker use unmounted /media/kielo? (If the mount point is not empty, sshfs outputs
> fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option

and does not mount there.) But anyway using mount point in /home is not less safe for sure, so thanks for the hint.

---

### Post by bodhi.zazen on 2006-12-06
Nice How-to

This thread has been added to the UDSF wiki.

[Sshfs](http://doc.gwos.org/index.php/Sshfs)

---

### Post by will m. on 2007-02-02
Hello!

I realize this is an older post but I am hoping you might be able to clarify something.

First, thank you so much for the instructions!  They seems to be working, all the necessary modules for SSHFS are installed, I seem to be talking to the SFTP remote site. However, when I input these the response I get is

ubunutu_username@remotehost's password:

I expect to be required to provide my remotehost username and password (Windows Active Directory) but it seems that SSHFS is using my Ubuntu login and password and assuming that some match exists on the remotehost. Is there something I can do to specify the difference between the two of these?

I'm so close to being able to sync up my files remotely! I've really looked around, spoken with my workplace's network admin and found that the support that SSHFS provides is what I need (I think ; )).

Does you know how to clarify this problem?

Thanks,

Will M.

---

### Post by crazymonkey on 2007-02-07
Make sure you use the command this way : sshfs remoteusername@remotehost:/etc/etc /mnt/etc

Everythings should work fine this way. However i'm not sure of the way this interacts with AD...

---

### Post by joshkidd on 2007-02-07
Also, it's worth noting since I had some trouble with this today.  sshfs doesn't know how to deal with ~ in the remote path name.  e.g. I was trying to mount with a command something like this:

```
sshfs user@remotehost.com:~/files /mnt/files
```

Which was making the directory show up like this in ls -l:

```
?————– ? ? ? ? ? files
```

Using the full path, however, works:

```
sshfs user@remotehost.com:/home/user/files /mnt/files
```

It's just a little thing that might be important to note in a HowTo.

---

### Post by snowboard975 on 2007-02-27
I had an error as follows when I tried to save a file in gedit to the sshfs mount position.
"Could not save the file XYZ... Could not create a backup file"

I googled it and found the following solution from [http://www.arcknowledge.com/gmane.comp.file-systems.fuse.sshfs/2006-03/msg00018.html](http://www.arcknowledge.com/gmane.comp.file-systems.fuse.sshfs/2006-03/msg00018.html)

```
sshfs myuserid@xxx.xxx.xxx.xxx:/ /my_mount_directory -o workaround=rename
```

---

### Post by svh on 2007-03-29
I have been using sshfs for some time and found it a really useful tool. The only problem has been remembering to type the sshfs ...  command each time I log in so that I can access the directory I am after.  Thanks to this thread I have just set up an fstab entry automate the mounting process as follows:

sshfs#steven@mfg:/home/steven   /home/steven/steven-mfg  fuse   users,noauto    0       0

I have set up an ssh rsa key so that I can connect to mfg with no password and put the following in my .bashrc:

mount /home/steven/steven-mfgpro

It is working well and I can access the files in my home directory on mfg.  However, whenever I open a new terminal screen on the machine from which I am making the sshfs connection I get the following error:

fusermount: failed to access mountpoint /home/steven/steven-mfg: Permission denied

However, I can access the directory and everything seems to be working.

Any suggestions as to what might be causing this error.

Thanks and regards
Steven

---

### Post by Darwin Award Winner on 2007-05-02
Your .bashrc file is executed every time you open a termnial. So every time except the first, the sshfs mount will already be mounted. I believe that trying to mount on top of an existing mount would give you a permission denied error. What you want to do is check if it's already mounted, and if not, then mount it
Try this:
```
if grep /home/steven/steven-mfgpro /etc/mtab &>/dev/null; then true; else mount /home/steven/steven-mfgpro &; fi
```

Also, I've written a howto for completely automatic sshfs mounting. You can find it here: [SSHFS Automount on Feisty]("http://ubuntuforums.org/showthread.php?t=430312")

---

### Post by arkangel on 2007-05-04
One question more  related to the  key generation for ssh .

On the client side I generated  an authorized_keys file. 
From the client i want to connect to the server using 2 (or +) users .  So I  copied the authorized_keys (generated on the client side ) on each .ssh directory (in the server)  of all acounts i want to login.

I can login into the first accout  using ssh (which is the admin or first user ubuntu user)  when i try to login into the second account  it still  asks for the password ,  any idea  what could be  wrong ?

---

### Post by skelooth on 2007-05-04
```
pa817927@lilith:~$ sshfs pa817927@netregdev.itsli.albany.edu:/ /mnt/dev
pa817927@netregdev.itsli.albany.edu's password: 
reply len too large: 1315271794
```


I am receiving this error when I try to follow these instructions.

I used to connect using "connect to server" and I've been doing it that way all semester long. Now suddenly Nautilus refuses to do it. If I try connecting manually in nautilus it says unable to connect try another viewer. Yet I can connect to ssh just fine through the terminal!

I don't know why it magically stopped working, but I need to be able to access this machine for work purposes, and nothing is working. (gftp in ssh mode will not connect either)

Edit: Deleting my bashrc file fixed the problem.... the guy who told me to do it doesn't even know why.

---

### Post by durus on 2007-05-30
Thanks for the tutorial I have done the steps below but i can't get it to work. I do not know if my school has openssh installed but i assume that they have it if i can use putty with ssh and ssh "ftp" apps in windows to get access to my folder. When i do this steps, i still have mount available when i use ls, but i can't use cd mount, and if i use a file browser it do say "unknown file type". Can you see some steps that i have forgotten or are doing the wrong way ?

```
sudo apt-get install sshfs
sudo modprobe fuse

mkdir /home/durus/mount

sudo sshfs username@my.nada.kth.se:/afs/nada.kth.se/home/2/usename /home/durus/mount
```

---

### Post by Darwin Award Winner on 2007-05-31
> **durus said:**
> Thanks for the tutorial I have done the steps below but i can't get it to work. I do not know if my school has openssh installed but i assume that they have it if i can use putty with ssh and ssh "ftp" apps in windows to get access to my folder. When i do this steps, i still have mount available when i use ls, but i can't use cd mount, and if i use a file browser it do say "unknown file type". Can you see some steps that i have forgotten or are doing the wrong way ?

```
sudo apt-get install sshfs
sudo modprobe fuse

mkdir /home/durus/mount

sudo sshfs username@my.nada.kth.se:/afs/nada.kth.se/home/2/usename /home/durus/mount
```

You're not meant to use sudo with sshfs. Sshfs is a module for FUSE, with stands for filesystem in userspace, so you don't need to be an admin to use it. Using sudo to run the command could cause the mount to be accessible only to root. However, to use fuse filesystems as a user, you do have to add yourself to a particular group, called plugdev. You can do this from System -> Administration -> Users and Groups, or by running gksu users-admin. then mounting without sudo.

---

### Post by TomFumb on 2007-06-04
Sorry if this is a dumb question, but it's been bugging me for some time - how do I unmount an sshfs mounted directory? 

At the moment I have to restart, which is no fun


cheers for the howto, very useful.

---

### Post by Laterix on 2007-06-04
I still can't mount as a normal user. With sudo it works, but without I get this error:
```

fusermount: mount failed: Operation not permitted

```
I have added my user to fuse group and changed fusermount permissions
```

-rwxrwxr-x 1 root fuse 19456 2007-03-13 00:34 /usr/bin/fusermount*

```
Any ideas?

---

### Post by Darwin Award Winner on 2007-06-04
> **TomFumb said:**
> Sorry if this is a dumb question, but it's been bugging me for some time - how do I unmount an sshfs mounted directory? 

At the moment I have to restart, which is no fun


cheers for the howto, very useful.

Any fuse filesystem can be unmounted with "fusermount -u [mountpoint]" if you have the permissions to do so. Any filesystem can be unmounted with "sudo umount [mountpoint]". If the filesystem says that it's busy, try "sudo umount -l [mountpoint]".

---

### Post by TomFumb on 2007-06-05
Thanks for replying about unmounting, but unfortunately this is all I get

   tom@x22:~$ fusermount -u /home/tom/GIS/cgi_bin
   fusermount: entry for /home/tom/GIS/cgi_bin not found in /etc/mtab

any suggestions? To mount I am typing 

   sshfs username@server:/home/username/cgi_bin /home/tom/GIS/cgi_bin

am I trying to unmount the wrong location?


thanks

---

### Post by Darwin Award Winner on 2007-06-06
/etc/mtab is a listing of all currently mounted filesystems. Look in that file for the mount point that you are trying to unmount. If it is not in there, then something odd is going on.

---

### Post by yang on 2007-06-17
Everything went smoothly for me, from install through mount, except that I cannot access the mount as anyone but root:

```

$ sudo sshfs -p 8822 yangzhang@localhost:/ /mnt/google/

$  ls -l /mnt/
total 4
drwxr-xr-x 2 root root 4096 2007-04-13 23:28 home
?--------- ? ?    ?       ?                ? /mnt/google

$ sudo ls -l /mnt/
total 8
drwxr-xr-x 1 root root 4096 2007-06-04 23:03 google
drwxr-xr-x 2 root root 4096 2007-04-13 23:28 home

$ ls -l /mnt/google
ls: /mnt/google: Permission denied

$ sudo ls -l /mnt/google/
total 212
drwxr-xr-x 1 root  root     0 2007-06-16 23:25 auto
drwxr-xr-x 1 root  root  4096 2007-05-31 12:05 bin
...

```

Any ideas? Thanks in advance.

---

### Post by DeamonAxe on 2007-09-25
Hi have the same problem, did somebody found a solution?

I'm on Feisty...

---

### Post by DeamonAxe on 2007-09-25
Ok, I found it, I simply create the file /etc/fuse.conf

and in the file I wrote
user_allow_other

([as stated in this post]("http://ubuntuforums.org/showthread.php?t=430312"))

Then save it, restart (might have been and other solution, but I don't know it).

Then the instruction
mount /yourlocaldirectoryasinthefstabfile

And everything works...

---

### Post by Darwin Award Winner on 2007-09-27
Sorry, everyone, I temporarily lost track of the email account that I use to receive notifications of replies on this forum, so I neglected to reply. I have developed a better script that should work when run as either root or as a user. When run as root, it will try to mount all the sshfs filesystems listed in fstab. As a user, it will only try to mount the ones with your user id. In either case, it now works in parallel, meaning that you don't have to wait for one filesystem to finish mounting before the next starts. I'll try to update the scripts on this page this weekend.

---

### Post by Scotty562 on 2007-10-01
Everything works great for me, but if I don't use the mounted share for a while it disappears or times out. Once this happens I'm forced to mount the shares again. Is there a way to keep this from happening?

---

### Post by bodhi.zazen on 2007-10-01
You need to configure /etc/ssh/sshd_config (on server) and /etc/ssh/ssh_config (on the client)

> IdleTimeout time
    Sets idle timeout limit to time in seconds (s or nothing afternumber), in minutes (m), in hours (h), in days (d), or in weeks (w).If the connection have been idle (all channels) for that long time thechild process is killed with SIGHUP, and connection is closed down.

Try these settings :

```
TCPKeepAlive yes
ClientAliveInterval 30
ClientAliveCountMax 99999
```

You may be able to increase the ClientAliveInterval: 

ClientAliveInterval 120

---

### Post by thatt on 2007-10-03
Hi guys and gals,

some basic info first:
server - headless running ubuntu edgy desktop version (i need the gui due to laziness :-) )
client - laptop running ubuntu feisty

I've followed the instruction above on how to setup SSHFS - installing sshfs on the client machine, add myself to fuse group and add execute permission to fusermount, create the local mount point and log out and log back in, modprobe fuse and then used the command

```
sshfs username@dyndns_server_url:/media/storage/Media/Videos /home/username/local_mount -p 43211
```

it looks like it gets mounted correctly (no error message pops up so i guess it's correct) but when i try to access the folder through Nautilus, i can't find it. I can see it in the terminal and when i cd into it and do ls, it said permission denied.

thinking that this might be a server issue, i looked through auth.log and saw a message for 

```
subsystem request for sftp
```

and when i look at sshd_config i see the line

```
Subsystem sftp /usr/lib/openssh/sftp-server
```

but browsing to openssh directory, I don't seem to have sftp-server.

My question is
[LIST=1]
[*]Am I on the correct path to assume that I need to install the sftp-server?
[*]I thought that sshfs uses scp as oppose to sftp, am i wrong?
[*]If i install sftp, will it automatically tunnel over the open sshfs connection or will i have to setup a seperate portforwarding on the firewall?
[*] Am i using a diffent openssh server than what the how-to poster is using?
[/LIST]

Somebody out there that can help please? Thanks

Updated:
Found the answer to my own question, if the remote folder belongs to another user, the remote folder's permission must be read & write to everyone or the local mount point will act all screwy. I don't think this is good practice security wise (opening the folder to everyone) but it'll works since all I need to do is use it as a staging area for transferring file between the server and my local machine and then the folder will be empty.

---

### Post by Scotty562 on 2007-10-05
> **bodhi.zazen said:**
> You need to configure /etc/ssh/sshd_config (on server) and /etc/ssh/ssh_config (on the client)



Try these settings :

```
TCPKeepAlive yes
ClientAliveInterval 30
ClientAliveCountMax 99999
```

You may be able to increase the ClientAliveInterval: 

ClientAliveInterval 120

I added those lines and after I did I wasn't able to use ssh until I removed them. Is there another solution?

---

### Post by DannyW on 2007-10-06
I too am being disconnected after a period of time, and I don't have access to edit the servers sshd config so this method is not available for me.

Is there any way of maybe sending a simple command to the server at specified intervals just to keep the connection alive, or is there an easier way?

---

### Post by bodhi.zazen on 2007-10-06
Try adding this lilne to /etc/ssh/ssh_config (on the client):

> ServerAliveInterval 5

You may be able to increase this number to 120 or higher. This is how often you send a keep alive signal to your server in seconds, and  seems quite short to me :)

---

### Post by DannyW on 2007-10-06
> **bodhi.zazen said:**
> Try adding this lilne to /etc/ssh/ssh_config (on the client):



You may be able to increase this number to 120 or higher. This is how often you send a keep alive signal to your server in seconds, and  seems quite short to me :)

Thanks, this seems to be working fine!

=D>

---

### Post by BenjaminGTF on 2007-10-18
I had to restart (the client) for this to work. 

It should also be noted that I was mounting without sudo (as described in other post)

---

### Post by sbussy89 on 2007-10-18
i ran the command listed to install openssh in the very first post, but after it runs (successfully) i cant find it anywhere on my computer... where is it?  if i go to the package manager i can only select to reinstall or remove it, so it must be here somewhere, i just cant find it. (i am a former windows user who used ssh secure shell client to update a webpage, so i am looking to do the same thing through ubuntu. if i am doing this totally wrong or need a different program, let me know)

---

### Post by thejart on 2007-10-18
it's probably /usr/bin/ssh

'which ssh' should tell you, though.

---

### Post by thejart on 2007-10-18
one more thing for those who keep getting the 'failed to open /dev/fuse: Permission denied' error after adding the fuse group to your user (as i did).

> The shell from which you ran "sshfs" probably doesn't "know" that
you're in the fuse group.  Try logging out and logging back in; or if
that's too tedious, try "su - user" to get a new login.

In any case, you can check which groups you're currently in by running the "id" program (or groups).  If that program doesn't show "fuse" as one of theentries, sshfs won't work.

-eric hanchrow ([https://lists.ubuntu.com/archives/ubuntu-users/2006-June/080743.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-June/080743.html))

for those of you like me who don't like ruining your 72d 4h 20m of uptime, this is a life-saver.

---

### Post by JarrettBillingsley on 2007-10-18
> **joshkidd said:**
> Also, it's worth noting since I had some trouble with this today.  sshfs doesn't know how to deal with ~ in the remote path name.  e.g. I was trying to mount with a command something like this:

```
sshfs user@remotehost.com:~/files /mnt/files
```

Which was making the directory show up like this in ls -l:

```
?————– ? ? ? ? ? files
```

Using the full path, however, works:

```
sshfs user@remotehost.com:/home/user/files /mnt/files
```

It's just a little thing that might be important to note in a HowTo.

OMFG, I have been bashing my head against the wall trying to get sshfs working all day, this was exactly my issue and you fixed it.  Thank you so much.  This should DEFINITELY be mentioned in the FAQ.  In fact, why don't I put it there.

---

### Post by interim descriptor on 2008-04-27
For reference, I had to modify these scripts for this to work in Hardy Heron.

/etc/network/if-up.d/mountsshfs:
```

#!/bin/sh

## The script will attempt to mount any fstab entry with an option
## "...,comment=$SELECTED_STRING,..."
## Use this to select specific sshfs mounts rather than all of them.
SELECTED_STRING="sshfs"

# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

## define a number of useful functions

## returns true if input contains nothing but the digits 0-9, false otherwise
## so realy, more like isa_positive_integer 
isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

## returns true if the given uid or username is that of the current user
am_i () {
        [ "$1" = "`id -u`" ] || [ "$1" = "`id -un`" ]
}

## takes a username or uid and finds it in /etc/passwd
## echoes the name and returns true on success
## echoes nothing and returns false on failure 
user_from_uid () {
    if isa_number "$1"
    then
                # look for the corresponding name in /etc/passwd
        local IFS=":"
        while read name x uid the_rest
        do
                if [ "$1" = "$uid" ]
                        then
                                echo "$name"
                                return 0
                        fi
        done </etc/passwd
    else
        # look for the username in /etc/passwd
        if grep -q "^${1}:" /etc/passwd
        then
                echo "$1"
                return 0
        fi
    fi
    # if nothing was found, return false
        return 1
}

## Parses a string of comma-separated fstab options and finds out the 
## username/uid assigned within them. 
## echoes the found username/uid and returns true if found
## echoes "root" and returns false if none found
uid_from_fs_opts () {
        local uid=`echo $1 | egrep -o 'uid=[^,]+'`
        if [ -z "$uid" ]; then
                # no uid was specified, so default is root
                echo "root"
                return 1
        else
                # delete the "uid=" at the beginning
                uid_length=`expr length $uid - 3`
                uid=`expr substr $uid 5 $uid_length`
                echo $uid
                return 0
        fi
}

# unmount all shares first
sh "/etc/network/if-down.d/umountsshfs"

while read fs mp type opts dump pass extra
do
    # check validity of line
    #if [ -z "$pass" -o -n "$extra" -o "`expr substr ${fs}x 1 1`" = "#" ]; 
    if [ "`expr substr ${fs}x 1 1`" = "#" ];
    then
        # line is invalid or a comment, so skip it
        continue

    # check if the line is a selected line
    elif echo $opts | grep -q "comment=$SELECTED_STRING"; then

        # get the uid of the mount
        mp_uid=`uid_from_fs_opts $opts`

        if am_i "$mp_uid"; then
                        # current user owns the mount, so mount it normally
                        { sh -c "mount $mp" &&
                                echo "$mp mounted as current user (`id -un`)" ||
                                echo "$mp failed to mount as current user (`id -un`)";
                        } &
                elif am_i root; then
                        # running as root, so sudo mount as user
                        if isa_number "$mp_uid"; then
                                # sudo wants a "#" sign icon front of a numeric uid
                                mp_uid="#$mp_uid"
                        fi
                        { sudo -u "$mp_uid" sh -c "mount $mp" &&
                                echo "$mp mounted as $mp_uid" ||
                                echo "$mp failed to mount as $mp_uid";
                        } &
                else
                        # otherwise, don't try to mount another user's mount point
                        echo "Not attempting to mount $mp as other user $mp_uid"
                fi
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

wait


```

/etc/network/if-down.d/umountsshfs:
```

#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

# umount all sshfs mounts
mounted=`grep 'fuse.sshfs' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do fusermount -u $mount; done; }


```

These changes deal with the following issues:
[LIST]
[*]/etc/mtab sshfs entries don't start with "sshsf#", which breaks the umountsshfs script, as well as umount itself
[*]/etc/network/if-up.d/mountsshfs wasn't detecting my sshfs mounts in /etc/fstab
[/LIST]

So, if you're running Hardy Heron, try these scripts if the originals don't work.

---

### Post by ericdegen on 2008-05-09
So I've used sshfs for connecting between my Gutsy systems for a while now, but since installing a couple of new hardy systems I can not connect to them.

Is there anything new in apparmour or some other default I need to enable on the sshfs server side?

Thanks!

---

### Post by Darwin Award Winner on 2008-05-09
If you mean you are having trouble connecting to Hardy servers from a Gutsy client, I'm not sure what the problem would be, because that is exactly my setup right now, and it works fine. As soon as I update everything to Hardy, I'll take another look at this script and rework anything that needs reworking.

---

### Post by ericdegen on 2008-05-09
Correct, from the GUI (gnome) on a Gutsy box, I can not to ssh to a Hardy box. I've tried two Hardy boxes both have ssh and sshfs installed, and I can terminal ssh to them, just not file transfer.

---

### Post by ericdegen on 2008-05-09
Ok, never mind... my bad.

When I rebuilt these Hardy systems I gave them the same name (hostname) as before, but a new RSA key was generated that conflicted with the cached on in my known_hosts file.

When I cleared that out, gnome was all better. Funny though, how you don't get any error dialogue in the gui, but it is on the terminal.

Cheers,

---

### Post by robertmf on 2008-11-03
> **jis said:**
> Now 
```
ls -l /usr/bin/fusermount
``` outputs 


Then I try to mount using sshfs without sudo, and first it asks password, but after I return it, I get 


So it did not help. However, if I change permissions of my mountpoint like this ```
sudo chmod a+w /media/kielo
```, I can mount the directory by sshfs without using sudo.
[COLOR="DarkRed"]
Beginning with Ibex v8.10 fusermount is located in /bin

[/COLOR]

---

### Post by jegerjensen on 2009-12-02
> **crazymonkey said:**
> *Change permissions of fusermount*
```
sudo chmod +x /usr/bin/fusermount
```
Once this is done you wont need to use sudo to mount directories using sshfs.

That change is an unnecessary security risk and should be avoided.  The default permissions (on hardy) are:
```

[...]$ ls -l /bin/fusermount 
-rwsr-xr-- 1 root fuse 20056 2008-02-26 19:25 /bin/fusermount

```
which means that as long as the user belongs to the fuse group, you should be able to run fusermount without sudo.

If you want to setup a system wide mount point (in /mnt or /media for instance) and get the error 
```
fusermount: user has no write access to mountpoint
```
what you need is write permission to the mount point.  Enable that by 
```

[...]$ sudo chgrp fuse /path/to/mountpoint
[...]$ sudo chmod g+w /path/to/mountpoint

```
This will only give members of the fuse group write permission.  You generally want to be restrictive about permissions in system directories, so chmod a+w which was suggested in an earlier post is not optimal.

---

