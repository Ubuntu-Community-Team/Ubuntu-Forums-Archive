---
title: "Howto setup secure access with ntfs-3g"
date: 2007-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by zkeng on 2007-10-30
This howto shows how to mount an ntfs partition in a restricted folder and then bind parts of the partition to your user folder, so that you can access your user files on a windows partition but not any other files such as windows system files...

First I create a mount point (a mount point is just a folder) located in another folder I call "restricted". The mount point in my ubuntu machine will be like this:

/media/restricted/vista

Then I right-click the folder called "restricted" and navigate to the permissions tab and set the permissions so that only root can access it.

Now we will edit the /etc/fstab file to mount the ntfs partition.

First make a backup of it, in terminal write: "sudo cp /etc/fstab /etc/fstab_copy"

Now edit the file with gedit. In terminal write: "sudo gedit /etc/fstab"

To mount the ntfs partition add this line:


/dev/sda2 /media/restricted/vista  ntfs-3g users,locale=en_US.UTF-8,uid=1000,gid=1000,umask=0002 0 0


(The id of my ntfs partition is /dev/sda2, you can check what your id is by typing the following in terminal "sudo fdisk -l" and look for your ntfs file system)

After adding the above line, with the correct id, save and close the text editor.

Then its time to make mount points in your home folder for the Desktop and Documents folder in the windows account. (Note that in my case the user-name is "user" both in linux and windows and my windows system is vista.) The mount points will be like this:

/home/user/Vistadocs/Desktop
/home/user/Vistadocs/Documents

And finally we will make two binds in fstab that will enable these specific parts of the mounted ntfs file system from /media/restricted/vista in the home folder.

Open fstab again with "sudo gedit /etc/fstab"

Add the two lines below (but do not add the blank line in between them):


/media/restricted/vista/Users/user/Documents /home/user/Vistadocs/Documents none bind 0 0

/media/restricted/vista/Users/user/Desktop /home/user/Vistadocs/Desktop none bind 0 0


Save and close the text editor.

In terminal write the following to mount everything in your fstab without having to reboot: "sudo mount -a"

Thats it, now when you log in as the linux-user "user" you will have access to the windows-user "user" Desktop and Documents folder from your linux home folder, but you will not be able to reach any other files on the windows file system.

Hope it shows useful for anyone.
/Micke

---

