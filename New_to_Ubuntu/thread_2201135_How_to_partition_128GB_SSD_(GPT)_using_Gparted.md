---
title: "How to partition 128GB SSD (GPT) using Gparted"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by jferreir on 2014-01-22
I just formatted the SSD as GPT, and I have 119.24GiB of unallocated space. I need SPECIFIC instructions on how to create the various partitions, including how much space to allocate, file extensions, basically everything. I have no idea what I'm doing and I'm absolutely, hopelessly lost. I need to install it as EFI, and I have booted the LiveUSB using EFI.

I have to install Ubuntu via the 'Something Else' option because I have Windows 8.1 installed on a second SSD. So, I also need to know which partition to selection during the installation process. 

Please make your answer as simple as possible. I'm *this* close to giving up on Ubuntu entirely.

---

### Post by justleen on 2014-01-23
Perhaps you should stick with one partition then, if you don't know how to size various partitions?

If your Windows is on a different disk, there is no need to use the something else option. Select the disk you want to use in the menu, and let Ubuntu do the partitioning. 

I have no clue what kind  of file extentions you would want, during an install..


Perhaps rephrase you're question? Owh wait.. [http://ubuntuforums.org/showthread.php?t=2200636](http://ubuntuforums.org/showthread.php?t=2200636)

---

### Post by Odyssey1942 on 2014-01-23
If I may weigh in here with a suggestion. And let me declare at the outset that I consider myself a noob even though I started playing with Ubunu 5 or 6 years ago, installed 10.04 as my main OS and have never once since considered returning to Windows. I am a heavy user, keeping 8 workspaces open for different purposes with 16 Gb of RAM supporting literally dozens of open tabs across 15 or 20 different windows, but what I know about Ubuntu would not fill a teaspoon.

Ubuntu is widely considered the easiest linux distro, but it simply is not as easy as Windows. There is a learning curve. So if you plan to do the install with the hope you never need to come back to the forum, you might want to consider just staying with Windows (which by the way, in my very limited experience, Win 7 is a much improved OS.)

Another thing to consider is how the forum works. We noobs post our questions, usually badly phrased or incomplete because our experience is so limited we don't know how to phrase them well. The regulars roll their eyes and occasionally with barely concealed disdain tell us either that we haven't given them enough information, or more constructively tell us what they need to know to help us.

But let's consider the regulars. These good hearted folks are unpaid. They are GIVING us the benefit of their enormous experience and expertise. They only get the satisfaction of helping another stranger on the path of life to take their next step. I can well imagine that when they read a post that demands this or the other, they just go to the next thread. Had the phrasing of such a post been along the line of a polite and appreciative nature, explaining what it is we noobs don't understand and courteously requesting what we think we need, they might well have cheerfully, and generously, donated their time to helping solve the OP's (Original Poster) problem.

So it is a give and take. They give, we take. Tact is very productive.

As to any specific problem, here is a suggestion, and an approach that might be productive. Set aside some time. Define your project broadly, ideally with a step by step plan. Let the first post be one that helps you shape your ultimate course of action. You may find that you change course at this stage because of what you learn (see below). Repeat if necessary in this case as every thread eventually runs out of steam with respect to the original post.

Then let the next new thread deal with the specific steps, maybe one at time, maybe 2 or 3 if they logically bunch together, then the next, etc.

Feel free to completely disregard the above suggestion. I just think it might be a good approach as I am learning from my own experiences.

If you don't have the time and patience for this, maybe linux is not for you. I realize that you already have a lot of time invested in this, and the good news is that you are persevering. Keep the faith.

