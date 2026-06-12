---
title: "Sharing in VirtualBox"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by tentel on 2008-05-06
I managed to install XP as a virtual machine and the whole thing went very smoothly.

Unfortunately, I am now completely stumped.

I can't figure out how to share my /home folder with XP. and I don't know how to access my wireless network.

I have tried to read through tutorials, but I can't seem to get anywhere.


I'd appreciate some help.

(By the way, I'm using 1.6, Puel, not OSE)

Thanks
-TIM

---

### Post by mlentink on 2008-05-06
I use 1.5.6, and with that, I can edit the virtual machine settings for shared folders. I'm in the office behind a windows machine unfortunately, otherwise I could give you a detailed walk-through

---

### Post by tentel on 2008-05-06
IN the VirtualBOx GUI, I can to go settings, and in the shared section, I added /home to the list, but in XP, nothing seems to happen.


Should note:

When I click settings, I get this message:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}

 

But when I click okay, it still takes me to the settings section.


-Tim

---

### Post by mlentink on 2008-05-06
> **tentel said:**
> When I click settings, I get this message:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Yeah, I seem to remember it does that when you've got USB enabled. It should go away if you disable USB in the virtual machine settings.

But did you share /home? or was it /home/user/somesubdirectory?
Because /home will not work as you have no privileges to share that.

---

### Post by tentel on 2008-05-06
I tried adding /home/tim/documents


but when I went to the shared folders in XP, it wasn't there.


I get the feeling that I'm missing a crucial step to activate the sharing.

or I'm looking for the folders in the wrong place in XP.

In Ubuntu, should I enable sharing with each folder I want to share?  or maybe add it to the vboxuser group?



-Tim

---

### Post by MyR on 2008-05-06
you have to map the drive in xp.  you can read about it the manual:
> 4.4. Folder sharing
Shared Folders allow you to access files of your host system from within the guest system, much like ordinary shares on Windows networks would -- except that shared folders do not need a networking setup. Sharing is accomplished using a special service on the host and a file system driver for the guest, both of which are provided by VirtualBox.
In order to use this feature, the VirtualBox Guest Additions have to be installed. Currently, Shared Folders are limited to Windows XP, Windows 2000 and Linux 2.4 and 2.6 guests.
To share a folder with a virtual machine in VirtualBox, you must specify the path of the folder to be shared on the host and chose a "share name" that the guest can use to access it. Hence, first create the shared folder on the host; then, within the guest, connect to it.
There are several ways in which shared folders can be set up for a particular virtual machine:
In the graphical user interface of a running virtual machine, you can select "Shared folders" from the "Devices" menu, or click on the folder icon on the status bar in the bottom right corner of the virtual machine window.
If a virtual machine is not currently running, you can configure shared folders in each virtual machine's "Settings" dialog.
From the command line, you can create shared folders using the the VBoxManage command line interface; see Chapter 8, VBoxManage reference. The command is as follows:
VBoxManage sharedfolder add "VM name" -name "sharename" 
                   -hostpath "C:\test"
There are two types of shares:
VM shares which are only available to the VM for which they have been defined;
transient VM shares, which can be added and removed at runtime and do not persist after a VM has stopped; for these, add the -transient option to the above command line.
Then, you can mount the shared folder from inside a VM the same way as you would mount an ordinary network share:
In a Windows guest, starting with VirtualBox 1.5.0, shared folders are browseable and are therefore visible in Windows Explorer. So, to attach the host's shared folder to your Windows guest, open Windows Explorer and look for it under "My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". By right-clicking on a shared folder and selecting "Map network drive" from the menu that pops up, you can assign a drive letter to that shared folder.
Alternatively, on the Windows command line, use the following:
net use x: \\vboxsvr\sharename
While vboxsvr is a fixed name (note that vboxsrv would also work), replace "x:" with the drive letter that you want to use for the share, and sharename with the share name specified with VBoxManage.


hope this helps

peace

---

### Post by mlentink on 2008-05-06
> **MyR said:**
> you have to map the drive in xp.  you can read about it the manual:


hope this helps

peace

And I assume too much. Thx for pointing that out to me!

---

### Post by tentel on 2008-05-06
Okay, I got it working.

In Ubuntu, I rightclicked each folder I wanted to share, and then selected Sharing Options and checked all three boxes.

Then, in XP, I went to the Shared folders window, and clicked Tools>Map New Network Drive, and then browsed to the folder I had eneabled for sharing.

I can now access these folders from My Computer.

Thanks for the help guys!



Could anyone point me in the right direction for enabling wireless?
Or should I start a new thread for that?


-Tim

---

### Post by MyR on 2008-05-06
> **tentel said:**
> Could anyone point me in the right direction for enabling wireless?
Or should I start a new thread for that?

new thread please ;]

---

### Post by tentel on 2008-05-06
NOw that I think about it, i don't think I'll need internet access.

I'm only using XP so I can run AutoCAD.  I don't really need the internet for that, and that isn't really a problem I want to deal with just yet anyways.


Thanks for all the help everyone.


-Tim

---

### Post by SlappyPappy on 2008-05-06
Just use the network settings in Windows and it will piggyback the internet through your host Linux settings. Works great even using dialup in Ubuntu.

---

### Post by dRock1286 on 2008-05-07
> **tentel said:**
> Okay, I got it working.

In Ubuntu, I rightclicked each folder I wanted to share, and then selected Sharing Options and checked all three boxes.

Then, in XP, I went to the Shared folders window, and clicked Tools>Map New Network Drive, and then browsed to the folder I had eneabled for sharing.

I can now access these folders from My Computer.

Thanks for the help guys!



Could anyone point me in the right direction for enabling wireless?
Or should I start a new thread for that?


-Tim

Thanks!  I have tried every tutorial on this I could find and this got it working for me!  Thanks again!  You rock!  :guitar:

---

### Post by blondebeard on 2008-06-15
i have done this like 20 times and you have to install xp the guest additions then you shut the virtual machine down then you go to setting then add your folder you desire to share. if you do it out of order it wont work and i have not figured the work around for this so i always do it in that order, you might have to shut the vmachine down all the way to install th guest additions sometimes too.

---

