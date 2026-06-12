---
title: "Not Enough Disk Space - How Do I Shrink The Installation"
date: 2023-11-12
forum: New to Ubuntu
---

### Post by fiscoking on 2023-11-12
Hello,

I'm trying to install Ubuntu_22.04.03 on a hard drive from an ISO.

Part way through the installation I receive the error message:

You need at least 15.7GB disk space to install Ubuntu.

I only have 5GB left on a small SSD. 

There doesn't appear to be any option to disable any unnecessary stuff. Does Ubuntu really need 15.7GB just for the OS and supporting utilities?

Final question; how do I install Ubuntu on 5GB of disk space?

Thanks.

---

### Post by MAFoElffen on 2023-11-12
What else is on it?

Form a terminal session on the installer LiveUSB
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```

---

### Post by Impavidus on 2023-11-12
You could start from the server iso and only add the software you really need. I think you can get it down to about 8GB, but not 5GB. My root partition has 16GB including a few large and non-vital applications, but no snaps. My home directory is on a different partition. Another approach is to move some of the less essential stuff to a separate partition. Whether that's a practical solution depends on the details. Are there any other drives in that computer?

---

### Post by yancek on 2023-11-12
The Ubuntu site from which you downloaded the iso file tells you how much space you can expect to need for Ubuntu and it is a lot more than 5GB.  You would have to go back a decade or more to have an OS which could install on a 5GB partition.  

You could start with the server iso if you can work with it from a terminal and no GUI.
You could run Ubuntu on a 'live' usb until you are familiar with it.  Posting more information as requested above as to what else is on the drive and are there any other drives available might help.  You might be able to shrink or resize some other partition to free up more space.  Getting a full install of any current mainstream OS on 5GB is very unrealistic.  I remember over a decade ago with windows 7 pre-installed and the base system partition taking up over 17GB the first time I booted it.

---

### Post by ian-weisser on 2023-11-12
> **fiscoking said:**
> 
There doesn't appear to be any option to disable any unnecessary stuff. 


What is "necessary" is often a matter of opinion.

There is a "minimal" option in most installers. Perhaps you chose an install image without that option, or didn't see it in your installer. However, even a minimal install may require much more than 5GB. Depends what you add to make it useful.

---

### Post by MAFoElffen on 2023-11-12
You still have not booted from the LiveUSB, opened a terminal session, done the commands I posted in Post #2, for you to post the output of that in a Post, posted within CODE Tags....

So that anyone can see what you do have, and what might be able to be resized...

You asked "how do I shrink..." But have done nothing to help people help you with that. Rather, we are working in the dark here. We have no idea what to suggest, because we cannot read your mind, nor see through your eyes.

We could suggest a lot of things, but at the moment you are having us guess.

Please help others to help you. Show us the data.

---

### Post by fiscoking on 2023-11-13
Hi, I've gone back to ubuntu version 20, which had an installer that allowed for a minimum install. Not sure why this has been removed in the latest version. Ver20 is also smaller. I'll see how I get on with that.

---

