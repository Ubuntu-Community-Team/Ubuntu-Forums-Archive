---
title: "Linux Headers Missing?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by xItachi on 2008-07-20
I'm using Ubuntu Hardy and I'm trying to install VirtualBox but when it tries to compile the kernel, it says:

```
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

I tried to install the headers with 

```
sudo apt-get install linux-headers-`uname -r`
```

But it says that they are not available:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-14-generic has no installation candidate
```

What should I do? Thanks!

---

### Post by zipperback on 2008-07-20
Please provide the output from the following:

```

sudo dpkg -l | grep -i linux-image

```

- zipperback
:popcorn:

---

### Post by schmick on 2008-07-20
I'm using hardy heron server.
the pakages I've used and worked are:
- linux-headers-2.6.24-16-server
- make
- gcc

---

### Post by stmiller on 2008-07-20
linux-headers-2.6.22-14-generic

That is an older kernel from gutsy. Hardy uses a 2.6.24 kernel. What kernel are you running?

Do a:

uname -a

---

### Post by xItachi on 2008-07-20
```
sudo dpkg -l | grep -i linux-image
```

Gives me:

```
ii  linux-image-2.6.22-14-generic              2.6.22-14.52                                               Linux kernel image for version 2.6.22 on x86
ii  linux-image-2.6.24-16-generic              2.6.24-16.30                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-17-generic              2.6.24-17.31                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-18-generic              2.6.24-18.32                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-19-generic              2.6.24-19.36                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.19.21                                               Generic Linux kernel image

```


```
uname -a
```

Gives me:

```
Linux stephen-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

How do I update to Hardy's kernel version?  I think I seem to have it on my computer, but I'm just using the older version.

---

### Post by xItachi on 2008-07-20
Do you think it is safe to remove the 2.6.22-14-generic kernel? If so, how do I do this?

---

### Post by zipperback on 2008-07-20
> **xItachi said:**
> Do you think it is safe to remove the 2.6.22-14-generic kernel? If so, how do I do this?


Check to make sure your system will boot with the newest kernel you have.

Reboot the computer, when the text message appears on screen about loading grub, press the 'esc' key. This will give you a text based menu of Kernel images. Select the most recent version from the list.

Once the system boots up, login and launch synaptic, then use synaptic to remove the old versions of the kernel that you don't need.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-07-20
Another thing you could do, in case you don't want to actually delete them from your system is to remove the listing from the grub loader.

Open a terminal window.

sudo gedit /boot/grub/menu.lst

Scroll down until you find the listings for the old kernels.

It will look similar to the following:


title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1234 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Just comment that out by putting a # in front of each of the lines in that section so it looks like as follows:

#title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1234 ro quiet #splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

Now save the file and reboot.

If you go back into the grub text menu, you should no longer see the kernel listed as an option.

- zipperback
:popcorn:

---

### Post by xItachi on 2008-07-20
Thanks for the help! I was messing around because no one replied for a while and I started to get impatient to I used synaptic to remove the old kernel and when I restarted my computer, I couldn't boot into it anymore so I had to boot into one of the newer ones.  The latest one didn't work so I panicked and finally after 30 mins I tried the 2nd latest one and it worked.  I went to edit the menu.lst file and now everything works fine so far.  This also solved my problem with the 'unable to find the sources of your current Linux kernel' problem, so VirtualBox is running fine so far past that part :)  THANK YOU!!

---

### Post by zipperback on 2008-07-20
> **xItachi said:**
> THANK YOU!!

You are very welcome.

- zipperback
:popcorn:

---

### Post by chebar on 2010-05-19
Mine boots fine, but caused all sort problems on my asterisk install.

---

