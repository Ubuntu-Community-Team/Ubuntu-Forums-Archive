---
title: "Windows7 Pictures to Ubuntu Pic's folder"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by rjwinters on 2011-12-15
Hello 
I would like to know if there is a way to take or copy pictures from windows7 to Ubuntu pic/folder.I have been doing this with a Flash Voyager USB stick.Is there a easier way to do this?I tried to copy & paste but did not work.

See attachment 

Thanks 

Bob

---

### Post by yetiman64 on 2011-12-15
You could go into the Virtualbox settings and enable the shared folders, a folder in the Ubuntu filesystem is allocated as a shared folder which can be accessed as a network drive in Windows networking settings. You can literally pass files between the VM and the Host in seconds with no outside media needed.

After connecting to the folder as a network folder in Windows, just copy your pics folder contents to there and in Ubuntu you can open them in a nautilus window in the VM guest install. Copy and paste to the Ubuntu folder. Have fun :)

Note to get to the settings for the Ubuntu VM will require powering down Ubuntu, when powered up again the shared folders will become available in Windows.

**Edit**: you will first need the guest additions pack for Ubuntu installed to use shared folders etc.

---

### Post by rjwinters on 2011-12-15
Hello
Thanks for your reply.
See the attachment that i have.I don't know how to set this up right,this is my first VM/Box with Ubuntu it is all greek to me.
I would appreciate if some one could help me set this up.:confused:

Thanks for your help:popcorn:
 Bob

---

### Post by yetiman64 on 2011-12-15
Click on the new folder button, <edit: see attachment inline image removed>

Then navigate to a folder to be shared in Ubuntu. I would suggest the Public folder in your home folder, it can be any of your folders though including one made specifically to be shared.

Click ok to add it. Reboot into the Ubuntu VM and then go into the windows networking and connect to it as a network folder.

Edit: check (tick) the auto mount and full access options for ease of use.

---

### Post by rjwinters on 2011-12-15
> **yetiman64 said:**
> Click on the new folder button, <edit: see attachment inline image removed>

Then navigate to a folder to be shared in Ubuntu. I would suggest the Public folder in your home folder, it can be any of your folders though including one made specifically to be shared.

Click ok to add it. Reboot into the Ubuntu VM and then go into the windows networking and connect to it as a network folder.

Edit: check (tick) the auto mount and full access options for ease of use.


Hello
The part i don't understand is windows networking and connect to it as a network folder.:confused:

---

### Post by BC59 on 2011-12-15
Do you have a dual boot Win7/Ubuntu?

---

### Post by yetiman64 on 2011-12-15
> **BC59 said:**
> Do you have a dual boot Win7/Ubuntu?
It's Ubuntu in a VM with a Windows Host (see 1st post attachment).

@ OP I am no longer familiar with the Windows networking settings, maybe if a Windows user can spell out the steps it would help. I remember with Vista I had to go into the Network and Sharing settings folder or such and navigate the "connect network folder" dialogue to the Virtualbox Shared folder that showed up in there.

---

### Post by rjwinters on 2011-12-15
> **BC59 said:**
> Do you have a dual boot Win7/Ubuntu?

Hello No dual boot in windows7 64 bit.

---

### Post by rjwinters on 2011-12-15
> **yetiman64 said:**
> It's Ubuntu in a VM with a Windows Host (see 1st post attachment).

@ OP I am no longer familiar with the Windows networking settings, maybe if a Windows user can spell out the steps it would help. I remember with Vista I had to go into the Network and Sharing settings folder or such and navigate the "connect network folder" dialogue to the Virtualbox Shared folder that showed up in there.

It's Ubuntu in a VM/box with a Windows Host!

---

### Post by BC59 on 2011-12-15
From the options of Virtualbox you choose the host's shared folders. Usually you share your desktop. Then go to Ubuntu, open a nautilus file browser and to the left panel you see Network--Browse Network. Normally Windows Desktop should be there.

---

### Post by rjwinters on 2011-12-15
> **rjwinters said:**
> It's Ubuntu in a VM/box with a Windows Host!


Hello 

This is what i have now in, It's Ubuntu in a VM with a Windows Host
See Attach

Thank for your Help Guys's:)

---

### Post by BC59 on 2011-12-15
Look here

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

and here 

[http://essayboard.com/2011/06/14/how-to-share-files-and-folders-between-virtualboxs-ubuntu-11-04-virtual-machine-and-windows-7-host/](http://essayboard.com/2011/06/14/how-to-share-files-and-folders-between-virtualboxs-ubuntu-11-04-virtual-machine-and-windows-7-host/)

for instructions, on how to do it.

---

### Post by Shibblet on 2011-12-15
> **rjwinters said:**
> Hello 
I would like to know if there is a way to take or copy pictures from windows7 to Ubuntu pic/folder.I have been doing this with a Flash Voyager USB stick.Is there a easier way to do this?I tried to copy & paste but did not work.

See attachment 

Thanks 

Bob

That looks a lot like Vista... not 7.  ;)

---

### Post by mike555 on 2011-12-15
wont putting a mess of pictures in a vb quickly fill the allotted space

---

### Post by yetiman64 on 2011-12-15
> **mike555 said:**
> wont putting a mess of pictures in a vb quickly fill the allotted space
It can do if the virtual machine is made too small initially, but if made the same size as a hard drive install (say above about 20 GB) then it's usually not a problem.

---

### Post by rjwinters on 2011-12-15
> **yetiman64 said:**
> It can do if the virtual machine is made too small initially, but if made the same size as a hard drive install (say above about 20 GB) then it's usually not a problem.


Hello
My virtual machine is over 30GB + my windows 7-64bit Dell CPU has (3) Hard drives + 12MB Ram. I am good in Windows 7 but not Ubuntu 11.10.

I would like to play around with pic's in Ubuntu and some PDF files. I don't like going back & back with USB Flash drives.

Thanks

---

### Post by yetiman64 on 2011-12-15
> **rjwinters said:**
> Hello
My virtual machine is over 30GB + my windows 7-64bit Dell CPU has (3) Hard drives + 12MB Ram. I am good in Windows 7 but not Ubuntu 11.10.

I would like to play around with pic's in Ubuntu and some PDF files. I don't like going back & back with USB Flash drives.

Thanks
Sounds good with regard to mike555's comments. 

Have you tried out the steps in the second link BC59 posted in post #12 (looks ok to me)? My earlier comments may have been around the wrong way (for a Windows guest not for a Windows host as you need), try out the second link in post 12 and you should be alright.

---

### Post by rjwinters on 2011-12-15
> **BC59 said:**
> Look here

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

and here 

[http://essayboard.com/2011/06/14/how-to-share-files-and-folders-between-virtualboxs-ubuntu-11-04-virtual-machine-and-windows-7-host/](http://essayboard.com/2011/06/14/how-to-share-files-and-folders-between-virtualboxs-ubuntu-11-04-virtual-machine-and-windows-7-host/)

for instructions, on how to do it.
Thanks BC59 The URL's were right!

PS Thanks to all you guys for your help!!

---

