---
title: "Share different folders with different users"
date: 2016-03-27
forum: New to Ubuntu
---

### Post by Chrismallia on 2016-03-27
Hi I am Chris and I have spent my life as a windows power user and always wanted to learn   Linux, this week I removed Windows 10 from my laptops and PC and installed Ubuntu, I have done alot of reading and found everything I needed, I also am using terminal and getting familiar with commands. Now to come to the question I fell In love with ubuntu linux so much that I have a server running  windows server on and want to replace windows with ubuntu also on my server, all I have are 2 questions coming from Windows all my life please excuse me if they are a little dumb  

1 what type of storage solution do you suggest ? In windows I am using stablebit drivepool  but I am open for any suggestions you guys have 

2 this is something I could not figure out, How can I share folders from my storage drives to multiple users but each own there own folder as in windows? Example I have 2 folder  folder a and folder b,now I want to give folder a reed and write permissions  to Chris and folder b reed and write permissions  to example Joe   but the users can not reed and write to each others folder. These are the only thing I need to now to start installing ubuntu on my server and btw I will still be using ubuntu desktop for my server.

Thank you for your help and support

---

### Post by nerdtron on 2016-03-27
> **Chrismallia said:**
> Hi I am Chris and I have spent my life as a windows power user and always wanted to learn   Linux, this week I removed Windows 10 from my laptops and PC and installed Ubuntu, I have done alot of reading and found everything I needed, I also am using terminal and getting familiar with commands. Now to come to the question I fell In love with ubuntu linux so much that I have a server running  windows server on and want to replace windows with ubuntu also on my server, all I have are 2 questions coming from Windows all my life please excuse me if they are a little dumb  

Thank you for your help and support

Welcome to the Ubuntu Linux community.

We'll I'm saying don't expect too much god-like powers from Linux since you come from a windows world. Sometimes the power users are the ones having a hard time getting the grips with Linux :)
Just be patient and try to read/practice a lot since the Linux is different from windows. Don't get frustrated when something doesn't work as you expect on linux. People can voluntarily help you with your problems.

> 1 what type of storage solution do you suggest ? In windows I am using  stablebit drivepool  but I am open for any suggestions you guys have 
Storage solution for what use? Just storage of the server? A network shared folder? Backup storage solution?

>  2 this is something I could not figure out, How can I share folders from  my storage drives to multiple users but each own there own folder as in  windows? Example I have 2 folder  folder a and folder b,now I want to  give folder a reed and write permissions  to Chris and folder b reed and  write permissions  to example Joe   but the users can not reed and  write to each others folder. These are the only thing I need to now to  start installing ubuntu on my server and btw I will still be using  ubuntu desktop for my server. 
Are you going to share via network and the users will access the folders via their windows computer? Then you'll need samba.
Samba if you have a GUI [http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/](http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/)
No GUI server: [http://www.linuxveda.com/2015/01/01/install-samba-server-ubuntu/](http://www.linuxveda.com/2015/01/01/install-samba-server-ubuntu/)
[http://computerbeginnersguides.com/blog/2015/10/22/install-and-configure-a-basic-samba-file-sharing-server-in-ubuntu-15-10-wily-werewolf/](http://computerbeginnersguides.com/blog/2015/10/22/install-and-configure-a-basic-samba-file-sharing-server-in-ubuntu-15-10-wily-werewolf/)

Mostly, for editing settings or permissions, you'll use the command line and edit some text files. That's the way linux does things. Most of the time there are no tickboxes to check, you need to define what exactly you want to set on those text configuration files.

If you stumble on problems, ask this forums and provide as much details as possible so people can better understand your problem.

---

### Post by Chrismallia on 2016-03-28
Hi thank you so much for your reply. Yes being a windows power user I understand it might be a little harder as a windows user I modify and setup tasks I want in a blink of a eye (including windows server), but I also had to learn first in windows and now  as you stated I am in no hurry and will learn as I go along, In my small experience I already have with Ubuntu I always feel rewarded when I learn and get something right, and as I said I want to switch all my devices including My server to Ubuntu.

For storage sorry for I did not explane it  right, I have a storage pool with wd red drives I use to store my media on and stream from using Plex also store files documents and do some backups on, in windows I use stablebit drivepool here I read about greyhole but as I read on it I do not see it mature enough (please correct me if I am mistaken in anyway) there seams to be some thing that I did not like like if a drive failed it take a while to recover the duplication  and it does not handle small files and changing of files well, so the way I see it is to use MDADM Raid and speaking of mdadm raid are there any performance  charts to see what type of read and write speed to expect in raid levels?  or use pci e  raid card. If you have any suggestions I am open

For sharing files 

I want to give users a personal space each where they can store there private data on the server, in windows I did this by using samba but if there are any other suggestions or maybe a software that can do something like anything, devices are windows and Ubuntu (hope to be all Ubuntu very soon )

Regards and thank you again  

[h=1][/h]

---

### Post by Chrismallia on 2016-03-28
I have a other question, I tried transferring  a 4gb file from my windows samba share to ubuntu 15 on my laptop that has a ssd, usually from windows server to windows laptop I got 113MB/S now with ubuntu I get 42 MB/S max. any ideas why I have  Gigabit switch and gig Ethernet cards (as i wrote I get 113MB/S from windows to windows

---

