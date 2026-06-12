---
title: "saving libreoffice files to network drives"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by elron on 2012-06-07
Background:  
I am working in a school in NSW(Australia). I have a number of machines that will not work with windows xp or connect to our 2008 server.

I decided to try ubuntu and settled on two os. Zorin os for the slightly better ones and Lubuntu for machines that were slower again.

It has worked remarkably well and the computers are zippy and responsive. Initially I installed office 2007 under wine but this caused more problems than it was worth so I started to teach the kids libre office.

I have a ubuntu box with with the 10 desktop distro on it. I have shared some folders so the kids can save their files without any login. It's really just meant to be a drop off point so they are not bound to one machine. I was going to get the children to create a folder with their name and save all their files to that.


The problem:
It doesn't work. The long explanation is that pictures can't be inserted into libreoffice documents from the network drive, nor can the children save under libreoffice to these drives.

I have done some reading and it seems to be a problem with how network shares work and not Libreoffice.

The question is, what is the simplest option for me to achieve my goal taking into account I have little experience with Linux. I would put my skills at the "trained monkey" stage :) By this I mean I can follow guides and work through very basic problems.

Regards,


Ian

---

### Post by drdos2006 on 2012-06-07
More details required.
What does this mean ?
"I have a ubuntu box with with the 10 desktop distro on it."

Are you setting up a Ubuntu box as a server for them to make their own folders, or do you want them to connect into the Windows server ?
Or do you have a box with Virtual Machines running ?

You mentioned you have shared folders. Have you installed Samba ?

regards

---

### Post by elron on 2012-06-07
Apologies. What I mean is that I have installed ubuntu 10 on a machine. It is the desktop 10.04 distribution I think. I Have installed samba. 

All I have done in it is created a folder called transfer. Then i right clicked and chose sharing options. 

I ticked:
-share this folder
-allow others to create and delete files
-guest access

Anymore info you need?

regards,


Ian

---

### Post by drdos2006 on 2012-06-08
How did you create the share ?
If you used "sudo mkdir /transfer" then the folder is owned by "root".
To allow access to other users or groups, you need to change the owner from root to someone or some group who can access the Samba shared folder.

My suggestion would be to install "webmin_1.580_all.deb" on the machine so that you can easily use a GUI with browser to modify shares, start up programs etc.

The desktop you are using is a server with added bells and whistles.

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server, use terminal with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://your_server_IP:10000](https://your_server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by 3rdalbum on 2012-06-08
What happens when the children attempt to add pictures from the network drive or save to it?

If the drive does not appear in the left pane of their Open/Save dialog box, then you need to create a bookmark for the folder "~/.gvfs" (it's a hidden folder called '.gvfs' inside the home directory) on each machine. This will appear in Open/Save dialog boxes and double-clicking on it will reveal any mounted network drives.

---

### Post by drdos2006 on 2012-06-08
And as an addendum to 3rdalbum, does each child have their own machine ?

regards

---

### Post by elron on 2012-06-08
> **drdos2006 said:**
> How did you create the share ?


I made a folder in the documents directory and then did a right click and chose sharing options as i described above.

If I use a windows machine I can copy files to it and read off it no problems. It's when i try to save to it using libreoffice or insert a picture from this folder that it doesn't work.

> **3rdalbum said:**
> What happens when the children attempt to add pictures from the network drive or save to it?

If the drive does not appear in the left pane of their Open/Save dialog box, then you need to create a bookmark for the folder "~/.gvfs" (it's a hidden folder called '.gvfs' inside the home directory) on each machine. This will appear in Open/Save dialog boxes and double-clicking on it will reveal any mounted network drives.

Under zorin I did bookmark the networked drive (called transfer) but when a child clicks on the bookmark they can get to the drive but not save on it. The same is true trying to insert pictures from the network drive into impress. The children can browse the pictures but get an error when they try to insert. Do I need to do it specifically they way you have described because I just browsed to the network drive using zorin filemanager and then bookmarked it.

> **drdos2006 said:**
> And as an addendum to 3rdalbum, does each child have their own machine ?

regards
There are 26 machines in the room. Children are not assigned a specific machine.

---

### Post by drdos2006 on 2012-06-08
Sounds like a permissions problem to me.

When you type "ls -l /transfer" from the terminal, you should get the permissions such as "drwxrwxrwx".
The "d" stands for directory, "r" stands for reading the directory, "w" stands for writing the directory and "x" stands for executable file. 
The first "rwx" is the owner of the file or directory, the second "rwx" is the group owner and the third "rwx" is for others.


Who is the owner of "/transfer", who is the group owner of "/transfer".

If it is "root" then you may have to change the owner to the login name or "nobody" in order to allow read and write access.

** More information for you **
[http://ubuntuforums.org/showpost.php?p=11884837&postcount=9](http://ubuntuforums.org/showpost.php?p=11884837&postcount=9)

regards

---

### Post by elron on 2012-06-09
Success!!

As you suspected it was a permission problem. After following your advice and reading the link you sent me it enabled me to determine it was owned by root. I then found some instructions that showed me how to fix it.

Thank you so much for your help!

Regarding you suggestion about webmin. I have the machine at home with me now. If I install webmin, will it work at school where the ip setup is different. Here I am 192.168.0.x while at school it starts with 10.xx.xx.x

Many thanks again,

Regards,

Ian

---

### Post by drdos2006 on 2012-06-09
Webin can run on the localhost that you have setup as the server with :
[https://localhost:10000](https://localhost:10000)  or Webmin can be run from a different machine on your local area network with :  [https://the-IP-address-of-your-server-machine:10000](https://the-IP-address-of-your-server-machine:10000). You just have to accept the new IP address and connect.

regards

PS: Please mark your thread as solved so it helps someone else.

---

