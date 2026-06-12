---
title: "RE: configure kernel"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Varsel on 2012-05-06
I'm sure this has been covered before, but I can't get 'search' to find it, and I'm on public computer, so do not have time to sift through everything bit by bit. Can someone please advise where a newbie can find all info needed to DIY "configuring the kernel"? Seems this is necessary for me to learn.

---

### Post by Cheesemill on 2012-05-06
What are you trying to achieve?

Information on compiling the Ubuntu kernel can be found here:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I use the alternate build method mentioned about half way down the page when I compile my own custom kernel (to apply the ck patchset and change the timing to 1000Hz).

---

### Post by grahammechanical on 2012-05-06
Notice this point under Reasons for NOT compiling a custom kernel

> You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.

I would not call compiling a kernel an absolute beginner subject and you are asking this questing in the Absolute Beginner Talk section and you call yourself "a newbie."

regards.

---

### Post by buzzingrobot on 2012-05-06
> **Varsel said:**
> I'm sure this has been covered before, but I can't get 'search' to find it, and I'm on public computer, so do not have time to sift through everything bit by bit. Can someone please advise where a newbie can find all info needed to DIY "configuring the kernel"? Seems this is necessary for me to learn.

If you have experience compiling from source, configuring and building a kernel could be tackled by a patient newbie who is prepared for several false starts.  But, if you haven't the foggiest notion of how to use things like gcc, make, autoconf, etc., then jumping into kernel configuration and compiling is not the best place to start, to say the least.

I compiled lots of kernels in days gone bye, but these days I don't see a need.  Perhaps if you could tell us why compiling a kernel is "necessary" for you?

Tip:  You'll need to have a detailed understanding of all the hardware your machine before you start configuring kernels appropriately.

---

### Post by Varsel on 2012-05-08
> **Cheesemill said:**
> What are you trying to achieve?
 
Information on compiling the Ubuntu kernel can be found here:
 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
 
I use the alternate build method mentioned about half way down the page when I compile my own custom kernel (to apply the ck patchset and change the timing to 1000Hz).
 
Excellent! Is there anything else I need to know or study that is not included in link above? Also, is this only for the Linux kernel in Ubuntu, or will it work for Linux kernel in all distros?

---

### Post by Varsel on 2012-05-08
> **grahammechanical said:**
> Notice this point under Reasons for NOT compiling a custom kernel
 
 
 
I would not call compiling a kernel an absolute beginner subject and you are asking this questing in the Absolute Beginner Talk section and you call yourself "a newbie."
 
regards.
 
