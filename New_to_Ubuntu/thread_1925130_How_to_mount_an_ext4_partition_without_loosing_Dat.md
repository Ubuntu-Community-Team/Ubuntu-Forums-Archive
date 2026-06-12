---
title: "How to mount an ext4 partition without loosing Data"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by vinvinod on 2012-02-14
Hi,
I have been using ubuntu 10.04 LTS for last one year..
i had a 250 GB harddrive. 
around 100 gb was for ubuntu. its name as i found in gparted was sda1 (ext4 partition)
another partition 136 GB sda6 (ext4) which was mounted in /home.
another partition 3GB sda5 which was linux swap.

sda5 and sda6 were extended partitions.

Recently i had to install windows 7. so i shrinked sda1 partition using ubuntu live cd and created a 30GB ntfs partition. I installed windows on it.
Now i could not boot ubuntu. I knew this would happen and i had gone through the various threads to fix this problem.
So i fixed the grub booting from live cd and using boot-repair (*ppa*:*yannubuntu*/*boot*-[I]repair).


Now the real problem occurred. Ubuntu was booting. But It said 
[/I]*"an error occurred while mounting /home. press s to skip* mounting or *M* for *manual*  recovery"[I]
i pressed s and i cant see my usual nautilus desktop and taskbars. Its a blank desktop. i can start terminal by "ctrl+alt+t".

[/I][I]i did googling the problem.
 [/I]```
sfdisk -l 
```[I] 
(attached) showed that the partition names are changed. 

[/I]*i booted live cd and checked using gparted. (**The image is attached.). **it  shows sda6 as unallocated. how can i rename that as sda6 and mount that  to /home without loosing data. *
*I dont know how to fix.*[I]I have some important project files that i dont want to loose.

[/I]sda2 has windows and sda1 has ubuntu. how to mount that unallocated space as /home.?

[ATTACH]212653[/ATTACH]

[ATTACH]212654[/ATTACH]
[I]
Please help.


[/I]

---

### Post by vinvinod on 2012-02-14
I have been searching about the above said problem.

According to [http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

I need to add a line for sda6 to the partition table.
I saved my partition table using the code 
```
sudo sfdisk -d /dev/sda > Table.txt
```

Please tell me the new line i have to add for sda6. file Table.txt is attached.

---

### Post by vinvinod on 2012-02-14
The Problem is solved. I used testdisk to restore the partition into the table..
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

