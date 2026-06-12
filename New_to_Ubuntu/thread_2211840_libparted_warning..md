---
title: "libparted warning."
date: 2014-03-18
forum: New to Ubuntu
---

### Post by jmontano27 on 2014-03-18
Hello, 

I am completely new to using Linux. I wanted to use it to gain more understanding on computers in preparation for a pre-computer sciences degree. I was following a guide on how to dual boot Ubuntu and Windows 7 and it had me shrink the partition that had windows on it than go into gparted on Ubuntu. As soon as I open Gparted I get this message.

[I]Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?

[/I] I'm not sure what any of that means. If I should hit yes or no and continue on my way? I just want to learn as much as I can but when looking into the problem there is so much jargon that I can't understand what I read haha.

---

### Post by TheFu on 2014-03-18
Welcome to the forums! 
I cannot answer the question with the data provided.

[http://www.partitionguru.com/seo/MBR-or-GPT.php](http://www.partitionguru.com/seo/MBR-or-GPT.php) is a comparison.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table) is a good overview.
GPT is a good thing, but different. You want to be certain that you absolutely KNOW whether MBR or GPT is being used before proceeding.  

Also, if the system uses UEFI - things get more complex.  Google is your friend for learning about UEFI too.  As a "pre-Computer Science" major, you'll need to get good at internet searching.  "Ubuntu UEFI" is a good start.

The way to learn the jargon is to read, sleep, read, sleep, and keep going for a few weeks until it starts to click. I've been doing this 20+ yrs and there are new terms every day.  Like I've never heard of a "pre-computer sciences degree" before.

Oh - and before you do move forward, be certain you have a 100% recoverable backup. This partition stuff can be extremely dangerous to anything on the system and anyone can trash the disk accidentally - experts and less-than-experts alike.

---

### Post by jmontano27 on 2014-03-19
> **TheFu said:**
> Welcome to the forums! 
I cannot answer the question with the data provided.

[http://www.partitionguru.com/seo/MBR-or-GPT.php](http://www.partitionguru.com/seo/MBR-or-GPT.php) is a comparison.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table) is a good overview.
GPT is a good thing, but different. You want to be certain that you absolutely KNOW whether MBR or GPT is being used before proceeding.  

Also, if the system uses UEFI - things get more complex.  Google is your friend for learning about UEFI too.  As a "pre-Computer Science" major, you'll need to get good at internet searching.  "Ubuntu UEFI" is a good start.

The way to learn the jargon is to read, sleep, read, sleep, and keep going for a few weeks until it starts to click. I've been doing this 20+ yrs and there are new terms every day.  Like I've never heard of a "pre-computer sciences degree" before.

Oh - and before you do move forward, be certain you have a 100% recoverable backup. This partition stuff can be extremely dangerous to anything on the system and anyone can trash the disk accidentally - experts and less-than-experts alike.

I suppose I did word this wrong. I wanted to know what caused this message and what exactly it meant.

I did all the suggested reading and it made little sense to me, but as you said just keep reading and one day it'll click.

"Pre-comp sci" Is just a community college thing, you take it then transfer out to a different university in 2 years to finish your BA.

I have the recovery partition, or is it recommended to back up in a different manner?

---

### Post by jmontano27 on 2014-03-19
Oh I also wanted to add I was able to see that my HDD was MBR.

I'm using my android to boot up a live version of Ubuntu? Is the android device what is causing the error message?

---

### Post by TheFu on 2014-03-19
> **jmontano27 said:**
> I suppose I did word this wrong. I wanted to know what caused this message and what exactly it meant.

I did all the suggested reading and it made little sense to me, but as you said just keep reading and one day it'll click.

"Pre-comp sci" Is just a community college thing, you take it then transfer out to a different university in 2 years to finish your BA.

I have the recovery partition, or is it recommended to back up in a different manner?

I cannot tell exactly what it meant from here. Sorry. Could mean any of 20 different things.  I could "guess" that it means you have a GPT partition and are trying to treat it like an MBR partition. That would be bad.  MBR tools don't recognize GPT at all, so be extra careful and use some GPT tools before trusting what any MBR tool says.

Nothing wrong with community colleges.  Lots of REALLY, REALLY smart people did/do the same thing. Seems like you are in a comp-sci degree program to me.

Recovery partition will put the box back to factory defaults with all other data lost. The type of stuff you are doing might wipe the recovery partition too - so NO, IT IS NOT enough.  How to backup is a huge question and depends on many different factors. For Windows, only a bare metal recovery tool is useful, IMHO. That means image-based backup - something like clonezilla, partimage or fsarchive --- or even just a 100% bit-for-bit copy with dd. This is relatively inefficient, but necessary.  

For Linux, we can be much, much, much more efficient with backups.  I don't bother backing up the OS, just get settings, list of packages and data. That saves about 4-5G per instance.

---

