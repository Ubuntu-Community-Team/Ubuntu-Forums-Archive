---
title: "A couple (quick) questions"
date: 2008-01-21
forum: Programming Talk
---

### Post by DanielJackins on 2008-01-21
I was just wondering a couple of things:

1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc.  No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way. 

2) I'm about to attempt to create some things for my website involving PHP (comment box, users) and was wondering if I could create any security loopholes in doing so (I'm not very good with PHP). Furthermore, even if the security does get bypassed by somebody, is my computer itself at risk? Or just the website?

3) Is it possible to completely mess up a computer (eg by making my own OS) or does a reinstall of a working OS clean up any errors. 

Thanks for any and all help! :)

---

### Post by Scarath on 2008-01-21
> **DanielJackins said:**
> I was just wondering a couple of things:

1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc.  No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way. 

2) I'm about to attempt to create some things for my website involving PHP (comment box, users) and was wondering if I could create any security loopholes in doing so (I'm not very good with PHP). Furthermore, even if the security does get bypassed by somebody, is my computer itself at risk? Or just the website?

3) Is it possible to completely mess up a computer (eg by making my own OS) or does a reinstall of a working OS clean up any errors. 

Thanks for any and all help! :)

1) Depends what u wanna do, it seems that creating another *buntu just needs a different desktop enviroment and some new art work :( and im sure u'll agree the world doesnt need another *buntu.
However if u wanna make ur own linux distro i'd start looking into debian cos its just friggin' brilliant and many of the best distros are based off it.

2) dont know sorry :)

3) yeah just reinstall ubuntu and u'll be fine, but u may loose all ur data if its not on a separate partition. I have 'broken' my computer countless times and then just reinstalled (debian in my case) over the top of whatever didnt work.

---

### Post by Majorix on 2008-01-21
> **DanielJackins said:**
> 1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc.  No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way.

I wouldn't attempt it at this stage :popcorn:

---

### Post by popch on 2008-01-21
A modern OS consists of well over 100'000 lines of code. Depending on what you consider part of the OS proper, that number is easily in the lower millions, let's say four millions.

A reasonably experienced and efficient programmer usually writes on the order of 10 to 50 lines of code per day. That's an average which includes 'dead' time and overhead, time not spent coding but designing, time spent writing the documentation, debugging and improving and so on. 

A typical work year has 200 days.

Thus, we arrive at a work volume between 10 and 2000 person-years, provided those persons work on it full time.

---

### Post by tashe on 2008-01-21
The question about writing a OS is interesting for me too. I have a OS class and we got into the basic stuff about the structure of OS. 

If I wanted to write something basic (nothing like making a *buntu lookalike), like the simplest OS that can be made and still have some very basic functionality what do you thing I should start with and how?

Is it only recommended to do it in C/C++ or I can do it in Java?
thanks

---

### Post by geirha on 2008-01-21
> **DanielJackins said:**
> 1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc.  No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way. 


An OS, or more specifically, a linux OS, is just a linux kernel and whatever applications you choose to accompany the kernel with. If you want to learn the basics of linux, I suggest you try out [LFS](http://www.linuxfromscratch.org/). Do it in a [qemu](https://help.ubuntu.com/community/Installation/QemuEmulator) vm, or boot your ubuntu CD, shrink a few gigabytes off your partition(s) in gparted and create an LFS partition.

---

### Post by mathisdermaler on 2008-01-21
1) others have answered

2) yes!  It's pretty easy to make an insecure PHP web site if you don't know what you're doing.  The best way to approach this is to make sure that even if an attacker does take over your PHP box, he can't do any other damage.  (For example, don't keep your backups on there.)  If your PHP server is hosted by someone else, likely that have already done some work to secure it.

3) No.  You can always re-install another OS.  (The advice to develop it in a VM is good advice.)  

Now, lest someone come along and correct me, it's theoretically possible to make your motherboard unusable by flashing your bios with bad code, but you're *extremely* unlikely to do that by accident. :)

---

### Post by pmasiar on 2008-01-21
1) Writing on OS, or even kernel for it (Linux), if using GNU utilities, is quite difficult: years of working alone. When Linus started writing Linux, he already was quite a decent hacker, and 
- (a)  went through college-level course of OS-design (using Minix, which included source code). 
- (b) AND he immediately attracted interest of other hackers interested in kernel hacking, who helped him with patches.

I doubt you have (a), and will get (b), and don't think anyone (not even you) can hack kernel alone "for fun" for 10 years. If your idea is to create yet another ubuntu clone, it is simpler, but it is not kernel hacking: you will learn packaging and distro management. Which might be just fine too.

If you want to learn packaging, seach for ubuntu MOTU team: they look for new packagers and will train you.

Hacking on your own kernel you will not teach you a lot: how you will be able to bebug it if it does not boot? In short: if you are asking **here** how to do that, you are not ready yet.

