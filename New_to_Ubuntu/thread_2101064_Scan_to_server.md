---
title: "Scan to server"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by StrangerSa on 2013-01-03
Hi guys

all the best for 2013 :guitar:  hope its ablast

Can you please tell me if it is possible to scan  to a server linked to an Ubuntu machine.

I run a desktop with Ubuntu 12.10. The server runs clear OS which i know nothing about.

The Ubuntu machine can see the server and retrieve files from it and I can save files to it but when I do a scan, I cannot see the server files

The scanner is a HP 4624 advantage which works well through Xsane

Any assistance much appreciated.

Thanks

---

### Post by lykwydchykyn on 2013-01-03
When you access files on the server, how do you go about it?

Is the scanner on the desktop, or connected to the server?

---

### Post by TheFu on 2013-01-03
> **StrangerSa said:**
> Can you please tell me if it is possible to scan  to a server linked to an Ubuntu machine.

I run a desktop with Ubuntu 12.10. The server runs clear OS which i know nothing about.

The Ubuntu machine can see the server and retrieve files from it and I can save files to it but when I do a scan, I cannot see the server files

The scanner is a HP 4624 advantage which works well through Xsane

Well, this shouldn't be any issue if the desktop and server are able to mount storage from one or the other, then you just need to tell the scannnig software where to write the files.

Common ways for Linux-to-Linux file sharing would be NFS, CIFS, sshfs, ... pretty much any network file sharing method should work.  

The specific way to make this happen would depend on your permissions on both machines and where the scanning software runs.

---

### Post by StrangerSa on 2013-01-03
> **lykwydchykyn said:**
> When you access files on the server, how do you go about it?

Is the scanner on the desktop, or connected to the server?

Thanks for the reply

the scanner is on the desktop and connected via a USB cable. It is an HP and  I downloaded HPLIP and ran that from the terminal as per the walkthrough page.

I also got Xsane from the Ubuntu software centre but I am struggling to get it to work with the adf.

I can access the files on the server by my home folder, network, public files

---

### Post by StrangerSa on 2013-01-03
> **TheFu said:**
> Well, this shouldn't be any issue if the desktop and server are able to mount storage from one or the other, then you just need to tell the scannnig software where to write the files.

Common ways for Linux-to-Linux file sharing would be NFS, CIFS, sshfs, ... pretty much any network file sharing method should work.  

The specific way to make this happen would depend on your permissions on both machines and where the scanning software runs.

Thanks FU

but I am a dummy, you have lost me already :lolflag:

---

### Post by TheFu on 2013-01-03
> **StrangerSa said:**
> Thanks FU

but I am a dummy, you have lost me already

Nobody here is dumb.  Sometimes the flexibility that Linux provides offers many, many solution options and knowing what is possible is the hardest part for someone warped by Microsoft.

First, the nicest scanning GUI that I've found is **gscan2pdf**. Don't worry, you don't need to use the OCR and/or convert to PDF if you don't want, but it is nice to have that option.  Just install it using **software center **or **synaptic **or **apt-get** - completely your choice.

So, here are some assumptions:
* Scanner is **directly attached** to the desktop, not the server
* You **do** control the desktop
* You** do not** control the server
* You want to save scanned files to the "server"
* You have a shared folder on the server that can be accessed by the people who you want to share scanned files.

Please correct if any are not true.

The scanner itself has nothing at all to do with the server and doesn't care where the files are saved. Anywhere that "looks" like a local disk will work.
The trick is to **mount** a file system from the other machine onto your desktop.  To do this, you need to understand how the server shares files with your desktop. Does it use **NFS, Samba, CIFS, or some other method?  **

Sometimes the person who setup the desktop will make the server storage available under /export/, but it could be anywhere or not available at all.

If you have ssh access to the server, then you, without any other help, can use **sshfs **to mount the remote storage.  At this point, you should get the feeling that "mount" is the command to connect storage either local or remote to your desktop.  To learn how to use it, either use a terminal and type "man mount" or just google for "man mount ubuntu".

If you don't have access to any storage on the server, then the server admin will need to make that available. She/he should also set up this server storage so the people that need to write can and the people that need to read can. She/he should tell you how the storage is shared on the network.

A few primers to get you started:
* [http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)
* [http://www.ghacks.net/2010/03/01/share-ubuntu-folders-with-nfs/](http://www.ghacks.net/2010/03/01/share-ubuntu-folders-with-nfs/)
* [https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

You'll need to create a directory for the remote "mount" to attach. Usually, it should be empty.  The command should look something like this if samba/cifs is shared:
$ sudo mount -t cifs //myserver_ip_address/myshare /mnt -o username=samb_user,noexecIf this all seems complex, don't worry, it isn't. There are just a few steps, but understanding how things fit together matters.

Connecting to the remote storage through Nautilus will not work ... ok, it might, but I doubt it. Without a **mount**, your desktop client software will not see the storage.

Anyway, I hope this helps.

---

