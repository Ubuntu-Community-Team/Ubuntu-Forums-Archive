---
title: "Script for FTP connection"
date: 2017-02-13
forum: Programming Talk
---

### Post by geoborja01 on 2017-02-13
Hi guys, I've been doing this script, which is already working correctly, but there's some things that I would like to change but I don't know how to make it work.

[TABLE="width: 500"]
[TR]
[TD]#!/bin/sh
HOST='localhost'
USER='geoborja'
PASSWD='contraseña'
ftp -n -i $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd /home/geoborja/Desktop/FTPPrueba/
mget *.iso
quit
END_SCRIPT


chmod 777 /home/geoborja/Desktop/*.iso
mv /home/geoborja/Desktop/*.iso /media/geoborja/GeoBorja1/RECIBIDOS/
[/TD]
[/TR]
[/TABLE]

-In the row, where "mget *.iso", I would like to make the mget download all the files into a certain folder, which you can see is "/media/geoborja/GeoBorja1/RECIBIDOS/".
The way I am doing it right now is, as you can see, moving from Desktop (where the FTP sends files when are downloaded) to the "RECIBIDOS" folder.

-I would wish to execute my script and make it check if any ".iso" is already in the computer, so if it is already in the computer don't download it.
[B]
Sorry guys if my english isn't really good.[/B]

---

### Post by TheFu on 2017-02-13
This script makes ZERO sense.  Why would anyone use FTP on localhost to move files around?  Seriously. Why?
The last line is the only thing needed and you probably want to copy the files from the source to the target.  If the FTP server is running inside a chroot (and I really, really, really hope it is), then the source will need to be found somewhere on the system - they are there and accessible by this userid.

**rsync** over ssh would be the way I did this between 2 different hosts (or even on the same host). If the remote server doesn't support ssh, I'd fire them (or install it).

With rsync, you specify the source and the target. No need to have multiple steps to get, then move the files around.

---

### Post by geoborja01 on 2017-02-13
1st - I'm not using the script on localhost, it's supposed to work towards a remote host, I wrote localhost for writing something.
2nd - Please try to not talk like that, it feels disrespectful, I know that my script is probably bad, that's why I am looking for help because I have no idea.
3rd - I'm gonna get some info about rsync, thanks about that.

---

### Post by bearlake on 2017-02-13
I hope you are not using FTP over the Internet.

Use SFTP - secure file transfer.

A quick search gave me this -  [https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server)

---

### Post by The Cog on 2017-02-13
Everyone will tell you not to use FTP over the internet - it's just not secure because it's not encrypted.

I would advocate using either SCP (secure copy - uses SSH underneath) or possibly rsync over SSH. 
You can configure SSH for password-less login by using public keys if you want - this avoids having to script a password exchange.
Assuming password-less ssh has been configured, here are the commands (I think they're right):
For scp:
```
scp "$USER@$HOST:/home/$USER/Desktop/FTPPrueba/*.iso" /media/geoborja/GeoBorja1/RECIBIDOS/
```
For rsync:
```
rsync --rsh=ssh "$USER@$HOST:/home/$USER/Desktop/FTPPrueba/*.iso" /media/geoborja/GeoBorja1/RECIBIDOS/
```

If a file has already been copied once, rsync will figure that out and only copy any differences in its content.
You may have to script it if you want to apply the chmod 777 afterwards.

---

### Post by TheFu on 2017-02-13
> **geoborja01 said:**
> 1st - I'm not using the script on localhost, it's supposed to work towards a remote host, I wrote localhost for writing something.
2nd - Please try to not talk like that, it feels disrespectful, I know that my script is probably bad, that's why I am looking for help because I have no idea.
3rd - I'm gonna get some info about rsync, thanks about that.

No disrespect intended. I apologize.  

Usually when folks do odd things, there is a good reason. I really wanted to understand because I assumed you had a good reason. Figured the ftp connection was inside a chroot and the only way to get there was through FTP that the admin had setup, even though it was on the same machine. The would be odd, but no telling what an admin would do in the name of "security."  There are probably other reasons where this would be necessary too.  Nobody knows everything.  The flexibility of Unix like systems is nearly endless.

rsync is an amazing tool for many reasons. The trick is to setup ssh connectivity (with ssh-keys) BEFORE using rsync. By that I just mean to get ssh working between the systems, and push the public key to the remote system using **ssh-copy-id**.  **rsync** will use the ssh-tunnel by default if ssh is setup and working. Highly secure, only 1 port opened (ssh port).  ssh is really the primary way that Unix people remote into systems and move things around. We use ssh, scp, sftp, rsync and other tools based on those.  For example, most commonly used backup tools for Unix/Linux are based on librsync and libssh, so almost all of them support remote push or pull backups through a secure channel.

There isn't any need to add **-e ssh** anymore to rsync commands. ssh is assumed and has been since around 2006-ish. From the manpage:
```
 For remote transfers, a mod&#8208;
       ern  rsync  uses  ssh for its communications, but it may have been configured to use a different
       remote shell by default, such as rsh or remsh.

``` This is easy to validate on any system that only has ssh ports open, the rsync still works.

If rsync doesn't work (there are some edge situations), **sftp** is designed to be a replacement for plain FTP, just secure. The scripting of sftp would be similar ... plus it has a batch mode to make things easier, but rsync is much easier.  **scp** is a drop-in replacement for the old rcp command, should that help.  

rsync is an amazing tool. So is ssh [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)

---

### Post by The Cog on 2017-02-13
> **TheFu said:**
> There isn't any need to add **-e ssh** anymore to rsync commands. ssh is assumed and has been since around 2006-ish.  

Ooh. That's clever. I hadn't realised that. Thanks.

---

### Post by TheFu on 2017-02-13
> **The Cog said:**
> Ooh. That's clever. I hadn't realised that. Thanks.

There's a bunch of new options for all sorts of commands these days.  

df, du, and sort all have "-h" for human options.  For sort, that means   **du -sh * |sort -h ** understands the T/G/M/K sizes. Very handy.  Learned about these maybe a year ago. ;)  I'm slow in that way.  

ssh-copy-id changed my life and don't get me started about the ~/.ssh/config file - BETTER than sliced bread - by far! 

Oh ... and in the original script, **chmod 777** is a bad idea 99.99999999999% of the time.  **chmod 640** is probably what you really want, but 660 shouldn't be too bad on a stock Ubuntu system.  Just depends on how groups are setup and the umask used.

---

### Post by geoborja01 on 2017-02-14
Thanks all of you guys, I really appreciate it. :D
I'll look for some guides and I'll try everything you said when I'm not busy.
I'm sorry for not explaining my idea correctly, what I am trying to do is a computer wich connects to a remote server and downloads all the .iso files and checks them before.
Thank you again guys, I think this is what I am looking for so I'll try it out and I'll post here if it's working, I'm really grateful. :D

---

