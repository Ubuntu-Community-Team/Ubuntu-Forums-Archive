---
title: "rsync"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by user2000 on 2008-10-27
Hello,

I am looking for a program to run on a local server of mine to synchronize all the files from a particular directory on my dedicated web server (colocated). My local server and dedicated server are both running linux. I want the data to be pulled from my local server and not pushed from the dedicated server.

I am wondering whats the best, most reliable program i can use to pull the data to my local server. Also, can you please guide me on how to set it up? Will I have to do any configuration on the dedicated server?

Is rsync the best option with a cron job? Or should I use something like mirror or wget? I want synchronization also so that incase the same file is updated, it should update my local copy also. I want only one way synchronization from my dedicated server folder to my local server. 

Security is not too much of a concern.

I tried using mirror, but it asks me to enter the password everytime. I am not able to include the password in the arguments i pass to mirror. Then, how do i use this with cron then?

Thank you very much.

---

### Post by amac777 on 2008-10-27
Hello, rsync will work if you only want to synchronize the files. If you also want to keep snapshots of the backups without using too much space, then you should take a look at "rsnapshot". 

[http://rsnapshot.org/](http://rsnapshot.org/)

Rsnapshot is in the repositories and I use it to pull backups off my computer. It can keep as many snapshots as you like such as hourly, weekly, monthly, yearly etc... So if you end up needing a file that you deleted a long time ago, or if your files get corrupted at some point after you've done a synchronization, you can still have backups archived via earlier snapshots. There is lots of help on how to configure it on that website.

Anyway, both rsync or rsnapshot can "pull" the files from another computer so that is not a problem.

To avoid having to type your password each time you run the command to do the backup, for example from a cron task, you will probably need setup an ssh key so rsync or rsnapshot can login to the remote computer without needing to enter a password. This is very easy to do and there are many tutorials on these forums. Also, a quick google search shows this page:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

see the section "SSH Keys".

---

### Post by hyper_ch on 2008-10-27
rsync and hardlinks make incremental snapshots ;) very simple to setup ;)

---

### Post by user2000 on 2008-10-27
okay ive now got a better picture of what i really want to do:

my dedicated server has a folder: /temp/abc

my local server: 
1. i want to run rsync to download all the contents of /temp/abc'
2. i want to make sure that incase someone gets access to my local server, he still is not able to download any other stuff from my dedicated server (i.e. using the ssh keys)

in extremely simple words, i will be uploading data/updating existing data on my /temp/abc folder. I just want my local server to run rsync and download all the contents of abc folder and make sure that incase a file got updated, then download the file again but not simply download files if they are latest (and waste my bandwidth).

i understand i have to setup ssh keys. but i want my local server which is running rsync to be able to access only /temp/abc folder. nothing else.

thank you again for your prompt replies.

---

### Post by hyper_ch on 2008-10-27
Let me get this straight:

(1) you have a dedicated server
(2) you have a home "server"
(3) you want to backup a specific folder from the dedicated server to your home server
(4) you want to make sure, that in case someone gets access to your home server, that they can only get limited acces (/temp/abc) on the dedicated server

---

### Post by user2000 on 2008-10-27
yes absolutely perfect... amazing

thank you... is there a solution for my problem?

---

### Post by hyper_ch on 2008-10-27
well, I think you have it all together so far

- use rsync to backup
- use ssh-keys to create passwordless login

except for one thing

- limit login user to a certain directory

I'd suggest you look at mysecureshell for chrooting a ssh login to a certain directory. It's not that difficult.
So if someone gets access to your box they will only be able to get into the designated folder on the server - however in there, they can delete everything.

---

### Post by user2000 on 2008-10-27
just a few more points:

(5) I want to run my backup program (rsync/mirror/whatever) from my home server only... (i dont want the dedicated server to do any sort of work really.. except sending the files ofcourse)
(6) i want the solution to be reliable and simple...
(7) i want the backup to check incase my server updates an existing file then it should download the file again, incase my server deletes a file then it should delete a copy... basically it should maintain an exact replica of the dedicated server folder. exact.

