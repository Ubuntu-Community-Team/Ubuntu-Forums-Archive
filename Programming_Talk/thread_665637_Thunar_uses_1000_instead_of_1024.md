---
title: "Thunar uses 1000 instead of 1024?"
date: 2008-01-12
forum: Programming Talk
---

### Post by xlinuks on 2008-01-12
Hi,
It looks like Thunar counts the size of the partitions by 1000 for a unit (KB, MB, GB) rather than 1024. Is it true?
I'm judging by the results I get.
For example Thunar displays 255GB for a given partition, while Nautilus and a java app (console output) display 234GB for the same partition, here's a screenshot:
[http://xlinuks.googlepages.com/thunar_partition_size.jpg](http://xlinuks.googlepages.com/thunar_partition_size.jpg)

Does anyone think this is a feature or should I submit a bug?

---

### Post by popch on 2008-01-12
The prefixes G, M and k stand for factors of 10^9, 10^6 and 10^3, respectively. The use of those very same prefixes for 2^10^n (with n=9, 6 and 3, respectively) is in fact contrary to the definition of those prefixes.

I think that 1000*1000*1000 Bytes should be called 1GiB, at least according to an article I read recently.

In short, it's possible that Thunar got it right and the others did not. Do some research before reporting a bug.

---

### Post by xlinuks on 2008-01-12
In fact I remember an HDD maker (I guess Seagate, not sure though, and they lost the case) being sued for counting 1GB as 1000MB, so they had to use from that moment 1GB=1024MB. Anyway I guess it's a messy issue I don't wanna dive into, so be it as everyone likes. btw konqueror counts like Thunar

---

### Post by Quikee on 2008-01-12
10^9 B or 1000*1000*1000 B is 1 GB 
2^30 B or 1024*1024*1024 B is 1 GiB (giga binary byte)

---

### Post by Lster on 2008-01-12
I think Quikee is right. Look at this from Wikipedia:

[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

---

### Post by Wybiral on 2008-01-12
I think it [depends on the context]("http://en.wikipedia.org/wiki/Binary_prefix#SI_prefixes_used_in_the_binary_sense"). But in the case of a memory measurement, I would think the binary usage would be correct, right?

---

### Post by Lster on 2008-01-12
[QUOTE=Wikipedia]There has been considerable confusion about the meanings of SI prefixes used with the word "byte", such as kilo- (k or K) and mega- (M), as shown in the chart Quantities of bytes. Since computer memory comes in powers of 2 rather than 10, the industry used binary estimates of the SI-prefixed quantities. Because of the confusion, a contract specifying a quantity of bytes must define what the prefixes mean in terms of the contract (i.e., the alternate binary equivalents or the actual decimal values, or a binary estimate based on the actual values).[/QUOTE]

I use either depending on context and what I'm talking about - I don't know whether that would be correct or not though...

---

### Post by engla on 2008-01-12
Well basically the binary form should always be used, it's what we mean when we say gigabyte and megabyte too, even though there are formal differences defined now..

Using the decimal forms only makes sense if you are an engineer or mathematician wanting to count the number of sectors on your hard disk -- not to figure out how your computer would use them, but just in case you wonder how many they are.

I think thunar should change, but if konqueror does the same thing I'm pretty surprised (thunar probably just does what konq does); konqueror is so established they must have done a conscious decision on this case. Why decimal?

---

### Post by popch on 2008-01-13
> **engla said:**
> Well basically the binary form should always be used, it's what we mean when we say gigabyte and megabyte too, even though there are formal differences defined now..

Using the decimal forms only makes sense if you are an engineer or mathematician wanting to count the number of sectors on your hard disk -- not to figure out how your computer would use them, but just in case you wonder how many they are.

I think thunar should change, but if konqueror does the same thing I'm pretty surprised (thunar probably just does what konq does); konqueror is so established they must have done a conscious decision on this case. Why decimal?

I don't think that using powers of two to the tenth gives anyone but some engineers any kind of advantage. Who on earth is comfortable with subtracting or even only adding that kind of numbers? Quick: how much room in bytes is there on a disk with partitions of 10.86GiB, 13.47GiB and 11,52GiB? Can you prove that your result is accurate?

When discussing memory chips on silicon chips and such, counting capacities in a number system closely related to the addressing scheme makes sense.

It does not make sense on a fixed disk where the capacity derives from the number of platters, surfaces used, cylinders on a surface, number of sectors on a cylinder (variable because the circumference varies with distance from center) and intersector gap size.

As far as I am aware, not even the BIOS takes the least interest in the geometry of a disk. It just calls off the sectors to be read or written by sector number relative to the beginning of the drive.

---

### Post by Wybiral on 2008-01-13
I put my faith in Google:
[LIST]
[*][1 byte = ? bits]("http://www.google.com/search?q=1+byte+%3D+%3F+bits")
[*][1 kilobyte = ? bytes]("http://www.google.com/search?q=1+kilobyte+%3D+%3F+bytes")
[*][1 megabyte = ? kilobytes]("http://www.google.com/search?hl=en&q=1+megabyte+%3D+%3F+kilobytes")
[*][1 gigabyte = ? megabytes]("http://www.google.com/search?hl=en&q=1+gigabyte+%3D+%3F+megabytes")
[/LIST]

---

### Post by popch on 2008-01-13
> **Wybiral said:**
> I put my faith in Google:[LIST]
[*][1 byte = ? bits]("http://www.google.com/search?q=1+byte+%3D+%3F+bits")
[*][1 kilobyte = ? bytes]("http://www.google.com/search?q=1+kilobyte+%3D+%3F+bytes")
[*][1 megabyte = ? kilobytes]("http://www.google.com/search?hl=en&q=1+megabyte+%3D+%3F+kilobytes")
[*][1 gigabyte = ? megabytes]("http://www.google.com/search?hl=en&q=1+gigabyte+%3D+%3F+megabytes")[/LIST]

Go back to square one.

---

### Post by Quikee on 2008-01-13
Well.. who needs standards anyway. Right?

---

### Post by Lster on 2008-01-13
I think different situations require you to take one or the other. And I guess as long as you and whoever you are communicating with understand which definition you're using, there isn't any problem.

---

### Post by Wybiral on 2008-01-13
Perhaps we should make the distinction between "giga byte" and "gigabyte"? I just don't think I'm ready to call 1024 bytes a kibibyte. Everyone I know uses the term "kilobyte" and it's just understood what you are talking about.

---

### Post by Lster on 2008-01-13
Good luck. ;)

I'm happy to just go on using kilobyte to mean 1024 bytes - whether it's right or not.

---

