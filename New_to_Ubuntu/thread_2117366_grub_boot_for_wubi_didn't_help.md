---
title: "grub boot for wubi didn't help"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by wtrypste on 2013-02-18
Hi all
 
I have wubi-installed ubuntu 12.04 LTS (dual boot with windows 7).
Last week, when I wanted to boot into ubuntu I got the grub command line. (obviously smthg is wrong..)
 
I scanned web and this forum for finding a solution but I could'nt find something that fits my problem.
 
By accident (when I was still running ubuntu and moving/copying files in terminal) I copied some folders (like /root, /boot, /lost+found, /sbin, /lib, ...) into the /opt directory.
 
When I restarted I got the grub command line ( I figured that boot files, grub files, vmlinuz, ... are all in the wrong directory). I tried following:
[http://ubuntuforums.org/showthread.php?t=1314064&page=7](http://ubuntuforums.org/showthread.php?t=1314064&page=7)
 
but didn't help.
 
I think I just have the move de directory's back to their old position but I can't find a command 'move' in the grub manual!
 
Help is required cuz I don't wont to reinstall wubi..
 
gr

---

### Post by oldfred on 2013-02-18
Welcome to the forums.

Once you mess up the / (root) file system it is almost always easier just to reinstall. You should not have been able to move those folders as only root can do that. 

Grub is the boot loader for Ubuntu and only has limited commands to load and boot, you are not in your system. And if / is not in correct places you cannot boot.

You may be able to chroot into your system if you want to attempt to fix, but with wubi it is a bit more complex. I do not really know wubi, but have a few links to get you started.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You need liveCD or flash drive and may need gksudo nautilus? But again you have to be extremely careful when in admistrator mode as deleting or moving any system files may break system. (as you have found out).
       sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt

If you like Ubuntu it may be time to go to a full partitioned install.
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)> 
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    

---

