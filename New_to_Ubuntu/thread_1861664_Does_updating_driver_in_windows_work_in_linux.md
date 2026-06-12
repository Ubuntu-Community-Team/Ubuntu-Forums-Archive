---
title: "Does updating driver in windows work in linux?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by listerdl on 2011-10-15
I have a dual boot - long story short - I am having a nightmare trying to find a driver that I can update due to SATA issues.

I have found the updated version but it only applies for windows. Just to rule out the (obvious) - if I update the driver in windows in my dual boot that will have zero impact in ubuntu right?

PS This is for a driver called: Intel 2829 ich92Fm family 4 port sata ahci controller

In short it keeps throttling my hard drives - I have tried to use different hard drives both SSD and normal and still the same throttling issue....

Solution must be to update the driver for ubuntu to read properly but alas there seems to be no linux update or am I wrong?

Can anyone point me in the right direction please? All googling seems to be in vain....

thanks

---

### Post by meatytaco on 2011-10-16
Drivers won't work for ubuntu. As far as the drivers you're needing, I can't help :/

---

### Post by Mark Phelps on 2011-10-17
Correct -- updating drivers in MS Windows will have not effect on your Ubuntu install, even controller drivers.

However, that also means that it will do nothing to solve the throttling issue if you also experience that in Ubuntu.

---

### Post by Redblade20XX on 2011-10-17
If there was a fix for your problem, it would probably come as a firmware update for the component, if I'm not correct! :)

-Red

---

### Post by Mark Phelps on 2011-10-17
> **Redblade20XX said:**
> If there was a fix for your problem, it would probably come as a firmware update for the component, if I'm not correct! :)

-Red

Not disputing the possibility of this, but I've applied HDD controller driver updates in Win7, for AHCI, and they never involved firmware changes.

Plus, if the AHCI driver update DID involve firmware changes, that means that the existing Linux driver would most likely NOT work anymore after the firmware update.

---

### Post by mglennpooh on 2011-10-17
The answer is NO. Click on the silver 11.10 Ubuntu Button top left, then, type " s " to reveal Software Sources (not Software Center) which is the simplified 11.10 replacement for Synaptic Packages (11.04 or earlier) - select Software Sources, then, OTHER, then, check mark Partners & Independents, then, go back & type " u " to reveal & select Update Manager, then, click on CHECK to refresh the update search cache to incl Partner & Independent Updates.

However, if you want odds & ends you will have to look to Software Center, or then, the Command Prompt Terminal (type " t " the same as above). or also download  from whatever website.

Canonical has a relationship with Intel. I suggest you google & phone Intel Customer Support to see if there's a solution for your problem, or then, also try the same for your PC Manufacture. If neither have a solution (or esp if they do) then come back to cut & paste here whatever fully detailed explanation they gave you. 

Happy Hunting
                                                                                                                             :popcorn:

---

### Post by Mark Phelps on 2011-10-17
> **mglennpooh said:**
> The answer is NO. Click on the silver Ubuntu Button top left, then, type " s " to reveal Software Sources which is the simplified replacement for Synaptic Packages - select Software Sources, then, OTHER SOFTWARE, then check mark most options, esp Partners & Independents, then, go back & type " u " to reveal & select Update Manager, then, click on CHECK to refresh the update search cache to incl the above mentioned update option additions. 

However, if you want programs you will have to look to Software Center, or then, the Command Prompt Terminal (type " t " the same as above). or also download the key setup.exe from whatever website.

Happy Hunting
                                                                                                                             :popcorn:

Synaptic does provide the capability to find drivers -- if you know the package name, but from what I've seen, Software Center does not do this.

Also, "setup.exe" is an MS Windows program -- and Windows drivers (with the rare exception of using NDISWrapper for Networking) can NOT be installed in Linux, even using Wine (and its derivatives).

---

### Post by MartyBuntu on 2011-10-17
> **listerdl said:**
> 
PS This is for a driver called: Intel 2829 ich92Fm family 4 port sata ahci controller



Let me see if I understand...you are running hard drives off a controller card and you need drivers for this card?

---

### Post by egalvan on 2011-10-17
check on how the SATA drives are being accessed in the BIOS..
native SATA or ahci.

also see if a RAID function is enabled.

---

### Post by listerdl on 2011-10-19
> **egalvan said:**
> check on how the SATA drives are being accessed in the BIOS..
native SATA or ahci.

also see if a RAID function is enabled.

How do I check if RAID is enabled? I guess that would be in the BIOS right?

I am unable to change the BIOS settings for SATA or AHCI. This error is v odd to fix - just to be clear again, the message is this:

```

limiting SATA link speed to 1.5 Gbps
ata4: hard resetting link
```

Life seems to go on without any problems using ubuntu but I dont like knowing that there "is an issue" with the above error message coming twice every second....

Thanks for all help and pls let me know if you have any other thoughts? Thanks

---