Let's see if I understand your thinking. I'm a newbie, and I don't know what I'm doing, therefore I should not even try to learn what is necessary to know (so that I can know what I'm doing), because I'm a newbie and should be content to remain so (and never know what I'm doing). Now I need a megadose of aspirin!  
 
And just where should a newbie post to learn how to compile a kernel...oh that's right, he shouldn't post anywhere, as newbies are not allowed to learn how to do such stuff.

---

### Post by Paqman on 2012-05-08
> **Varsel said:**
> therefore I should not even try to learn what is necessary to know

There's really no need to learn how to recompile kernels. I've been using Linux for years and I only have the vaguest idea of how it's done. It's not something you'll ever need to do. People do it because they can, and because they're curious.

It's a bit like disassembling the gearbox in your car. Sure, you could learn how to do it, but it's difficult and extremely unlikely to be necessary. But some people do it anyway.

---

### Post by Varsel on 2012-05-08
> **buzzingrobot said:**
> If you have experience compiling from source, configuring and building a kernel could be tackled by a patient newbie who is prepared for several false starts. But, if you haven't the foggiest notion of how to use things like gcc, make, autoconf, etc., then jumping into kernel configuration and compiling is not the best place to start, to say the least.
 
I compiled lots of kernels in days gone bye, but these days I don't see a need. Perhaps if you could tell us why compiling a kernel is "necessary" for you?
 
Tip: You'll need to have a detailed understanding of all the hardware your machine before you start configuring kernels appropriately.
 
Sorry...complete and total Linux newbie here. No experience at all. Think starting from scratch, rock bottom, etc.  Currently I'm looking to learn how to **delete** (i.e. erase fully and completely) certain items in the linux kernel, without turning OS unstable. Notice I did not use the word disable here. Longterm goal is to learn how to compile, configure, and build.
 
Okay, so how do I learn how to "use things like gcc, make, autoconf, etc." I'm willing to start from scratch...advise how to begin, what do I need to know, where to go to find out, and so on.

---

### Post by Paqman on 2012-05-08
> **Varsel said:**
> Currently I'm looking to learn how to **delete** (i.e. erase fully and completely) certain items in the linux kernel, without turning OS unstable.

What sort of stuff were you looking to delete?

Linux is very modular. Removing parts of your OS that you don't use or want is generally as simple as uninstalling those components through your package manager without having to mess with the kernel. The kernel handles support for hardware, and only loads the modules it needs for the hardware you've actually got, so there's generally no advantage to removing chunks of it.

Having said that the kernel that Ubuntu ships with is deliberately quite generic, so isn't technically optimal for anybody. Recompiling the kernel for your exact setup will (at least theoretically) optimise it for your system. However, the improvements would be so small that only the very keen think it's worth the hassle, and you'd have to repeat the process every time the new kernel was released (which is quite often).

I would definitely optimise what packages and services you're running before looking to the kernel though.

---

### Post by buzzingrobot on 2012-05-08
> **Varsel said:**
> 
Okay, so how do I learn how to "use things like gcc, make, autoconf, etc." I'm willing to start from scratch...advise how to begin, what do I need to know, where to go to find out, and so on.

Search "linux development tutorial".  You'll need to know C and/or C++. 

There are many sites about Unix/Linux development in general and kernel development specifically.  Books, too.

If your goal is just to pare down the kernel, you won't be writing any code.  But, you will be using the GNU/Linux toolset, so search for tutorials on that.  That was my reference to gcc, etc.

You will also need a detailed knowledge of the specific hardware the kernel will run on, because configuring it amounts to going through a very extensive program and choosing what you want to support, and how. Think hundreds of options. The risk of not checking something that needs to be checked is real.

That said, I'm not sure, beyond its educational value, why you want to do this. There is very little, if anything, to be gained from reconfiguring and recompiling your kernel.

Not trying to discourage you, but you have picked a very daunting, and usually unnecessary, first project.

---

### Post by Varsel on 2012-05-13
> **Paqman said:**
> There's really no need to learn how to recompile kernels. I've been using Linux for years and I only have the vaguest idea of how it's done. It's not something you'll ever need to do. People do it because they can, and because they're curious.

It's a bit like disassembling the gearbox in your car. Sure, you could learn how to do it, but it's difficult and extremely unlikely to be necessary. But some people do it anyway.

Up til about three months ago, when I stumbled across the missive "Flame Linus to a Crisp", I would of agreed with you 100%. Now that I know that Linux is not the anti-DRM operating system that I had been led to believe, it appears that if I want a DRM-free OS, I must work for it. Research indicates the only way to erase CONFIG_INTEL_TXT (and any other nasties I find, or is included in the future), is to learn to configure the kernel.

---

### Post by Varsel on 2012-05-14
> **Paqman said:**
> What sort of stuff were you looking to delete?

Linux is very modular. Removing parts of your OS that you don't use or want is generally as simple as uninstalling those components through your package manager without having to mess with the kernel. The kernel handles support for hardware, and only loads the modules it needs for the hardware you've actually got, so there's generally no advantage to removing chunks of it.

Having said that the kernel that Ubuntu ships with is deliberately quite generic, so isn't technically optimal for anybody. Recompiling the kernel for your exact setup will (at least theoretically) optimise it for your system. However, the improvements would be so small that only the very keen think it's worth the hassle, and you'd have to repeat the process every time the new kernel was released (which is quite often).

I would definitely optimise what packages and services you're running before looking to the kernel though.

Thank for your advice! I'm already somewhat familiar with removing components of the OS, in that I've basic idea what is needed to do, but that is of minimal interest at present, as I have yet to find anything in any of the distros I wish to trial, that I absolutely cannot tolerate. Maybe later I might want to streamline and jettison components I never use, but for now I'm focused on erasing DRM-based "Linux kernel configuration items". So far, I've found CONFIG_INTEL_TXT and maybe CONFIG_HAVE_INTEL_TXT. There maybe other nasties I've yet to uncover that must be **deleted**. Advisers from other forums say to totally erase such stuff requires me to reconfigure the kernel, hence my interest in learning.

---

### Post by Varsel on 2012-05-14
> **buzzingrobot said:**
> Search "linux development tutorial".  You'll need to know C and/or C++. 

There are many sites about Unix/Linux development in general and kernel development specifically.  Books, too.

If your goal is just to pare down the kernel, you won't be writing any code.  But, you will be using the GNU/Linux toolset, so search for tutorials on that.  That was my reference to gcc, etc.

You will also need a detailed knowledge of the specific hardware the kernel will run on, because configuring it amounts to going through a very extensive program and choosing what you want to support, and how. Think hundreds of options. The risk of not checking something that needs to be checked is real.

That said, I'm not sure, beyond its educational value, why you want to do this. There is very little, if anything, to be gained from reconfiguring and recompiling your kernel.

Not trying to discourage you, but you have picked a very daunting, and usually unnecessary, first project.

Thanks for your answer! Great to hear I will not need to compile code, as it sounds like all I really need is "pare down the kernel". I'm doing a custom-build PC...any advice on using this towards "detailed knowledge of the specific hardware"? Sites maybe?

My goal is to eventually make the jump from XP Pro to Linux. However, I absolutely **require** a DRM-free operating system, to replace it with, and it appears Linux cannot meet this requirement 'out of the box'. Just as I will have to run a SAD mission on XP Pro to eradicate all of lil Billie's DRM surprise packages, it seems I must do the same with Linux. 

 This will not be my "first project". Becoming as comfortable with Linux as I am with XP Pro is my first goal, which I've alloted a year to do. Then comes longterm goal of having a totally DRM-free OS...and I'm willing to do whatever it take to accomplish this.

---

### Post by HiImTye on 2012-05-14
I think youre mixing your terms here, closed source is not DRM, it is just a binary blob that does not include its' source code. removing these binary blobs can have serious impacts on your system if your machine makes use of them (as all of the binary blobs in the kernel, to my knowledge, are hardware specific drivers)

---

### Post by buzzingrobot on 2012-05-14
> **Varsel said:**
> Thanks for your answer! Great to hear I will not need to compile code, as it sounds like all I really need is "pare down the kernel". I'm doing a custom-build PC...any advice on using this towards "detailed knowledge of the specific hardware"? Sites maybe?

My goal is to eventually make the jump from XP Pro to Linux. However, I absolutely **require** a DRM-free operating system, to replace it with, and it appears Linux cannot meet this requirement 'out of the box'. Just as I will have to run a SAD mission on XP Pro to eradicate all of lil Billie's DRM surprise packages, it seems I must do the same with Linux. 

 This will not be my "first project". Becoming as comfortable with Linux as I am with XP Pro is my first goal, which I've alloted a year to do. Then comes longterm goal of having a totally DRM-free OS...and I'm willing to do whatever it take to accomplish this.

Tomshardware.com is one good site devoted to hardware.  Of course, it's the hardware inside your hardware that you need to know.

And, you will be compiling when you build your own kernel.  It's been a long time since I've done that, but, in general, you are presented with many, many options.  Some will be relevant to your needs and your hardware, some won't be, and some will conflict with others.  In simplistic terms, you check the options you want and compile the new kernel, install it, and hope it works.

However, as others have pointed out, kernel code that does not need to be executed on your machine is not executed. The kernel identifies the hardware that is present and loads the needed drivers. Some of those drivers are digital blobs provided by hardware vendors who want their devices to work on Linux but do not want to distribute source code.

---

### Post by bodhi.zazen on 2012-05-14
Well, if you want to learn to build kernels, I HIGHLY suggest you do your homework.

[http://kernelnewbies.org/](http://kernelnewbies.org/)

[http://www.kernel.org/faq/](http://www.kernel.org/faq/)

kernel-seeds.org/working.html

Otherwise the entire process boils down to 

```
make menuconfig 

# Configure your kernel
# This is where the rubber hits the pavement. You need to know your hardware and what kernel modules you need.

make -j5

# -j5 is your number of cores +1

make install
```

---

### Post by Varsel on 2012-05-20
> **bodhi.zazen said:**
> Well, if you want to learn to build kernels, I HIGHLY suggest you do your homework.

[http://kernelnewbies.org/](http://kernelnewbies.org/)

[http://www.kernel.org/faq/](http://www.kernel.org/faq/)

kernel-seeds.org/working.html

Otherwise the entire process boils down to 

```
make menuconfig 

# Configure your kernel
# This is where the rubber hits the pavement. You need to know your hardware and what kernel modules you need.

make -j5

# -j5 is your number of cores +1

make install
```

According to buzzingrobot all I really need to learn to accomplish my goal of a totally DRM-free kernal/OS is how to pare down the kernal, so that is what I'm now focused on. Previously had been told that to erase nasties in the kernel required knowing how to configure, rebuild, etc. Anyway, thanks for your links. Will printout, and keep on file, in case I ever have new incentive to learn how to build kernals.

---

### Post by buzzingrobot on 2012-05-20
> **Varsel said:**
> According to buzzingrobot all I really need to learn to accomplish my goal of a totally DRM-free kernal/OS is how to pare down the kernal, so that is what I'm now focused on. Previously had been told that to erase nasties in the kernel required knowing how to configure, rebuild, etc. Anyway, thanks for your links. Will printout, and keep on file, in case I ever have new incentive to learn how to build kernals.

Varsel, Bodhi.zazen's post explains how to do what you seem to want to do. If you want to "pare down" or otherwise alter your kernel, those are the steps you need to follow.  It is in the configuration stage that you do the paring down. So, don't file it away for future reference.

---

### Post by bodhi.zazen on 2012-05-20
> **Varsel said:**
> According to buzzingrobot all I really need to learn to accomplish my goal of a totally DRM-free kernal/OS is how to pare down the kernal, so that is what I'm now focused on. Previously had been told that to erase nasties in the kernel required knowing how to configure, rebuild, etc. Anyway, thanks for your links. Will printout, and keep on file, in case I ever have new incentive to learn how to build kernals.

You can use the libre kernel

[http://www.fsfla.org/svnwiki/selibre/linux-libre/](http://www.fsfla.org/svnwiki/selibre/linux-libre/)

There is an apt repository

[http://jxself.org/linux-libre/](http://jxself.org/linux-libre/)

---

### Post by Varsel on 2012-05-22
> **HiImTye said:**
> I think youre mixing your terms here, closed source is not DRM, it is just a binary blob that does not include its' source code. removing these binary blobs can have serious impacts on your system if your machine makes use of them (as all of the binary blobs in the kernel, to my knowledge, are hardware specific drivers)
 
Well, I will readily admit I have not researched "closed source", open source, and all that jazz, so little understanding about this stuff. That said,  i've done a load of research on DRM, HDCP, etc., over past year...enough to know that Intel TXT, vPro, and so on is just Microsoft's Palladium renamed & repackaged.
 
Now I've done everything I can think to do to make sure any/all hardware in my custom build will not support DRM, HDCP, TPM, etc., but on off chance anything slips by me, I definitely don't want any software (especially my OS) working with it behind my back! So if removing this crud from the kernel "impacts" my PC, then that will mean some hardware DRM slipped by, and that will mean some hardware component needs to be junked/replaced. So I would consider it an additional failsafe to filter out any DRM garbage.

---

### Post by Varsel on 2012-05-22
> **bodhi.zazen said:**
> You can use the libre kernel
 
[http://www.fsfla.org/svnwiki/selibre/linux-libre/](http://www.fsfla.org/svnwiki/selibre/linux-libre/)
 
There is an apt repository
 
[http://jxself.org/linux-libre/](http://jxself.org/linux-libre/)
 
So how would you compare/contrast using this libre kernel against erasing the nasties from the regular kernel? I'm assuming the libre version would be easier, but what would I be giving up....that is , what does the regular kernel have (other than the DRM junk) that the libre kernel does not? At the moment I don't know enough to make informed choice between the two, so any advice is appreciated.

---

