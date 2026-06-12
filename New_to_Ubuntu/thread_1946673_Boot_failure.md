---
title: "Boot failure"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by rem1100 on 2012-03-25
Have a dual boot Ubuntu 11.10 and Windows XP machine. When I type in my password for Ubuntu the screen goes dark then back to login. Started Ubuntu in recovery mode with no difference. XP will boot up but is painfully slow. At one point XP went to chkdsk, fixed errors, then worked normally. Tried Ubuntu again, could not get to desktop, tried XP again and it was bact to being very slow. XP has been slow for a couple of weeks but Ubuntu has worked fine until now. I suspect I have a hard drive issue but do not know how to repair. Could this issuse be caued by the fact that I have this machine set as a dual boot?
Thanks in advance for any help,
Jeff

---

### Post by waynefoutz on 2012-03-25
Dual booting  doesn't cause this at all. It could be a bad hard drive, It could be two separate issues. First thing I would do is put an Ubuntu live cd in, run the "disk utility" from the live environment. It will let you read the SMART data stored on your drive and give you an idea how healthy the drive is. Then I would probably  back up my data and reinstall both operating systems.

---

### Post by garvinrick4 on 2012-03-25
If you want to you can use a liveCD and run e2fsck on your / and see if it needs fixing up.
Put in live CD and open terminal:
```
sudo fdisk -l 
```(lower case L)
find your linux install lets say sda5 for this use your own:
```
sudo e2fsck /dev/sda5
```If needs fixing just answer with y.

Previous post to check if disk has errors is wise.

---

### Post by rem1100 on 2012-04-01
Ran SMART throught live disk, found errors. Tried the 2 commands that gavinrick4 suggested, both ran successfully but made no difference as far as being able to get operating system to run. Was able to get XP working properly through chkdsk/r. There were several disk errors in XP that were eliminated. This has so far seemed to elimate a persistant Netgear error that started to appear every time XP was booted.  I have looked but cannot find the equivalnt of chkdsk in Ubuntu, if it exists would appreciate instructions on how to get there. Last resort would be to reinstall Ubuntu, I do not know hos to get at the data stored on it when the operating system will not run. Would rather not do that if I can avoid it. For what it is worth the hard drive was replaced around 6 months ago with a refurbished Western Digital unit. It really should not have failed this soon but I imagine it is possible. Up to this point it has worked as it is supposed to. Thanks again for any help.
Jeff

---

### Post by garvinrick4 on 2012-04-01
The second command in my post was the equivalent of chkdsk.
```
sudo e2fsck /dev/sda5
```   (red number use your own linux install sda#)

 "fsck" has to be run from a unmounted partition.

---

### Post by garvinrick4 on 2012-04-01
What actually happened to make Ubuntu stop booting process to Desktop? Was there a incident of some sort you could tell us?

---

### Post by rem1100 on 2012-04-02
I am pretty sure I did run e2fsck from an un mounted partition. Listed are sda1, sda2, sda5 , sda6. Sda1 I believe is the Windows partition, when I ran e2fsck on sda2 message came that there was a short read and could be zero length partition, sda5 is listed as Linux and only fault that came up was "Superblock last mount time is in future" less than a dayprobaly due to hardware clock being incorrectly set. Sda6 comes up as mouunted and message comes up that serious damage will be done if e2fsck is run. This is all done from live disk. Running SMART data reveals 786 bad sectors and fails self test. There is one warning in the Attributes, # 197 Pending Sector Count. 
To answer you last question, I cannot tell you a specific event that happened  before Ubuntu failed to go to desktop when password is entered. All I noticed is that a couple weeks prior to this XP got terribly slow and every time XP was loaded recieved an error message reguarding Netgear. Even while this was going on Ubuntu was working fine.  My kids also use this computer, if something happened while they were using nobody is admitting to it.
Thanks

---

### Post by Mark Phelps on 2012-04-02
> I have looked but cannot find the equivalnt of chkdsk in Ubuntu, if it exists would appreciate instructions on how to get there. 

Unfortunately, there is no such equivalent.  There is ntfsfix, but it can only fix trivial NTFS errors and, if anything serious happens, you have to use Windows CHKDSK to do the repairs.

Really does look like your replacement drive is failing -- especially if you're experiencing symptoms of filesystem corruptions in both Windows and Ubuntu.

I had a WD 2TB (brand new) fail me within 3 months of use.  Unfortunately, I could not locate the sales receipt, so I could net get it exchanged.  So, I know that some WDs can fail after only a few months of use.

---

### Post by rem1100 on 2012-04-02
How do I go about repairing the Ubuntu partition of the hard drive with chkdsk? 
As far as the drive failing I fear you are right, did chkdsk on the computer I use for work (about 1 yr old) there were no errors on it. Have run chkdsk multiple times on this machine and it finds at least one error every time. If I do have replace the drive any suggestions on what to get? I did some poking around prior to purchasing this drive. Found that every drive manufactuer has someone that has had bad luck with their drives. 
Thanks, 
Jeff

---

