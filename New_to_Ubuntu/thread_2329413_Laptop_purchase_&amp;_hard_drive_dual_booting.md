---
title: "Laptop purchase &amp; hard drive dual booting"
date: 2016-07-01
forum: New to Ubuntu
---

### Post by misswham2 on 2016-07-01
Good morning.  My husband said he would only buy me a new laptop IF I dont put linux on it and he hates anything outside of Windows first off and he says I will void the warranty if I mess with the partition and I asked the Geek Squad and they said yes that most manufacturers will void the warranty if I do that and I see too many problems in review sections of all laptops.  So my question to you all is, if I put Ubuntu Mate in a Virtual Machine, will that be the same as messing with the harddrive, will it run as smoothly as if I had it on its own partition, will my windows be vulnerable to viruses, malware/spyware if I access something on Linux in the Virtual Machine and what type of processor and ram would I need to accomplish running Linux in a virtual machine for it too run just as sufficiently as if the harddrive was partitioned?  I only use the computer to look at videos on youtube, access websites, chat etc (basic stuff).   I have used VM in Linux but not through Windows.  I dont use windows  for SQUAT but once a year and thats to do my taxes because Turbotax isnt  compatible with Linux.

Also, I was under the impression that linux didnt work with touchscreens on computers but I took Ubuntu Mate 16.04 on a flashdrive to BestBuy and booted the live version and guess what, the touchscreen worked on the HP I tried it on.  Does linux now work with touchscreens?  Also,

---

### Post by howefield on 2016-07-01
> **misswham2 said:**
> Good morning.  My husband said he would only buy me a new laptop IF I dont put linux on it and he hates anything outside of Windows first off and he says I will void the warranty if I mess with the partition and I asked the Geek Squad and they said yes that most manufacturers will void the warranty if I do that and I see too many problems in review sections of all laptops.

Hmm.. so [what changed then]("http://www.geeksquad.com/intelligence/blog/thinking-about-changing-your-os-some-points-to-ponder/") ?

>  So my question to you all is, if I put Ubuntu Mate in a Virtual Machine, will that be the same as messing with the harddrive, will it run as smoothly as if I had it on its own partition

No, it won't run as smoothly however depending on the specifications of the host machine it may well be a negligible difference. It would help if the Virtual Machine was on a separate disk. 

> will my windows be vulnerable to viruses, malware/spyware if I access something on Linux in the Virtual Machine

Malware could in theory cross from guest to host especially if using shared folders, bridged networking and the like, but a lot depends on the user :)

> and what type of processor and ram would I need to accomplish running Linux in a virtual machine for it too run just as sufficiently as if the harddrive was partitioned?

Most laptops these days would be capable of running virtual machines, but I'd be looking for a quad core processor, at least 4GB of RAM and preferably 8 and a decent graphics card.
  
> I only use the computer to look at videos on youtube, access websites, chat etc (basic stuff).   I have used VM in Linux but not through Windows.  I dont use windows  for SQUAT but once a year and thats to do my taxes because Turbotax isnt  compatible with Linux.

A VM should sail through any of that.

> Also, I was under the impression that linux didnt work with touchscreens on computers but I took Ubuntu Mate 16.04 on a flashdrive to BestBuy and booted the live version and guess what, the touchscreen worked on the HP I tried it on.  Does linux now work with touchscreens?  Also,

Cool.

---

### Post by oldfred on 2016-07-01
One user a year or two ago posted that he regularly buys a higher end laptop with a hard drive. Before even booting it, removes hard drive & puts in a SSD and installs Ubuntu.
Then later he can sell system with "new" copy of Windows that does not have any of his data and buy a new system.

Vendors help lines will say they do not support anything but Windows and they do not always support that. Users have posted that they suggest calling Microsoft & Microsoft says to call vendor.

Have not seen a system that has the fine print that use of your system voids warranty. 
Ubuntu is just software.

---

### Post by kurt18947 on 2016-07-01
> **oldfred said:**
> One user a year or two ago posted that [B]he regularly buys a higher end laptop with a hard drive. Before even booting it, removes hard drive & puts in a SSD and installs Ubuntu.
Then later he can sell system with "new" copy of Windows that does not have any of his data and buy a new system.
[/B]
Vendors help lines will say they do not support anything but Windows and they do not always support that. Users have posted that they suggest calling Microsoft & Microsoft says to call vendor.

Have not seen a system that has the fine print that use of your system voids warranty. 
Ubuntu is just software.

That might be a bit of an expensive way to go about it but it should sure cover any attempts by a manufacturer or vendor to avoid honoring their warranty. I wouldn't be surprised if buying the same machine with an SSD installed would cost more than buying an aftermarket SSD so perhaps the price difference would not as great as one might think. 


> Microsoft says to call vendor.]

I thought one reason OEM Windows is cheaper than retail Windows is that Microsoft is not required to provide support for OEM/system builder versions. So yeah, it seems to me like Microsoft would be correct to require the seller to provide after sale support.

---

### Post by Vincent_Massi on 2016-07-02
If you have Linux on a virtual machine within Windows, you would have a hard time transferring a virus.

Few viruses can function in Linux to begin with, and Windows viruses don't work on Linux. Sharing files between Linux and Windows is difficult.

No, a virtual machine protects your main operating system from any viruses that the virtual machine picks up.

---

