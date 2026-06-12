---
title: "Windows share in applications"
date: 2016-03-26
forum: New to Ubuntu
---

### Post by neylon79 on 2016-03-26
I am new to Ubuntu, coming from Windows. I am on 14.04 using KDE with Dolphin as my file manager. I added my windows shared folders in my network area very simply, and can see them there. However, if I want to open an xls file from that shared drive, I cannot double click it and have it open in LibreOffice. Nor can I navigate to it in LibreOffice with Open>file. 

I have my music collection on the shared folder and would like to be able to edit tags and manage it with puddle tag or something similar. And play music off it also with Clementine or something similar. Both allow me to navigate to the network share, but won't actually open it. Only Kate allows me to see the network folder and open files as if they were on my laptop.

I have searched many threads regarding mounting a network folder as a local drive, but have been unsuccessful. I tried smb4k to do this with a gui. It asks me for a login to view the Windows share even though none is required. My Windows admin login doesn't even work when I try that either.  I tried some command line guides, edited fstab as directed, but when I used the cfis mount code it said it couldn't find the Windows share in fstab. I confirmed the spelling many times. 

Ideally I could add the folder in network area of dolphin, right click it and select mount as local drive or something simple like that. Is there a reason some programs can see the network folder and open a file, like Kate, while others see it but cannot open anything, like clementine, and others can't even see it in the open file navigation. 

I'd love to use a gui of some sort, but I'm not going to be mounting drives regularly, so if I can successfully do it once via terminal, I'm fine with that. 

I used mp3tag in Windows before for this, but it closes after 3 seconds when running in wine right now, so I don't even know if this would work for me. 

If there is a better forum to ask this, please let me know. Sorry for the rambling, just want to give all info I can. Thanks.

Edit: these are the instructions I used to mount the share-https://wiki.ubuntu.com/MountWindowsSharesPermanently
It is read/write by everyone in windows so I was following the unprotected guest instructions

---

### Post by neylon79 on 2016-03-26
Solved my own problem. I assumed I could mount all shared folders by just putting the IP address/ with no folder name in the fstab. Once I put the folder name to mount each folder individually, worked perfectly. Thanks to all of you for the 50 other things your answers helped me with before I even joined the forum!

---

### Post by SeijiSensei on 2016-03-26
Just a hint for the future.  Dolphin will let you access remote Windows shares by entering a URL like this:
```
smb://server/share
```
into the address bar.  You'll be prompted for a username and password if one is needed.

Another useful trick if you are connecting to a Linux machine that has openssh-server installed is to use the "fish" URL in Dolphin
```
fish://server
```
which sets up a connection via SSH and lets you browse all the folders on the remote machine to which you have access rights.  I use this method to transfer files between my desktop and the servers I rent at [ Linode](http://www.linode.com/). I split the directory window so I can have both the local and remote directory lists available.

In both these cases "server" can be either a textual hostname or an IP address.

---

