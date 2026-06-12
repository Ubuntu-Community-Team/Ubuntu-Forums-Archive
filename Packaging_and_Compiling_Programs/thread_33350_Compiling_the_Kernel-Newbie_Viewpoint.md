---
title: "Compiling the Kernel-Newbie Viewpoint"
date: 2005-05-10
forum: Packaging and Compiling Programs
---

### Post by larry on 2005-05-10
Hi Everybody,
I am a newbie and my idea of compiling the kernel may be too ambitious, but I want to find out more about it.
My desktop is a 900MhZ Athlon AMD, i installed warty for a i386 machines and then I upgraded to hoary via the net.
Sometimes the Gnome desktop is not very responsive, but maybe it is simply due to my seasoned hardware.
Should I need a different kernel (I mean a kernel for a e.g. a i486 machine, I do not think about some other version of a i386 kernel, which the one I have installed).
I am a bit afraid of breaking the system by playing with the kernel, so I first would like to know if there is a simple and above all safe way of toying around with the kernel without having much knowledge about it.
Cheers
Larry

---

### Post by LordHunter317 on 2005-05-10
Installing the approrpiate Ubuntu supplied kernel would be a better idea, I think.  This can be done by installing the appropriate linux-image package (you want a k7 one in your case).

---

### Post by Xian on 2005-05-10
[QUOTE=larry]I am a bit afraid of breaking the system by playing with the kernel, so I first would like to know if there is a simple and above all safe way of toying around with the kernel without having much knowledge about it.
Larry[/QUOTE]
I would encourage you to experiment as much as you'd like. Head over to the wiki and do a keyword search for "kernel". There are several good how-to's on this subject. The reason I encourage you is that any kernel you attempt to build will not replace the one you currently use to boot Ubuntu, and so as long as you do not remove that kernel from your grub config you will never have a 'broken' system. The worst (and most likely) issue you will find is that it will take you numerous attempts before you can compile a kernel that performs properly.

---

### Post by larry on 2005-05-13
Ok, I will try to do some reading in depth. According to what I saw, I still have to get a bit more experienced before trying my habds at compiling the kernel.
Thanks
Larry

---

### Post by az on 2005-05-13
[QUOTE=larry]Ok, I will try to do some reading in depth. According to what I saw, I still have to get a bit more experienced before trying my habds at compiling the kernel.
Thanks
Larry[/QUOTE]
LordHunter317 suggested you install a precompiled k7 kernel.  That would be recommended.  It is also completely safe.

---

### Post by larry on 2005-05-15
I tend to agree with the idea at this point. I tried to compile my own kernel according to the wiki (in the end I tried the so-called Debian way), but, believe it or not, I managed to break the system! At some point I was actually compiling something, but the output of the debugger stated the chosen architecture was i386. I stopped the compilation, thinking nothing could go wrong, but when I rebooted the machine tried to load the k7 kernel...probably as a result of some previous attempt of mine.
Online I found the sintax:

sudo apt-get install linux-k7

which kernel will that line install? And when I update to breezy in November, will it be upgraded to another k7 kernel?
Last question: the difference between compiling my own kernel and using a precompiled one is just in terms of customization or does it potentially lead to some differences in the performances of the system?
Thanks 
Larry

---

### Post by Xian on 2005-05-15
[QUOTE=larry]Which kernel will that line install? And when I update to breezy in November, will it be upgraded to another k7 kernel?[/quote]
Heh. I doubt anyone could definitively answer that right now.
It _should_ just update your kernel type version.
[QUOTE=larry]Last question: the difference between compiling my own kernel and using a precompiled one is just in terms of customization or does it potentially lead to some differences in the performances of the system?
[/QUOTE]
The short answer is both. If you customize the kernel to only include what your hardware requires then in theory it should be less bloated and run more responsively. However, AFAIK the method you used just recompiles the kernel using the present config, so I can't say that you would really gain anything by doing it that way.

---

### Post by N'Jal on 2005-05-15
That's the point of compiling your own kernel, you can make it do backflips if you are so talented, however if, like me you are not then the choice means bugger all when you don't know how to do it right. I have tryed rolling my own kernel to no avail, in the end i just stick with the binary one's.

In fact what do people think to n00b kernel compiling, it's all good and well to have follow this command follow that command etc but would it be possible to have a thread where we can ask questions and get answers. For me getting a lot of the settings right in the first place can be tough. So would it be possible for a thread where n00b's, like me can post what they tryed and what failed etc?

I realise that the ammount of people posting errors would be massive so could it be possible that you email the stuff and then it's addressed on the forum's and anyone jumping the que has their post deleted?

Have i got my idea accross or are people confused?

---

### Post by Xian on 2005-05-15
[QUOTE=larry]
Online I found the sintax:

sudo apt-get install linux-k7[/QUOTE]
That is the kernel meant to be used with AMD Duron/Athlon processors.
But don't confuse that with the Athlon64 kernel...totally different thing.

---

### Post by Xian on 2005-05-15
[QUOTE=N'Jal]That's the point of compiling your own kernel, you can make it do backflips if you are so talented, however if, like me you are not then the choice means bugger all when you don't know how to do it right. I have tryed rolling my own kernel to no avail, in the end i just stick with the binary one's.[/QUOTE]
Compiling your own kernel (with custom configurations) is a great learning tool, and if you really want to get immersed in Linux then at some point you will want to go this route, as the kernel is the heart of the system and knowing how to manipulate it to your needs can be a valuable asset.

But I really don't advise that people compile kernels strictly for performance reasons. The reasons are fairly simple: (1) The gain in speed is not that substantial and things like prelinking will boost system responsiveness more effectively. (2) Any seconds realized in performance is more than lost in the time spent on compilation. (3) You have to recompile the kernel each time there is a security version bump if you want the latest secure release. A person using APT can just keep up with a quick download and install using Synaptic.

---

