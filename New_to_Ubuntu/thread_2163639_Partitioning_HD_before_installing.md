---
title: "Partitioning HD before installing"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by iXod on 2013-07-19
I am just starting the installation process with Ubuntu 12. The installer detected an existing Win Vista Home install. Then I was shown a 2-part diagram with a sliding partition and asked to move it to size the install space for Ubuntu. 

There is waay too little information on that diagram. What volume am I resizing? Where is the existing Win install? I clicked "Advanced" (I think it was called that) which showed me a table of volumes and their size. But how does relate to the install space I was adjusting in the previous graphic? Which of those volumes was Ubuntu installer adjusting and preparing to install? 

I need to know what these volumes are and which Ubuntu installer wants to use as the volume for Ubuntu.

Is there an alternative installer or means of installing Ubuntu? 

A bad first experience -- and Ubuntu isn't even on the computer yet...

Thanks.

---

### Post by bmavbeard on 2013-07-19
Requesting just a little more information...

1) Do you still use the Windows Vista Home.  It sounds like you want to keep that from the above post but I just want to clarify that you do.

2) How big of a hard drive do you have (If windows vista is up and running then you should be able to look that up - reply back if you need help with that)

3) How much space are you hoping to give for ubuntu (25 gb?)

I have did a couple of these before and I will say that since I already had Windows working I partitioned it on Windows first (since I didn't have to do anything other than use the tools windows provided) and then I installed ubuntu.  Would you like directions on how to do this in Vista (that is if it is working)

Lets start with this and then go from there.

By the way, have you backed everything up as a precaution.   Always a good idea.

---

### Post by ajgreeny on 2013-07-19
Yes, I suggest you use the disk management utility in Vista to shrink the main OS partition, not carry out that operation while installing Ubuntu as it is much better to work on Windows with Windows applications.

Now when you are installing Ubuntu it will be best if you choose "Something Else" at the partitioning stage; it will allow you to make partitions as you wish.  I suggest you use all the unallocated space to maker one extended partition and within that make three logical partitions, about 15-20GB for / (root), 2-4GB for swap, and the rest for /home.

If that does not mean much to you at the moment, come back again after shrinking Vista and ask for more details, once you have the space free.

---

### Post by mastablasta on 2013-07-19
> **ajgreeny said:**
> Yes, I suggest you use the disk management utility in Vista to shrink the main OS partition, not carry out that operation while installing Ubuntu as it is much better to work on Windows with Windows applications.


True. it is also good to defragment the "drive"/partition you intend to shring before doing that,.

> 
Now when you are installing Ubuntu it will be best if you choose "Something Else" at the partitioning stage; it will allow you to make partitions as you wish. I suggest you use all the unallocated space to maker one extended partition and within that make three logical partitions, about 15-20GB for / (root), 2-4GB for swap, and the rest for /home.
.

let's not unnecessarily complicate it for new user.

Simply shrink partition in Vista (using windows disk manager) - give it about 25-30 GB (depends how much data oyu plan to have there). leave the empty space as it is - unformated. Then during install simply install to largest unformated disk space. installer will create all the necessary partitions. and reformat it to default file system (ext4).

also check out the Ubuntu manual in my signature - and post back if you have more questions.

---

### Post by Claus7 on 2013-07-19
Hello,

> **iXod said:**
> I am just starting the installation process with Ubuntu 12. The installer detected an existing Win Vista Home install. Then I was shown a 2-part diagram with a sliding partition and asked to move it to size the install space for Ubuntu. 

There is waay too little information on that diagram. What volume am I resizing? Where is the existing Win install? I clicked "Advanced" (I think it was called that) which showed me a table of volumes and their size. But how does relate to the install space I was adjusting in the previous graphic? Which of those volumes was Ubuntu installer adjusting and preparing to install? 

I need to know what these volumes are and which Ubuntu installer wants to use as the volume for Ubuntu.

Is there an alternative installer or means of installing Ubuntu? 

A bad first experience -- and Ubuntu isn't even on the computer yet...

Thanks.

1) NOT bad experience at all! Just imagine manipulating two hdd with 3 OS or more...
Sth that is unfamiliar at first, will become 2nd nature after a while. You wanted to try ubuntu for some reason. Then, have in mind that you are switching to an entire different OS. I was very careful with disk partitioning at first, but after a while it is much easier and still learning.
2) As mentioned above, backup everything in case you make a mistake.
3) And... have in mind that some years ago, all these were taking place from command line.
4) It won't be a bad idea to attach a pic with your partitioning, in order to provide a better insight on what you have and how you want to change your configurations. (mobile phone -> taking pic -> attaching file)

I do not remember if you can take a screenshot while partitioning, yet I do not think so. And sth else: do not be in a hurry. Take your time, before you partition your hdd, because it is not sth you will do every day.
And sth more: it will be a veeery nice idea to separate home partition of ubuntu from the rest. And... give more than 20GB to your root partition (where most programs will lie).

Happy ubuntu-ing,
Regards!

---

### Post by newb85 on 2013-07-19
That first slider you mentioned was: Windows on the left, Ubuntu on the right.

There are scores of people on the forums who strongly urge you to shrink your Windows partition from Windows rather than during installation.  I've never had any success trying to shrink the Windows partition from Windows, and I've never had any problems shrinking it during Ubuntu installation.  (Ubuntu's utilities for managing Windows volumes have come a long way...)

Having a separate /home partition and a SWAP partition are nice ideas, but they're both unnecessary.  If you somehow trash your Ubuntu system, the separate /home partition will make it slightly easier to keep your Documents, Music, etc.  Slightly.  SWAP is only useful if your system is light on RAM (2GB or less) or you plan to use Hibernate, which doesn't work with all hardware and is disabled in Ubuntu by default.

Provided you're not installing Ubuntu to the 4th partition on a MBR hard-drive, you can always add those separate partitions later.

---

