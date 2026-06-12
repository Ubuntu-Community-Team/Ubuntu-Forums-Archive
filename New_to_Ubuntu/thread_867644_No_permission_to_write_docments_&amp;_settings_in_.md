---
title: "No permission to write docments &amp; settings in XP"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Lowtec on 2008-07-23
I am a newbie and apologize in advance if this has been covered
before. I didn't turn it up when searching the forum.

I have a Western Digital My Book external hard drive,previously
I copied the Documents and Settings folder in windows XP to this hard drive using Ubuntu 7.04 (Fiesty Fawn), formated C: and then
copied back after the reinstall. This worked fine the first time but on repeating this process I now find that I only have permission only to read the new instal of XP so I am unable to paste the documents and settings folder back from the hard drive to C:

---

### Post by lisati on 2008-07-23
If you are copying using Ubuntu, you might need to install the NTFS-3G utility before you can write to your documents folder.

---

### Post by Lowtec on 2008-07-23
The NTFS-3G utility must have been the during the first instal
(as it worked), also if not present now would I have been able to transfer the folder from XP to the hard drive this time?

I have tried to change permissions on C: in properties but access
is deied and remains at read only.The owner of C: is unknown according to properties.
I am running ubuntu from CD (as I did the first time) will a full install work? .

 I opened terminal and attempted to use su -l and sudo passwrd -l root  I am very green and can just about fumble aroud in DOS but I am stuggling to navigate around folders and failed to how use this to change permissions

---

### Post by aktiwers on 2008-07-23
How did you try to change the permission of the Windows drive?

Try this form terminal (applications => accessories => Terminal):
```
sudo chown -R **username**:**username** /media/**Windowsdrive**
```Where both username should be replaced by your Ubuntu username and Windowsdrive with the name of you windows drive.

---

### Post by Lowtec on 2008-07-23
I tried to change permission in Ubunto properties and failed,
then I opened XP and changed  C: in Properties to "Share this Network" and "Allow network users to change my files" ( yes I'll turn it off when this is sorted) and attempted change properties of Documents and Settings in XP to uncheck read only, it appears to be unchecked after applying, but on return the box is still checked!
You might be on to something, but I'm still at a loss.

---

### Post by northern lights on 2008-07-23
Sharing the folder/drive under XP makes no difference - you're accessing it not via network, but from the same machine afterall.

Did you run "chown"?
--> See above post, first thing to run now.

What version of Ubuntu are you running?
--> lisati's "ntfs-3g" should only be relevant if it's not Gutsy or Hardy (as those ship with it initially). However, to check, you could run ```
aptitude search ntfs-3g
``` and check whether there's an "i" to the left of it, just to be on the safe side. A look into Synaptic would clarify that also.

---

### Post by Lowtec on 2008-07-23
OK  
I typed in "aptitude search ntfs-3g" and entered. The the computer "did Something" with the hard drive but returned nothing leaving me back with just at 
user name@host name:~$


I tried sudo chown with this command,

sudo chown -R username:username /media/465.8 GB Volume: disc 
also
sudo chown -R username:username /media/"465.8 GB Volume: disc"
the anwser was no such file or directory

I'm running Ubuntu 7.04 (Fiesty Fawn)

---

### Post by forger on 2008-07-23
post back the result of these commands:
```
sudo fdisk -l
sudo mount
apt-cache policy ntfs-3g ntfs-config
```

---

### Post by northern lights on 2008-07-23
> **Lowtec said:**
> OK  
I typed in "aptitude search ntfs-3g" and entered. The the computer "did Something" with the hard drive but returned nothing leaving me back with just at user name@host name:~$

For real? Nothing along the lines of ```
user@host:~$ aptitude search ntfs-3g
p   libntfs-3g-dev                  - ntfs-3g filesystem in userspace (FUSE) lib
i   libntfs-3g23                    - ntfs-3g filesystem in userspace (FUSE) lib
i   ntfs-3g                         - read-write NTFS driver for FUSE           
user@host:~$ 

```
--> That would mean the repository containing all three is not even enabled. Lemme check where it's in.

> **Lowtec said:**
> OK  
sudo chown -R username:username /media/465.8 GB Volume: disc 

Did you replace "username:username" by your username?
Is "465.8 GB Volume: disc" really what your Windows partition is labeled under /media?
--> I'd doubt it is. Can you post the output of ```
ls /media
```

---

### Post by Lowtec on 2008-07-23
The exact command I used for sudo chown was:-

sudo chown -R ubuntu:ubuntu /media/465.8 GB Volume: disc

This is a copy of ubuntu is running from a CD called
ubuntu-Live session user




ls /media 

returned : disc My Book

I dont appear to be doing what you think I doing! Sorry,
I am very green
  ( my extrnal harddrive)

---

### Post by forger on 2008-07-23
**[SIZE="4"]LOWTEC:[/SIZE]**
Open from the Ubuntu menu: Applications > Accessories > Terminal

Execute and post back the result of these commands:
```
sudo fdisk -l
sudo mount
apt-cache policy ntfs-3g ntfs-config
```

(Select the output text with your mouse and right-click > copy)

---

