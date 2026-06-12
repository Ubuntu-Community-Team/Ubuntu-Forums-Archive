---
title: "Bluefish - Remote FTP"
date: 2007-10-27
forum: Programming Talk
---

### Post by Paris Heng on 2007-10-27
Dear all,

How to connect to FTP, by using Bluefish (HTML editor)? 

I can't search any, please help! Thanx

---

### Post by Cybergod on 2007-10-27
The only way I know how to do it is by using "Connect to Server" under "Places".  Setup your FTP connection here.  This way you can edit your files using Bluefish.

---

### Post by Paris Heng on 2007-11-12
> **Cybergod said:**
> The only way I know how to do it is by using "Connect to Server" under "Places".  Setup your FTP connection here.  This way you can edit your files using Bluefish.

Thanx ya, i will try it later, sorry for tha late reply!

---

### Post by MiniMe on 2008-05-09
Excellent! Create the FTP site in "Places" and open in Bluefish!

---

### Post by insub2 on 2008-07-10
this may be a little closer to what you are looking for:

[http://bluefish.openoffice.nl/movies/working_with_remote_files.html](http://bluefish.openoffice.nl/movies/working_with_remote_files.html)

EDIT:
I am having trouble getting it to work.

RE-EDIT:

I got it working...I think.  Here's how:
Go to File > Open URL...
Put in [ftp://[URL](ftp://[URL) of your FTP Server]
It'll prompt for a username and password.


So far, so good.

---

### Post by themusicwave on 2008-07-10
I often use the Places method with BlueFish.

However, this method is really slow, so perhaps the second method suggested is better.

With the places method, BlueFish tends to go to the greyed out screen you get when an application is frozen or just really churning.  It usually takes about 45 seconds or so to save.

I'll have to try the other method mentioned.

---

### Post by sirenaa on 2008-07-23
Hi!
I have a following problem: I cannot connect with Bluefish to one remote ftp, although I can connect to this servert through ftp client, I am using filezilla. To other servers I can connect without a problem. Anybody has a clue what could be a problem? I need to edit some websites and if this is not working, I need to find another html editor that will be "compatible" with my FTP server (any suggestions). 
Thanks
Sirene

---

### Post by tvcasualty on 2008-07-25
Alright I'm feed up.
Why does bluefish allow me to open any file I want on my remote server via ubuntu's FTP connect to server option, yet ONLY SOMETIMES allows me to save?  I don't see why on time A it will save fine... time B it will flat out refuse... and on time C it will prompt me for a password, which I will enter only for it to prompt me again.  Is this someone trying to hack me or what?  HOW DO YOU GUYS DO WEB EDITING???  I know everyone here dosen't host their own server?!  Surely this problem has be encountered before?  

Tried SCREEM had the same issues... leads me to believe something more generic is the cause.

ideas?

---

### Post by Felson on 2008-07-25
Never used bluefish, but I do edit over FTP. The way I do it is with a FuseFTP mount. At that point, you can use whatever you want on it.

---

### Post by mia.king on 2008-12-01
> **Felson said:**
> I do it is with a FuseFTP mount. 

Is this curlftpfs?

Can someone do a good FTP tutorial and Sticky it?

1. Places - Connect to server
why it works or doesn't work
problems ?eg. very slow

2. alternate FS mounts

3. native text editors that have built in ASCII/full FTP support



That would be much appreciated. I can't seem to find such a post.

---

### Post by mia.king on 2008-12-02
#curlftpfs works!! But requires you to use commandline.

#Get curlftpfs (synapse) or 
sudo apt-get install curlftpfs

#Create a directory to be your mount point  (-p if more than 1 deep)
mkdir <mount directory>


#Consider doing up a bash file to mount and unmount the directory. Need to chmod +x <filename> to make it executable
--------------------
#!/bin/bash

#mount the directory using following line (-o allow_other else might need sudo)
#(use %40 instead of @ if your server uses this for username)
sudo curlftpfs -o allow_other ftp://<username>:<password>@<hostwww> <mount directory>

#pause
ls <mount directory>
read -p "press any key to unmount the FTP volume..."

#Unmount
sudo umount <mount directory>

---

### Post by btermeli on 2010-02-05
I can't find "Places".
Version 1.0.7

---

### Post by andrew.46 on 2010-03-11
Hi btermeli,

> **btermeli said:**
> I can't find "Places". Version 1.0.7

The "Places' referred to is not in Bluefish but on the top panel of the Ubuntu Desktop...

Andrew

---

### Post by thienhaxanh2405 on 2011-05-01
> **insub2 said:**
> this may be a little closer to what you are looking for:

[http://bluefish.openoffice.nl/movies/working_with_remote_files.html](http://bluefish.openoffice.nl/movies/working_with_remote_files.html)

EDIT:
I am having trouble getting it to work.

RE-EDIT:

I got it working...I think.  Here's how:
Go to File > Open URL...
Put in [ftp://](ftp://)[URL of your FTP Server]
It'll prompt for a username and password.


So far, so good.
oh, thanks. :)

---

### Post by yz89 on 2012-04-09
> **insub2 said:**
> this may be a little closer to what you are looking for:

[http://bluefish.openoffice.nl/movies/working_with_remote_files.html](http://bluefish.openoffice.nl/movies/working_with_remote_files.html)

EDIT:
I am having trouble getting it to work.

RE-EDIT:

I got it working...I think.  Here's how:
Go to File > Open URL...
Put in [ftp://](ftp://)[URL of your FTP Server]
It'll prompt for a username and password.


So far, so good.

Hi there,

I found out something which I wish to share: If you run bluefish in root mode the above solutions will not work:KS

I was confused for hours because I always ran via following command:
> sudo bluefishAnyone know why bluefish has this behaviour when it has been ran in root mode?:confused:

---

### Post by 53om on 2012-12-01
> **yz89 said:**
> Hi there,

I found out something which I wish to share: If you run bluefish in root mode the above solutions will not work:KS

I was confused for hours because I always ran via following command:
Anyone know why bluefish has this behaviour when it has been ran in root mode?:confused:
I might be having this problem 'cause Bluefish ftp won't work for me at all, although I'm not opening it using sudo, just clicking from the launcher. 

What I'm really trying to set up is an FTP connection like Notepad++ where I can edit a local file and then immediately upload to the server right from the text editor. Super convenient to not have to go to another application to upload.

Am I on the right track with Bluefish? Is it possible?

---

### Post by Szise on 2013-01-15
I have the same problem with the latest version, 2.2.4-rc2

---

