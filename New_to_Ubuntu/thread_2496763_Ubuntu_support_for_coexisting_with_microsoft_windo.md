---
title: "Ubuntu support for coexisting with microsoft windows"
date: 2024-04-11
forum: New to Ubuntu
---

### Post by hyperlinxe on 2024-04-11
Hello guys, this is my first post on the ubuntu forums 

I am a long time linux user and have used all the different distro's

also I like coffee and reading, and sunny days, if they're not too hot

I was curious if anyone could tell me what the current status of support 

is for ubuntu living with microsoft windows on the same computer.

I know in the past it was recommended that ubuntu be installed after

windows, but now time has passed, and there is windows 11, and 

also noble numbat ubuntu, so if anyone has any information 

about this scenario in general that would be helpful. My PC 

is actually a windows 11 PC, that's how I purchased it, and

it has a legal license to use windows 11 associated with it, 

and so I was thinking of a dual boot scenario with noble numbat,

to take advantage of the unique features offered by both operating systems!

Thank you : p

---

### Post by tea for one on 2024-04-11
Ubuntu and Windows 11 can co-exist peacefully.
Now, you have a PC with Windows 11 pre-installed but it would be helpful to supply more info.
Specifically, can you accommodate two disks and allow each OS to occupy a separate disk?

---

### Post by hyperlinxe on 2024-04-11
I actually want to know as much as possible honestly. My preferred method has been to use one hard drive for both of them. I'm curious as to
what the status is for Ubuntu's support of this use case, and possibly new developments such as with the next version of ubuntu
coming out soon. 

I already know a lot about how to get this setup working manually on my own. I know how to get it working for example, whether or not windows or ubuntu
was installed first, but what what I'm interested in learning is specifically about how Ubuntu is supporting using microsoft windows concurrently.

edit: I don't have windows 11 installed right now, but am planning on possibly reconfiguring the operating system with Ubuntu+Windows 11 in the near future,
what I was saying in the top post is that I have a windows 11 PC, that's made to work with windows 11, and has a windows 11 license, so I can go and download
windows 11, install it, verify it, without issues at any point in time.

---

### Post by psychohermit on 2024-04-11
You would be better off installing Windows first, Then partition the drive for Ubuntu and install Ubuntu beside Windows.  Ubuntu will install the boot loader and detect Windows and make a provision for booting in from the boot loader.

Good Luck,
--glenn

---

### Post by oldfred on 2024-04-11
New systems since 2012 are UEFI with gpt partitioning.
Microsoft required vendors to install in UEFI mode with release of Windows 8.

I installed Kubuntu 22.04 to my Dell laptop with Intel 11th gen chip, no nVidia to complicate install.
Worked fine until I had to return system to Dell for repair as it would not charge. Came back & Kubuntu worked just fine, but Windows would not boot. Tried every repair option, tried new total install to existing partitions, nothing worked. I think Dell did not copy Microsoft Product Key over, so Windows thought it was a new system.

But then installed a Dell recovery image. That reset system to as purchased. My Kubuntu was gone, but it was just the same data as desktop, so no great loss. 

But that shows why you need good backups of both Windows & Ubuntu.

I also now have two external SSD to USB3 adapters with SSDs (one is actually NVMe type). Those have worked so well for both booting, data backup,  and use with several systems, that I have not reinstalled Kubuntu to Dell laptop. I use external drive most of the time, except tax time when I have to use Windows.

---

### Post by yancek on 2024-04-11
> how Ubuntu is supporting using microsoft windows concurrently.
 

I don't really know what that means as windows and Ubuntu (Linux) are totally separate operating systems.  With Linux, you can read/write to windows filesystems.  With a default windows install, you can't do either.  So what do you mean by 'supporting'?  Also, as mentioned in previous posts, you need to post more details on your hardware and age of your system as well as whether you are using EFI.

With EFI, it is quite simple to install windows first and Linux second and if you have them on separate drives, it is even easier to use them by selecting the drive in the BIOS.

---

### Post by hyperlinxe on 2024-04-11
I actually like to install windows after linux, I like having a neat tidy harddrive that makes sense to me with simple partitioning, and obviously I only rarely use windows anyways so I put ubuntu first.

idk what support means, that's why I'm asking about it specifically. The levels of support for different features like using windows changes over time, I thought maybe casually asking in here might generate some useful info if anyone here knew anything about ubuntu's development whatsoever. Like I said I have a newer pc that came with windows 11 on it, so it has all the latest secure booting features and whatnot. 

I understand ubuntu has secure boot support now, so I can use it with both of them?

---

### Post by hyperlinxe on 2024-04-13
So nobody knows what the current status of Ubuntu's support is for Microsoft Windows on ubuntuforums.org as the latest noble numbat release is coming out.

