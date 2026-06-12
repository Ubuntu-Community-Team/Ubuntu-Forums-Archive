---
title: "Ubuntu only boots in command line"
date: 2023-10-23
forum: New to Ubuntu
---

### Post by thormine on 2023-10-23
Hello :)

I typed this command: [HTML]sudo apt-get remove python3[/HTML], then black screen!

Since then, when I boot Ubuntu, i only get Ubuntu in command line, without any graphical interface.

Do you know how to solve this problem?

Here is a Boot Info Summary : [https://paste.ubuntu.com/p/jQn3YhyRvr/](https://paste.ubuntu.com/p/jQn3YhyRvr/)

Thank you very much!

---

### Post by MAFoElffen on 2023-10-23
Ouch. My sincere condolences for your lose.

Do you have recent backups? Is so, restore them.

If not...Two choices...

1) Backup the data that is there. Install fresh. Restore the data.

2) Try to fix what is there. Noticing this is the "New To Ubuntu Section"... Unfortunately, that might be a bit above your skill level. APT packaging and networking is broken without Python3. I might have to spin up a VM, remove Python3 from it and see if this is even possible. I'm not sure if it is.

Let me see what is on the Ubuntu Installer LiveUSB ISO that might help, to see how deep we would have to dive into things to correct this... BRB

In the meanwhile, what Release of Ubuntu was this? And boot from a LiveUSB, even the Boot Info disk would work, and run the system-info script in my signature line and post the URL of where the report uploads to. We need to see what we are trying to rescue.

EDIT -- Yes. When you remove 'python3' it removes 'ubuntu-desktop', breaks apt, dpkg, and all networking, among other things. I only boots to a very crippled console.

---

### Post by MAFoElffen on 2023-10-23
Option 2 is possible to do, but you need to follow directions very carefully, and not do anything beyond what it says to do. If one command fails and has any errors, stop there and post back to say what is going on or ask any questions if unsure of anything. Understood?

Note that you went ahead and did a repair with the Boot Repair disk... And it failed, because it could not find any EFI Variables. That may have caused additional problems, but we can deal with those, if we need to. Lesson learned, if you do have booting problems, run the boot-info report on that disk, then post the URL of that report, without doing the repair, for one of us to look at first, before any repair. 

Required is that you have an Ubuntu Installer LiveUSB... That is created as GPT, so that it only boots as UEFI boot mode... If you do not understand what that means, please ask.

Boot from it. Open a Browser and get back to these instructions, so you can cut and paste commands into.

Open a terminal session. These are the commands:
```

sudo ls /sys/firmware/efi/efivars

```
If that does not return lots of output, stop right there. That would mean that it booted in the wrong boot mode.

If okay, then
```

sudo su
lsblk -e7
mount /dev/nvme0n1p4 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /proc  /mnt/proc
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
mount -a
apt update
apt install --reinstall python3 ubuntu-desktop
exit
reboot

```
Tell us if it rebooted.

If not then I will continue with instructions to manually re-install the boot loader, Grub2.

---

### Post by thormine on 2023-10-24
Thank you so much for your help!

I only have partial backups... I planned to learn how to make complete backups next week when I have time, but it's too late haha

Here is the system-info report: [https://termbin.com/nsjg](https://termbin.com/nsjg)

I'm going to follow option 2. I'm sorry to have done a Repair with the Boot Repair disk. I will not do it again. I definitely have a lot to learn so I will carefully follow your instructions.

> Required is that you have an Ubuntu Installer LiveUSB... That is created  as GPT, so that it only boots as UEFI boot mode... If you do not  understand what that means, please ask.

I have an Ubuntu Installer LiveUSB. I've used it to make the boot info report and the system info report and I use it to post messages here. However I don't understand what GPT and UEFI boot mode are.

Can I can start to follow the instructions you gave me or is there anything I need to do/understand before?

Again, thank you very much for your help :)

---

### Post by MAFoElffen on 2023-10-24
You can start. The report said when you ran it, that it was in UEFI Boot mode, and that the LiveUSB you ran it from had a GPT partition type. You are good so far.

---

### Post by ActionParsnip on 2023-10-24
Could possibly chroot in. Python is a big part of Linux

---

### Post by thormine on 2023-10-24
Okay, thank you very much

All commands worked until 'aot update' :

