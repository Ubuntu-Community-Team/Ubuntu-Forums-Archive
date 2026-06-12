---
title: "Partitioning gone really wrong"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by n00bi on 2012-04-21
Ok so, following my wonderful endeavors trying to increase the brightness of the net book's screen which I have failed at miserably, I couldn't un install ubuntu from the dual boot.

Trying to be a smart ***, i booted through XP, deleted the other partition using mmc and disk management, rebooted and the damn thing gave me a grub error not that i know what the hell that is, but i am betting that it was set to boot using Linux as default so i can pick between XP and Ubuntu.

So I used the pen drive to delete everything and now i have have formatted the entire hard drive and reinstalled Linux on my net book, the sad part, it doesn't have CD drive.

Now i am stuck and i don't know how to return it back to windows if i wanted.

Any help on how to turn it back to what it was. I am using an Acer Aspire One D250

---

### Post by Bucky Ball on 2012-04-21
Best to install Windows first. If you have wiped the entire hard drive, as you say, then Win will be gone. 

I suggest install Windows then install Ubuntu.

---

### Post by Stanwilliamsmusic on 2012-04-21
> **n00bi said:**
> Ok so, following my wonderful endeavors trying to increase the brightness of the net book's screen which I have failed at miserably, I couldn't un install ubuntu from the dual boot.

Trying to be a smart ***, i booted through XP, deleted the other partition using mmc and disk management, rebooted and the damn thing gave me a grub error not that i know what the hell that is, but i am betting that it was set to boot using Linux as default so i can pick between XP and Ubuntu.

So I used the pen drive to delete everything and now i have have formatted the entire hard drive and reinstalled Linux on my net book, the sad part, it doesn't have CD drive.

Now i am stuck and i don't know how to return it back to windows if i wanted.

Any help on how to turn it back to what it was. I am using an Acer Aspire One D250


IF you formatted the Entire hard drive, including the partition where windows  was,  I think you will need to use  the Windows disk to re-install Windows, as far as I know,  If so,  I would Install Windows First, Then I would reinstall Ubuntu in that order.

 To see  If Windows is still on your hard drive, and  maybe fix your problem, you can try   **boot-repair** , just follow the instructions **Here:**

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)


It should  repair your  bootloader  for you.
And If  Windows is still on your machine, then it should find it for you,  and also  Ubuntu  and  then give you a choice at boot time  to either boot into Windows or Ubuntu .
 I hope this helps, best of luck.

---

### Post by houseworkshy on 2012-04-21
Machine specific I don't know.  Grub is the bootloader.  However the general rule is put windows on first, because windows can't see linux but linux can see windows.  Sorry about that but the easy none techy way will be the long way round.  Bung windows back on, use it to partition the drive into two and only install windows to one of them.  Then put Ubuntu in and install to the empty partition, linux will sort out the bootloader and give you the choice at boot up.  
Another way which is a bit more tecky but quicker is to use the gparted tool in Ubuntu which can shrink the ubuntu partition making room for windows, make sure the new empty partition is bootable, then install windows to the empty bit, then update the grub loader.  ( there are many many threads explaining that just search for "update grub".)   Worth clarifying what you mean by "no cd drive" as in it has been physically removed, broken, or just doesn't work anymore.  That is the first thing to sort out if your windows is on a disk.   Hang fire for a while though as you will probably get a far better answer than that.  Ah I took so long writing that you already have had a better reply, good.

---

### Post by n00bi on 2012-04-21
Thanks for all the replies, well first no cd drive as this is a netbook it came preinstalled with xp so i will have to find a way to boot through usb to reinstall windows.

Now i think i know what i have to do.

---

### Post by n00bi on 2012-04-21
Thanks for all the replies, also i wanted to mention that it's a netbook so a win disk is useless as i don't have a physical cd rom drive. The netbook came with preinstalled XP i will have to manage around that.

---

### Post by Bartender on 2012-04-21
External optical drives aren't all that expensive.  Depends on how badly you want to get it fixed.  Contact Acer and see if they'll sell you a recovery disc.  
I know that Acer won't sell XP Pro discs anymore.  That's what I read on their website anyway, something about Microsoft not wanting them to offer XP discs as of some date.  Since the netbooks didn't come with XP Pro maybe you could get a disc.
Spilled milk now, but it sure woulda been easier if you'd made recovery discs on your own.

The GRUB error you describe is exactly what should happen when you wipe out the Ubuntu partitions, then don't repair the Windows MBR.  If you'd stopped right there and asked about it you coulda gotten directions for fixing the MBR.