Mods can close the thread I guess. (it's been two days with no answer)

---

### Post by him610 on 2024-04-13
Maybe this answers your question,
> OSS  &#8800; CSS
or maybe vice versa

---

### Post by QIII on 2024-04-13
"Ubuntu's support for Microsoft Windows" is nonsensical.

You can dual boot.  Lots of people do that.  It's not a "support" relationship.  You can run Windows in a virtual machine on Linux. That is not a "support" relationship, either.

Ubuntu provides no "support" for Windows.

---

### Post by MAFoElffen on 2024-04-13
Well, I can respectfully say there are periodically problems. My niche professinally is trying to get Windows and Linux to live together peacefully.

Even though I have done that for decades, there are sometimes problems. I'm used to them.

For example, on my Lenovo T-520 Intel i7 laptop... Just today, I booted Windows 10 to check something in Windows... Let it update a Windows Quarterly Cumulative Update... (That's how much I use that.) Update failed resulting in both Windows and Ubuntu not booting.

I have Ubuntu starting up again. Thank goodness for ZFS. Getting Windows back up is not my pressing priority at the moment.

Quoting John Lennon: "Life happens when you don't expect it."

Just be aware that it takes understanding and work. Have good backups.

---

### Post by hyperlinxe on 2024-04-13
There will never be another windows for me after 7, I miss that one so much. It was perfect.

The way I interpret the meaning of 'support' is actually pretty loose. I am a member of the ubuntu community right now for example, and I will happily support microsoft windows, it's users, and will happily support helping them solve their problems, any time, no strings attached. 

And so I am in no way implying negative connotations obviously. Although some people might draw those conclusions, it's not my intention to communicate in such a way.

SO again, if anyone knows anything about how Ubuntu is supporting windows, which it does, that would be helpful!

Microsoft even supports Ubuntu specifically, and linux broadly. No reason to get upset about it.

I enjoy technology in general, and so I like to use all the different operating systems actually. The fact that Microsoft Windows 11 and Ubuntu Noble Numbat work together, and support each others features is uniquely beneficial.

---

### Post by QIII on 2024-04-13
We have a sub-forum specifically for Windows help [here]("https://ubuntuforums.org/forumdisplay.php?f=170").

Does this meet your expectations of us?

" ... Microsoft Windows 11 and Ubuntu Noble Numbat work together ... "  Unless you are talking about WSL, this might be true in some parallel universe.

---

### Post by hyperlinxe on 2024-04-13
I was just curious about the current status, of support, by Ubuntu, for using Microsoft Windows! 

If no one knows, no one knows. Ok. Like I said, no one has answered in two days, so I guess mods can close the thread! 

> So nobody knows what the current status of Ubuntu's support is for  Microsoft Windows on ubuntuforums.org as the latest noble numbat release  is coming out.

Mods can close the thread I guess. (it's been two days with no answer) 				

---

### Post by QIII on 2024-04-13
There is not now, nor has there been, any such "support".  That is why you have gotten the answers you have.

The ability to dual boot is a function of hardware.  Virtualization can be used on many OSes to provide a playground for many other OSes.  It's not a matter of "support".

---

### Post by hyperlinxe on 2024-04-13
I actually have a lot of questions about Ubuntu, if anyone on Ubuntu forums could possibly answer them?

I want to understand more about the os and it's design, and policy, but if I can't even get an answer to questions about basic issues such as this, I am inclined to look elsewhere...

Obviously Ubuntu supports Microsoft Windows, just like Microsoft Windows supports Ubuntu,. It's not a debate...

---

### Post by QIII on 2024-04-13
Please educate me.

---

### Post by hyperlinxe on 2024-04-13
Well another question I have is whether or not Ubuntu supports using the vanilla kernel from it's own sources, as well as the driver for Nvidia's hardware which provides it's own installation medium as well, we can grab straight from their website...

I think I probably have about 1000 questions and more actually, if anyone were nice enough to communicate with here about them...

---

### Post by QIII on 2024-04-13
What is your definition of "the vanilla kernel"?  

OSes don't "support" hardware drivers.  It's exactly the other way around.  Either the OEM provides drivers for their hardware tailored to an OS or it does not work. If the OEM does not have an open-source driver, then unless it can be reverse-engineered it won't be included in most Linux distributions.  If it does not meet Microsoft's standards, it will not be included in their driverbase, which includes the OEM drivers -- but does not "support" them.

---

### Post by hyperlinxe on 2024-04-13
The one that linus torvalds develops. The Linux Kernel.

edit: i'd also like to point out, im not inviting anyone to get combative. This is a public webforum... I was hoping for a casual conversation about how Ubuntu works? 

Anyone up for that?

---

### Post by QIII on 2024-04-13
The mainline kernel?

Do you understand how the Linux ecology works?  Virtually all distributors of Linux-based OSes use kernels modified to suit their OSes.  That is what you get from Canonical's repos.

You are free to mix and match whatever kernel you desire, but you had better know what you are doing.

You have strayed from the original subject of this thread.  If you wish to get help, start another thread.  And in your new thread, please do not simply dismiss the perfectly valid answers you have been getting from some very knowledgeable old hands.  The issue here is not that you have not been answered.  The issue is that you refuse to accept them.

---

