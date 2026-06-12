---
title: "HOWTO: Use Shared Folders in Gnome"
date: 2007-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Darkdelusions on 2007-05-10
After looking around on the web and not being able to find anything on how to use the shared folders option in feisty I thought I would write a guide on how to. Since this is a quick alternative to trying to fully configure samba. 

Overview
This guide will teach you how to use the shared folders feature in feisty so your windows box can connect to you ubuntu folders. This guide will assume you have a static ip if not please use this **[post]("http://ubuntuforums.org/showthread.php?t=432813&highlight=static+ip")** if you are unsure how to create one.

Tested on:
Ubuntu Feisty Fawn


Disclaimer: Use at your own risk. I will assist as much as possible. 

Step 1: Locate the folder you want to share 

- We will use /home/bob/music for an example

Step 2: Right click on the music folder and choose share folder. 

- This will install samba if its not already installed. 
- Once the install is done it should pop up the share folder window 

Step 3: In the Share through field select Windows Network (SMB)

- You will then see the share Properties and you will have a Name field and a comment field become visable

Step 4: (Optional Step) Name the Folder what ever you want and save

- I highly suggest keeping it short other wise you will hate your self later there is nothing like a share folder name like Share Name: ROFLOMGMUSICGALORIELOL

Step 5: Open a terminal and type sudo smbpasswd -a A_Username_Here. You then will be prompted for a password 

[COLOR="Red"]***Important***[/COLOR] Set the user name and password to something your going to remember.  I set mine to the user name and password I use for my box

- This is the part where I got stuck for a few minutes I was able to get connected to the box but I couldn't get logged in  

Step 6: There are a couple of different ways to get connected in windows

1) Go To Start, Run, then type in \\Your Static Ip\music 
- The you will be prompted for that user name and password I had you set in step 5 

2) Goto Tool, Map Network Drive 
- Select a drive Letter then in the folder Box type \\YourStaticIP\music
- Hit the select Connect to this drive using a different user name and password and enter your user name and password 

And there you have the Ubuntu Shared Folders in a nutshell

---

### Post by chang47 on 2007-05-17
Thank you very much for providing this tip.  I was scouring through the forum for days looking for a simple answer without having to go into smb.conf etc.  I found the Shared Folder setting so there must be an easier way than all the samba CLI and editing.  As you were, I was unable to find any mention of Shared Folder in the official documents.

The key for me was creating the samba user and password.  This is still strange to me as reading through the comments in the smb.conf file there seems to be a way to synch samba userid and password with the system id and password.  Coming from the Windows world it is a bit challenging to understand why different sets of userids and passwords.  I guess if you look at it from the server world it makes sense as samba users may not be a system user on the server box. 

Anyway, the long and the short is.  This is the most simple way to access Linux folders from a Windows machine without having to worry about all the ip, DHCP, ...

Now if I can only figure out how to access Windows folders from the Xubuntu side.

Home network with D-Link DI-524 wireless router. Xubuntu Feisty Fawn, 2 WinXP.

---

### Post by Darkdelusions on 2007-05-17
> **chang47 said:**
> Thank you very much for providing this tip.  I was scouring through the forum for days looking for a simple answer without having to go into smb.conf etc.  I found the Shared Folder setting so there must be an easier way than all the samba CLI and editing.  As you were, I was unable to find any mention of Shared Folder in the official documents.

The key for me was creating the samba user and password.  This is still strange to me as reading through the comments in the smb.conf file there seems to be a way to synch samba userid and password with the system id and password.  Coming from the Windows world it is a bit challenging to understand why different sets of userids and passwords.  I guess if you look at it from the server world it makes sense as samba users may not be a system user on the server box. 

Anyway, the long and the short is.  This is the most simple way to access Linux folders from a Windows machine without having to worry about all the ip, DHCP, ...

Now if I can only figure out how to access Windows folders from the Xubuntu side.

Home network with D-Link DI-524 wireless router. Xubuntu Feisty Fawn, 2 WinXP.


Doing it from the windows side is just as tricky. Most of the time when you setup windows. It asks you for a user but does not have you set a password for the user. There for when you go to Places>Network then click on the computer it will prompt you for a user name and password. And anything you attempt will get you no where. 

The fix for this is setting up a password on you windows box (this will disable auto sign in) I will post how to fix it when i get home and have use of both my boxes

---