```
ubuntu@ubuntu:~$ sudo ls /sys/firmware/efi/efivars
[lots of output]
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# lsblk -e7
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    1   7.2G  0 disk 
&#9500;&#9472;sda1        8:1    1   4.7G  0 part /cdrom
&#9500;&#9472;sda2        8:2    1   4.9M  0 part 
&#9500;&#9472;sda3        8:3    1   300K  0 part 
&#9492;&#9472;sda4        8:4    1   2.5G  0 part /var/crash
                                      /var/log
nvme0n1     259:0    0 476.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   260M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 303.8G  0 part 
&#9500;&#9472;nvme0n1p4 259:4    0 170.9G  0 part 
&#9492;&#9472;nvme0n1p5 259:5    0     2G  0 part 
root@ubuntu:/home/ubuntu# mount /dev/nvme0n1p4 /mnt
root@ubuntu:/home/ubuntu# mount --make-private --rbind /dev  /mnt/dev
root@ubuntu:/home/ubuntu# mount --make-private --rbind /sys  /mnt/sys
root@ubuntu:/home/ubuntu# mount --make-private --rbind /proc  /mnt/proc
root@ubuntu:/home/ubuntu# mount --make-private --rbind /run  /mnt/run
root@ubuntu:/home/ubuntu# chroot /mnt /usr/bin/env bash --login
root@ubuntu:/# mount -a
root@ubuntu:/# aot update
bash: aot: command not found
```

---

### Post by Rubi1200 on 2023-10-24
Spelling mistake.

It should be **apt** update

Try the command again.

---

### Post by thormine on 2023-10-24
Alright thanks

'apt update' worked fine

The next command produced this :

```
root@ubuntu:/# apt install --reinstall python3 ubuntu-desktop
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by Rubi1200 on 2023-10-24
If you are still root then you can run this:

```
dpkg --configure -a
```

If there are errors stop and post them here.

---

### Post by thormine on 2023-10-24
Alright thanks

None of the following commands produced an error. When I typed 'reboot', the PC didn't reboot but instead was blocked on a screen which you can see in attached file. So I pressed the power button to shut down the PC. Now Ubuntu boots normally :) Thank you all for your help

However while booting it displays stuff which I don't know what it means. You can see it in attached file. Maybe it's not a problem, I'm just asking :) (This stuff already displayed before I removed python3, but while we're at it, I think I'd better ask you.)

---

### Post by Rubi1200 on 2023-10-24
If you are booting normally again that is great news.

I would wait until MAFoElffen comes online or sees the responses. He may have additional comments or checks you need to do.

---

### Post by MAFoElffen on 2023-10-24
The first were messages about your USB Flash drive,. That shows up as /dev/sda right? Which really is just temporary? Not really part of your computer right? Is so, then check the filesystem of the partitions. If not, just rewrite the LiveUSB image and recheck it.

The boot messages in the second attachment are harmless APCI warnings, not errors, that show up with some BIOS's and can be ignored. The warning about "integrity:  problem loading x.509 certificate" is also a warning, and if you want, can be investigate further by doing:
```

journalctl -b -l -g 'X\.509' --no-pager

```
That will show you which X.509 certificates were loaded, and which one had a problem... Which is usually an outdated certificate in the BIOS. Since you have SecureBoot disabled it's no really a problem.

I do not know how to remove an outdated X.509 security that is within the BIOS. I have not seen or heard of anyone really doing that. Most are told what it is an left to accept and ignore it.

---

### Post by #&amp;thj^% on 2023-10-24
Just my effort to help along with MAFoElffen's  great advice we have a tool to help:
```
certutil -viewstore
certutil - Utility to manipulate NSS certificate databases

Usage:  certutil <command> -d <database-directory> <options>

Valid commands:
-A              Add a certificate to the database        (create if needed)
-B              Run a series of certutil commands from a batch file
-E              Add an Email certificate to the database (create if needed)
-C              Create a new binary certificate from a BINARY cert request
-G              Generate a new key pair
-D              Delete a certificate from the database
--rename        Change the database nickname of a certificate
-F              Delete a key and associated certificate from the database
-U              List all modules
-K              List all private keys
-L              List all certs, or print out a single named cert (or a subset)
--build-flags   Print enabled build flags relevant for NSS test execution
-M              Modify trust attributes of certificate
-N              Create a new certificate database
-T              Reset the Key database or token
-O              Print the chain of a certificate
-R              Generate a certificate request (stdout)
-V              Validate a certificate
-W              Change the key database password
--upgrade-merge Upgrade an old database and merge it into a new one
--merge         Merge source database into the target database
-S              Make a certificate and add to database

