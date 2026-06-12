---
title: "sharing folders"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by georged1981 on 2012-03-02
Im wanting to have a local folder that can be accessed by all other users. 

What I have done so far....created a folder on my desktop put permissions for each user but still doesn't show in other user accounts.

The reason why i want to do this is so that i can have each user ssh to the machine and edit and create files.

Any help would be greatly appreciated.

---

### Post by Jake5 on 2012-03-02
You need to make sure the folder you are trying to share is marked as a shared folder, I am pretty sure you just right click on the folder, choose properties, and a window should open up with all kinds of options, one should be a share folder option, if this box does not display a checkmark in it, go ahead and check the box. I'm not sure if this is the right method right now because I'm at work. Should be home in about a half hour and I will double check and get back to you.

---

### Post by Jake5 on 2012-03-02
So the method I posted previously works, but heres a screenshot of a couple different options, notice the boxes are unchecked, that is because this folder is not shared between users or the network.

---

### Post by Jake5 on 2012-03-02
> **Jake5 said:**
> So the method I posted previously works, but heres a screenshot of a couple different options, notice the boxes are unchecked, that is because this folder is not shared between users or the network.
 
If this works for you, don't forget to mark the thread as [Solved]. Thanks.

---

### Post by georged1981 on 2012-03-02
I've selected sharing options > share this folder and allow other to create and delete files in this folder > clicked on create share.

When I've logged out then logged into another account it doesn't show in any of the user folders.

I've tried in the public folder and on my desktop.

---

### Post by Jake5 on 2012-03-02
What version are you running, 11.10?

---

### Post by georged1981 on 2012-03-02
> **Jake5 said:**
> What version are you running, 11.10?

yep

---

### Post by Jake5 on 2012-03-02
I am sorry, I have mislead you, these options are for over the network sharing, not local sharing. I am new to this too, so please forgive. Just trying to help. Looking for more info found a couple of links, the first of which sounds like you have already done, confirm please.

[http://ubuntuforums.org/showthread.php?t=1869900](http://ubuntuforums.org/showthread.php?t=1869900)

maybe this will help: check post numbers six, eight, and nine. 
To sum it up you may have to re-install.

[http://ubuntuforums.org/showthread.php?t=1406506](http://ubuntuforums.org/showthread.php?t=1406506)

again, 
Sorry for the misinformation,

---

### Post by slyspring on 2012-04-28
To preface this, I am using Ubuntu 11.10 64-bit and am actively sharing with my other Win7 computer.

OMG! I just solved this in 15 minutes with just SAMBA and a few Win7 tweaks! Follow these to the letter

1. Using Ubuntu, open Terminal and run **sudo apt-get install samba**

2. Run the command sudoedit **/etc/samba/smb.conf**

3. Under "Global Settings", where it says #Change this to the Workgroup/NT-domain....#, change the workgroup the actual name of your group. Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer.

4. Hit CTRL and the letter X at the same time to exit. When, asked to save, press the letter Y, and hit Enter.

On to Windows 7 (bane of existence)

1. Open Network and Sharing Center.
2. On the left, click "Change Advanced sharing options"
3. Perform the following (make sure your computer is set for Home/Work):
  a: Network Discovery - On
  b: File and Printer Sharing - On
  c: Public Sharing - On
  d: file sharing connection - 128-bit encryption
  e: password protected sharing - off
  f: use user accounts (just as a precaution)
4. In the Control Panel, select User Accounts.
5. Enable the Guest Account. It is not automatically a part of every folder for permissions sake.
6. On the in the folder permissions (or the root of the external drive you want to share), add the Guest account, and I recommend you give it up to MODIFY rights to all folders and subfolders you need. NTFS permissions trump Share permissions.
7. Create the share you want, with me STRONGLY recommending adding the Group user and giving it up to Modify rights. 

All that other crap about winbind and nss... i undid on my Ubuntu, and my fixes persisted forever. take it or leave it.

---

