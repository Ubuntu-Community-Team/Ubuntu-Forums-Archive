---
title: "Web Dev on Ubuntu"
date: 2006-06-20
forum: Programming Talk
---

### Post by crhall on 2006-06-20
Maybe I'm asking a stupid questionn here... I'm a would-be Ubuntu convert trying to leave behind my life of wickedness in a Windows world. I am a web developer by trade and am trying to figure out how the long-timers do it aroundn here. Typically, I have always kept my dev code on a dev server (also happens to be Windows), and I do my coding remotely (so to speak) using Dreamweaver and remote access. The code is not stored on my desktop.

I'm struggling to figure out how to arrange my dev environment to work with my newfound Ubuntu life. I can map to/mount the remote drive, but can't seem to access it thru any of my tools (Eclipse). Further, I'm not terribly interested in turning my desktop into a server by running a web front end and a 4 TB Oracle DB. Storing my files locally for changes, etc, makes it a several step process because I would have to 'push' after every save, then go to the remote server to test. 

I hope I'm being clear. Any suggestions are appreciated.
Thx

---

### Post by philipgm on 2006-06-20
How are you mounting the remote drive?

---

### Post by crhall on 2006-06-20
Places -> Connect to Server 
Select 'Windows Share' in the drop down.

---

### Post by philipgm on 2006-06-20
when you connect can you browse the disk?

---

### Post by philipgm on 2006-06-20
I've had another look at this and it seems that eclipse cannot see remote file systems - maybe I'm not looking in the right place. In any case I'm a bit confused about you are moving from Dreamweaver to Eclipse. The one being a web page development environment and the other a Java application development environment. 

I have just checked this and I find that I can remote mount, via ftp (I didn't know this was possible so thanks for asking your question) and then edit the files in Bluefish, which is a popular html, php editor. You could also try screem or quanta, i.e. other applications can see the remote file system.

Aside from this, a 4TB DB could be a problem, but really all you need is a local Apache server and some code that points at the database server which can stay wherever it is. There are smaller http servers if you are short on resources.

HTH

Phil

---

### Post by ynef on 2006-06-21
[QUOTE=crhall]Places -> Connect to Server 
Select 'Windows Share' in the drop down.[/QUOTE]
You should try to mount it in a regular directory instead, using smbfs[1] -- it'll appear as any other part of the file system, meaning programs other than gnome should have no problems using it.

[1] [http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by thumper on 2006-06-21
I had a lot of problems with smbfs under load.

Investigations showed that smbfs is deprecated and you should use cifs.  cifs is very similar to smbfs in its configuration parameters, so you should be OK.

---

### Post by s|k on 2006-06-22
I am also interested in a way to connect to my ftp servers through Eclipse rather than using gFTP which is an extra bother. Anyone figured it out or know of a simple HOWTO? Thank you.

---

### Post by philipgm on 2006-06-22
Eclipse cannot connect to the ftp share directly like using this method. Sorry that that doesn't help.

---

### Post by crhall on 2006-06-23
[QUOTE=philipgm]In any case I'm a bit confused about you are moving from Dreamweaver to Eclipse. The one being a web page development environment and the other a Java application development environment. [/QUOTE]
True that Eclipse is primarily used for Java, but with the right plugin it can be used for web, CF, PHP, C, C++...etc...

[QUOTE=philipgm]I have just checked this and I find that I can remote mount, via ftp [/QUOTE]
Our production and dev servers do not (nor are they allowed to) run FTP services.

[QUOTE=philipgm]all you need is a local Apache server [/QUOTE]
And we're not allowed to run web servers in our desktop enviroment. =)

But I think everyone has answered my questions.... :(  It's not possible to do what I want to do.

---

### Post by philipgm on 2006-06-23
So you have to use eclipse? It seems that you are used to using Dreamweaver, which is not naturally the same as using Eclipse. It seems to me that there is more to your original question than you are telling. You CAN do what you SAY you want to do, but not with Eclipse! 

So what is the real problem?

---

### Post by s|k on 2006-06-23
[QUOTE=philipgm]So you have to use eclipse? It seems that you are used to using Dreamweaver, which is not naturally the same as using Eclipse. It seems to me that there is more to your original question than you are telling. You CAN do what you SAY you want to do, but not with Eclipse! 

So what is the real problem?[/QUOTE]
Eclipse is an IDE (Integrated Development Environment), Dreamweaver is a wyswyg HTML editor. Very different animals.

---

### Post by philipgm on 2006-06-23
No argument there, but if the starting point is Dreamweaver then saying that Ubuntu fails because Eclispe isn't possible then I have to ask the question because that is not a level playing field. This seems to be a "stalking horse" to argue internally in an organisation that Windows is a better alternative by placing the bar higher for a competitive technology.

Or am I just paranoid... twenty years in the proprietary IT industry suggest to me that I am not. (and don't patronise if you can avoid it!)

---

### Post by wh0rd on 2006-06-24
crhall I use Dreamweaver on Vmware Server under Kubuntu. It's great. Your not really using Windows but then you are. Now Windows and along with it's non-open source programs are my bitches under Kubuntu.

Here's a screen shot:

[[IMG]http://img517.imageshack.us/img517/692/dreamweaver1vw.th.png[/IMG]](http://img517.imageshack.us/my.php?image=dreamweaver1vw.png)

---

### Post by skymt on 2006-06-24
[QUOTE=crhall]Our production and dev servers do not (nor are they allowed to) run FTP services.

<snip>

But I think everyone has answered my questions.... :(  It's not possible to do what I want to do.[/QUOTE]

Can you run SSH on the server? In that case, use sshfs! Also, have you tried using Samba/CIFS?

---

### Post by JackandJohn on 2006-06-27
I don't know why this hasn't been suggested yet:

Why not use Dreamweaver right in ubuntu?


I have Dreamweaver 8 running perfectly using wine; it even has the same cpu spike during ftp transfers that I get in windows ;)



The worlds need not be exclusive!

---

