---
title: "Academic books or articles on why Linux/Unix/Mac/Solaris is better than Windows"
date: 2010-11-15
forum: Programming Talk
---

### Post by altonbr on 2010-11-15
That's right, for my Operating Systems class, my professor wants me to speak on the advantages of Linux over Windows.

I can think of a whole slew of reasons (and there are thousands of articles on the Internet of why), but I'm having problems finding technical documents on why.

I'm thinking of speaking on (these are just rough ideas),

[LIST]
[*]how open source increases security, flexibility and allows developers to "stand on the shoulders of giants"
[*]the pipe "|" operator in the terminal
[*]the ext2/3/4 file system
[*]the efficiency of directory tree traversal in the Linux kernel
[*]SELinux
[*]etc.
[/LIST]
I'm not looking for anyone to write this paper for me, by any means, but any leads to references would be much appreciated.

---

### Post by s3MA00RRNY on 2010-11-15
Found this on ACM. Check to see if your university gives you access.

          Yuqun Chen, Stefanos N. Damianakis, Sanjeev Kumar, Xiang Yu, and Kai Li.  1999. Porting a user-level communication architecture to NT:  experiences and performance.  In *Proceedings of the 3rd conference on USENIX Windows NT Symposium - Volume 3* (WINSYM'99), Vol. 3. USENIX Association, Berkeley, CA, USA,  6-6.

---

### Post by altonbr on 2010-11-15
> **pcdude2143 said:**
> Found this on ACM. Check to see if your university gives you access.

          Yuqun Chen, Stefanos N. Damianakis, Sanjeev Kumar, Xiang Yu,  and Kai Li.  1999. Porting a user-level communication architecture to  NT:  experiences and performance.  In *Proceedings of the 3rd conference on USENIX Windows NT Symposium - Volume 3* (WINSYM'99), Vol. 3. USENIX Association, Berkeley, CA, USA,  6-6.

Ah, ACM, I forgot about that resource. Looks like [it's all over the Internet]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=Porting+a+user-level+communication+architecture+to+NT%3A+experiences+and+performance.&ie=utf-8&oe=utf-8") too. Thank you.

---

### Post by Some Penguin on 2010-11-15
> **altonbr said:**
> 
[LIST]
[*]how open source increases security, flexibility and allows developers to "stand on the shoulders of giants"
[*]the pipe "|" operator in the terminal
[*]the ext2/3/4 file system
[*]the efficiency of directory tree traversal in the Linux kernel
[*]SELinux
[*]etc.
[/LIST]
I'm not looking for anyone to write this paper for me, by any means, but any leads to references would be much appreciated.


on 1- would be a better argument for OpenBSD, frankly, as they tend to take security *MUCH* more seriously than any Linux distribution with the possible exception of SELinux.  Serious security vulnerabilities are still very common in Linux.

on 2- Shell feature, not OS feature. 
[http://technet.microsoft.com/en-us/library/ee176927.asp](http://technet.microsoft.com/en-us/library/ee176927.asp)

on 3- "Btrfs is intended to address the lack of pooling, snapshots, checksums and integral multi-device spanning in Linux file systems, these features being crucial as the use of Linux scales upward into larger storage configurations common in the enterprise."
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)
Compare with ZFS, say.

on 5- SELinux /is/ nifty for those that care about security... which should be more people than currently do.


Might want to look at comp.os.linux.advocacy.

---

### Post by krazyd on 2010-11-15
> **Some Penguin said:**
> on 1- would be a better argument for OpenBSD, frankly, as they tend to take security *MUCH* more seriously than any Linux distribution with the possible exception of SELinux.  Serious security vulnerabilities are still very common in Linux.

This is a common misconception not borne out by the numbers. While Linux has had more reported vulnerabilities (possibly due to popularity?), OpenBSD has had a much higher proportion of remote exploits (58% vs. 17%), and Moderately Critical exploits (50% vs. 11%).

[http://secunia.com/advisories/product/19640/?task=statistics](http://secunia.com/advisories/product/19640/?task=statistics)
[http://secunia.com/advisories/product/2719/?task=statistics](http://secunia.com/advisories/product/2719/?task=statistics)

This might be a good example of the "many eyeballs" theory.

---

### Post by Some Penguin on 2010-11-15
> **krazyd said:**
> This is a common misconception not borne out by the numbers. While Linux has had more reported vulnerabilities (possibly due to popularity?), OpenBSD has had a much higher proportion of remote exploits (58% vs. 17%), and Moderately Critical exploits (50% vs. 11%).

[http://secunia.com/advisories/product/19640/?task=statistics](http://secunia.com/advisories/product/19640/?task=statistics)
[http://secunia.com/advisories/product/2719/?task=statistics](http://secunia.com/advisories/product/2719/?task=statistics)

This might be a good example of the "many eyeballs" theory.

"PLEASE NOTE: The statistics provided should NOT be used to compare the overall security of products against one another. It is IMPORTANT to understand what the below comments mean when using the statistics, especially when using the statistics to compare the vulnerability aspects of different products."

---

### Post by krazyd on 2010-11-16
true, but marginally better than the baseless assertion that> **Some Penguin said:**
> Serious security vulnerabilities are still very common in Linux.

---

### Post by worksofcraft on 2010-11-16
Better for what purpose?
If you want better for employment opportunities or better for available games I'm afraid Windows is well ahead.

---

### Post by Some Penguin on 2010-11-16
> **krazyd said:**
> true, but marginally better than the baseless assertion that

It's certainly not baseless.  Read any mailing lists?  Pay attention to any patches?  Or do you like root exploits that sit in your kernel for 8 releases in a row?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/190587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/190587)

Perhaps two in the same week?
[http://linux.slashdot.org/story/10/09/20/0217204/Linux-Kernel-Exploit-Busily-Rooting-64-Bit-Machines](http://linux.slashdot.org/story/10/09/20/0217204/Linux-Kernel-Exploit-Busily-Rooting-64-Bit-Machines)

Perhaps you like privilege escalation bugs that are unfixed for *five years* ?
[http://forums.theregister.co.uk/forum/2/2010/08/19/linux_vulnerability_fix/](http://forums.theregister.co.uk/forum/2/2010/08/19/linux_vulnerability_fix/)

---

### Post by Some Penguin on 2010-11-16
> **worksofcraft said:**
> Better for what purpose?
If you want better for employment opportunities or better for available games I'm afraid Windows is well ahead.

Depends on what employment area.  Developing apps for the consumer desktop space (which is, perhaps, not the most happening place to be... mobile, web, consoles for the gaming market), sure -- Microsoft Windows is a far larger market, and if not there, then OSX.  Both of those markets are probably more likely to be willing to pay for software, anyway, if they're sticking with decidedly non-free OSes.

Developing the server-side systems powering 'cloud-based' apps where the user is mostly fiddling with a client -- which includes lots of mobile apps, web apps, et al -- and you're probably much better off knowing the LAMP stack (substituting PostgreSQL or Oracle for MySQL if you like, of course) because 'nix-based server farms are usually seen as much more reasonable than MS Windows-based server farms.  For a server farm, you generally don't *need* a lot of the layers that are pretty integral to Microsoft Windows and would only needlessly burn CPU time (like freaky backwards-compatibility layers for old and screwy APIs, fancy windowing systems, and so forth), and it's also good to have an OS with more transparency -- easier to replicate, easier to customize, easier to audit for instance.

So what if it lags in fully exploiting 3D hardware in modern GPUs -- that's not the server's job.  Somebody like Google doesn't really care if their servers could run CoD:MW.

---

### Post by ssam on 2010-11-16
there is a talk by greg kh a few years ago that among other things says that linux supports more architectures and has more build in drivers than any other OS/kernel. might be worth hunting it down.

---

### Post by Reiger on 2010-11-16
That ACM article requires verification (to check if any points mentioned still apply) on your part. It refers to NT 4, which is positively ancient; and the Linux kernel of ~1997 is not exactly the Linux kernel of today either.

---

### Post by ssam on 2010-11-16
found it in the end
[http://www.kroah.com/log/linux/ols_2006_keynote.html](http://www.kroah.com/log/linux/ols_2006_keynote.html)

---

### Post by altonbr on 2010-11-21
Thanks everyone.

Any other ideas from the community? I guess it's not exactly an academic topic to say _why_ Linux is better than Windows, so I'll have to derive my conclusion from papers that state why Linux is amazing and juxtapose that to Windows.

Seems difficult because I don't think there will be many academic papers on Windows due to its closed source nature. I do understand that there are licenses professors can get to study Windows code (networking code for example) to students, but I'm not sure if that's enough for any professor to write a paper on.

If anyone can prove me wrong, I've love to know.

---

### Post by t1497f35 on 2010-11-21
Here's my opinion:
1) The Linux kernel is monolithic while Windows' kernel is not. A monolithic kernel is generally considered faster but more difficult to extend. Linux has solved the "extension" problem by introducing kernel modules which when loaded work as if they were native (without any performance penalties).

2) Linux/Unix/Mac/Solaris use POSIX compliant file systems which are more mature and extensible, for example to specify a full path under unix you don't have to specify the name of the device "C:\" or "D:\"  like on windows, I think if you study the differences between the architectures of these file systems you might come to the conclusion that the windows filesystem is an unfinished unix filesystem, I know it sounds too dramatic and sarcastic but that's the conclusion other folks I read from came to.

---

### Post by worksofcraft on 2010-11-21
> **t1497f35 said:**
> 
2) Linux/Unix/Mac/Solaris use POSIX compliant file systems which are more mature and extensible, for example to specify a full path under unix you don't have to specify the name of the device "C:\" or "D:\"  like on windows, I think if you study the differences between the architectures of these file systems you might come to the conclusion that the windows filesystem is an unfinished unix filesystem, I know it sounds too dramatic and sarcastic but that's the conclusion other folks I read from came to.

TBH I don't think that is a very fair assessment. Windows uses a file system that can have multiple roots while POSIX has a single root.

Explicit multiple roots **does** have some advantages:

[LIST=1]
[*]Knowing the separation between different devices with different performance characteristics e.g. read-only, removable, slow backup, etc... can be beneficial.

[*]Identifying the different devices is helpful to the casual computer user: e.g. that USB memory stick isn't just another path. It has physical reality.

[*]It also helps to know when you are trying to move large amounts of data from a folder on one device to another as opposed to just rewriting the directory entry.

[*]Separate devices can operate concurrently and an intelligent use of this can serve to minimize disk head movements and make a significant performance increase.
[/LIST]

I personally would have no hesitation in adopting a multiple root file hierarchy on Linux if such were available.

---

### Post by t1497f35 on 2010-11-21
I'm not sure what 4th point has to do with it since "multiple devices" + "speed" have nothing to do with where you mount them, be it on C:\ (that is without choice where it is mounted) or say on /media/sda2 (that is you have a choice where to mount them).

I agree that C:\ D:\ stuff is more intuitive for many desktop users since the device name is right there in the path, but, since Linux is more of a server beast it's supposed to be as extensible as possible (afaik one of the main reasons why Linux is on 90% of supercomputers), and while windows afaik runs out of disk names once all english letters are used, Linux doesn't.

---

### Post by worksofcraft on 2010-11-21
> **worksofcraft said:**
> TBH I don't think that is a very fair assessment. Windows uses a file system that can have multiple roots while POSIX has a single root.

Explicit multiple roots **does** have some advantages:

[LIST=1]
[*]Knowing the separation between different devices with different performance characteristics e.g. read-only, removable, slow backup, etc... can be beneficial.

[*]Identifying the different devices is helpful to the casual computer user: e.g. that USB memory stick isn't just another path. It has physical reality.

[*]It also helps to know when you are trying to move large amounts of data from a folder on one device to another as opposed to just rewriting the directory entry.

[*]Separate devices can operate concurrently and an intelligent use of this can serve to minimize disk head movements and make a significant performance increase.
[/LIST]

I personally would have no hesitation in adopting a multiple root file hierarchy on Linux if such were available.

p.s. also I think that scientists and philosophers don't normally look for specific evidence to supports a forgone conclusion. Instead I thought they do experiments and tests from which they can eventually draw said conclusion... don't they?

> **t1497f35 said:**
> I'm not sure what 4th point has to do with it since "multiple devices" + "speed" have nothing to do with where you mount them, be it on C:\ (that is without choice where it is mounted) or say on /media/sda2 (that is you have a choice where to mount them).

Well say I want to process my recorded video files and I know it's going to read a huge input file and write out a huge output file. With the actual devices being explict I can tell it to process say my input files from C: and write my output to D: and both those drives can virtually just operate sequentially.

OTOH if I do that all on one drive I'll probably end up with terrible disk fragmentation and the heads bopping from track to track endlessly.

Ditto if I put all my executables on one drive or partition and my data files elsewhere, my programs can be kept it all nicely efficient and defragmented :)

---

### Post by t1497f35 on 2010-11-21
> **worksofcraft said:**
> p.s. also I think that scientists and philosophers don't normally look for specific evidence to supports a forgone conclusion. Instead I thought they do experiments and tests from which they can eventually draw said conclusion... don't they?
haha they do.. of course they do.. As they say, in theory practice and theory are the same, in practice they're not.

---

### Post by t1497f35 on 2010-11-21
> **worksofcraft said:**
> 
Well say I want to process my recorded video files and I know it's going to read a huge input file and write out a huge output file. With the actual devices being explict I can tell it to process say my input files from C: and write my output to D: and both those drives can virtually just operate sequentially.

OTOH if I do that all on one drive I'll probably end up with terrible disk fragmentation and the heads bopping from track to track endlessly.

Ditto if I put all my executables on one drive or partition and my data files elsewhere, my programs can be kept it all nicely efficient and defragmented :)
I think you're confusing the mount points with the physical HDDs/partitions. If you mount what on windows is C: and D: on Linux respectively as /media/sda2 and /media/sda3 - it doesn't mean on Linux now they're on a single HDD or partition or anything like that, to Linux they're still two different HDDs (or paritions) and hence has nothing to do with speed.

---

### Post by worksofcraft on 2010-11-21
> **t1497f35 said:**
> I think you're confusing the mount points with the physical HDDs/partitions. If you mount what on windows is C: and D: on Linux respectively as /media/sda2 and /media/sda3 - it doesn't mean on Linux now they're on a single HDD or partition or anything like that, to Linux they're still two different HDDs (or paritions) and hence has nothing to do with speed.

Yes it's very easy to confuse mount points when they are not explicit.

When I boot to Windows I have drives C: D: E: and F:  four separate physical hard drives.
[LIST=1]
[*]Drive C is predominantly exectables and installation stuff that has nothing to do with me and should be relatively constant.
[*]Drive D: has all MY data on it... If the house is on fire I need to save drive D ;)
[*]Drive F: is for FRAPS to record videos to and basically it's a big scratch pad that I try to keep defragmented to improve performance of that kind of thing.
[*]Drive E is my Linux drive.
[/LIST]
Now I also mount drive D in Linux... actually it goes in as /home I think... but I would have to check my fstab entries... and well I do get really confused with them even when they are right there in front of me :P

---

### Post by Simian Man on 2010-11-21
There's no such thing as an operating system being "better" than another.  You have to take the usage into consideration.  I would focus on one area that Linux is a commonly used solution, such as web servers or supercomputers and investigate why.

Just saying, "Linux is better because there are no viruses and you can do pipes" wouldn't be an interesting presentation.

---

### Post by t1497f35 on 2010-11-21
@Simian Man
100%. The key question is the usage area, not to mention taste, subjective dialectics and biased benchmarks.

For those who wanna have quite some fun I'd suggest reading "The unix haters book" (note that some points from the book don't apply any longer) it has valid technical points but the most I like about it is that it's the funniest book on OSes and I'd really like someone to write "The windows haters book" to have more fun!

---

