---
title: "Where to mount HDD?"
date: 2017-03-27
forum: New to Ubuntu
---

### Post by matovina-mario on 2017-03-27
Hello everyone. I'm new to linux. I have ubuntu 16.04 with kubuntu-desktop. I experimented with linux a bit over last year, but this time I think I'm here to stay. So here's my question

My hard drive that stores my data (it's not a system disk) is currently mounted in /media/mario/DOC. This is not very convenient location for me and I would like to mount it somewhere else, maybe in /root. Is that a good idea? Where would you recommend to mount it and that it's still easily accessible?

Mario

---

### Post by mastablasta on 2017-03-27
you can leave it where it is and add a symlink to it in your /home folder.

[http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link](http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link)


you can name the link however you want. but it will then always be there when you try to save things. you can also change the link icon so you will know it is your data disk you are saving to or taking data from.

---

### Post by Impavidus on 2017-03-27
You can mount is wherever you want, with two rules: Don't mount that data partition on a place already in use for other files (as they will be hidden behind the mounted partition) and don't mount it in a directory where some program expects other files. So /root is out of the question. Usually we mount such data partitions on a directory in /mnt. /mnt/data isn't too hard to find if you want to save or open some file, but you can make a symlink to make it even easier. Mount the partition automatically at boot by using fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by shridhar-kapshikar on 2017-03-27
It recommended that root partition would be reserved for system usage. User partition can be mounted on /mnt partition.

---

### Post by matovina-mario on 2017-03-27
Thanks guys. I was worried to mount it to /root and decided to ask here before. I already added hard drive to Fstab. I will check out symlinks.

---

### Post by oldfred on 2017-03-27
I use /mnt/data, but have sym-linked all the folders into /home.
If you want to see folders in Naulitus you need to use /media/ something as /mnt will not directly show in Nautilus and you have to go to computer & drill down to /mnt and where every actually mounted.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