I am dealing with a similar challenge, i.e. putting 12.04 onto a SSD alongside a HDD with Win 8 already installed, and keeping the data on the HDD. (  [http://ubuntuforums.org/showthread.php?t=2200667](http://ubuntuforums.org/showthread.php?t=2200667)  ) I started out with the idea that I would put /home/odyssey on the HDD. OldFred suggested leaving home in the system (i.e. what is referred to as "/" [please forgive me for adding explanations for things you most probably already know, but if this happened more often, many of the beginner threads would move faster and to more successful conclusions by avoiding misunderstandings]), keeping all my data (i.e., the non-hidden [folders beginning with "."]) user folders under /home/odyssey) on the HDD, and "linking" the folders back to /home. After discussion, I adopted his suggestion which, as time permits, I am implementing.

A big complication in all of this is UEFI, which appears to be the "successor" to BIOS. Win 8 uses it natively, maybe Win 7 but I do not know. It seems to enormously complicate dual boot with Win 8 (maybe 7) and apparently pre-install UEFI settings, the order of installation, where the boot loader (maybe using the wrong term here) is placed, and other aspects are important.

Another thing to think about is that any shared (between Windows and linux) data folders must be NTFS, not EXT, so please confirm this (as well as anything else above that I have stated because it is all *as I understand it*) which may frequently be flawed. I am a newbie.

I hope this helps you and that you stay the course. I can tell you that it is worth all the initial pain and frustration. IMO, Windows is not a patch on Ubuntu which is a truly industrial strength OS. Good luck!

---

### Post by jferreir on 2014-01-23
I get what you're saying, but I make no apologies for my frustration. There's simply no reason why the installation process should be this difficult! The complete lack of clear documentation regarding UEFI issues is somewhat astounding given that Ubuntu is supposed to be the Linux for "noobs". I appreciate the help of this forum, but after reformatting a drive over 5 times, you bet I'm going to get cranky. 

Mods are welcome to delete this thread as I'm addressing the problem in another thread. I created this one because I thought the questions were getting too off-topic, but the other thread seems to be getting more traction.

---

### Post by whitesmith on 2014-01-23
> **Odyssey1942 said:**
> Ubuntu is widely considered the easiest linux distro, but it simply is not as easy as Windows. There is a learning curve. So if you plan to do the install with the hope you never need to come back to the forum, you might want to consider just staying with Windows (which by the way, in my very limited experience, Win 7 is a much improved OS.)!There is also a learning curve in transitioning from *nix to Windows. The more you know about *nix, the steeper that learning curve will be. So it is for those going in the other direction. "Dir" makes little sense for those who are used to "ls" ... needing to download and install device drivers sounds insane to those used to having the necessary code right in the kernel, where it belongs ... paying for software utilities that are included free of charge in *nix is ludicrous. Yes, to become proficient at Linux you'll have to open the hood and get oil under your fingernails. Time and patience are necessities. This is the only cost of using FOSS. If you aren't willing to pay it--and many people are not--then the best course of action is to stick with Windows and express awe and admiration for its many "innovations," which are usually nothing but warmed-over imitations of functionality that *nix had before dollar signs began spinning in the mind of a certain entrepreneur who made the Pacific Northwest his base of operations.

---

### Post by Odyssey1942 on 2014-01-23
whitesmith, a cogent comment. But I can't imagine there are many seasoned linux users migrating to Windows, or perhaps why anyone might, unless maybe it is a sys admin taking on a job related Windows environment

On the other hand, many of those migrating to linux from Windows (and I am guessing that there is an increasing stream) have at least considerable time in front of a windows computer, if not some serious competence "under the hood" in Windows.

---

### Post by whitesmith on 2014-01-24
> **Odyssey1942 said:**
> On the other hand, many of those migrating to linux from Windows (and I am guessing that there is an increasing stream) have at least considerable time in front of a windows computer, if not some serious competence "under the hood" in Windows.I agree. Microsoft dug a very deep hole when they announced support for XP will be going to sleep with the fishes.  There is a certain university in Chicago (a client) with well over 5000 PCs, all running XP Pro. Many run software written by consultants and university staff. The university also operates a number of large hospitals, so HIPPA (look it up!) is another concern. The cost of certifying operability -- only that, nothing more -- of all this stuff on Windows 8 is around a million dollars. The conversion cost? I'm guessing north of $5 M, maybe even 10. I'm arguing for at least a partial conversion to Ubuntu or RHEL. Executives are listening. MCSEs and the like would be foolish not to pay attention. Times are changing.

---

