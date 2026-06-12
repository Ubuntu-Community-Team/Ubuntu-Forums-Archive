---
title: "Unable to download/install today's updates"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by harfin on 2014-09-26
Was advised new updates available, but at start of process I was messaged to say that boot needed to be freed up as there was insufficient space.  Advised to run sudo apt-get clean. Entered that on terminal, was asked for my password and within 30 seconds it appeared to have completed.

Update still says insufficient space on boot.

Laptop has large HD (735 GB) free space and ample memory (3.5GiB). Nothing in the rubbish bin. Downloads cleared.

Help!

Alan

---

### Post by harfin on 2014-09-26
Actual message was:
***"Not enough free diskspace***
***The upgrade needs atotal of 81.6 M free space on disk '/boot'. Please free at least anadditional 73.9 M of disk space on '/boot'. Empty your trash andremove temporary packages of former installations using 'sudo apt-getclean'."***

---

### Post by slickymaster on 2014-09-26
Most probably your **/boot** partition is filled with old kernels. You can easily remove the old kernels if you know which packages they came in but firstly can you please provide us the output of```
ls -l /boot
```and```
uname -a
```

---

### Post by ajgreeny on 2014-09-26
Once again we seem to have this problem of a separate /boot partition.

I have been using Ubuntu for 9 years now and suddenly this seems to be happening with increasing frequency.  I can only assume it is because users are choosing either LVM partitions or encryption when the system is installed, or have followed some third party installation instructions which suggest that a separate /boot partition is the right way to go.

@OP
Do you have either LVM or an encrypted system?

Either way, you definitely need to remove old kernels, and probably the simplest way to do that, once we know what is on your system from the commands shown by stickymaster, is to search for them by version number using synaptic, which you will need to install first as it is no longer installed by default.

---

### Post by Impavidus on 2014-09-26
If you're running 14.04, the command```
sudo apt-get autoremove
```should automatically remove old kernels.

---

### Post by harfin on 2014-09-26
> **slickymaster said:**
> Most probably your **/boot** partition is filled with old kernels. You can easily remove the old kernels if you know which packages they came in but firstly can you please provide us the output of```
ls -l /boot

harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -l /boot
total 212206
-rw-r--r-- 1 root root  1158016 May  3 01:30 abi-3.13.0-24-generic
-rw-r--r-- 1 root root  1162712 Jul 15 05:29 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1162712 Jul 29 18:41 abi-3.13.0-33-generic
-rw-r--r-- 1 root root  1162712 Aug 13 17:45 abi-3.13.0-34-generic
-rw-r--r-- 1 root root  1163858 Aug 15 03:56 abi-3.13.0-35-generic
-rw-r--r-- 1 root root   165510 May  3 01:30 config-3.13.0-24-generic
-rw-r--r-- 1 root root   165611 Jul 15 05:29 config-3.13.0-32-generic
-rw-r--r-- 1 root root   165611 Jul 29 18:41 config-3.13.0-33-generic
-rw-r--r-- 1 root root   165611 Aug 13 17:45 config-3.13.0-34-generic
-rw-r--r-- 1 root root   165652 Aug 15 03:56 config-3.13.0-35-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     1024 Aug 30 11:56 grub
-rw-r--r-- 1 root root 29062733 Jul 28 13:55 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root 29215274 Jul 28 13:58 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 29214088 Aug 12 07:28 initrd.img-3.13.0-33-generic
-rw-r--r-- 1 root root 29214922 Aug 21 08:46 initrd.img-3.13.0-34-generic
-rw-r--r-- 1 root root 29221946 Aug 30 11:56 initrd.img-3.13.0-35-generic
drwx------ 2 root root    12288 Jul 28 12:48 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3372643 May  3 01:30 System.map-3.13.0-24-generic
-rw------- 1 root root  3381262 Jul 15 05:29 System.map-3.13.0-32-generic
-rw------- 1 root root  3381262 Jul 29 18:41 System.map-3.13.0-33-generic
-rw------- 1 root root  3381262 Aug 13 17:45 System.map-3.13.0-34-generic
-rw------- 1 root root  3386444 Aug 15 03:56 System.map-3.13.0-35-generic
-rw------- 1 root root  5776416 May  3 01:30 vmlinuz-3.13.0-24-generic
-rw------- 1 root root  5798112 Jul 15 05:29 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  5800024 Jul 28 13:10 vmlinuz-3.13.0-32-generic.efi.signed
-rw------- 1 root root  5798688 Jul 29 18:41 vmlinuz-3.13.0-33-generic
-rw------- 1 root root  5800600 Aug 12 07:28 vmlinuz-3.13.0-33-generic.efi.signed
-rw------- 1 root root  5797728 Aug 13 17:45 vmlinuz-3.13.0-34-generic
-rw------- 1 root root  5799640 Aug 14 07:59 vmlinuz-3.13.0-34-generic.efi.signed
-rw------- 1 root root  5806368 Aug 15 03:56 vmlinuz-3.13.0-35-generic


