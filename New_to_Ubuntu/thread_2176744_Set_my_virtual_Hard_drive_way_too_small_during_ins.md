---
title: "Set my virtual Hard drive way too small during installation"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by nikolai4441 on 2013-09-25
During installation of Ubuntu 13.04, i selected a 20 gigabyte virtual hard drive on accident, and I have 300 gigs left on my physical drive. I am getting warnings about storage running low so I need to know how to enlargen the virtual drive or make a new one.

---

### Post by whitesmith on 2013-09-25
Welcome to the forum! Your best choice is gparted, the Gnome Partition Editor that you can download from the Ubuntu Software Center, or by entering ```
sudo apt-get install gparted
``` in a terminal. With this editor you can resize the partition to whatever value you want. After installation the editor will be in Applications->System Tools->Administration. If this answers your question please use Thread Tools to mark this thread as closed.

---

### Post by Bashing-om on 2013-09-25
nikolai4441; Hi ! Welcome to the forum.

Along with whitesmith.
Show us what there is to work with .. maybe as easy as enlarging (resizeing) that partition with ubuntu's partition editor "GParted";
Post the output of terminal codes:
```

sudo fdisk
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

[INDENT][INDENT]ain't no step for a stepper

[/INDENT][/INDENT]

---

### Post by QIII on 2013-09-25
Hello!

Which virtualization solution are you using?  

You can clone your current virtual disk to a newly created larger one in Virtualbox and I believe you can manipulate the size of the virtual disk directly in VMWare.

If we drill down to the virtual machine itself you may have space, but if you created a / partition that was small you may have filled just that.

Which do you want to do:  Resize your virtual disk, or find out why the one you created is full?

---

