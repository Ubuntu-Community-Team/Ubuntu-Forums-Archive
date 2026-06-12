---
title: "Folder showing 48.9 GB as size of data on on version of Ubuntu and 46.7 GB on another"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by ask_ on 2013-04-28
Hello .

I have Ubuntu 12.04 on my laptop and recently installed Lubuntu 13.04 on my old Desktop.

I have a portable hard disk containing data. In it I have a folder , I check it's size sometimes. 

I found out that in Lubuntu 13.04 that folder is showing 46.7 GB data as compared to 48.9 GB on Ubuntu 12.04 , I thought I may have inadvertently deleted some thing so check that folder again in Ubuntu 12.04 and it showed 48.9 GB. 
(Earlier that folder used to show 48.9 GB on Lubuntu also when I had Lubuntu 11.10 on my system)

This really surprised me . As such it does not effect me as I am a very basic user. But asking this in a thread just as a curiosity. What could be a reason this may be happening ? Do different OS have different way of counting bytes.

Thanks.

P.S :- By the way older Lubuntu would show size on disk as 8 times original file size. Newer Lubuntu does not have that , which is good.

---

### Post by DuckHook on 2013-04-28
Interesting. Did not know that it did that. But to hazard a guess, 46.7 is almost exactly equal to 48.9 in GiB, so I suspect that Lubuntu 13.04 is reporting in GiB whereas Ubuntu 12.04 is reporting in GB. I guess it just depends on where each flavour/version is getting its data.

For those who don't know: iB is sometimes called "true" bytes because binary does not equate exactly to base-ten decimal system. The closest number is 1024 (2^10), so whereas a GB is 1,000,000 KB, a GiB is 1,048,576 KB.

46.7 x 1,048,576 = 48.9 less rounding error.

Disk manufacturers have taken to stating HDD capacities in GB whereas system and memory module manufacturers state their numbers in the more sensible GiB (after all, computers ***are*** binary systems). This occasionally leads to issues when users do not set aside enough space in their HDDs to hibernate to disk. This is a small peeve of mine, as I suspect HDD vendors of trying to inflate their capacity numbers purely for marketing purposes, at the expense of confusion for users, as per your question above.

---

### Post by ask_ on 2013-04-28
> **DuckHook said:**
> Interesting. Did not know that it did that. But to hazard a guess, 46.7 is almost exactly equal to 48.9 in GiB, so I suspect that Lubuntu 13.04 is reporting in GiB whereas Ubuntu 12.04 is reporting in GB. I guess it just depends on where each flavour/version is getting its data.

For those who don't know: iB is sometimes called "true" bytes because binary does not equate exactly to base-ten decimal system. The closest number is 1024 (2^10), so whereas a GB is 1,000,000 KB, a GiB is 1,048,576 KB.

46.7 x 1,048,576 = 48.9 less rounding error.

Disk manufacturers have taken to stating HDD capacities in GB whereas system and memory module manufacturers state their numbers in the more sensible GiB (after all, computers ***are*** binary systems). This occasionally leads to issues when users do not set aside enough space in their HDDs to hibernate to disk. This is a small peeve of mine, as I suspect HDD vendors of trying to inflate their capacity numbers purely for marketing purposes, at the expense of confusion for users, as per your question above.


Hi, thanks for the informative reply.

You are right Lubuntu is showing data in 'GiB' . 

Cool , learned something new.

Thanks again.

---

### Post by DuckHook on 2013-04-28
Since you seem interested in the minutiae of computing, another hazarded guess is that the older versions of Lubuntu that you referred to showed capacity in bits rather than bytes. Since a byte is equal to 8 bits, the capacity number would be 8 times as high. I am not as sure on this one because I did not start using Lubuntu until it became an official flavour, so am unfamiliar with its history.

---

### Post by Impavidus on 2013-04-28
> **DuckHook said:**
> 
Disk manufacturers have taken to stating HDD capacities in GB whereas system and memory module manufacturers state their numbers in the more sensible GiB (after all, computers ***are*** binary systems). This occasionally leads to issues when users do not set aside enough space in their HDDs to hibernate to disk. This is a small peeve of mine, as I suspect HDD vendors of trying to inflate their capacity numbers purely for marketing purposes, at the expense of confusion for users, as per your question above.

Not sure I would call it sensible. Saying 101110.11 GiB instead of 48.9 GB would definitely make sense, but a mixed decimal-binary system makes it nearly impossible to convert GiB to kiB using mental calculation. The only advantage is when things come in powers of two and you get round numbers, which tends to be the case for RAM, but not for disk space.

---

### Post by DuckHook on 2013-04-28
> **Impavidus said:**
> The only advantage is when things come in powers of two and you get round numbers...

There are far more advantages than only one.

I think that the faster new users get used to the binary nature of computers, the faster they will feel comfortable and not be lost on even basic system tasks. One would think that the OP's initial post was evidence enough. If it doesn't suffice then consider:

Permissions are in Octals.
UUIDs are hexadecimal.
RAM is MiB or GiB.
The OS itself operates in either 32 or 64 bits.
HDDs themselves operate in 512-byte sectors.
MBRs are 512 bytes.
The size limit of a classically partitioned HDD is exactly 2TiB.
All are base-two.

There are literally thousands of other examples, but the above pop up all the time and so many issues arise from their misunderstanding and subsequent misapplication that an iB convention is, in my opinion, a necessity. Since apps run in RAM, their size should be stated in iB not least if simply to figure out whether they fit into memory. And if it makes the most sense to measure apps in iB, then it only makes sense for their storage devices to be measured likewise. Similarly, due to the binary-based limits in the MBR, it only makes sense to say that such a disk maxes out at 2 TiB. It makes no sense whatsoever to say that the maximum is 2.147 TB. Insisting on decimalization just confounds understanding and divorces hard drives from their technical realities. If everything were expressed in GiB, this would far and away be the most sensible scheme because it obviates much of the need for conversion to start with.

In any case, mine is fated to be an academic complaint. HDD vendors are not about to change and will not be swayed by considerations of what is sensible. Users will continue to allocate too little swap space, have trouble figuring out permissions and wonder why they can't access a drive larger than 2-terabytes-and-a-little-bit-extra.

---

### Post by Impavidus on 2013-04-28
We shouldn't hijack this thread with a discussion on units so I'll stop after this post, but I don't really insist on decimalisation, more on not using a *mixed* system. Using units with conversion factors of 2^10 only provides for easy calculation if the base of the numerical system is either 2, 4, 32 or 1024 (2^1, 2^2, 2^5 or 2^10; 1, 2, 5 and 10 being the divisors of 10). Apart from arithmetic, the conversions only have visible effect by giving round numbers for high powers of 2 (more than 2^10). The size of the disk is however still indicated using a decimal number (46.7 in this case). This is about as inconvenient as using 12 inches in a foot or 112 pounds in a hundredweight, reason why most of the world has switched to the metric system. I think, maybe it seems less inconvenient to people still using more traditional units (and maybe the MiB could only have been invented by the few people still using such a system). It would be great to use units with conversion factor 1024, but we'd need to switch to a quarternary or a base-32 numeral system. I'm familiar with duodecimal, octal etc., I even regularly do long divisions in octal, it's all very easy, *as long as you don't mix systems*.

Anyway, we're getting somewhere. It must have something to do with the relatively large number of non-metric people in the computer world. I don't think a Frenchman would come up with the idea of usin a non-decimal prefix. Little more advantages than the round numbers in RAM size and the 2^41 byte limit on MBR disks. 41, that's a prime number.

---

