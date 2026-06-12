---
title: "Setting up Ubuntu NAS"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by Tom Violence on 2013-07-03
Hi, I have just got myself an HP microserver to setup as a NAS to store and stream all my media files.  I decided on trying Ubuntu Server 12.04.2 LTS 64 bit as it seemed a popular choice of OS, however I am finding it hard going as this is my first attempt at linux, I have only ever used Windows before.
Here is where I am at.  I have followed a guide online to install ubuntu and webmin and have also managed to setup my static IP and that all seems to be working fine.  I can access my server through my Win7 pc using putty.  The problem I have hit is that I can't seem to get samba shares working.  I followed this guide [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) pointing the share to my media folder, but nothing seems to have happened.
Ideally I want to get it set up so that all devices in my home network can stream media from the server and eventually so that I can ftp files to and from the server from my main pc.
Any advice would be appreciated.
Thanks.

---

### Post by Thee on 2013-07-04
Instead of trying to get every feature of your NAS that you need working on Ubuntu server, I would suggest going with easier route, like [http://www.freenas.org/](http://www.freenas.org/) or simular projects.
It's an all in one solution without the headaches.

---

### Post by mastablasta on 2013-07-04
open media vault (debian based) is like freenas (in case you are not into BSD).

---

### Post by Tom Violence on 2013-07-05
Thanks but I think that slowly I am making some progress.  I setup a shared folder on my server and that now shows up when I go to my network places in Windows 7, however I cannot copy and paste my files from Windows to the shared folder as I get a popup message saying Destination Folder Access Denied "You need permission to perform this action".
Anyone have any clues as to what I have done wrong ?
Thanks.

---

### Post by Tom Violence on 2013-07-05
Double

---

### Post by Morbius1 on 2013-07-05
Using this odd little HowTo may be the problem: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

If you followed it exactly then you created a share that looks like this:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
And set permissions to this:
> Owner = nobody
Group = nogroup
Perms = 755
Only the user "nobody" will gain write access. 

That share will break the instant you do one of 2 things:
[1] Create another share that requires the client provide authentication.
[2] Create a samba user that matches or maps to a Windows user's login name.

In both cases the client is no longer "nobody" but in the words of the Rev. Jessie Jackson "he is somebody"

If you have done [1] or [2] above then fix it by adding one line to the share definition:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    [COLOR=#0000cd]**force user = nobody**[/COLOR]
    read only = no
    create mask = 0755
Then restart samba:
```
sudo service smbd restart
```

---

### Post by Tom Violence on 2013-07-05
Thanks Morbius1.  My share/s looks exactly like this now

> 
[COLOR=#000000]*[share]*[/COLOR]
[COLOR=#000000]*comment = Ubuntu File Server Share*[/COLOR]
[COLOR=#000000]*path = /srv/samba/share*[/COLOR]
[COLOR=#000000]*browsable = yes*[/COLOR]
[COLOR=#000000]*guest ok = yes*[/COLOR]
[COLOR=#0000cd]***force user = nobody***[/COLOR]
[COLOR=#000000]*read only = no*[/COLOR]
[COLOR=#000000][I]create mask = 0755


But I still get the same error when I try to copy and paste into the folders in Windows.  I can access the files I already had in there and they play perfectly.[/I][/COLOR]

---

### Post by dannyboy79 on 2013-07-05
what are the outputs of entering the following commands in a terminal window please. i just want to check your owners/groups and permissions. Since you're using security="user", are your users on ubuntu the same as the user on windows?
```
ls -la /
```
```
ls -la /srv/
```
```
ls -la /srv/samba/
```

---

### Post by Morbius1 on 2013-07-05
> **dannyboy79 said:**
> Since you're using security="user", are your users on ubuntu the same as the user on windows?

The use of user level security does not require the setting up of any users on the ubuntu machine ( other than the default "nobody" ) especially since he created a guest accessible share.

---

### Post by Tom Violence on 2013-07-05
Here you go -
ls -la /
total 104
drwxr-xr-x 24 root root  4096 Jul  2 23:48 .
drwxr-xr-x 24 root root  4096 Jul  2 23:48 ..
drwxr-xr-x  2 root root  4096 Jul  2 19:52 bin
drwxr-xr-x  3 root root  4096 Jul  2 19:54 boot
drwxr-xr-x 15 root root  4100 Jul  5 17:36 dev
drwxr-xr-x 89 root root  4096 Jul  5 17:36 etc
drwxr-xr-x  2 root root  4096 Jul  2 23:48 hdd
drwxr-xr-x  3 root root  4096 Jul  2 19:57 home
lrwxrwxrwx  1 root root    33 Jul  2 19:43 initrd.img -> /boot/initrd.img-3.5.0-23-generic
drwxr-xr-x 18 root root  4096 Jul  2 19:52 lib
drwxr-xr-x  2 root root  4096 Jul  2 19:41 lib64
drwx------  2 root root 16384 Jul  2 19:40 lost+found
drwxr-xr-x  4 root root  4096 Jul  2 23:57 media
drwxr-xr-x  2 root root  4096 Jan 25 11:31 mnt
drwxr-xr-x  2 root root  4096 Jul  2 19:41 opt
dr-xr-xr-x 98 root root     0 Jul  5 17:36 proc
drwx------  4 root root  4096 Jul  2 21:32 root
drwxr-xr-x 16 root root   560 Jul  5 20:34 run
drwxr-xr-x  2 root root  4096 Jul  3 18:15 sbin
drwxr-xr-x  2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x  4 root root  4096 Jul  3 20:06 srv
dr-xr-xr-x 13 root root     0 Jul  5 17:36 sys
drwxrwxrwt  4 root root  4096 Jul  5 20:17 tmp
drwxr-xr-x 10 root root  4096 Jul  2 19:41 usr
drwxr-xr-x 13 root root  4096 Jul  5 17:35 var
lrwxrwxrwx  1 root root    29 Jul  2 19:43 vmlinuz -> boot/vmlinuz-3.5.0-23-generic
-rw-r--r--  1 root root  8412 Jul  2 21:31 webmin-setup.out



ls -la /srv/
total 16
drwxr-xr-x  4 root root 4096 Jul  3 20:06 .
drwxr-xr-x 24 root root 4096 Jul  2 23:48 ..
drwxr-xr-x  2 root ftp  4096 Jul  3 19:13 ftp
drwxr-xr-x  3 root root 4096 Jul  3 20:06 samba

ls -la /srv/samba/
total 12
drwxr-xr-x 3 root   root    4096 Jul  3 20:06 .
drwxr-xr-x 4 root   root    4096 Jul  3 20:06 ..
drwxr-xr-x 2 nobody nogroup 4096 Jul  3 20:06 share

---

### Post by Morbius1 on 2013-07-05
Are you adding things directly into that share or are you adding things to subfolders within that share. All subfolders have to allow write access to "nobody" one way or the other.

You might want to post the output of this command so we call all get the complete picture of your setup:
```
testparm -s
```

---

### Post by Tom Violence on 2013-07-05
I have added a couple of test files directly into the shared folders using Webmin.
Here are the results of testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Movies]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[TV]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        encrypt passwords = No
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


[Movies]
        comment = Ubuntu Movies
        path = /media/mynewdrive1/Movies
        force user = nobody
        read only = No
        create mask = 0755
        guest ok = Yes


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

---

### Post by Morbius1 on 2013-07-05
This is a booboo even for guest shares:
```
         encrypt passwords = No
```
Change it to yes:
```
         encrypt passwords = Yes
```
And restart smbd again.

[COLOR=#0000cd]**EDIT**[/COLOR]: Almost missed this: And you switched the location of your shared folder. So what is the output of this command:
```
 ls -al /media/mynewdrive1
```

---

### Post by dannyboy79 on 2013-07-05
your /srv/ folder as well as the /srv/samba/ folder are owned by root and group root, you won't be able to write to the sub-folder i don't think if the parent folders are owned by root. 

EDIT:
WAIT, I don't even see that folder even being shared?????

---

### Post by Tom Violence on 2013-07-05
Here is the result of [COLOR=#000000][FONT=Ubuntu Mono]ls -al /media/mynewdrive1

[/FONT][/COLOR]total 36
drwxr-xr-x 6 root root  4096 Jul  3 14:12 .
drwxr-xr-x 4 root root  4096 Jul  2 23:57 ..
drwx------ 2 root root 16384 Jul  2 22:37 lost+found
drwxr-xr-x 2 root root  4096 Jul  5 20:06 Movies
drwxr-xr-x 2 root root  4096 Jul  3 14:12 Music
drwxr-xr-x 5 root root  4096 Jul  3 18:04 TV

---

### Post by Morbius1 on 2013-07-05
That will do it. If you want to have guest access to [COLOR=#000000][FONT=Ubuntu Mono]/media/mynewdrive1/Movies then you have 2 options:

Set permissions for everyone to access it:
```
 sudo chmod 777 /media/mynewdrive1/Movies[/FONT][/COLOR]
```
[COLOR=#0000cd]**OR**[/COLOR]

Change ownership to "nobody":
```
sudo chown nobody [COLOR=#000000][FONT=Ubuntu Mono][COLOR=#000000][FONT=Ubuntu Mono]/media/mynewdrive1/Movies[/FONT][/COLOR][/FONT][/COLOR]
```

---

### Post by Tom Violence on 2013-07-05
Thanks again for the reply.
I have tried both of those solutions mate and none of them seem to have worked.  I tried copying from one of the shared folders over to my desktop and that worked fine, I just can't seem to send files the other way.

---

### Post by Morbius1 on 2013-07-05
Do you mind posting the output of this again:
```
ls -al /media/mynewdrive1
```

---

### Post by Tom Violence on 2013-07-05
Sure.
total 36
drwxr-xr-x 6 root   root  4096 Jul  3 14:12 .
drwxr-xr-x 4 root   root  4096 Jul  2 23:57 ..
drwx------ 2 root   root 16384 Jul  2 22:37 lost+found
drwxrwxrwx 2 nobody root  4096 Jul  5 20:06 Movies
drwxrwxrwx 2 nobody root  4096 Jul  3 14:12 Music
drwxrwxrwx 5 nobody root  4096 Jul  3 18:04 TV

---

### Post by Tom Violence on 2013-07-05
I've just pointed my popcorn hour media tank to these shared folders and they are streaming fine to that.  If I can just get the writing to them from windows sorted then we've about nailed it as I'd like to move a load of files from my pc to the server.
EDIT - Ok.  I right clicked in windows on the shared folders and changed the security settings to allow full control and bingo I can now copy files into there from my pc :) BUT I cannot modify sub-folders inside the main shares :confused:

---

### Post by Morbius1 on 2013-07-05
There might be some significance to that if I had any idea what a "popcorn hour media tank" was. There's not much else to do on the Linux end of this but it occurred to me that in your posts you mentioned putty, ftp, and Webmin. The only thing you never mentioned is the smb client on Win7 - explorer.

I want to make sure we are still talking about Samba here so go to your Windows box and select the Windows Key + R.

That should bring up the run console. Now that it's open type in:
```
\\192.168.0.100\movies
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the Ubuntu server*[/COLOR]

Now that explorer is up you cannot add a new file to the Movies share?

---

### Post by Tom Violence on 2013-07-05
Morbius I think we've nailed it pal.  I deleted all sub-folders and changed each shared folders security in Windows to full control and now I can copy files over, delete and make new folders :)

---

### Post by Tom Violence on 2013-07-06
Thanks again guys for all the advice.  One more quick question,  is it possible for ubuntu server to unrar files from the command line or webmin ?

---

### Post by Tom Violence on 2013-07-08
After running fine for the last couple of days I have encountered a problem with my server.
I powered it up when I got home today and I get the following error/errors - 

> 
fsck from util linux 2.20.1
mount : dev/sda1 already mounted or media/mynewdrive1 busy
mount : according to mtab, dev/sda1 is mounted on /
mountall: mount /media/mynewdrive1 [404] terminated with status 32
mountall: Filesystem could not be mounted /media/mynewdrive1

An error occurred while mounting /media/mynewdrive1
Press S to skip recovery or M for manual recovery 

Any ideas as to what this is please ?
Thanks.

---

### Post by Tom Violence on 2013-07-09
Bump :)

---

### Post by mastablasta on 2013-07-09
the error means that disk got corrupted. for example if the power suddenly went out when it was working (it's goot to get a UPS to avoid this). and now the system can't mount it. you need to use fsck to repair it.

2 more things - Zentyal is Ubuntu based small server that has a nice GUI for setting it up.

there really is no need for samba since you plan FTP. just install FTP server (for example filezilla) and then use FTP.

---

### Post by dannyboy79 on 2013-07-09
that's weird, it almost looks like it's saying that /dev/sda1 is your  media drive when normally sda1 is your first hard drive and gets mounted to /. are you using UUID in your fstab or /dev/ nodes?

---

### Post by Tom Violence on 2013-07-09
Thanks for the replies guys.  I am out at work at the moment so can't give too many details other than it was working fine all weekend.
I shut it down sunday night and when I powered up monday it got the error.
When I installed ubuntu server I just had the one ssd drive in.  I added my main storage drive after installation was complete.

---

### Post by mastablasta on 2013-07-09
ah yes ---->>>  /media is usually where removable media and drives get mounted (e.g. CD, DVD, USB...)

---

### Post by Tom Violence on 2013-07-09
Thanks.  Hopefully it's fixable.

---

### Post by dannyboy79 on 2013-07-09
this error, "mount : dev/sda1 already mounted or media/mynewdrive1 busy" is weird. can you boot into recovery mode OR hit the "s" key to skip and tell us what your /etc/fstab file looks like please?

---

### Post by Tom Violence on 2013-07-09
Ok this is odd.  Just got home and fired up the server and it's booted perfectly :confused:

---