---

### Post by Stanwilliamsmusic on 2012-04-21
> **n00bi said:**
> Thanks for all the replies, also i wanted to mention that it's a netbook so a win disk is useless as i don't have a physical cd rom drive. The netbook came with preinstalled XP I will have to manage around that.
Sorry that I didn't really see the part about  not having a CD drive, I saw it but thought you meant it didn't show up in your devices..
I have never had an Acer but  HP and Compaqs had  a partition on the drive just for reinstalling Windows.
If I were you i think I would try the boot-repair and see if it  finds anything, I have had it find the resotre partition on  HP machines with OEM Windows installs, (no disk)   and list it among the boot options,  so if it is still on your hard drive it may find it for you.

I found a couple of articles about it, by searching Google.[http://www.google.com/#hl=en&gs_nf=1&cp=54&gs_id=a&xhr=t&q=how+to+install+windows+xp+on+a+laptop+without+cd+drive&pf=p&output=search&sclient=psy-ab&oq=how+to+install+windows+xp+on+a+laptop+without+cd+drive&aq=0&aqi=g1&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=6da3e81fc300790e](http://www.google.com/#hl=en&gs_nf=1&cp=54&gs_id=a&xhr=t&q=how+to+install+windows+xp+on+a+laptop+without+cd+drive&pf=p&output=search&sclient=psy-ab&oq=how+to+install+windows+xp+on+a+laptop+without+cd+drive&aq=0&aqi=g1&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=6da3e81fc300790e)




By the way [I]houseworkshy gave a great answer.

[/I]

---

### Post by Stanwilliamsmusic on 2012-04-21
Great answer! I hadn't even thought about  an external CD drive,and it was so simple :)

---

### Post by houseworkshy on 2012-04-21
You have another choice.  Leave the whole drive to Ubuntu but install wine, it's in the software centre.  It's a windows emulator which can run windows programs.  A bit patchy on versions of windows which are still supported ( meaning some things will work and some won't ).  On any of the unsupported windows it runs practically anything.  Should you put it in it is a good idea to remove it's access to root ( / ) as it can also run malware. It sets up a virtual dynamically expanding drive in your home directory in a folder called ".wine"  ( the . means that it's hidden so you will have to choose show hidden files to see it.  If you have removed it's access to root then you'll need to bung any .exes on that drive to install them, but that's no big deal.  That way you should be able to run most of you old XP and earlier windows applications and games.  If you want you could also put on DosBox which emulates a dos machine, and that runs everything I've tried.

---

### Post by Bartender on 2012-04-21
Stan, the OP states in the first post that he used the pendrive to wipe the drive completely.  I assume he had the Ubuntu installer on a pendrive and used gparted to wipe the drive.  It's unlikely that the recovery partition survived...

Not impossible, but unlikely.  I wasn't looking over his shoulder when he hit the button.  If you ask gparted to wipe a drive from front to back, that's what it'll do.  You would have to take extra steps to NOT wipe the recovery partition, so I'm going with the more likely outcome unless the OP states differently.

EDIT: I googled Acer Aspire D520 and Acer Europe came up.  The OP's location isn't shown in his sig so I don't know if the D520 is European?  Here's the U.S. Acer recovery disc [website]("http://us-store.acer.com/rcd/").  Notice they won't sell XP Pro anymore as per MS.  But the netbooks didn't come with XP Pro so there's still a chance...

---

### Post by critin on 2012-04-21
If you can get an iso for your version of Windows by contacting the manufacturer, you can create a bootable usb  for Windows by using Rufus .  I tried it with my XP to install into a virtual box and it worked wonderfully.

[http://rufus.akeo.ie]("http://rufus.akeo.ie/")

---

### Post by n00bi on 2012-04-24
Hi All

So I think i shouldn't have jumped to quickly formatting the ENTIRE drive "n00b"

Well I think it's a good opportunity for me to force myself to use linux, because i believe i have to be FORCED to shift.  

So I just ordered a new keyboard and i will wait till it ships in and start logging more into terminal and use the commands that i have been learning.

Thanks for all the support everyone, you guys are great.

:guitar:

---

### Post by audiomick on 2012-04-24
> **n00bi said:**
> 
Well I think it's a good opportunity for me to force myself to use linux, ...

That's the spirit. :popcorn:

---

### Post by Bucky Ball on 2012-04-24
Please mark thread as 'Solved'. ;)

---

