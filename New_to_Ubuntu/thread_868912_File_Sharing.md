---
title: "File Sharing"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ryanmiller18 on 2008-07-24
Hello!

I am a complete noob to Linux and chose Ubuntu to start my quest.

I have done research concerning how to setup file sharing in 8.04.  However, I have encountered many different ways to set up file sharing between Windows Vista and Ubuntu 8.04.  For example, I have encountered [http://www.upmykilt.net/2008/07/folder-sharing-in-ubuntu/]("http://www.upmykilt.net/2008/07/folder-sharing-in-ubuntu/") and also found sites that want you to set up SAMBA?

This leads me to my next point.  Is there a recommended way to set up file sharing in Ubuntu for use with Windows?

Any input will be appreciated.

---

### Post by argail1980 on 2008-07-24
my recommended way is to install a SSH-client on the windows machine, but you can also install SAMBA. that will give you sharings, just as between two windoze PCs.
In ubuntu the latter can be done via system -> administraton > shared folders
It will ask you whether to install SAMBA and NFS, install them both.

---

### Post by mikewhatever on 2008-07-24
I don't know of a preferred way, but the link you posted also involves samba, as is evident from <sudo gedit /etc/samba/smb.conf>.

---

### Post by cozmicharlie on 2008-07-24
> **ryanmiller18 said:**
> Hello!

I am a complete noob to Linux and chose Ubuntu to start my quest.

I have done research concerning how to setup file sharing in 8.04.  However, I have encountered many different ways to set up file sharing between Windows Vista and Ubuntu 8.04.  For example, I have encountered [http://www.upmykilt.net/2008/07/folder-sharing-in-ubuntu/]("http://www.upmykilt.net/2008/07/folder-sharing-in-ubuntu/") and also found sites that want you to set up SAMBA?

This leads me to my next point.  Is there a recommended way to set up file sharing in Ubuntu for use with Windows?

Any input will be appreciated.

There are lots of ways to share files between Windows and Ubuntu it really depends on what you want to do.  Samba is the most common method and generally works very well.  The advantage of Samba is you can mount folders on either computer and it acts like a folder on that computer normally does (for example you could play music files right from the folder without having to download it).  Or, if you just want file sharing to be able to move files from one computer to the other you can set up ssh or ftp.  These are generally faster than Samba for downloading files. I use my Ubuntu box as my ssh server (install open ssh server from Synaptic) and have tunnelier set up on Windows ([http://www.bitvise.com/tunnelier](http://www.bitvise.com/tunnelier)).  It's very easy to set up and very secure. My experience is I have more problems with Samba (usually because of my Windows box) than with ssh.  I find ssh to be very reliable and once set up it just keeps working. 

Enjoy

---

### Post by tagra123 on 2008-07-24
One thing I recommend is to set up one PC as the SAMBA server -- let the other computers you have save and read files from this one PC. Why? I have a server set up as the main server for everything. It is my mythtv recorder, my samba server, and my backup storage device. It is located near the back door. I also backup with DVD's. If there is ever an emergency I can grab this PC on the way out the door and lose very little of my work.


NFS is my preferred method of sharing between other linux computers, but I also use samba and ssh. gftp makes sharing files using ssh a breeze.

---

### Post by ryanmiller18 on 2008-07-24
> **argail1980 said:**
> my recommended way is to install a SSH-client on the windows machine, but you can also install SAMBA. that will give you sharings, just as between two windoze PCs.
In ubuntu the latter can be done via system -> administraton > shared folders
It will ask you whether to install SAMBA and NFS, install them both.

There is no "Shared Folders" option under that location.

---

### Post by tact on 2008-07-24
> **ryanmiller18 said:**
> There is no "Shared Folders" option under that location.

Yep it changed with v8.04.  That menu is no longer present.

Just right click on a folder in your home folder that you want to share (in ubuntu) .... then click on "Sharing Options"...  set it how you want it.  If any software needs to be downloaded it will be.  When it tells you that you need to set appropriate permissions it also offers to do that for you  -  let it.   Done.

This  uses a new feature in samba (usershares) that was not present in earlier versions of ubuntu.  It not a full on "samba" installation.  If needed you can later install samba, smbclient, smbfs, etc but its not necessary for a basic folder sharing.

Cheers

---

### Post by ryanmiller18 on 2008-07-24
> **tact said:**
> Yep it changed with v8.04.  That menu is no longer present.

Just right click on a folder in your home folder that you want to share (in ubuntu) .... then click on "Sharing Options"...  set it how you want it.  If any software needs to be downloaded it will be.  When it tells you that you need to set appropriate permissions it also offers to do that for you  -  let it.   Done.

This  uses a new feature in samba (usershares) that was not present in earlier versions of ubuntu.  It not a full on "samba" installation.  If needed you can later install samba, smbclient, smbfs, etc but its not necessary for a basic folder sharing.

Cheers

So just do this and don't bother with going into terminal and **sudo apt-get install samba smbfs**?  Just right click on the folder and then share it?

I don't need to install samba or perform any steps before this?

---

### Post by ryanmiller18 on 2008-07-24
When I get home today I will try to run the command above just to be safe.  Either way, I don't think it would corrupt anything?

Clarification?  Thanks everyone for your help so far... much appreciated!

---

### Post by tact on 2008-07-24
> **ryanmiller18 said:**
> So just do this and don't bother with going into terminal and **sudo apt-get install samba smbfs**?  Just right click on the folder and then share it?

I don't need to install samba or perform any steps before this?

Correct....

---

### Post by ryanmiller18 on 2008-07-24
Thank you everyone for the insight on my Linux quest.

---

