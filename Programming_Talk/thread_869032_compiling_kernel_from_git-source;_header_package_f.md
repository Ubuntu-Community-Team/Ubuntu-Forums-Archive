---
title: "compiling kernel from git-source; header package for &quot;2.6.24-21&quot; missing"
date: 2008-07-24
forum: Programming Talk
---

### Post by Krank on 2008-07-24
(Long post, but please- bear with me.)


Here's the deal:

I got a Psion 5mx handheld, and I like to be able to put its memory card into my card reader and do regular backups. Trouble is, Ubuntu's way of handling FAT isn't really compatible with the Psion way of doing things, which results in rather... odd behaviour. Ayway, I got a patch from [http://software.frodo.looijaard.name/fat-epoc/](http://software.frodo.looijaard.name/fat-epoc/) .

So, I set out to recompile the kernel. Using the instructions [here](https://help.ubuntu.com/community/Kernel/Compile) as a giude, I first tried the "old method" which worked perfectly - I got both a linux-image and linux-headers and all was fine and dandy. Well, mostly.

I decided to try and do thing the "proper" way, with Git.

I got the source, I applied the patch, and I compiled using "AUTOBUILD=1 fakeroot debian/rules binary-debs".

I got the following files:

linux-headers-2.6.24-21-386_2.6.24-21.38_i386.deb
linux-headers-2.6.24-21-generic_2.6.24-21.38_i386.deb
linux-headers-2.6.24-21-server_2.6.24-21.38_i386.deb
linux-headers-2.6.24-21-virtual_2.6.24-21.38_i386.deb
linux-image-2.6.24-21-386_2.6.24-21.38_i386.deb
linux-image-2.6.24-21-generic_2.6.24-21.38_i386.deb
linux-image-2.6.24-21-server_2.6.24-21.38_i386.deb
linux-image-2.6.24-21-virtual_2.6.24-21.38_i386.deb
linux-image-debug-2.6.24-21-386_2.6.24-21.38_i386.deb
linux-image-debug-2.6.24-21-generic_2.6.24-21.38_i386.deb
linux-image-debug-2.6.24-21-server_2.6.24-21.38_i386.deb
linux-image-debug-2.6.24-21-virtual_2.6.24-21.38_i386.deb
linux-libc-dev_2.6.24-21.38_i386.deb

Installing the image went great. However, since I use the official NVIDIA drivers rather than the usual ones, and since I'm also doing all sorts of things with various virtualization thingies, I need the headers, as well.

And each and every one of the above headers give me the same lip:

Package X depends on linux-headers-2.6.24-21; however:
  Package linux-headers-2.6.24-21 is not installed.

And, of course, there are no linux-headers-2.6.24-21 in the repos.


This is not my first time compiling a kernel, but it is the first time I do so by the Git-method. I just need a pointer or two, you don't need to hold my hand during the entire process. You just need to give me an URL or a few keywords to google, or a few lines explaining what I'm doing wrong.

C'mon, show me some of that sense of community Ubuntu'sd supposed to be all about...

---

### Post by Car60n on 2008-07-24
You can try this one out--
[https://wiki.ubuntu.com/KernelGitGuide]("https://wiki.ubuntu.com/KernelGitGuide")

install git-core,
then enter this command
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ubuntu-hardy
```
after that search for your header package...

I dont know about the availability of 2.6.24-21
check it out...

Good luck man...

---

### Post by Krank on 2008-07-24
> **Car60n said:**
> You can try this one out--
[https://wiki.ubuntu.com/KernelGitGuide]("https://wiki.ubuntu.com/KernelGitGuide")

install git-core,
then enter this command
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ubuntu-hardy
```
after that search for your header package...

I dont know about the availability of 2.6.24-21
check it out...

Good luck man...

Errrh, yeah. I love that you try to help out, man, and I'm really grateful that you took your time and gave me a proper answer. ANd I'm seriously sincere here, I know how often people actually take time to help other people out on the vast, limitless 'net.

...but it might've been a bit more usefull if you'd read my entire post. I state that I got the sources bi git, applied the patch I needed, and then compiled. I even state exactly what files I get. And yes, I looked for my header package. Towards the end of my post, I even state exactly what I get when I try to dpkg -i the suitable package.


So - While I am infinitely grateful and very happy that you wanted to help, I continue my search for an answer...

---

### Post by Car60n on 2008-07-25
OK, there are no header packages in repo,
and could not find it anywhere on the net either..
so all you can do is build your own kernel-header package,

You already compiled you kernel,
now try this 
```
make-kpkg --initrd --append-to-version=-krank kernel-headers
```

you should get the header package..
try to dpkg -i it tell me what happens....

hope it helps.

---

### Post by Archmage on 2008-07-25
Keep in mind that this kernel is FOR testing purpose only. There is a high possilbity that it is broken.

I would suggest to use the standard kernel (e.g. in Hardy this is 2.6.24-19) and build on this base.

---

### Post by Krank on 2008-07-25
> **Car60n said:**
> you should get the header package..
try to dpkg -i it tell me what happens....

hope it helps.

The UTS Release version in include/linux/utsrelease.h
     "2.6.24.3-krank-gc1d87cd9" 
does not match current version:
     "2.6.24.3-krank-gc1d87cd9-dirty" 

is what I get, at the very end.



> **Archmage said:**
> Keep in mind that this kernel is FOR testing purpose only. There is a high possilbity that it is broken.

I would suggest to use the standard kernel (e.g. in Hardy this is 2.6.24-19) and build on this base.

Errrh, yeah. I'd love to do that. I must be stupid or something, but I can't seem to understand how to Git the sources for the standard kernel...

---

### Post by Car60n on 2008-07-25
My last idea...
here it goes--

```
make-kpkg clean
```

then 
```
make-kpkg --initrd --append-to-version=-krank kernel-image kernel-headers
```

then dpkg it,

if that does not work, 2.6.24-19 would really be better...

---

### Post by Krank on 2008-07-25
Sorry to say, same result...

It seems the make-kpkg way of compiling, which served me well when I used the ubuntu-source package, doesn't work at all with Git:ed source.

Now, if I could just make the compilation process not increase the version number to 21 - the one in the repos is 20...

---

### Post by Car60n on 2008-07-25
why dont you try 2.6.24-19...
i should work just fine and it's in the repo too ...

---

### Post by Krank on 2008-07-25
> **Car60n said:**
> why dont you try 2.6.24-19...
i should work just fine and it's in the repo too ...

Sure, if I knew how to Git the source of it, I'd do it in a second.

I can get the linux-source-2.6.24 package and compile it, but that doesn't include all the latest patches etc of 2.6.24-19/20... 20 is the latest one in the repos.

Like I wrote in the first post; I want to compile and use the Git-sources, since they are more up-to-date and also more "proper"...




Anyone out there with some experience regarding Git:ed sources?

---

### Post by eldragon on 2008-08-27
right now im building 2.6.27-rc5-git7 just for the sake of it........

followed this guide, its supposed to work, something i read about requiring sata built right into the kernel, the previous attempt to build 2.6.27 resulted in an unbootable kernel :(

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

im subscribing to this thread since im intereste in everyones responses..

---

