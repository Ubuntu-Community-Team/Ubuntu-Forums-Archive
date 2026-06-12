---
title: "Share files between Ubuntu host and Ubuntu guest."
date: 2012-08-28
forum: New to Ubuntu
---

### Post by A4driano on 2012-08-28
Ok, so I installed Ubuntu 8.04(guest) into Ubuntu 10.04(host) and everything is running fine. I have been trying to share my /home folder to open it while using Ubuntu 8.04 (guest). I am using Virtualbox, Guest Addittions and both operating systems are updated. I also added my user to vboxusers group and it does not work. I was able to share files when I had Ubuntu 12.04 as host but now I do not know why this do not work with my Ubuntu 10.04. I had opened "/home" that was located in "media" but now it does not work with 10.04 host and 8.04 guest. That's all. Thanks.

---

### Post by critin on 2012-08-29
> **A4driano said:**
> Ok, so I installed Ubuntu 8.04(guest) into Ubuntu 10.04(host) and everything is running fine. I have been trying to share my /home folder to open it while using Ubuntu 8.04 (guest). I am using Virtualbox, Guest Addittions and both operating systems are updated. I also added my user to vboxusers group and it does not work. I was able to share files when I had Ubuntu 12.04 as host but now I do not know why this do not work with my Ubuntu 10.04. I had opened "/home" that was located in "media" but now it does not work with 10.04 host and 8.04 guest. That's all. Thanks.

right click on the folders you want to share and click SHARE.  Right click and open PROPERTIES. Add permissions.  I don't remember the steps in the 8.04 and 10.04 versions, but they shouldn't be too different from 12.04.  I've listed the various ways, check them in your versions.

The system may add samba shares, or you may have to add it from Software Center.  Either way, you will need samba to share and the permissions to share must be activated in both systems.

---

### Post by 2F4U on 2012-08-29
Did you read the VirtualBox documentation about folder sharing?

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

Works fine for my VM's.

---

### Post by Morbius1 on 2012-08-29
> **A4driano said:**
> Ok, so I installed Ubuntu 8.04(guest) into Ubuntu 10.04(host) and everything is running fine. I have been trying to share my /home folder to open it while using Ubuntu 8.04 (guest). I am using Virtualbox, Guest Addittions and both operating systems are updated. I also added my user to vboxusers group and it does not work. I was able to share files when I had Ubuntu 12.04 as host but now I do not know why this do not work with my Ubuntu 10.04. I had opened "/home" that was located in "media" but now it does not work with 10.04 host and 8.04 guest. That's all. Thanks.

Just to clarify:

** You created a Ubuntu 8.04 guest on Ubuntu 10.04
** You created a [COLOR=Blue]**VirtualBox Shared Folder**[/COLOR] pointing to /home on the host.

What should have happened when you started the 8.04 guest is that the shared folder is automatically mounted to:
> /media/sf_*sharename*Are you saying that didn't happen?

Or are you saying you don't have access to /media/sf_[I]sharename?

[/I]If it's the second one it may be because you are not a member of the vboxsf group _[COLOR=Blue]on the guest[/COLOR]_:
```
sudo gpasswd -a your-user-name vboxsf
```Then logoff the guest and login again for the memebership change to take affect.

---

### Post by A4driano on 2012-08-29
OK, last time I did it with Ubuntu 12.04  			 				**/media/sf_*sharename ***were there and everything was running fine. Now  			 				**/media/sf_*sharename ***does not exist. So I can not access  			 				**/media/sf_*sharename.***

/home is shared and with automatic mount option. So it is supposed that I can access /home folder from /media. I added my Ubuntu 8.04 user to vboxsf group, with graphical interface and using terminal.
[INDENT]sudo usermod -aG vboxsf myuser


[/INDENT]I also have permissions with host: vboxusers group and VirtualBox option of user privileges.

sudo -s
nautilus
Share options
Inside media

But /home sf is not there. Maybe some folder permissions, but I just simply do not understand. Thanks everyone by answering.

---

### Post by dodo3773 on 2012-08-30
Are you trying to mount /home or /home/username as your shared folder? Try to do /home/username or /home/username/sharedfolder

---

### Post by Morbius1 on 2012-08-30
Are you using the VBox application installer in the repositories or are you using the one from Oracle directly? If you used the one from Oracle is it the same one you installed in Ubuntu 12.04 because each version of the Ubuntu host has a different version of VirtualBox. You need to install the one for Ubuntu 10.04 not the one you installed in Ubuntu 12.04.

Outside of that I don't know why the VBox shared folder mechanism isn't working unless you installed the guest additions package but didn't install it in the guest: VBox > Devices > Install Guest Additions

You can create a samba share on the host and then access the share that way. It won''t be in /media it will be in $HOME/.gvfs. Since this is a VBox guest you can also set up SSH and just have access to the whole host:

On the host install the following package:
```
sudo apt-get install openssh-server
```On the guest access the host through:
nautilus ssh://host-ip-adress
OR
nautilus ssh://host-name

---

### Post by A4driano on 2012-08-30
I have just solved my problem, I reinstalled Ubuntu 8.04 and now I can share files. Weird thing is that it did not work first time. I had VirtualBox for Lucid, Guest Addtitions and everything was well done. So, I reinstalled guest O.S. and works, I do not know why. Thanks a lot for helping me.

---

### Post by A4driano on 2012-08-30
> **A4driano said:**
> I have just solved my problem, I reinstalled Ubuntu 8.04 and now I can share files. Weird thing is that it did not work first time. I had VirtualBox for Lucid, Guest Addtitions and everything was well done. So, I reinstalled guest O.S. and works, I do not know why. Thanks a lot for helping me.

I also have to say that if Guest Additions is reinstalled after updating guest operating system, sharing files could work again.

Reinstall Guest Additions:

sudo /media/cdrom/VBoxLinuxAdditions.run

---

