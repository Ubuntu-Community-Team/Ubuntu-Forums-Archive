---
title: "clarifying raid 1 doubt"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by sazan on 2008-11-06
RAID 1 requires at least 2 hard drives, and additional hard drives must always be added in pairs. It is ideal for applications where data is critical.

we can use mdadm to create Raid 1 using 3 disks.. 

i tried this on 3 disks and got usable space of only 1 disk. . 

i get that the 2nd  disk will be used for mirroring.. 

now my question is wat happens to the 3rd disk..?? does the data get written in it also.. if so y is the usable space only of single disk.. ??

---

### Post by Mr_JMM on 2008-11-06
raid 1 is mirror raid. It will mirror all drives regardless of how many you have. If you therefore have 3 drives then all three will be mirrored and so give you the equivalent capacity of one. That's the point of Raid 1.

Perhaps if you tell us what you're trying to achieve, we'll be able to help you better.

---

### Post by sazan on 2008-11-06
> **Mr_JMM said:**
> raid 1 is mirror raid. It will mirror all drives regardless of how many you have. If you therefore have 3 drives then all three will be mirrored and so give you the equivalent capacity of one. That's the point of Raid 1.

Perhaps if you tell us what you're trying to achieve, we'll be able to help you better.

wat i summarized is... in even no. of disks for RAID 1 , the usable memory will be just half and this half data is mirrored in other disks respectively.. 

and in odd no. of disks as u hav mentioned(in our case 3 disks).. 1 disk will hav the data and the other 2 disks will hav the mirrored data of it.. 

i want to confirm wat i am understanding here is right ? also when i add 1 more spare disk to raid 1 with 3 disks.. then my first case holds true ??

---

### Post by Mr_JMM on 2008-11-06
If you keep adding discs in a raid 1 array you won't gain any more hard drive space. You will still get the equivalent of just the smallest drive (normally) with all having exactly the same data on them.

