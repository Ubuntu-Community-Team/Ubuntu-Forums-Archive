---
title: "Why separate /home?  I regress I guess"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by anewguy on 2011-10-26
For some of the newer users out there who may wonder why so many of us recommend you install ubuntu with a minimum of 3 partitions - swap, / and /home, let me give you a good reason:

I recently made the step up to 11.10.  Now mind you, there is nothing wrong with that release if you want it - I would recommend it.  However, through some things I did long after the install, I ended up making my ubuntu unusable.  My only choice was to reinstall.  So I made the decision to regress back to 10.10 for now and play with 11.10 in a vm until I can make sure I don't hose it up again being stupid.

At any rate, someday you may find yourself in a similar position, or even more, hopefully, doing a clean install with each new release.  Well, with my /home in a separate partition, all of my files, settings, virtual machines, photos, music, etc., etc., etc., were all preserved and just waiting for me after I reinstalled the OS.

I know this is simple.  I know this is something we try teach here all the time.  I just thought maybe a simple example might help the newer or want to be user decide on how to partition.

Dave ;)

---

### Post by waynefoutz on 2011-10-26
I never mess with it, I probably should. But I usually have 3-4 OSes installed on my machine at a given time. I usually keep all my data on an external.

---

### Post by rivenathos on 2011-10-26
While a /home is a good idea, I have found that a /data partition is even better.

---

### Post by anewguy on 2011-10-26
> waynefoutz 	
Re: Why separate /home? I regress I guess
I never mess with it, I probably should. But I usually have 3-4 OSes installed on my machine at a given time. I usually keep all my data on an external.

Yep - if the new user has an external drive this always makes a good option as long as they know how to mount as they move forward in releases.


> rivenathos 	
Re: Why separate /home? I regress I guess
While a /home is a good idea, I have found that a /data partition is even better. 

Another good idea, however if the new user is not familiar with placing data in another place, using /home at least keeps the default location of their storage.

---

### Post by collisionystm on 2011-10-26
Make sure you make your root / partition big enough. 

I hate when it runs out of space!

This reminds me of something I absolutely hate that I see in Windows Servers time to time. The C: Drive separated from everything else with different partitions. 

Doing this in Windows is absolutely ridiculous. It gives no benefit what so ever. All Windows programs point be default to the C: drive. All Windows programs write to the registry located on C:. Windows updates go to C:. If you re-install Windows a Windows XP Install disc does not let you choose what drive to assign the letter C: to. 

Blah... anyways. Back to the topic!

---

### Post by alphacrucis2 on 2011-10-26
> **collisionystm said:**
> Make sure you make your root / partition big enough. 

I hate when it runs out of space!

This reminds me of something I absolutely hate that I see in Windows Servers time to time. The C: Drive separated from everything else with different partitions. 

Doing this in Windows is absolutely ridiculous. It gives no benefit what so ever. All Windows programs point be default to the C: drive. All Windows programs write to the registry located on C:. Windows updates go to C:. If you re-install Windows a Windows XP Install disc does not let you choose what drive to assign the letter C: to. 

Blah... anyways. Back to the topic!

It is quite common on windows servers to have c: on a mirrored pair of internal disks but all the databases etc on d:.... etc running off an external SAN.

---

### Post by collisionystm on 2011-10-26
> **alphacrucis2 said:**
> It is quite common on windows servers to have c: on a mirrored pair of internal disks but all the databases etc on d:.... etc running off an external SAN.

Anyone that has ever built and had to fix Windows Servers know's that it makes absolutely no difference to have your C: drive separate. I can only see having a separate hard drive installed to act as the paging file.

---

### Post by alphacrucis2 on 2011-10-26
> **collisionystm said:**
> Anyone that has ever built and had to fix Windows Servers know's that it makes absolutely no difference to have your C: drive separate. I can only see having a separate hard drive installed to act as the paging file.


The point is that you may not be able to boot off a SAN. So you need your OS on the internal server drives.

---

### Post by collisionystm on 2011-10-26
> **alphacrucis2 said:**
> The point is that you may not be able to boot off a SAN. So you need your OS on the internal server drives.

Well with a SAN that makes sense. 

I went to a technical class for a DVR system and a company called NICE.

They built their servers with a 8gb C: Drive, and 3 other partitions all on the same physical disks. 

This caused so many problems.

---

### Post by vasa1 on 2011-10-26
Maybe this thread should be moved out of Absolute Beginners?

---

### Post by anewguy on 2011-10-26
Maybe people should quit talking about Windows servers and concentrate on the object of this thread - that absolute beginner.  I'm going to ask a moderator to close the thread since you've taken it so far off topic.

PLEASE DO NOT POST ANY MORE REPLIES IN THIS THREAD and consider it rather useless now.

---

### Post by oldfred on 2011-10-26
I often suggest the separate /home for new users just to start the process of not just / (root) & swap. But for more advanced users /data makes even more sense but mounting and redirecting is not for a brand new user.

Even with my XP I redirected much of my data to d:. But that was difficult and I had to write a .bat file to copy some data that programs would only write to its own directory and that was not always consistent. Again not for beginners but for more advanced uses a way to separate data & system.

I prefer separating data & systems as system is a tiny bit more efficent especially with very large drives. It does not have to scan a 1TB / partition for system files as we have seen some default installs have to do.

Since I have added my 2 cents do you want this closed. I will not be back until tomorrow.

---

### Post by anewguy on 2011-10-26
Thanks oldfred - very definitely back on the track I was hoping for, but I'm afraid the posts about the Windows servers will turn any beginner/want to be away from the thread.  When you have time, I'd appreciate if you could close it.

Thanks, and hope you're doing great!

Dave ;)

---

### Post by PaulInBHC on 2011-10-27
I have only had to reinstall Windows XP twice in almost ten years. Both times I was saved by having a D: partition to copy My Documents and other data in to.

I think a separate /home is a great idea that should be automatic in the install, not an additional step for newbies to figure out.

---

### Post by sffvba[e0rt on 2011-10-27
*Thread **closed** as per OP's request.*


404

---