---

### Post by user2000 on 2008-10-27
thanks hyper... you are superb...

problem is that i barely understand rsync... and doing mysecureshell will be a major task... i dunt know if i will be able to do it right...

are you online on skype/msn/gmail etc. so that you cud help me setup a config...

thank you again very much.

---

### Post by user2000 on 2008-10-27
i also tried "mirror" but the problem is that it when i run it, i can only send the username as argument and not the password. it then manually asks me for the password. so how do i put it into cron? because everytime it runs it manually asks for password. can i hardcode the password in "mirror" somehow?

---

### Post by user2000 on 2008-10-27
i dont mind that risk... i.e. someone can delete only the contents of that folder alone...

---

### Post by amac777 on 2008-10-27
> **user2000 said:**
> 
(7) i want the backup to check incase my server updates an existing file then it should download the file again, incase my server deletes a file then it should delete a copy... basically it should maintain an exact replica of the dedicated server folder. exact.

rsync can delete files that it finds are no longer located on the source. So it will act as a mirror and only transfer files that have changed to reduce bandwidth.

To enable the automatic deletion of files on the destination that are not longer on the source just add the --delete parameter like this:

```
rsync -az -e ssh --delete username@dedicated_server:"/temp/abc" ~/backups
```

That command will mirror the directory /temp/abc from the dedicated server and put it in a /backups directory under your home folder. You can change the source and destination as you feel fit.

In that command, the -az means to preserve all the timestamps, owners, permissions of the files and to compress them during the transport across the network. The -e ssh part means to tunnel the transfer though ssh. The --delete parameter enables the deletion of files on the destination that no longer exist on the source. The username should be the username you login to the dedicated server when using ssh. The dedicated_server should be the IP address or domain name of the dedicated server.

> 
2. i want to make sure that incase someone gets access to my local server, he still is not able to download any other stuff from my dedicated server (i.e. using the ssh keys)

This requirement is a problem in my opinion. It will involve setting up something on your server to limit ssh access to only the directory you want, which of course directly conflicts with your requirement that you don't want the dedicated server to do any work except sending the files. The reason is that if you want to limit people only to one directory on the dedicated server, than the dedicated server will have to implement this.

In my opinion, you might want to reconsider the security implications. If you want automatic and passwordless login using ssh keys, then you need to trust your local server. You could setup a dedicated user on your local server just for doing these backups and then run the cron task as this user. But if someone hacks your server and gets root (or a user with sudo access), then they will be able to login to your dedicated server via the ssh key. So if you don't trust your local server or the users using your local server then you probably shouldn't use ssh keys if you're paranoid.

However, that said, if someone can hack your local server and get root (or a user with sudo access), they could install a key logging program and get the password to the dedicated server that way. So basically, if you don't trust your local server, you're not safe no matter what you do.

---

### Post by user2000 on 2008-10-27
Thank you for your reply. 

This is the exact reason why I wanted to use FTP. Cause ftp is simple, even if the person gets access to the local server, he can only get access to the ftp server.

Is ftping to the dedicated server a better option?

---

### Post by amac777 on 2008-10-27
Well.... It's hard to define "better". If your dedicated server already provides FTP access only to /temp/abc directory, and the there is no way for a user to navigate to other folders via the ftp server then perhaps it would be ok. 

A few security things about using FTP is that you will probably have to include the username and password to login to the FTP account on the dedicated server within the cron script. Obviously, these username/password had better not be the same username and password that a person could use to login using ssh on the dedicated server or you've just lost all your security. Also, maybe not important to you, but ftp transfers the password clear text so people sniffing the network or between you and the dedicated server can see the password.

If those bad points are acceptable to you, set up the ftp account on the dedicated server to only allow access to the particular directory (/temp/abc) for a username / password that is only used for making these backups and then use a program such as "ftpcopy" on your local server to make the mirrored copy.

```
ftpcopy -uusername -ppassword ftp://dedicated_server backups
```

You might need to run "sudo apt-get install ftpcopy" to install ftpcopy first.

---

