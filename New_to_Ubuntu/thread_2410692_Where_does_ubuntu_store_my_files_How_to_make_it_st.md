---
title: "Where does ubuntu store my files? How to make it store files to HDD instead of SSD?"
date: 2019-01-19
forum: New to Ubuntu
---

### Post by stabcode on 2019-01-19
Greetings.
I have a laptop with 128GB SSD (solid state drive) and 1TB HDD.
My question is where are the files and programs I install through Store and terminal(apt install) stored? Are they stored in SSD or HDD? 
If it is stored in SSD how to default it to HDD, so that only Ubuntu occupies SSD and rest eveything is stored in HDD.
Thank You.

---

### Post by TheFu on 2019-01-19
There is a **file system hierarchy standard** that is followed.
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

In general, Unix people use partitions to control which storage is used for each purpose by which directory (from the FSH) it is mounted onto.

It would be odd if the OS + all the application programs needed more than 25G total.  

Personal files are placed in the userid's HOME, unless the user does something special.  Many people will have a separate partition for /home.  This is common enough to have a guide about it - google finds it.

Some smart people here leave /home on their SSD, but make the subdirectories inside point to a data drive using symbolic links. Keeping tiny files like configs and settings on fast storage should make for a nicer experience. This is easier to accomplish than moving /home/ to a new partition since there aren't complexities of moving the HOME for a currently in-use userid.  Use the **ln -s source target** command.

---

### Post by SeijiSensei on 2019-01-19
The usual method in these situations is to install Ubuntu on the SSD and mount one or more filesystems on the HDD.

All the programs and associated files for *nix systems reside in directories like /bin, /usr/bin, /lib, /usr/lib, and the like.  You don't want to mess with any of those.  Putting them on the SSD will speed up loading an application's code and the libraries it requires.  

Everything that users own resides in the /home filesystem.  So if you choose "manual" when configuring the disks during installation, you'll be able to tell the installer to format the entire HDD as a single "ext4" filesystem and mount it as /home.  Then everything you create will reside in /home/yourusername on the hard drive.

You might consider telling the installer not to use the entire SSD for Ubuntu.  I recently installed Kubuntu 19.04, and it's currently occupying about 8 GB of space.  I'd consider using at most a 40 GB partition on the SSD for this installation.  Then if the time comes down the road you'd like to install another version of Linux, you could create another partition in the empty space.  With multiple installations you will be offered a choice at boot about which version you want to run.

---

