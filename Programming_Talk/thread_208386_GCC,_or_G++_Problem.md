---
title: "GCC, or G++ Problem"
date: 2006-07-03
forum: Programming Talk
---

### Post by muffinhead on 2006-07-03
I recently downloaded  gcc, or g++, along with the neccessary libraries via the Synaptic package manager.

I have to recompile VMware, in order for it to be compatable with my Ubuntu 6.06 Dapper Drake Kernal, so I can run other OS'es in Ubuntu.

The problem is, when I downloaded gcc via synaptic, I don't think it installed at all.

I tried using the command "gcc" in the terminal, to see if it was installed, and it returned a "Command Not Found" error.

I also tried testing another way, by attempting to recompile vmware, and it say the "make" Program cannot be found:confused:.

Can someone help me get this sorted out, Thank You;)

---

### Post by moberry on 2006-07-03
Try installing the "buildessential" package

---

### Post by thumper on 2006-07-03
build-essential

---

### Post by moberry on 2006-07-03
[QUOTE=thumper]build-essential[/QUOTE]

I thought it looked wrong, but I wasnt in front of my desktop to make sure. thanks.

---

### Post by muffinhead on 2006-07-03
Thanks got that problem sorted out, now I'm having another one:  I am trying to recompile vmware, or whatever it is to run on Ubuntu Linux 6.06 (Dapper Drake).  

I downloaded the tar.gz file of vmware, as there was no .deb file on thier website,  I downloaded it from thier official website, It says when I try to install it this error:  

```
Trying to find a suitable vmmon module for your running kernel.  

None of the pre-built vmmon modules for VMware Player is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.
```

It then asks:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include],

then it complains that:

The path "/usr/src/linux/include" is not an existing directory.

or it complains that: The kernel source package probably is not installed.

How the heck am I supposed to do this? Can someone please help, so I can get vmware running on ubuntu.

I believe my kernel version is: 2.6.23-i686, or something along those lines, I'll report back with the actual kernel version.

Thank you if anyone can help;)

---

### Post by anatol on 2006-07-03
That didn't resolve the problem for me.

hello-world program compiled without any messages, but launching it has no result

#include <stdio.h>
int main(){
printf("Hello world\n\n");
}

gcc -Wall -o test  hello.c     (no problem)
test     (no error messages, no output)

any insight?
Thanks!

---

### Post by mentok on 2006-07-03
> That didn't resolve the problem for me.

hello-world program compiled without any messages, but launching it has no result

#include <stdio.h>
int main(){
printf("Hello world\n\n");
}

gcc -Wall -o test hello.c (no problem)
test (no error messages, no output)

any insight?
Thanks!

There's no output because you're executing /usr/bin/test (see test(1))

To run your hello world program in the current working directory you must type
```
./test
```

---

### Post by anatol on 2006-07-03
ah!

thanks!

---

### Post by ynef on 2006-07-04
[QUOTE=muffinhead]Thanks got that problem sorted out, now I'm having another one:  I am trying to recompile vmware, or whatever it is to run on Ubuntu Linux 6.06 (Dapper Drake).  

[...]
it complains that: The kernel source package probably is not installed.
[/QUOTE]
Well, as you've figured out, you need to install the kernel source packages. You can install the package "linux-source" to get the full source tree. Most likely, though, you might get away with only installing the kernel headers -- try that first, you can always remove them if you don't feel like having them installed. Install the meta package "linux-headers-X" where X is the architecture that you're using with your kernel, for instance i686.

These packages are all under "Development" in Synaptic's sections.

---

### Post by tennvolsmb on 2006-07-08
hey guys my gcc installed but i use nano to make my progs and everytime i type in gcc test.c it says 
test.c:1:18: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by Randomskk on 2006-07-09
If you're writing C++, use g++ to compile it, not gcc.

---

### Post by tennvolsmb on 2006-07-09
well im not using C++ yet im stil learning C so any idea on how to fix it?

---

### Post by ifokkema on 2006-07-09
> **ynef said:**
> Well, as you've figured out, you need to install the kernel source packages. You can install the package "linux-source" to get the full source tree. Most likely, though, you might get away with only installing the kernel headers -- try that first, you can always remove them if you don't feel like having them installed. Install the meta package "linux-headers-X" where X is the architecture that you're using with your kernel, for instance i686.

These packages are all under "Development" in Synaptic's sections.
VMplayer has an package under Dapper as well, and includes the kernel modules, so you don't have to compile the whole thing.

Either way, if you want to compile anyway, install the kernel headers of your kernel and point the installer to /usr/src/linux-headers-[kernel version]/include/linux.

---

### Post by muffinhead on 2006-07-09
Thanks, but I cannot download, or install large files from the terminal, or synaptic.

I'd have to download with a download accelerator, because of currently being on 56k dial-up, without a choice.

This is also where I have a problem, because I want to download XGL and Compiz, but the files are to large to download via the terminal, so I have to find a way to obtain, or download a tar.gz of XGL, and compiz, with a download accelerator.

I appreciate your reply, Thank You;)

---

### Post by ifokkema on 2006-07-10
> **muffinhead said:**
> Thanks, but I cannot download, or install large files from the terminal, or synaptic.

I'd have to download with a download accelerator, because of currently being on 56k dial-up, without a choice.

This is also where I have a problem, because I want to download XGL and Compiz, but the files are to large to download via the terminal, so I have to find a way to obtain, or download a tar.gz of XGL, and compiz, with a download accelerator.

I appreciate your reply, Thank You;)
As far as I know, tar.gz files usually are bigger than .deb files. You can retreive .deb files through your download accellerator by getting them directly from the server:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player/vmware-player_1.0.1-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player/vmware-player_1.0.1-4_i386.deb)
You can deduce the exact location by looking at the 'Filename' info in
```
apt-cache show <package-name>
```
Hope this helps you in any way.

---