certutil -H <command> : Print available options for the given command
certutil -H : Print complete help output of all commands and options
certutil --syntax : Print a short summary of all commands and options

```
I also agree nothing needs to be done about that on a user's end as shown here for mine:
```
journalctl -b -l -g 'X\.509' --no-pager
Oct 24 07:03:56 crystal-arch kernel: Loading compiled-in X.509 certificates
Oct 24 07:03:56 crystal-arch kernel: Loaded X.509 cert 'Build time autogenerated kernel key: 59dfc31c07d37df63ce2b45e0dda2b911d93d5ed'
Oct 24 07:03:56 crystal-arch kernel: integrity: Loading X.509 certificate: UEFI:db
Oct 24 07:03:56 crystal-arch kernel: integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53'
Oct 24 07:03:56 crystal-arch kernel: integrity: Loading X.509 certificate: UEFI:db
Oct 24 07:03:56 crystal-arch kernel: integrity: Loaded X.509 cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bd82709c8cd54f316ed522988a1bd4'
Oct 24 07:03:56 crystal-arch kernel: integrity: Loading X.509 certificate: UEFI:db
Oct 24 07:03:56 crystal-arch kernel: integrity: Loaded X.509 cert 'OK Certificate: c8c73a37546046ab495c33f4d0856052'
Oct 24 07:03:56 crystal-arch kernel: integrity: Loading X.509 certificate: UEFI:db
Oct 24 07:03:56 crystal-arch kernel: integrity: Problem loading X.509 certificate -65
Oct 24 07:03:56 crystal-arch kernel: integrity: Loading X.509 certificate: UEFI:db
Oct 24 07:03:56 crystal-arch kernel: integrity: Loaded X.509 cert 'EUJinn: 2d9ec14a26c9fcae420ef406a6e9492b'
Oct 24 07:04:00 crystal-arch kernel: cfg80211: Loading compiled-in X.509 certificates for regulatory database
Oct 24 07:04:00 crystal-arch kernel: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'

```
Sorry for any added confusion on my part.

---

### Post by thormine on 2023-10-24
```
The first were messages about your USB Flash drive,. That shows up as  /dev/sda right? Which really is just temporary? Not really part of your  computer right? Is so, then check the filesystem of the partitions. If  not, just rewrite the LiveUSB image and recheck it.
```
I only know that these messages (those in the first attachment) showed up when I typed 'reboot', at the end of the repair process; and that they don't show up anymore when I boot or reboot. I don't know if these messages showed up as /dev/sda. How can I check that?

```
The boot messages in the second attachment are harmless APCI warnings,  not errors, that show up with some BIOS's and can be ignored. The  warning about "integrity:  problem loading x.509 certificate" is also a  warning, and if you want, can be investigate further by doing:
     Code:
     journalctl -b -l -g 'X\.509' --no-pager 
That will show you which X.509 certificates were loaded, and which  one had a problem... Which is usually an outdated certificate in the  BIOS. Since you have SecureBoot disabled it's no really a problem.

I do not know how to remove an outdated X.509 security that is within  the BIOS. I have not seen or heard of anyone really doing that. Most are  told what it is an left to accept and ignore it.                 
```
Okay, thank you for the information! Thank you 1fallen too! I will not try to fix this then.

---

### Post by MAFoElffen on 2023-10-24
Happy that everything is working for you again.

Now that this is fixed for you to your satisfaction... And we know you are "New To Ubuntu"... You started this thread. You are responsible for marking it as "Solved" when you decide it is done. Please select the "Thread Tools" link in the upper right of the first page of this thread to Mark it as "Solved". That really helps other users (later) with similar problems to search for, and find what worked for you, for them to solve their own similar problems. That is how things work here. We are just volunteers that help each other by sharing answers, education, and experience.

Welcome to the Community. 

Now for you to learn more about doing backups, right? I would search the Forum on User "TheFu" and "backups"... I think he explains that well.

---

### Post by thormine on 2023-10-25
Alright, thank you very much all of you :)

---

