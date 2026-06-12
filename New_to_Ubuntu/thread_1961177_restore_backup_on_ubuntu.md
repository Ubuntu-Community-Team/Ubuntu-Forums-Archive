---
title: "restore backup on ubuntu"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by wadie on 2012-04-18
Hi,

I have a Windows 7 backup image which I want to restore on Ubuntu. is that possible ? if not,how can I have whatever I have on Windows 7 to be on Ubuntu and then remove Windows ?

Thanks fellows :)

---

### Post by Bucky Ball on 2012-04-18
Are you talking about data or programs or both? Is this a backup of your whole Windows 7 partition?

---

### Post by wadie on 2012-04-18
I'm talking about both.

This is a backup of my whole Windows 7 partition.

---

### Post by Bucky Ball on 2012-04-18
Your data's fine but Windows programs won't work in Ubuntu unless you're using Wine. They can't be installed natively. Not really sure what you're getting at here. If you want to use Windows why not just restore your Windows to a partition of its own and run Windows? Ubuntu is Ubuntu which is a Linux operating system, not Windows ... ;)

---

### Post by wadie on 2012-04-19
I don't want to run Windows..all I want from my windows right now is the data. forget about the programs.

How do I move all the data to Ubuntu and then remove Windows ?

Sorry for my stupid questions,I'm a total newbie.

---

### Post by Mark Phelps on 2012-04-19
> **wadie said:**
> ...How do I move all the data to Ubuntu and then remove Windows ?...

Presuming that Ubuntu is installed on its own separate partition, do the following ...

To migrate the data, open the MS Windows partition, and use a file Manager (e.g., Nautilus) to COPY the files from the Windows partition to the Ubuntu partition.  Use COPY because after this is done, you want to CONFIRM that all the files are intact inside the Ubuntu partition.  If you MOVE them and something goes wrong, you will have lost the files.

To remove Windows, simply use the Disk Utility or GParted to remove the MS Windows partition.  You can then create a data partition in its place and use that.

However ... if you installed Ubuntu from INSIDE MS Windows using Wubi, you can do NONE of this -- because when you then remove Windows, you will also remove Ubuntu.

---

### Post by wadie on 2012-04-19
I download Ubuntu the .iso and now I'll burn it to a DVD and install it by creating a partition. won't use webui.

Everything else should go fine,else I'll just post here again.

Thanks Mark.

---

### Post by Cheesemill on 2012-04-19
The most important question is what application did you use to make your Windows backup image.

This will let us know whether or not it is possible to recover the data into Ubuntu.

---

### Post by wadie on 2012-04-19
I used Windows built-in backup system

---

### Post by Cheesemill on 2012-04-19
In that case it's not going to be easy restoring the files into Ubuntu.

Your backup is probably saved as a .vhd file which is a proprietary Microsoft file format. You have 2 options for getting at your data:

Apparently it is possible to mount these files in Ubuntu but it means using the program vdfuse which isn't available through the Software Center, you will have to compile it from source code.

The other option is to install VirtualBox, then install a Windows VM and set up file sharing, and then attach the vhd file as a secondary hard drive to the VM before extracting the files.

---

### Post by wadie on 2012-04-21
I guess I'll just install Ubuntu 12.04 this Thursday on a new partition,then move the files I have on Windows 7 to Ubuntu. using Nautilus file manager.

Thanks.

---