2) yes, security breaches can compromise lot of things. If you are not careful and unlucky to boot, someone can root your PC (gain root access) and do whatever he wants.

3) yes, if you try low-level disk write and miss proper sector/cylinder, you can mess your disk pretty badly and unrecoverably, even different partitions. I would recommend separate disk mechanics for this kind of learning tasks. If you are particularly unlucky you can damage the disk.

---

### Post by BobLand on 2008-01-21
Search for 'Linux from Scratch'
this is an excellent starting place!

bobland

---

### Post by Lster on 2008-01-21
[QUOTE=DanielJackins]1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc. No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way.[/QUOTE]

It is not as hard as you may think, but to develop a _useful_ OS takes a whole lot of work! I have been developing my own for quite some time now (started about a year and a half ago and stopped about a half year ago). Even during that year of work I have only managed very little. I have file loading and saving, mouse and keyboard drivers, limited software graphics, time and date functionality, memory allocation and freeing, multitasking, etc... keep in mind that the most you could ever develop for my OS is already available (but far far better) on Linux, Windows and Mac OS X.

Saying all of that, though, it is very fun indeed! :)

[QUOTE=DanielJackins]3) Is it possible to completely mess up a computer (eg by making my own OS) or does a reinstall of a working OS clean up any errors. [/QUOTE]

Quote from a page on OSDev.

[QUOTE=OSDev Wiki]WARNING: Improperly changing CRTC settings can be harmful to the monitor attached to it[/QUOTE]

Sounds dangerous, although I mostly tested my OS on an old machine or a virtual machine and never caused damage. I was frequently worried though - be very careful!

Origional article: [http://www.osdev.org/wiki/VGA_Hardware](http://www.osdev.org/wiki/VGA_Hardware)

If you are interested in OS development (and it can be a lot of fun and frustration) I would look at the OSDev website and perhaps talk to others on the forum over there. That's how I started, goodluck.

---

### Post by LaRoza on 2008-01-21
> **DanielJackins said:**
> I was just wondering a couple of things:

1) How difficult is writing an OS and what would I need to know, how time consuming would it be, etc, etc.  No, I do not expect to make a reliable, functionable OS. I just want to have some fun and maybe learn (quite) a few things along the way. 

2) I'm about to attempt to create some things for my website involving PHP (comment box, users) and was wondering if I could create any security loopholes in doing so (I'm not very good with PHP). Furthermore, even if the security does get bypassed by somebody, is my computer itself at risk? Or just the website?

3) Is it possible to completely mess up a computer (eg by making my own OS) or does a reinstall of a working OS clean up any errors. 

Thanks for any and all help! :)

1. Not extremely difficult to write simple useless OS's, but requires knowledge

[http://www.osdev.org/](http://www.osdev.org/)

2. Yes, watch out for injection. Also, limit the privileges of the script.

3. Do it in a VM anyway, faster that way.

---

### Post by DanielJackins on 2008-01-21
Thanks for all the replies!

What exactly is a Virtual Machine?

Also, I do only plan on writing a barely functionable OS, I do not plan on being even close to on par with and OS out there today. Even getting to the point of having just a  desktop (or if thats harder than it sounds, less) would be great

---

### Post by geirha on 2008-01-21
What better to explain a virtual machine than wikipedia :)
[quote=http://en.wikipedia.org/wiki/Virtual_machine]In computer science, a virtual machine (VM) is a software implementation of a machine (computer) that executes programs like a real machine.[/quote]

So whatever OS you would eventually create, you should test and run in a virtual machine. Then you can mess around as much as you want without causing problems with your currently running one :) Check out qemu which I posted a link to earlier.

---

### Post by LaRoza on 2008-01-21
> **DanielJackins said:**
> Thanks for all the replies!

What exactly is a Virtual Machine?

Also, I do only plan on writing a barely functionable OS, I do not plan on being even close to on par with and OS out there today. Even getting to the point of having just a  desktop (or if thats harder than it sounds, less) would be great

Personally, I use VirtualBox, but as stated before, Wikipedia is a good reference.

(For programming and computers at least, Wikipedia is remarkably good. Bookmark it, make it your search tool, or put it on speed dial.)

For your goals, you might want to use the site I linked to, and make a bootloader, a simple "Hello world" bootloader. It may satisfy your thirst for now, and give you a taste for such programming.

For making your own OS, I highly doubt you'd get to GUI's of any use. If that is your goal, look into existing code. Try: [Minix]("http://www.minix3.org/"), or [FreeDOS]("http://www.freedos.org/"), and see what you can find from there.

Minix is good for learning, and was designed for it. It is very small, and is what actually prompted Linus to make Linux. (Minix has a different license, although you can view the source and it is free) In my book on OS programming, the code (on paper) is pages 523 to 903 of pure (with comments) code. And they simplified it for the book.

The text is everything before that.

(Operating Systems Design and Implementation Second Edition, Andrew S. Tanenbaum, Albert S. Woodhull)

---