For example, if you have 4 hard drives in Raid 1 (you really wouldn't but for the sake of an example), 2x 320gb, 1x 500GB and 1x 120GB and put them all in a raid 1 array you will end up with a maximum of 120gb Hard drive capacity.

If all 4 drives are 320GB then you will have a total hard drive capacity of 320GB.

If you explain in detail what you want from your Hard drives I will advise the best way to set it up.

---

### Post by sazan on 2008-11-06
> **Mr_JMM said:**
> If you keep adding discs in a raid 1 array you won't gain any more hard drive space. You will still get the equivalent of just the smallest drive (normally) with all having exactly the same data on them.

For example, if you have 4 hard drives in Raid 1 (you really wouldn't but for the sake of an example), 2x 320gb, 1x 500GB and 1x 120GB and put them all in a raid 1 array you will end up with a maximum of 120gb Hard drive capacity.

If all 4 drives are 320GB then you will have a total hard drive capacity of 320GB.

If you explain in detail what you want from your Hard drives I will advise the best way to set it up.



that means no matter how many hard disks i add.. all the data will be mirrored to the new ones.. 

act i am workng on somethin that will allow users to create raid from available hard disks so they can maximum throughput from it... so i was working on RAID 1 and i came up with these doubts... which i need to clarify before goin into the implementation.. 

ur previous post gave rise to a new doubt for me now.. :)..

now what if i hav 4 hard disks of RAID 1 and i add a 5th hard disk now.. wht will be the scenario.. wat will be writtem in this 5th disk (where 1st and 2nd hav mirrored data ,3rd and 4th hav mirrored data)(whose data will be mirrored to 5th disk) ???

---

### Post by Mr_JMM on 2008-11-06
If all the disks are in the same raid 1 array then all disks will have the same data on them.

When you say "maximum throughput" do you mean read / write speed? If so, yo are correct that you will need several disks to see an improvement but needs to be set up to support split seek.

> workng on somethin that will allow users to create raid from available hard disks

Are you setting up a server? If multiple users share a Raid 1 array, you won't be able to choose which data is raided and which isn't (certainly not using raid 1).

You would need to set up a separate raid array (containing it's own dedicated HDD's) for each user.

---

### Post by sazan on 2008-11-06
> **Mr_JMM said:**
> If all the disks are in the same raid 1 array then all disks will have the same data on them.



but wat i hav understood is that all the disks wont be having the same data.. its like if i hav 4 disks..then 1st data is mirrored to 2nd and 3rd disk data is mirrored to 4th one.. isn't that the case ??

> 
When you say "maximum throughput" do you mean read / write speed? If so, yo are correct that you will need several disks to see an improvement but needs to be set up to support split seek.


raid 1 wil b just an option to the user.. so it wil b upon user to choose raid 1 no matter d throughput..but tats not the topic i want to understand here... than understanding abt kind of data being written on these disks..

---

### Post by Mr_JMM on 2008-11-06
> but wat i hav understood is that all the disks wont be having the same data.. its like if i hav 4 disks..then 1st data is mirrored to 2nd and 3rd disk data is mirrored to 4th one.. isn't that the case ??

That would be true if you have two separate raid 1 arrays.

Sorry, if I understand correctly then to answer your question, **Yes**, it is possible to set up multiple raid 1 arrays but this will depend on your hardware / software raid controller. Simply throwing a drive in may not work as you expect.

---

### Post by sazan on 2008-11-06
> **Mr_JMM said:**
> That would be true if you have two separate raid 1 arrays. It is possible to set up multiple raid 1 arrays but this will depend on your hardware / software raid controller. Simply throwing a drive in may not work as you expect.

ohh!! lemme summarize once again then.. raid 1 can take n no. of disks and usable memory wil be of 1 disk and rest will hav mirrored data and in case i need more storage then i will need multiple raid 1 arrays ....is it??

---

### Post by Mr_JMM on 2008-11-06
ohh!! lemme summarize once again then.. raid 1 can take n no. of disks and usable memory wil be of 1 disk and rest will hav mirrored data and in case i need more storage then i will need multiple raid 1 arrays ....is it??

> raid 1 can take n no. of disks
The number of raid 1 arrays and disks will be limited by your your system only. It is theoretically possible to have any number (at least 2) disks in a raid 1 array.

> usable memory wil be of 1 disk
if drives are of same size, total storage space will be 50% of total if two disk used.
If drives of different size used then total storage is:
size of smallest HDD / (size of smallest + size of largest).

> in case i need more storage then i will need multiple raid 1 arrays
You can either use larger HDD's or multiple arrays, yes.

It sounds like you're trying to set up a server. If you have several HDD's it may be worth considering raid 10 (raid 1+0) for the sake of speed and security against drive failure.

---

### Post by sazan on 2008-11-06
i just tried mdadm for 4 disks with all different sizes.. and i think i finally udnerstand now.. the usable memory was of the disk with minimum size.. 


finally i feel relieved. .. thanks to u.. !!:):):)



i hav more doubts in Raid 5 if u can clarify....

---

### Post by Mr_JMM on 2008-11-06
Glad to help, sorry it took me so long to understand.

Do please feel free to ask any further questions.

---

### Post by sazan on 2008-11-06
thanks a lot for ur assistance... u r really a great help..



my questions as follows.. 

1. mdadm allows us to make RAID 5 with 2 disks.. but i dont agree to that RAID as RAID 5.. but it is doing so.. so must be a reason.. cudnt understand that from a long time ??


2. assume i m using 3 disks for RAID 5..now i hav 2 main questions here.. 

  2.1 u must be knowin abt the hot swapping concept in RAID 5....
          
          what happens when 1 of my disk fails.. as far as i knw ... it will wait for the 3rd disk and wont fail 'cause parity bits are there to recover data.. but what if i want to read a file whose one block is there in the 3rd failed disk... then will the raid wait for the 3rd disk to be inserted or it will recover from parity eating processing power and give the data... ??

  
 2.2 what is degraded mode actually and what exactly happens in that mode.. ??

hope i am descriptive enough for these queries.. ask me if u need anythin in detail description...

---

