---
title: "Samba file permissions"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-09-18
Hello to all!

I was tasked to create a samba share on an ubuntu server. The set up is like this:

\\server\Folder1\folder2\folder3

from the station(server), there will be a shared folder(foler1). Inside that folder, there will be another folder(folder2). and inside folder2, I will be putting another folder(folder3).

What I want to do is have folder1 to folder2 a read only access to users but on folder3 they can now have fulla access.As of now Im able to have all of these folders on full access to users.

How will I able to do that? Being new to LINUX, Im completely lost. Please help.. Thank you very much!:)

---

### Post by jbrown96 on 2008-09-18
i think [this method]("https://help.ubuntu.com/community/SettingUpSamba") is the easiest for a beginner to ubuntu. Here is a great section that should make it easy, provided you are using Gnome. > Ubuntu Server
This section enables Ubuntu as a samba file server. 
Sharing a Folder
To share a directory you must have permission to access the directory. Go to your home directory ( Places -> Home folder). Right click on the "Documents" directory and in the pop up menu select "Share Folder". 
If samba is not installed you will get a pop up menu "Sharing services are not installed". Select "Install Windows networks support (SMB)" and deselect "Install Unix networks support (NFS)" -> then click "Install services". 
If you get an error message that the samba .deb could not be found, open a terminal and update apt-get. 
sudo apt-get update
Then again install SMB support. Ubuntu will download and install samba. After samba is installed again Right click on the "Documents" directory and in the pop up menu select "Share Folder". You will get a pop up menu "Share Folder". Select "Windows networks (SMB)" in the pull down menu and give your share a name in the "Name" box. Unselect the "Read only" check box if you want read/write access to the share. Click the "Share" button.

---

### Post by jerryheavyarms on 2008-09-18
Yes. Thank you for the reply. I've already done that. I had folder1 shared and be seen on the network. I also set its permission to read-only. What I want to be able to do is to have folder1 up to folder3 to be on read only and all the files and folder under folder3 to be on full access. 
Thank you very much!:)

---

### Post by jbrown96 on 2008-09-18
Have you tried adding folder1 as read-only, which would pass read-only permissions to all sub-directories, creating the proper permissions for folder2? Then create another shared entry for folder3, giving it read/write permissions?
If that doesn't work, it might be a limitation of Microsoft's sharing model.

---

### Post by jerryheavyarms on 2008-09-18
What I did was to share folder1, have it on read-only access and all sub-directories and files under it have the same restrictions. I also have it on writable.

Correct me if Im wrong. Having folder3 to be shared means it will be viewed on the Windows box right? I think I cannot do that. They told me that only folder1 should be viewed on the network...

Thanks for your answers..:)

---

### Post by jerryheavyarms on 2008-09-26
Ive edited my smb.conf, I think it is different from what I earlier did.

I have user1 and user2 as my samba users.

On my samba server, I have a shared folder "data".

Ive managed to make these 2 users to have full access to "data" folder and its subdirectories. My boss wants user1 to have full access to "data" and user2 to have read-only rights on "data" folder but full access on one of its subdirectories "data2".
Ive already have configured user2 to be read-only on "data" but how will I make user2 to have full access on "data2"

Thanks in advance and I hope all of you can help me.:)

---

