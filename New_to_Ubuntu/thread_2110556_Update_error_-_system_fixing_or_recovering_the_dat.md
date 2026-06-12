---
title: "Update error - system fixing or recovering the data"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by Logarytm on 2013-01-30
Hi,

Wasn't sure what to put in the title and where to post it...

My problem history:

I was updating ubuntu 11.10 to 12.4.1 and someone turned off the computem during the process :(

After that (no matter which GRUB option is being used) the system starts turning on and stays at the welcoming purple screen.

When I tried to run it as an older version it stucked in the same spot, but after pressing the arrow down key a few times - console appeared and there was an error communicate:

"Mountall: /lib/x86_64-linux-gnu/libc.so.b: version 'GLIBC_2.14' not found crequired by /lib/libply.so.2

general error mounting filesystem"

and it was possible to restart computer with ctrl   d

I tried to copy the libc.so.b file using Ubuntu 12.04 running live from pendrive.
But all I got was another error:

"there was an error getting information about destination details:
The specified location is not supported"

What I'm trying to accomplish is:
to fix the system, or to recover a few data from the user catalog. 

Of course access was denied when I tried to do so by browsing it via  Ubuntu 12.04 running live from pendrive.

my Disk partitioning:
 1 NTFS with win7; 1 NTFS with files; 1 ext4 with Ubuntu and the files I want to recover; 1 SWAP

When I try to run ubuntu from harddrive the purple screen says it's 11.10, but Ubuntu from pendrive says it's 12.4 installed on the hard drive

Of course I know the user password from the account where the wanted files are, but don't know how to make a use of it.

My question is: how to fix the system or how to recover the data?

Logarythm

---

### Post by NikTh on 2013-01-30
> **Logarytm said:**
>  

Of course access was denied when I tried to do so by browsing it via  Ubuntu 12.04 running live from pendrive.

Hi , 

there you have to use nautilus file manager as root  to be able to copy your data to an external HDD . Then install - fresh install Ubuntu 12.04.1. If the progress of upgrade corrupted is very hard to fix the system. 

So boot from a Live Ubuntu media and "Try Ubuntu" , then open nautilus as root with this command 
```
gksudo nautilus
``` 

find your important files - copy them to a safe place and proceed with the installation. 

Thanks

---

