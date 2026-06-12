---
title: "copying Virtual machines"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Roen hayden on 2008-06-10
how do I copy one vmware server machine to another computer that has vmware server.  also how can I do the same thing for virtual box.

---

### Post by HalPomeranz on 2008-06-10
I can't comment on Virtual Box, because I don't use it, but the VMware machine images can just be copied like regular files.  

First make sure that the virtual machine is shut down before you do the copy.  Once you take care of that, you can use something like rsync to do the copy from one machine to another:

```

rsync -avH /path/to/virtual/machine/ somehost:/new/install/directory/

```

Obviously you'll need to make appropriate substitutions in the command above for the directory and host names.

---

### Post by Roen hayden on 2008-06-10
no i mean how find the files i need to copy and burn them to a disk and then add them to the VMware server on the other computer.

---

### Post by HalPomeranz on 2008-06-10
To find out what directory the VMware virtual machine is running from, select "VM -> Settings", click on the "Options" tab.  Under the "General" category you should see the "Working Directory" setting:  that's where the virtual machine's files live on disk.

Copy that directory to the other machine using whatever mechanism you want.  To run the copied virtual machine, select "File -> Open..." and then click the "Browse" button.  Navigate to the directory where you copied the virtual machine and double-click the appropriate file.

---

### Post by Roen hayden on 2008-06-10
thanks for you help.  And btw do you mind telling me what do you prefer Vmware server or virtaul box?

---

### Post by Oldsoldier2003 on 2008-06-10
> **Roen hayden said:**
> thanks for you help.  And btw do you mind telling me what do you prefer Vmware server or virtaul box?

there are fans of both camps here on the forums. I personally use VirtualBox , but not the OSE version from the repositories. I use the PUEL version available on their website.

---

### Post by Roen hayden on 2008-06-10
Ok cool I&#8217;m also thinking of using virtualbox I have use the free version in past but I may use the puel version so I can usb support.  I found this guide here on how to install and configure it.

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

And do you know how to copy a os you install in virtualbox to another one?

Again thanks for you help.

---

### Post by Duck2006 on 2008-06-10
I find virtual box is best.

---

### Post by HalPomeranz on 2008-06-10
> **Roen hayden said:**
> thanks for you help.  And btw do you mind telling me what do you prefer Vmware server or virtaul box?

In my case it's just because VMware was available long before Virtual Box came on the scene.  Like most technology, people tend to stick with the one they use first.  I've never even tried Virtual Box, so I can't comment on which is better.

---

### Post by Vivaldi Gloria on 2008-06-10
Virtualbox uses .vdi files for virtual disk drives. Let us say that you have an OS intalled on a hd named oshd.vdi on the first computer. 

Copy that oshd.vdi file to another computer and on that second computer start virtualbox and click new and choose oshd.vdi as the hd and also choose the same amount of ram etc. as in the first computer. Then you'll have an exact copy of the os in the virtualbox of the first computer.

---

### Post by dje on 2008-06-10
> **Roen hayden said:**
> Ok cool I’m also thinking of using virtualbox I have use the free version in past but I may use the puel version so I can usb support.  I found this guide here on how to install and configure it.

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

And do you know how to copy a os you install in virtualbox to another one?

Again thanks for you help.

+1 for virtualbox puel and that guide is very good

---

### Post by Duck2006 on 2008-06-10
Are both these computers the same, if not your have to redo your drivers  (video & sound ect) on the new computer.

---

### Post by Vivaldi Gloria on 2008-06-10
> **Duck2006 said:**
> Are both these computers the same, 

I wrote for different computers. 

> **Duck2006 said:**
> if not your have to redo your drivers  (video & sound ect) on the new computer.

You just choose "pulseaudio" from a menu for sound. Simple as that. No need for video drives. You have a slider for how much video ram you want to give to the virtual os.

Just install it and you will immediately get it. It is really easy once you see it.

---

### Post by newbuntuxx on 2008-06-10
see this chart:

[http://www.virtualbox.de/wiki/VBox_vs_Others](http://www.virtualbox.de/wiki/VBox_vs_Others)

---

