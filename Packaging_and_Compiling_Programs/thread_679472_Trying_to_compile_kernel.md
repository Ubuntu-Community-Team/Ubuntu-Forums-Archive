---
title: "Trying to compile kernel"
date: 2008-01-27
forum: Packaging and Compiling Programs
---

### Post by JamesUser on 2008-01-27
I have linux-source-2.6.20.tar.bz2 in /usr/src directory. I want to compile this.

So I opened a terminal session and tried the below command.

```
sudo apt-get install build-essential fakeroot kernel-package
```

It gives the following error message.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  fakeroot: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
  kernel-package: Depends: dpkg-dev (>= 1.4.0.9) but it is not going to be installed
E: Broken packages

I am also confused whether I should use build-essential or kernel-package.

Please tell me if I should give more information. I am running Ubuntu 7.04 with latest versions of all the default packages, if that helps.

---

### Post by JamesUser on 2008-01-27
I would like to know why build-essential and/or kernel-package are necessary.

Right now, I am trying to do without them... I extracted the sources into /usr/src/linux-source-2.6.20. But when I run make oldconfig numerous errors. So my guess is this should be resolved when I use build-essential or kernel-package. Any clues or suggestions?

---

### Post by geraldm on 2008-01-27
build-essential installs working compiler(s), gcc g++ 
For the kernel, if you have a working gcc, then you may not need the build-essential.   
kernel-package is not needed to build a kernel.  I have built kernels and never used this.  It is probably helpful to keep in step with the way debian kernels are built ?

oldconfig errors?
Some of the kernel configuration methods have dependencies, based on the type of dialog interaction that is needed from the user.  If all else fails, there is a text method of make config.  

If you have oldconfig errors that you cannot find an answer for, please post

Gerald

---

### Post by JamesUser on 2008-01-27
Hi Geraldm,

Thanks for the info. I have gcc 4.1.2-0Ubuntu4. Guess this may not be the latest.

From the oldconfig errors, it seems that a lot of headers are either missing or not in the right place. I have attached the error text from running "make oldconfig".  If that is not comfortable, please let me know. I will paste it inline.

I copied oldconfig as follows.

```
cp /boot/config-2.6.20-16-generic /usr/src/linux-source-2.6.20/.config
```

And I am following the steps mentioned here. [http://lkml.org/lkml/2007/4/7/22](http://lkml.org/lkml/2007/4/7/22)

---

### Post by geraldm on 2008-01-27
The log shows that the headers for glibc are not installed.
I recommend you try to install build-essentials, as that will take care of the header dependencies, I think.  The headers for libc need to match the version that you are using.  There might be an alternate method, by using a package for glibc-dev that would have the headers, but you need the matching headers for your system.

Gerald

---

### Post by JamesUser on 2008-01-27
Yeah.... I tried that before. See my first post here. Apt is unable to get correct versions of package as there are many dependencies. Seems like installation of build-essential fails, as apt finds later versions on my machine. Any thoughts? Should I download a newer version of kernel source itself probably?

---

### Post by geraldm on 2008-01-27
You need a way to force install of build-essential package.
I think the error message stated it:
build-essential: Depends: libc6-dev but it is not going to be installed or
libc-dev
This package would contain the headers that you need, I think.
Another version of the kernel source would just provide the same problem.  

Try to just get build-essential installed and working.  Perhaps an alternate to apt-get.  There may be other threads where the build-essential failed, and they may have answers.

Gerald

---

### Post by JamesUser on 2008-01-30
ok.. I tried that and I managed to install build-essential from Gutsy CD. So, I have run make oldconfig.

The next step is to run make gconfig. Sigh! Again there are some package dependency issues. It expected certain versions of GTK+, glibc, libglade all of which I installed. Yet this step is failing. I will give you the exact details soon. 

Thanks a lot for helping out.

---

### Post by JamesUser on 2008-01-31
Update:

I managed to install the required gtk+2.0, libglib libraries from synaptic. And the last one, libglade with the following command.

```
aptitude install libglage2-dev
```

I am now able to run make gconfig.

Wow! This is cool... I am loving this.

Thanks Gerald for all your help. I will post again to this thread soon with my results. You will need kernel-package if you want to run "make-kpkg clean" after changing your kernel config.

---

### Post by JamesUser on 2008-02-01
Hey... 

Am able to boot into my kernel now. But am not posting this thread from that. It wont detect my wi-fi card. And it doesnt have wpasupplicant also. 

Now I wonder how I can optimize the kernel for my hardware and usage.

Have a nice day.

---

