---
title: "Where is the kernel directory for Ubuntu 12.10?"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by regency on 2012-12-27
I need to run the following instructions:
 
> Run build.sh as follows from a terminal window, where /path/to /expanded/folder is where build.sh is located, i.e. /home/user /Desktop/ap-kernelmodule-1.0.14-13: 
 
cd /path/to/expanded/folder 
 
sudo ./build.sh --kernel-dir /lib/modules /$(uname -r)/build
 In my case, “the path to expanded folder” is home/sharon/savfl/ap-kernelmodule-1.0.14-13
 
Now, as for the kernel directory, I tried searching within almost all directories/folders and managed to find the nearest match whose path is:
 
> /usr/src/linux-headers-3.5.0.21-generic/kernel So, I issued the following command:
 
> sharon@sharon:~/savfl/ap-kernelmodule-1.0.14-13$ sudo ./build.sh home/sharon/usr/src/linux-headers-3.5.0.21-generic/kernel /lib/modules/3.5.0.21-generic/build 
 [sudo] password for sharon:  
 And I got the following error message:
 
> Unknown Option: home/sharon/usr/src/linux-headers-3.5.0.21-generic/kernel 
  
 Usage: build.sh [options]  
 Options: 
   --kernel-dir [DIRECTORY] : DIRECTORY is to set kernel headers/makefiles directory to build kernel modules 
 The default is /usr/src/kernels/3.5.0-21-generic-x86_64 
  --kernel-rel [RELEASE]    : RELEASE is to set which kernel release the kernel modules are builded for 
 The default is the current kernel release(3.5.0-21-generic) 
   --debug                   : Build the kernel modules with debugging information 
   --clean                   : Delete all generated files 
   --version                 : Display the version number of the build script 
   --help                    : Display this help 
 Can someone help me with this please?
 
 Please note that prior to doing the above I have installed the linux-headers relevant to my current kernel version with the following command:
                                   
> sudo apt-get install linux-headers-3.5.0.21-generic build-essentialI am new to Linux and Ubuntu; hence detailed how-to instructions would be most welcome.
 
 Thanks in advance.

---

### Post by steeldriver on 2012-12-27
I don't know what you're trying to build, but that command looks like it should be run literally, i.e. after cd'ing to the "expanded folder" just

```
sudo ./build.sh --kernel-dir /lib/modules/$(uname -r)/build
```The [FONT=Courier New]--kernel-dir[/FONT] is an option flag and [FONT=Courier New][FONT=Arial][FONT=Courier New]$(uname -r)[/FONT][/FONT][/FONT] in the path should expand to your current linux-headers-x.x.x.x kernel header directory[FONT=Courier New][FONT=Arial]
[/FONT][/FONT]

---

### Post by regency on 2012-12-28
> **steeldriver said:**
> I don't know what you're trying to build, but that command looks like it should be run literally, i.e. after cd'ing to the "expanded folder" just

```
sudo ./build.sh --kernel-dir /lib/modules/$(uname -r)/build
```The [FONT=Courier New]--kernel-dir[/FONT] is an option flag and [FONT=Courier New][FONT=Arial][FONT=Courier New]$(uname -r)[/FONT][/FONT][/FONT] in the path should expand to your current linux-headers-x.x.x.x kernel header directory[FONT=Courier New][FONT=Arial]
[/FONT][/FONT]

Thanks for your reply. I obtained the complete instructions from the following article: [http://www.symantec.com/business/support/index?page=content&id=TECH95496](http://www.symantec.com/business/support/index?page=content&id=TECH95496)

Please click on the above link and I would appreciate it if you could help me further. Thanks in advance.

---

### Post by regency on 2012-12-28
@ steeldriver:

I followed your suggestion and below is the result:

> sharon@sharon:~/savfl/ap-kernelmodule-1.0.14-13$ sudo ./build.sh --kernel-dir /lib/modules/3.5.0.21-generic/build

Kernel release is not set
build the kernel modules for the current kernel release(3.5.0-21-generic)
Kernel headers/makefiles directory /lib/modules/3.5.0.21-generic/build does not exist.  Build was stopped due to error.What shall I do next, please?

---

### Post by Wim Sturkenboom on 2012-12-28
Did you do the first instruction in the page that you linked to?
```

sudo apt-get install linux-headers-$(uname -r) build-essential

```
What was the result?

PS
It's advisable to run the following first
```

sudo apt-get update
sudo apt-get upgrade

```
so your packages (and packqage information) is up-to-date.

---

### Post by regency on 2012-12-30
Hi guys,

Thanks for your replies.

I just wish to let you know that everything's alright now.

steeldriver is right. I just have to run the following command literally:

```
sudo ./build.sh --kernel-dir /lib/modules/$(uname -r)/build
```

Note to admin/webmaster: Could you be kind enough to close this topic? Thanks.

---

### Post by zombifier25 on 2012-12-30
> **regency said:**
> Hi guys,

Thanks for your replies.

I just wish to let you know that everything's alright now.

steeldriver is right. I just have to run the following command literally:

```
sudo ./build.sh --kernel-dir /lib/modules/$(uname -r)/build
```

Note to admin/webmaster: Could you be kind enough to close this topic? Thanks.

You can mark this thread as solved. Go to the top right, click Thread Tools > Mark as Solved.

But, looking at your other topics, I hope you are not trying to do what I think you're doing.

---

