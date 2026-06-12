---
title: "Boot Problems - Again"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by bencouve on 2014-03-31
Hi Experts,

I need some advice on getting my laptop booting again. I have tried a few things already. Please see below ...

ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work/boot
total 190812
drwxr-xr-x  3 root root     4096 Feb  3 10:49 .
drwxr-xr-x 27 root root     4096 Feb  3 10:46 ..
-rw-r--r--  1 root root  1006496 Jan 30 17:53 abi-3.11.0-15-generic
-rw-r--r--  1 root root   791023 Apr 11  2012 abi-3.2.0-23-generic
-rw-r--r--  1 root root   791132 May 24  2012 abi-3.2.0-25-generic
-rw-r--r--  1 root root   792532 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r--  1 root root   792830 Feb 19  2013 abi-3.2.0-38-generic
-rw-r--r--  1 root root   852490 May 14  2013 abi-3.5.0-30-generic
-rw-r--r--  1 root root   919810 Oct 23 09:42 abi-3.8.0-33-generic
-rw-r--r--  1 root root   919810 Dec  3 01:53 abi-3.8.0-35-generic
-rw-r--r--  1 root root   163245 Jan 30 17:53 config-3.11.0-15-generic
-rw-r--r--  1 root root   140279 Apr 11  2012 config-3.2.0-23-generic
-rw-r--r--  1 root root   140407 May 24  2012 config-3.2.0-25-generic
-rw-r--r--  1 root root   140488 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r--  1 root root   140488 Feb 19  2013 config-3.2.0-38-generic
-rw-r--r--  1 root root   148096 May 14  2013 config-3.5.0-30-generic
-rw-r--r--  1 root root   154961 Oct 23 09:42 config-3.8.0-33-generic
-rw-r--r--  1 root root   154950 Dec  3 01:53 config-3.8.0-35-generic
drwxr-xr-x  5 root root    12288 Feb  5 23:32 grub
-rw-r--r--  1 root root 17424749 Feb  3 10:49 initrd.img-3.11.0-15-generic
-rw-r--r--  1 root root 14164815 Jun 22  2012 initrd.img-3.2.0-23-generic
-rw-r--r--  1 root root 14170758 Oct 14  2012 initrd.img-3.2.0-25-generic
-rw-r--r--  1 root root 14204552 Mar  1  2013 initrd.img-3.2.0-32-generic
-rw-r--r--  1 root root 13537705 May 23  2013 initrd.img-3.2.0-38-generic
-rw-r--r--  1 root root 15440756 Nov 26 15:18 initrd.img-3.5.0-30-generic
-rw-r--r--  1 root root 16221264 Nov 26 19:12 initrd.img-3.8.0-33-generic
-rw-r--r--  1 root root 16446665 Feb  3 09:40 initrd.img-3.8.0-35-generic
-rw-r--r--  1 root root   176500 Jun 17  2013 memtest86+.bin
-rw-r--r--  1 root root   178680 Jun 17  2013 memtest86+_multiboot.bin
-rw-------  1 root root  3293845 Jan 30 17:53 System.map-3.11.0-15-generic
-rw-------  1 root root  2884358 Apr 11  2012 System.map-3.2.0-23-generic
-rw-------  1 root root  2886695 May 24  2012 System.map-3.2.0-25-generic
-rw-------  1 root root  2884076 Sep 26  2012 System.map-3.2.0-32-generic
-rw-------  1 root root  2887333 Feb 19  2013 System.map-3.2.0-38-generic
-rw-------  1 root root  2901505 May 14  2013 System.map-3.5.0-30-generic
-rw-------  1 root root  3062707 Oct 23 09:42 System.map-3.8.0-33-generic
-rw-------  1 root root  3068291 Dec  3 01:53 System.map-3.8.0-35-generic
-rw-------  1 root root  5631120 Jan 30 17:53 vmlinuz-3.11.0-15-generic
-rw-------  1 root root  4965840 Apr 11  2012 vmlinuz-3.2.0-23-generic
-rw-------  1 root root  4969488 May 24  2012 vmlinuz-3.2.0-25-generic
-rw-------  1 root root  4966768 Sep 26  2012 vmlinuz-3.2.0-32-generic
-rw-------  1 root root  4968592 Feb 19  2013 vmlinuz-3.2.0-38-generic
-rw-------  1 root root  5130128 May 14  2013 vmlinuz-3.5.0-30-generic
-rw-------  1 root root  5364816 Oct 23 09:42 vmlinuz-3.8.0-33-generic
-rw-------  1 root root  5391024 Dec  3 01:53 vmlinuz-3.8.0-35-generic
ubuntu@ubuntu:~$ Boot-Repair
Boot-Repair: command not found


I tried the Boot-Repair command which was suggested in another post of mine for a previous boot problem but it has not worked.

Just a quick history, I did upgrade to 13.04 from 12.04 and it ran fine for a month or two. I did try to recover with my usb version 
which was still at  12.04 and remeber running the Boot-Repair but it did not work, probably because I had upgraded. I have created a 13.04 iso on DVD which is working so am using that for the attempted recover. 

Please advise. Thanks in advance

---

### Post by Bashing-om on 2014-03-31
bencouve; Oh Boy !

That is an awfull lot of old kernels laying around taking up device space.
One reason that you may not be able to boot is out of room, and in the update process could not install the later kernel images (??).

It is best to get ya booting to something in order to trouble shoot this issue.
1) Can you boot in "recovery" mode ?
2) How about booting an older kernel ?
3) Maybe - just a maybe - boot to a texual terminal ?

There could be many other reasons for the failure-to-boot, we need some facts in this case .. what happens - in detail - when you attempt to boot via any of the above. Please provide the errors the system generates as you can. That would be good to know information.

[INDENT][INDENT]all things are possible
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-03-31
Every time you reboot live installer you have to re-download & install Boot-Repair.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

It looks like you have updated several times as you have many older kernels. May be time to houseclean.
You will have issues fixing 13.04 as it is not supported anymore.
      
 EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

### Post by bencouve on 2014-03-31
Ok, thanks for the repsonses, and sorry for being a pain....

I ran the diagnostic first and it gave this url

The url generated is [http://paste.ubuntu.com/7187416](http://paste.ubuntu.com/7187416)

The Recommended repair gave this url

[http://paste.ubuntu.com/7187431/](http://paste.ubuntu.com/7187431/)

I am now going to re-boot

---

### Post by bencouve on 2014-04-01
I decided to do a re-install. Thanks for the comments anyway

---

