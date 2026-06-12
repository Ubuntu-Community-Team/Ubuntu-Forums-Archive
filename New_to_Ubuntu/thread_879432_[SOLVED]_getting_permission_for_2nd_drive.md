---
title: "[SOLVED] getting permission for 2nd drive"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by redbelly on 2008-08-04
i just installed ubuntu, i installed it on my main drive, sda, and i've mounted my 2nd internal drive, sdb. i can view the drive but i can save or edit it at all. i've searched around, at one point i thought i had it, but when i go to edit /etc/fstap, it's saying that i dont have permission to save the file after i make the changes to it. 

am missing something? this is my first experince with linux.

thanks
dan

---

### Post by bpowell2005 on 2008-08-04
> **redbelly said:**
> i just installed ubuntu, i installed it on my main drive, sda, and i've mounted my 2nd internal drive, sdb. i can view the drive but i can save or edit it at all. i've searched around, at one point i thought i had it, but when i go to edit /etc/fstap, it's saying that i dont have permission to save the file after i make the changes to it. 

am missing something? this is my first experince with linux.

thanks
dan

You need to edit /etc/fstab (not /etc/fstap) as root...so you'll type: sudo gedit /etc/fstab...or sudo nano /etc/fstab...whichever editor you prefer.

---

### Post by ingeva on 2008-08-04
> **bpowell2005 said:**
> You need to edit /etc/fstab ....

Editing the fstab file can be risky. Make sure you read all the documentation you need so you can get it right.

The first tip I give you is: Create a directory on SDA1 where you want the disk to be mounted. Use that name as a mount point for fstab.

The last line of my fstab is:

```

/dev/sdb1 /home/store   ext3    relatime,errors=remount-ro 0       1

```

"/dev/sdb1", is the name of the disk partition. "home/store" is where I have mounted the disk. Can be any regular directory but it should be empty, otherwise you won't get access to the original content after the disk is mounted.
"ext3" is the file system on my disk. Yours is probably "ntfs". Check!

Note that the fstab entry is ONLY necessary if you want the disk to be mounted automatically at startup.

---

### Post by erickghint on 2008-08-04
this is how i mounted my storage partition. 

mkdir /storage

sudo cp /etc/fstab /etc/fstab_backup

sudo nano /etc/fstab

in the editor --- 
on the bottom line
/dev/(place your drive/partition here. ex. sda1 or sdb1 etc...) 

it should look like this on the bottom line:

/dev/sda3   /storage   ext3    defaults    0   0

hit ctrl-x and save... now we're back to the terminal

mount -a

sudo chown -R username:username /storage
sudo chmod -R 755 /storage

now you should  have a storage directory (in your case this directory will be your second hdd) in your home folder. easily accessed, and with full permissions. 


I'm still kind new at all of this, so if I've made a mistake of any sort, please let me know.

---

### Post by redbelly on 2008-08-04
i figured it out, thanks for all the help.

if i want to change the location of the 2nd drive (reading directions online, i put it in my media file), is it as simple as remounting it? what do i need to do?

also, does it really matter where its located? since mounting, i've read that it should go into the /mnt folder, which would make sense to me. 

thanks
dan

---

### Post by drs305 on 2008-08-04
> **redbelly said:**
> i figured it out, thanks for all the help.

if i want to change the location of the 2nd drive (reading directions online, i put it in my media file), is it as simple as remounting it? what do i need to do?

also, does it really matter where its located? since mounting, i've read that it should go into the /mnt folder, which would make sense to me. 

thanks
dan


To change the mount point, just create the folder wherever you want it and change fstab to reflect the new mount point. The advantage/disadvantage of mounting in /media is that the volumes will appear on the Desktop unless you change some options with gconf-editor.

Once you have made the changes, you can run the 'sudo umount /dev/sdXX' and 'sudo mount /dev/sdXX' to remount the device in the new location.

There is also a gui way to edit fstab. See the link in my signature.

Please mark the thread SOLVED when you have no more questions or issues. Top right of the first post, Thread Tools.

---

### Post by northern lights on 2008-08-04
> **bpowell2005 said:**
> sudo gedit /etc/fstab...or sudo nano /etc/fstab

While for 'nano' 'sudo' works, please _never_ run graphical with 'sudo'. If they need to be run as superuser, use ```
gksu GRAPHICAL APP
```.

For references, compare with [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

