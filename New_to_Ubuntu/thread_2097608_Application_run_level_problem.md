---
title: "Application run level problem"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by ITGuyChris on 2012-12-23
Hello Everyone!

To start things off, I'm reliability new to Linux and using Ubuntu. I've had a 3 month class on it (in 2007!), but lately I've been leeching off of how-to's and formulating an understanding of how things work in the Linux environment (I'm mainly Windows Server\Desktop admin). So, onto my question:

Can I run the VMware View Client in run level 5 without launching a complete desktop GUI?


Here's what I have so far:

I have built a PXE server using Ubuntu Server 12.04 LTS following the instructions provided here:

[http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/](http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/)

I have tested the ability to launch a boot menu using a test virtual machine and thin client connecting to the PXE server, before I continue with building a client to serve up through PXE, I was wondering if my question I posted above would be possible. The reasoning behind not launching the entire desktop is due to client hardware restrictions. I'm mainly using equipment that is at minimum 4 years old (1GHz single core proc, 512MB RAM) and upgrading the client hardware will not be possible without stopping the project and spending a large amount of money for new hardware that will be able to connect to our VMware View environment. Hopefully this makes sense.


Thanks!

---

### Post by fdrake on 2012-12-23
> **ITGuyChris said:**
> 
Can I run the VMware View Client in run level 5 without launching a complete desktop GUI?

there is a post similar to your but the question was like : how to autostart the virtualbox . see this thread.

[http://ubuntuforums.org/showthread.php?p=12418758#post12418758](http://ubuntuforums.org/showthread.php?p=12418758#post12418758)

in order to be run with the run-level option vmware needs to be user specific independent. Virtualbox in this case wasn't able to do that.

---

### Post by ITGuyChris on 2012-12-23
Ah! That gives me a few ideas. 

I'm going to create a VM to test out a few things and I'll report back. Thanks for the tip!

---

### Post by ITGuyChris on 2012-12-26
Well, I was able to create a new Ubuntu 12.04.1 Desktop vm and modify the /etc/defaut/grub so it boots in run level 2 (text only). I was also able to install VMware View Client and I can start the application when I run the command /usr/bin/vmware-view but I do not get a GUI window. 

I feel like I'm still missing a few things. I did follow the thread posted above, but I'm trying to connect to a session broker server.

Update!

I was able to get this to run by performing the following:

1. edit /etc/defaut/grub and replace the line that says: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** and replace it with **GRUB_CMDLINE_LINUX_DEFAULT="text"**. Save and exit the text editor
2. run the command **sudo update-grub** to update the grub.cfg file.
3. edit /etc/rc.local and type xinit /usr/bin/vmware-view before exit 0. Save and exit text editor.
4. Reboot the OS by running **sudo reboot**. This will then allow you to auto-launch the VMware View Client without a full GUI.


If anyone is a mod, I'd like to write a step-by-step procedure for others and make it a sticky.

---

### Post by fdrake on 2012-12-26
glad you got it working.

you should open a new thread and wrtite the steps there too for future refence.

it seems like that the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" creates some issues to the server version fo ubuntu.

---