### Post by Mr_JMM on 2008-11-06
Raid 5 in brief: 
Raid 5 will give you more capacity and requires at least 3 drives. The data is written across all of the drives rather than mirrored so if one drive fails you can replace it and build the data from the remaining.

Total storage is size of smallest drive x (number of drives - 1).

Eg. If you have 2x 320GB drives and 1x 500GB drive, total capacity would be:
320GB x ( 3 - 1) = 320GB x 2 = 640GB.

As you can see, Raid 5 will give more storage for 3+ drives than Raid 1 will.

However, to use raid 5 you really should use a hardware controller. It can be set up using a software controller but performance would be seriously reduced.


> 1. mdadm allows us to make RAID 5 with 2 disks.. but i dont agree to that RAID as RAID 5.. but it is doing so.. so must be a reason.. cudnt understand that from a long time ??
Very strange. I'd not advise less than 3.

Hot swapping: Raid 5 does allow for hot swapping drives but again, is dependant on system / hardware used.


> what happens when 1 of my disk fails
In theory, the data should be safe as info can be calculates from the remaining disks. This allows you the time to swap the failed drive and for the data to be re-created. A failure of a 2nd drive will destroy the array. However, a system failure can cause array failure especially if data is being written at the time. Similarly, if data is being written at the time of a drive failure, there is a risk of data loss.

---

### Post by sazan on 2008-11-06
m working on s/w raid here so that i can raid sata,scsi ,ide disks together as one of my reasons..
 
but mdadm made me think that how it is sayin that it is making raid 5 from 2 disks from nowhere.. 

u didnt answer my question reagardin data read from the disks.. as i had asked you that if 3rd disk fails out of 3 and i need data which is there in 3rd.. wat will happen .. ?? will d raid use system's processing to recover that data and then deliver it to me.. sounds uneasy to me.. 'cause the size of the data can be huge , so performance of giving me d data will reduce ..

---

### Post by Kellemora on 2008-11-06
Hi Sazan

My advice, forget RAID alltogether!  It will be obsolete in another year anyhow as it's reached it's limitations.

Think about this.  If your Raid controller fails, you've lost everything, unless you have an EXACT IDENTICAL Controller.  They are not mix n match, it MUST be EXACT, else you've lost everything.

Unless you truly need multi-user server speeds and can backup a Raid 5, 10 or 50 system, using RAID is like playing with gunpowder, it's going to eventually EXPLODE.

Raid 0 or Raid 1 only give a FALSE sense of security at best.

You would be better off just using a simple mirroring program to store data on two separate hard drives (or more if you have offsite backup).
You don't LOSE any more space than with Raid.  But if one drive fails, there is no problem replacing it.  If a controller fails, no biggie, each drive has it's OWN controller and all your data is one both drives equally.  
In Raid, even though the same data is on both drives, it's ONLY readable by the Controller that wrote it!  If that fails and you don't have a DUPLICATE, then what?

TTUL
Gary

---

### Post by sazan on 2008-11-07
> **Kellemora said:**
> Hi Sazan

My advice, forget RAID alltogether!  It will be obsolete in another year anyhow as it's reached it's limitations.

Think about this.  If your Raid controller fails, you've lost everything, unless you have an EXACT IDENTICAL Controller.  They are not mix n match, it MUST be EXACT, else you've lost everything.

Unless you truly need multi-user server speeds and can backup a Raid 5, 10 or 50 system, using RAID is like playing with gunpowder, it's going to eventually EXPLODE.

Raid 0 or Raid 1 only give a FALSE sense of security at best.

You would be better off just using a simple mirroring program to store data on two separate hard drives (or more if you have offsite backup).
You don't LOSE any more space than with Raid.  But if one drive fails, there is no problem replacing it.  If a controller fails, no biggie, each drive has it's OWN controller and all your data is one both drives equally.  
In Raid, even though the same data is on both drives, it's ONLY readable by the Controller that wrote it!  If that fails and you don't have a DUPLICATE, then what?

TTUL
Gary

appreciate ur advice.. but m working on software Raid now and even though Raid is reachin its limits, tat is a solution for many enterprises stil .. 
but i dont want to make a point here ... just want to clarify some doubts i have ??

---