and[CODE]uname -a
```

Linux harfin-HP-255-G1-Notebook-PC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
harfin@harfin-HP-255-G1-Notebook-PC:~$ ^C
harfin@harfin-HP-255-G1-Notebook-PC:~$ 

Alan

---

### Post by harfin on 2014-09-26
> **ajgreeny said:**
> Once again we seem to have this problem of a separate /boot partition.

I have been using Ubuntu for 9 years now and suddenly this seems to be happening with increasing frequency.  I can only assume it is because users are choosing either LVM partitions or encryption when the system is installed, or have followed some third party installation instructions which suggest that a separate /boot partition is the right way to go.

@OP
Do you have either LVM or an encrypted system?

Either way, you definitely need to remove old kernels, and probably the simplest way to do that, once we know what is on your system from the commands shown by stickymaster, is to search for them by version number using synaptic, which you will need to install first as it is no longer installed by default.

The laptop is encrypted yes.

I have just posted the requested data

Alan

---

### Post by slickymaster on 2014-09-26
You have several options to remove those old kernels, one being the suggestion ajgreeny made, using Synpatic for the effect or you could use this a one liner command I use ([written by a fellow forum moderator]("http://ubuntuforums.org/showthread.php?t=1961409&p=11856265&viewfull=1#post11856265")), that will delete all the old kernels, keeping only the you're current running, which is 3.13.0-35, and the previous as a safety fallback, which is 3.13.0-34.
If you opt for this solution, open a terminal window and run:```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```Reboot and then check you /boot partition```
du -h /boot --max-depth=0
```

---

### Post by harfin on 2014-09-26
> **slickymaster said:**
> You have several options to remove those old kernels, one being the suggestion ajgreeny made, using Synpatic for the effect or you could use this a one liner command I use ([written by a fellow forum moderator]("http://ubuntuforums.org/showthread.php?t=1961409&p=11856265&viewfull=1#post11856265")), that will delete all the old kernels, keeping only the you're current running, which is 3.13.0-35, and the previous as a safety fallback, which is 3.13.0-34.
If you opt for this solution, open a terminal window and run:```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```Reboot and then check you /boot partition```
du -h /boot --max-depth=0
```
Done the first bit. It seemed to on for a long time!
Will now reboot etc.
Alan

---

### Post by harfin on 2014-09-26
> **slickymaster said:**
> You have several options to remove those old kernels, one being the suggestion ajgreeny made, using Synpatic for the effect or you could use this a one liner command I use ([written by a fellow forum moderator]("http://ubuntuforums.org/showthread.php?t=1961409&p=11856265&viewfull=1#post11856265")), that will delete all the old kernels, keeping only the you're current running, which is 3.13.0-35, and the previous as a safety fallback, which is 3.13.0-34.
If you opt for this solution, open a terminal window and run:```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```Reboot and then check you /boot partition```
du -h /boot --max-depth=0
```
Did as suggested and got the following:
du -h /boot --max-depth=0
du: cannot read directory ‘/boot/lost+found’: Permission denied
55M	/boot


Is that the expected response?
Alan

---

### Post by slickymaster on 2014-09-26
```
sudo du -h /boot
``` should do the job.

Also have you tried to```
sudo apt-get update && sudo apt-get upgrade
```to check if you're still getting the same error message?

---

### Post by harfin on 2014-09-27
> **slickymaster said:**
> ```
sudo du -h /boot
``` should do the job.

output:
3.4M	/boot/efi/EFI/ubuntu
3.4M	/boot/efi/EFI
3.4M	/boot/efi
12K	/boot/lost+found
2.4M	/boot/grub/fonts
2.9M	/boot/grub/x86_64-efi
9.0K	/boot/grub/locale
7.5M	/boot/grub
55M	/boot



Also have you tried to```
sudo apt-get update && sudo apt-get upgrade
```to check if you're still getting the same error message?
I am currently running the update and I did not get the error message like before

Do I assume I may need to something similar to your 'clean up' above after a few more updates piling up?

Many thanks for your patience!

Alan

---

### Post by slickymaster on 2014-09-27
> **harfin said:**
> I am currently running the update and I did not get the error message like before
Since you didn't get any error messages while running the update commands I think you're OK now and you might want to [mark the thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for this type of issues.
> **harfin said:**
> Do I assume I may need to something similar to your 'clean up' above after a few more updates piling up?
If you're referring to kernels update, yes. Or else you'll be facing a similar situation in a matter of months. But like Impavidus already stated if you're running 14.04, the command```
sudo apt-get autoremove
```should automatically remove old kernels.
> **harfin said:**
> Many thanks for your patience!
Alan
You're welcome. Just glad you got it fixed and working.
Happy *buntuing.

---

