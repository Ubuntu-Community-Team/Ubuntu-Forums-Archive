---
title: "Can I partition a hard drive without formatting"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Amish_Gramish on 2008-05-02
Because my experience Hardy Heron has been just like Vista (barely anything works, and if it does it doesn't work well, and it is clunky as hell) I'm going to try to install Windows XP.

Because I still want to keep Ubuntu, I just want to make a partition and install Windows XP on that.  (Someone helped me with Flash and getting the wireless working, so I don't want to have to reinstall Ubuntu 7.10, and 8.04 isn't recognizing external hard drives, so I can't back up my data without writing to DVDs.)

I have a Compaq Presario F572US, AMD64, and I currently have Ubuntu 8.10.
I have a CD with GParted on it, but I don't know what to do with it without formatting my hard drive.

Any help?

---

### Post by tjwoosta on 2008-05-02
well i dont know what your windows install disc is like but when i tried manking a partition with ubuntu and putting windows on it windows just installed on the whole disc writing over ubuntu without ever asking what partition i wanted it on
then i had to shrink and reinstall ubuntu

but to answer your question yes you can add partitions or shink existing ones without reformating its just a matter of installing windows to the correct partition without it writing over all of them

edit: also to do it you just go into gparted and right-click the drive you want to shrink then click resize (or shrink) im not sure what it says exactly

---

### Post by kshtjsnghl on 2008-05-02
I think that you can certainly do it through your gparted.

Just reboot with your hardy live cd and then from partition editor resize the partition of the your ubuntu partition .

I am not quite sure but then you might have set the partiton type as ntfs.
after installing windows it will remove the grub of ubuntu which you can again restore by using super grub cd or you will have to boot through live cd and then try to setup the grub to your ubuntu partiton...(which you can find in the some threads).

---

### Post by kshtjsnghl on 2008-05-02
this link might be useful for you to restore the grub..

[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

---

### Post by Amish_Gramish on 2008-05-02
I thank all of you!
With Windows, you don't have to format it as NTFS, as it works with both, but it just prefers NTFS.
I updated my 7.10 to 8.04 without making a LiveCD, so I am downloading the 8.04 LiveCD as we speak.
I'll try out installing Windows XP on the NTFS partition, and if I can't reinstall it on the NTFS partition or if it instead installs on the Ubuntu partition, I guess I'll just have to reinstall Ubuntu...

Well, thanks for all of your help!

---

