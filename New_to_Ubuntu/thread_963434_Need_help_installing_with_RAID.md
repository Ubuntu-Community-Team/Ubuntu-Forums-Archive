---
title: "Need help installing with RAID"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Zeph79 on 2008-10-30
Hey everyone.

I have an Intel DQ965GF motherboard and I have 3 SATA drives attached to it.  

I go into the utility in the motherboard and set up a RAID 5 volume.   No problem at all.   The disks format and become a raid volume.

However when I go to install ubuntu, it still shows 3 drives and not one volume.   Why is this and how can I get the OS and everything on the RAID 5 volume?

---

### Post by brandoncolorado on 2008-10-30
> **Zeph79 said:**
> Hey everyone.

I have an Intel DQ965GF motherboard and I have 3 SATA drives attached to it.  

I go into the utility in the motherboard and set up a RAID 5 volume.   No problem at all.   The disks format and become a raid volume.

However when I go to install ubuntu, it still shows 3 drives and not one volume.   Why is this and how can I get the OS and everything on the RAID 5 volume?

This help?
[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by aeiah on 2008-10-30
apparently that motherboard actually uses fake RAID, basically software raid on the motherboard level. update your bios to the newest version and see if that helps, or see if 8.10 solves your problem. after a quick google, it seems some people with opensuse got it working with your motherboard so its certainly possible

---

### Post by Zeph79 on 2008-10-30
Awesome.   I figured it was FAKE raid but its better than nothing I guess.  I will do the steps in the method you posted and see if that takes care of it.  If not I guess Ill have to drop some money for a PCI raid card but Ill have to get suggestions as to which ones work with ubuntu if I take that route.  

Ill let you know how it goes either way.   Thanks again

---

### Post by Zeph79 on 2008-10-30
Meh forget this...  

Answer me another question.  Can you point me to a RAID card that will work with ubuntu without having to "hack" it?   I dont like the warning about losing data since this will be a file server.  

The drives are 1TB each and I have 3 of them.   

I guess if all else fails I can get another motherboard so feel free to suggest one of those too.   It is running a Core 2 Duo processor.    

Just seems like this will be the easier and safest route to take.

---

