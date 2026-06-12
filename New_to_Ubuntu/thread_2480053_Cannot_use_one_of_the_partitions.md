---
title: "Cannot use one of the partitions"
date: 2022-10-17
forum: New to Ubuntu
---

### Post by rupertpumpkin on 2022-10-17
Hi, I've installed Kubuntu a few weeks ago alongside windows and remember creating 2 partitions; 22 GB for root and 270 GB for data. Unfortunately I hadn't validated partitions were created correctly and just realised now that I have an issue as I ran out of space on 1st partition. 
The issue is that I don't seem to have any access to perform any actions on the 2nd partition. I cannot create any folders nor copy any data to this partition. I installed gparted, deleted the partition and set up an new one but have the same issue. Its 272 GBP empty partition. Mount point says media so it almost looks like that is seeing this partition as external device, like usb or sth... I don't know....

I can see that 2nd partition in Dolphin and it is mounted so I'm not sure what's wrong. Did sth went wrong with install? Is there a way to resolve this issue so I can start using this partition? 

Here's result for lsblk:
[FONT=monospace][COLOR=#54FF54]**kuba@kuba-laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lsblk[/COLOR]
```
[sudo] password for kuba:  
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0 269,5M  1 loop /snap/brave/179
loop2         7:2    0 269,5M  1 loop /snap/brave/180
loop3         7:3    0    62M  1 loop /snap/core20/1587
loop4         7:4    0  55,6M  1 loop /snap/core18/2566
loop5         7:5    0  63,2M  1 loop /snap/core20/1623
loop6         7:6    0 238,1M  1 loop /snap/firefox/1918
loop7         7:7    0 236,8M  1 loop /snap/firefox/1943
loop8         7:8    0   219M  1 loop /snap/gnome-3-34-1804/77
loop9         7:9    0 346,3M  1 loop /snap/gnome-3-38-2004/115
loop10        7:10   0 346,3M  1 loop /snap/gnome-3-38-2004/119
loop11        7:11   0  91,7M  1 loop /snap/gtk-common-themes/1535
loop12        7:12   0  37,1M  1 loop /snap/hunspell-dictionaries-1-7-2004/2
loop13        7:13   0 153,8M  1 loop /snap/mailspring/519
loop14        7:14   0    48M  1 loop /snap/snapd/16778
loop15        7:15   0    48M  1 loop /snap/snapd/17029
nvme0n1     259:0    0 476,9G  0 disk  
&#9500;&#9472;nvme0n1p1 259:1    0   260M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part  
&#9500;&#9472;nvme0n1p3 259:3    0 180,3G  0 part /media/kuba/Windows
&#9500;&#9472;nvme0n1p4 259:4    0   595M  0 part  
&#9500;&#9472;nvme0n1p5 259:5    0   518M  0 part  
&#9500;&#9472;nvme0n1p6 259:6    0   488M  0 part  
&#9500;&#9472;nvme0n1p7 259:7    0   272G  0 part /media/kuba/776d07ed-c9ed-466e-bb62-03424c48ff98
&#9492;&#9472;nvme0n1p8 259:8    0  22,8G  0 part /var/snap/firefox/common/host-hunspell
                                      /

```
[/FONT]

---

### Post by oldfred on 2022-10-17
If internal drive, better to mount with fstab. And if not using fstab better to add labels, so default mount is by label which you can understand, rather than some long UUID.
You also have to give yourself ownership & permissions to use the partition if ext4 format. NTFS often auto mounts, but default permissions are less than optimal. 

Some examples, but you do not have to do the linking of folders.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &

Example, but you have to use your UUID or label & create your own mount point.
[https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)

Good examples:
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)

---

