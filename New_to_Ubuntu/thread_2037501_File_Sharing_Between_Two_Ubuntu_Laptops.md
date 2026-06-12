---
title: "File Sharing Between Two Ubuntu Laptops"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by SEECo on 2012-08-04
Hi guys I have a Window XP Professional and two Laptops having Ubuntu 10.04 Netbook Edition. I have created a folder in the home directory of both laptops and the Folders are shared on Desktop having Windows now I want the same folders to be shared by the laptops and visible on the network. How could I do this. Please help.

---

### Post by GreatDanton on 2012-08-04
For sharing between Ubuntu and Windows you must have samba installed.
This link will help you: [http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

Regards.

---

### Post by Ubun2to on 2012-08-04
Quick question-do you want the files to be synchronized between computers? If so, just setup Ubuntu One to automatically keep the contents of certain folders the same. Much easier than using Samba, which would make for a lengthy post. It works on Ubuntu and Windows, and you get 5 GB of storage space for free.
If you just want to be able to access the contents of certain folders, but don't care if they are exactly the same or have nothing in common, you will need to use Samba.

---

### Post by dwhite on 2012-08-04
> **Ubun2to said:**
> Quick question-do you want the files to be synchronized between computers? If so, just setup Ubuntu One to automatically keep the contents of certain folders the same. Much easier than using Samba, which would make for a lengthy post. It works on Ubuntu and Windows, and you get 5 GB of storage space for free.
If you just want to be able to access the contents of certain folders, but don't care if they are exactly the same or have nothing in common, you will need to use Samba.


+1
this is what i do also, dropbox works well too

---

### Post by Dylan1473 on 2012-08-05
Uh, to clarify, were you asking how to share between Ubuntu and *Windows* or between the two Ubuntus?

EDIT: _[This thread here]("http://askubuntu.com/questions/95573/how-can-i-transfer-files-between-two-ubuntu-computers-on-a-lan-without-installin")_ presents an interesting solution. Just open a terminal, use

```

[SIZE=2]cd [PATH TO THE DIRECTORY YOU WANT TO SHARE][/SIZE]
python -m SimpleHTTPServer

```Hopefully that's applicable in your case. There are actually a bunch of methods but that one seems relatively simple. Samba might be a more ideal solution though.

EDIT AGAIN: [Link]("http://askubuntu.com/questions/45082/enable-personal-file-sharing") to a very detailed explanation of the Samba method if you choose to go that route.

EDIT YET AGAIN: And I see that GreatDanton already provided a link. Well, I'll leave that there just in case you should find it useful.

---

### Post by fractalman on 2012-08-05
i use ssh-server to transfer between my pc and my laptop which both run ubuntu

To install the OpenSSH server,  you need the packages

 openssh-server

sshfs


**GNOME**

 Click **File** -> **Connect to Server**. Select **SSH** for **Service Type**, write the name or IP address of the computer you're connecting to in **Server**.  Click **Add Bookmark** if you want to make the connection available later in the Places sidebar.  There are options to login as a different **User Name**, on a different **Port** number, and use a different default **Folder**. 
Files can be copied by dragging and dropping between this window and other windows.

---

### Post by gifford on 2012-08-05
Nitroshare is another option.
[https://launchpad.net/nitroshare/](https://launchpad.net/nitroshare/)

---

