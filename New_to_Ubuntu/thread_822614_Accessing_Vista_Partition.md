---
title: "Accessing Vista Partition"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Zebra Lord on 2008-06-08
Hello everyone
I have a dual boot with Vista and Ubuntu.  When I first installed Ubuntu it did not recognize Vista and I could not transfer my files from Vista.

After I tried to access my documents and settings from Ubuntu none of the folders showed up.

Is there any way to access my documents on Vista from Ubuntu without placing them on a flash drive and transfering them.  I really need to be able to access them

---

### Post by OldTimeTech on 2008-06-08
do you have ntfs-3g loaded and do you have the files in Vista shared that you want to use?

---

### Post by Xerp on 2008-06-08
All my drives and partitions just show up on my desktop. Which version of Ubuntu have you installed?

---

### Post by Victormd on 2008-06-08
> **Zebra Lord said:**
> Hello everyone
I have a dual boot with Vista and Ubuntu.  When I first installed Ubuntu it did not recognize Vista and I could not transfer my files from Vista.

After I tried to access my documents and settings from Ubuntu none of the folders showed up.

Is there any way to access my documents on Vista from Ubuntu without placing them on a flash drive and transfering them.  I really need to be able to access them

How are you trying to access your files? Does your vista partition show up in the PLACES menu?
Open a terminal and type
```
 sudo fdisk -l
```
and that will list the partitions "seen" by Ubuntu. Post the output...
you also might want to check [this thread]("http://ubuntuforums.org/showthread.php?t=802699").

---

### Post by Victormd on 2008-06-08
> **OldTimeTech said:**
> do you have ntfs-3g loaded and do you have the files in Vista shared that you want to use?

This isn't a deal breaker between ubuntu and windows. I dual boot and never installed any extra package to access my NTFS partitions, and file sharing won't do you any good either... Theoretically, the only thing you have to be worried about is properly shutting down windows, otherwise windows locks-up your NTFS partition...

---

### Post by Zebra Lord on 2008-06-08
> **Victormd said:**
> How are you trying to access your files? Does your vista partition show up in the PLACES menu?
Open a terminal and type
```
 sudo fdisk -l
```
and that will list the partitions "seen" by Ubuntu. Post the output...
you also might want to check [this thread]("http://ubuntuforums.org/showthread.php?t=802699").

my vista partition does show up in the PLACES menu. I can even access some of the folders in the partition. however, when i try to access the documents and settings folder, so that i can get to the Users folder and from there to my documents, nothing shows up in the Documents and Setting folder

---

### Post by Victormd on 2008-06-08
It's odd that you can only partially access your vista partition. In vista, did you set any file access permissions (with password or something)? If so, that might be the reason why you can't access your user folder.
I just ran a quick check here on my vista and ubuntu dual boot comp. and the only thing that keeps me from accessing it is if I'm hibernating windows (or didn't properly shut down), then the partition becomes locked...

---

### Post by Victormd on 2008-06-08
Ok, just remembered that I did have to set permissions in vista...
In vista:
1. Right click on the documents and settings folder, click on properties, then click on the security tab.
2. Click on the EDIT button to change permissions.
3. On the new window, click on ADD, then ADVANCED, then click on the FIND NOW button and scroll until you find "Everyone", select it.
4. Click on ADD, then OK. Now, you should be on the "Permissions for Documents" window.
5. Select "Everyone" under "Group or user names:" and then choose "full control" under the "Permissions for Everyone" section.

This will grant access to this folder so you can see it under ubuntu and you should be able to access your files which should be under
media/"partition name"/USERS/your name/my documents

Let me know if this works for you...

If there are any other folders you can't access, you'll have to set the permissions in the same way...

---

### Post by cariboo on 2008-06-08
I don't know what kind of vista installation you have but in my case all my documents are located in /usr/jimk/documents. Documents and Settings is empty. I beleive this is just a leftover that MS hasn't figured out how to remove without screwing up the os.

Jim

---

### Post by tgrimley on 2008-06-08
Jim/cariboo907 is right.

Vista uses some sort of symlink (called junctions I think) for legacy purposes which don't work under anything other than Vista.

You'll want to look in C:/Users/username/Music, etc. IIRC  In any case I think that's your problem and you just need to poke around a little more.

---

### Post by MattBD on 2008-06-08
Try installing the pysdm package from the repositories. Then look for Storage Device Manager in the menus (I think it's under System>Administration in Ubuntu). That tool will enable you to set Ubuntu up so that it will mount your Vista partition where you set it to.

---

### Post by Unix_Slayer on 2008-06-08
That's weird. I have no problems seeing everything on my Vista drive. Did you change the permissions in Vista at any time for your user folder?

---

### Post by Xerp on 2008-06-08
cariboo907 has it exactly right. "Document and Settings" isn't used in Vista . I can't see anything in there even in Vista :) (It actually errors when I click on it)

---

### Post by Unix_Slayer on 2008-06-08
> **Xerp said:**
> cariboo907 has it exactly right. "Document and Settings" isn't used in Vista . I can't see anything in there even in Vista :) (It actually errors when I click on it)
Yes.... they changed it to c:\Users

---

