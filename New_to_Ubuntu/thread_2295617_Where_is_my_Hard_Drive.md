---
title: "Where is my Hard Drive???"
date: 2015-09-20
forum: New to Ubuntu
---

### Post by Max_Kunstler on 2015-09-20
I installed Ubuntu on my Netbook. It's working fine, except I can't find my hard drive listed anywhere in Ubuntu.
For example, if I try to download an image from Google Images, it gives me an option to put it in a download
folder, but there's no hard drive listed. Looks like they made the file system interface radically different from Windows and
I don't like it so far. Am I supposed to just click on the Files Icon and just start making folders there?

---

### Post by Alex_Katsy on 2015-09-20
Hi,

Yes the Home directory is where you put all of your files. The Computer directory which is **/ **is where the system is installed and the programs are installed. 
In other words **/ **is your Local Disk C. 
So in Windows your Documents would in **C:\Users\(current user)\Documents**, in Linux it would be **/home/(current user)/Documents**.

---

### Post by buzzingrobot on 2015-09-20
Windows inherited and uses the file system created for DOS, which was very limited in its capacities due to the very limited hardware available at the time. That is, DOS was written for machines with only two floppy drives, which it labeled "A:" and "B:".  Later, when hard drives became available for PC's, this approach was simply extended:  The hard drive was treated as a big floppy drive and labeled "C:" 

To extend a Windows/DOS filesystem the user must add a new drive, which will be mapped to "D:" or "E:" or whatever, and then be aware of what files are located on which distinct drive.

Linux is derived from Unix, which was created before DOS and Windows existed (so no one "made the file system radically different from Windows"), for use on larger systems with different storage systems, i.e., multiple drives.  A Unix/Linux file system is built around partitions and directories, not individually separate drives. A Unix/Linux file system can exist on a single drive, or be extended across many drives.

---

### Post by grahammechanical on 2015-09-20
The Files icon is the launcher to the File Manager which is called Nautilus. We were going to call it Windows Exployer but Microsoft threatened legal action. That is not a true statement.

Linux developers have their own ideas about how a computer operating system should work and look and the names that utilities should have. If we don't like it we do not have to use Linux. After all we did not buy Linux. So, we have not lost financially.

The File Manager has a left hand pane that will list all the partitions on a hard disk with the exception of the swap partition. Now, depending on the version of Ubuntu that we are using we may see at the bottom of the left hand pane the words "File system," "Computer" or the machine name that we gave when we first installed Ubuntu. That is the hard disk or rather the partition that Ubuntu is installed in.

And that illustrates another point about Linux. It is constantly under development and the desktop environment and the user interface do change over time. As for creating new folders there are two ways to do that.

1) Right click the desktop wallpaper and select New folder. And we get a new unnamed folder on the desktop.
2) Open the File Manager and right click the main panel background and select New folder. Or open a folder and right click the panel background and select New folder.

---

