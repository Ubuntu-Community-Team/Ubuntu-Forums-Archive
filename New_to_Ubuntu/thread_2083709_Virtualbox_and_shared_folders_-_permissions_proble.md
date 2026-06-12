---
title: "Virtualbox and shared folders - permissions problem"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by dunbankin on 2012-11-13
This is my first foray into Linux, so please bear with me if this is a dumb question..
To try out Ubuntu 12.10 Desktop I installed VirtualBox v4.2.4 on my Win7 64-bit Home Premium PC, and installed Ubuntu 12.10 32-bit as a guest OS.  
However, I can't get to share folders between host and guest.  

In Win7, I've right-clicked the folder  to share, selected Share with.../Specific people/Everyone/'Read/Write', and named the share "Main".

In VirtualBox Manager, I've now got the guest OS Shared Folders Settings to show the share under "Machine Folders", with properties: 
Name: Main ; 
Path:  c:\users\john\documents\main; 
Auto-mount: Yes; 
Access: Full.

Rebooted the guest OS, and as stated in the Ubuntu documentation, I now have a folder in File System/Media called sf_Main.

However, opening this folder, gives me the error message:
[B]"The folder contents could not be displayed. 
 You do not have the permissions necessary to view the contents of "sf_Main". "[/B]
What am I doing wrong?  Surely "Access: Full." should give me full permissions?  How do I get Linux to recognise the permissions?

Regards
John

---

### Post by wheeze on 2012-11-13
> **dunbankin said:**
> However, opening this folder, gives me the error message:
[B]"The folder contents could not be displayed. 
 You do not have the permissions necessary to view the contents of "sf_Main". "[/B]

Your user in the Ubuntu guest OS must be in the **vboxsf** group.

From a terminal, type:
```
sudo adduser xxxxxxx vboxsf
```

where xxxxxx is your user account name. Log out and log back in to Ubuntu.

---

### Post by wheeze on 2012-11-13
Also, make sure the Virtualbox Guest Additions are installed in your Ubuntu guest, and the Virtualbox Extension Pack is installed in your VB installation in Win7.

---

### Post by dunbankin on 2012-11-13
wheeze - The Man!  Solved the problem instantly.  Thanks!

Took me a few minutes to work out what a terminal window was, and how to open one (just like Windows/run/cmd), but this now works a dream (if a little slow).  MUCH better than Windows Virtual PC - couldn't get Ubuntu to install at all in one of those.  

Thanks again!

How do I mark this thread as solved - not at all obvious....

Regards
John

---

### Post by audiomick on 2012-11-13
> **dunbankin said:**
> MUCH better than Windows Virtual PC - couldn't get Ubuntu to install at all in one of those. a suspicious person could suspect deliberate intent on Microsoft's part...:-\"

 > How do I mark this thread as solved - not at all obvious...

In the "thread tools" drop down menu at the top right of the thread.

---

