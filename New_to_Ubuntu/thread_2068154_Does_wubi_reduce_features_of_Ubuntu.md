---
title: "Does wubi reduce features of Ubuntu?"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by pras8421 on 2012-10-08
Hi....

I am using Ubuntu 12.04 LTS (Precise Pangolin that is installed inside windows using wubi.

I just wanted to know whether installing Ubuntu in wubi reduces any features of Ubuntu in comparison to installing it in the other way:)

---

### Post by jerrrys on 2012-10-08
Same ubuntu, same features.  The biggest complaint that I read about in the forums is it may be slower than a regular install.

---

### Post by pras8421 on 2012-10-08
I want to clarify one more thing, . . .

Laptop gets heated up much more though there is no great going on in Ubuntu compared to windows, this happens in both kinds of installation, as I observed and the battery consumption is more...

---

### Post by Bucky Ball on 2012-10-08
Overall better user experience with hard drive install. Wubi intended to try before install for awhile; not a long-term solution.

---

### Post by pras8421 on 2012-10-08
Thank you:)

---

### Post by will1982 on 2012-10-08
Wubi provides a full featured experience, albeit with slower disk read times.

---

### Post by DuckHook on 2012-10-08
Personally, I am uncomfortable with WUBI. I know that WUBI was developed to ease the transition from Windows to Ubuntu, but it makes a number of compromises that are problematic:

1. You are installing the Linux OS on NTFS which is not a journaling file system like ext4 and fragments too easily. Moreover, if you do not defrag your drive first, the initial Ubuntu image can be spread all over the HD. Consequently, sluggish performance gets attributed to Linux, notwithstanding that the advantage of Linux is its speedier performance over Windows.
2. You introduce an added layer of complexity by making the Ubuntu boot process dependent on Windows. Consequently, crashes/corruptions in Windows can effect the Ubuntu image "file" and Ubuntu ends up getting blamed for Windows problems.
3. The two systems are too closely intermingled, and it is too easy to corrupt the files of one system by using incompatible tools that properly belong only to the opposing system. e.g. Windows Notepad inserting <CR> characters in Linux config files.
4. However, my biggest anxiety is rather philosophical: one of the biggest hurdles for Windows users in learning Linux is their very different file and directory structures. This was a big learning curve for me, and I think that it is important to study the Linux file system at its most "generic". However, WUBI changes the Linux file structure in order to accommodate Windows, and this misleads people into learning the wrong file structure.

My preferences:

1. Install a proper version of Linux on its own partition, and then dual boot. If a third partition is created only for data, this has the added advantage that both OSes can now access common data without risking corruption of each others' system files.
2. Run Linux in a VM using something like VirtualBox or KVM. This is the method I use (only reversed, as I run Windows on a VM in Ubuntu) and has the additional advantage that you can have both OSes running at the same time. Of course, your system has to be a little more powerful, ideally with dual cores and sufficient memory, but there is a much smaller risk of file corruption, etc. choosing this route.

Just my $.02

---

### Post by will1982 on 2012-10-08
Duckhook, your points are valid, but isn't one of the major hurdles of installing
Linux actually figuring out how to install it side by side your other OS without eviscerating it?

---

### Post by Karlchen on 2012-10-08
Hello, pras8421.

Having run my Lucid Lynx 32-bit Wubi installation on a Windows 7 notebook more than 24 months now, I can confirm that the following limitations do exist:

[LIST]
[*]The maximum partition size of a Wubi installation is limited to 30 GB.
[*]A Wubi installation cannot be shutdown to hibernation.
[*]Ubuntu, installed via Wubi, will not startup in case the underlying NTFS filesystem is not clean and needs a chkdsk. (This has occurred 0 times in the past 2 years here.)
[*]You cannot use Remastersys to make a bootable and re-installable system backup of the Wubi installation.
[/LIST]

Apart from these limitations, I have not been able to confirm that my (Wubi) Lucid Lynx was slower than a normal installation. The OS and the installed applications run in the same reliable way as those that  I installed on other machines normally.
Final remark on my Wubi installation: it has been used for everyday's office work for the past two years almost daily.

But maybe my Wubi Lynx is just the exception to the rule. :wink:

Cheers,
Karl

---

### Post by will1982 on 2012-10-08
Karl,

The only performance difference you will notice is a slightly slower hard drive read/write time, such as saving or opening a large file.

---

### Post by DuckHook on 2012-10-08
> **will1982 said:**
> Duckhook, your points are valid, but isn't one of the major hurdles of installing
Linux actually figuring out how to install it side by side your other OS without eviscerating it?

You are right. A few years ago, GRUB was pretty good at incorporating the Windows partition in its startup menu choices, but these days, the two systems don't play so nicely with each other. Moreover, I agree that monkeying around with partitions is a critical process and a lot can go wrong. But that is why I run Windows inside a VM. I imagine that the reverse (running Ubuntu inside a VM on Windows) will also work well. Sort of gives you the best of both worlds, actually.

---

### Post by newb85 on 2012-10-08
I agree with DuckHook's concerns.  I have an additional concern.

(And this is anecdotal, so take it for what it's worth.)  Wubi installs create additional hurdles in troubleshooting.  Few of the experts use Wubi themselves, and so they aren't so familiar with the nuances of a Wubi install.  Meanwhile, many new users aren't aware that using Wubi will give them a setup that differs from one produced by a standard install.  

Personally, I've never had any troubles installing side-by-side, but I know that's partly due to a little experience and partly due to my machines being uncomplicated.  (Despite my current machine being pretty new, I didn't have any issues with UEFI.)

Ultimately, I think the solution would be to have the kinks worked out of the standard installer so it's easy enough for the greenest of users.  More specifically, it needs to be made more robust, so that it can automatically deal with scenarios like UEFI and RAID.

---

