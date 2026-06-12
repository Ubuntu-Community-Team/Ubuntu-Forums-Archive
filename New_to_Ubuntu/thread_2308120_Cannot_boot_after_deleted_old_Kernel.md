---
title: "Cannot boot after deleted old Kernel"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2015-12-31
Hi,

I'm a bit sketchy on the details here and I cannot boot in to confirm anything. Ubuntu 14.04.3 LTS. I have the only copy of important photos on the HD. Also it is encrypted. 

I followed this link:
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
and deleted what I thought were old kernels.

However when I put 
dpkg -l linux-image-\*

into the terminal it listed several kernel versions but as far as I can remember they were listed as
'linux-image-3' (then a space and then more details about the version)

Further down the list there was: 'linux-image-5' so I presumed that l was safe to enter:
sudo apt-get autoremove linux-image-3

Is there anything that I can do? Thanks in advance

---

### Post by leunam12 on 2015-12-31
Restore your system partition from your most recent backup.

---

### Post by grahammechanical on 2015-12-31
Have you tried using a live session to access the hard disk and backup those important files?

You need to install a kernel. I am not sure how to do that. Re-installing may be the easy way if your data is safe. Do you have your data on a separate partition? Or a separate home partition or is it all in the /home folder in the Ubuntu partition. I guess that encryption will complicate matters. I have no experience with encryption. I cannot advise.

I am guessing that if you try to install a kernel, it would have to be done from a live session as recovery mode will not work as it needs a Linux kernel.

My advice is to concentrate on backing up that important data before trying to correct the original problem. You may make things worse and be left in a situation where re-installing becomes the uncomplicated solution.

Regards.

---

### Post by bikefreakvinnie on 2015-12-31
Thanks Leunam12,

Does ubuntu do this automatically and if so how would I access this?

I do a full new installation rather than upgrade between versions.... 

Many thanks

---

### Post by bikefreakvinnie on 2015-12-31
Hi  grahammechanical,

Its all on the one partition /home. I presumed that I could not access the HD at all when the home folder was encrypted but I will try a live cd. If I could just get the files off it I would do a full new installation then...

Thanks again I will try a live cd..

---

### Post by leunam12 on 2015-12-31
If you didn't backup manually then there is no backup. But all your data should be there. You have to find a way to transfer it over to another disk.

---

### Post by bikefreakvinnie on 2015-12-31
Brilliant!

I was able to access and unencrypt the files from a live cd. I almost have access to everything however some folders are not accessible - is there a way I can log with more permssions in to have access to these?

---

### Post by bikefreakvinnie on 2015-12-31
When I try to move a particular folder it says: 'The folder "Name" cannot be handled because you do not have permission to read it.'

but I do have access to another similar folder

---

### Post by monkeybrain20122 on 2015-12-31
For your future reference. Don't run commands that you don't understand. I know, some people think it is cool to give instructions in a bunch of incomprehensible gibberish and tell you to just cut and paste. But I try to explain them a little bit if I am giving them and ask for explanations or google them up if I am given them. The easiest and safest thing to do (which may not seem as cool to cli people) is to find these packages in synaptic and delete them. Synaptic is an excellent gui-package manager. You can install it with 
```
sudo apt-get isntall synaptic
``` 
or install it via the software centre.

Once installed you just open it, search for "linux" from the "installed" section to find all the Linux images and the corresponding headers with a green box next to each. Then click to uninstall all of them (images and headers) except the ones that you want to keep (say the two latest ones), and click apply. Then you are done.

P.S just to drive home the point some guy on another thread just has his whole system blown away by trying to uninstall wine with
```
sudo apt-get remove wine*
``` The "*" happens to be a regular expression in apt, not a wild card like it is used in other context. He could have avoided a painful reinstall had he looked it up first or just used synaptic (or ran it without the *, and use autoremove instead)

---

### Post by brian-mccumber on 2015-12-31
For future reference there is a tool called Ubuntu Tweak that has a Janitor tab that will help you remove old packages and kernels without the worry of deleting the current kernel you are using. You can download the .deb here - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

I always keep a couple old kernels just in case but tweak Janitor will not flag your current kernel for deletion. If you are unsure which kernel you are using you can run ```
uname -r
``` and it will show you your current kernel version.

---

### Post by bikefreakvinnie on 2015-12-31
Totally agree monkeybrain20122 - I just get by with basic command line, usually don't risk stuff like that unless I've moved important files off first.... Recon its my first almost data loss since I started using ubuntu in 2008...

Do you know is there a GUI way I can access the remaining folders or perhaps a fairly simple command line way...

Thanks a mil

---

### Post by bikefreakvinnie on 2015-12-31
Thanks brian-mccumber,

Thats a lot better i'll do a full installation soon - I seem to reinstall a couple of times yearly even if I don't want to!... I'm disappointed /boot wasn't bigger in the first place.... I used to set the partition sizes manually before this installation..

---

### Post by brian-mccumber on 2015-12-31
When you reinstall use the other option and don't format your /home drive and your data will still be there providing you created a separate home drive when you last installed Ubuntu. Just tell the installer to use your /home drive for /home and then DO NOT check the format drive option for /home. Some programs you had installed will still have data on your home so you would just have to reinstall the apps and they will use the existing user data saved in your home drive. When I installed Ubuntu on my Mom's computer, when she broke the install all I had to do was reinstall to the /root drive and all her data was still in the /home drive when it first booted.

---

### Post by monkeybrain20122 on 2015-12-31
> **bikefreakvinnie said:**
> Thanks brian-mccumber,

Thats a lot better i'll do a full installation soon - I seem to reinstall a couple of times yearly even if I don't want to!... I'm disappointed /boot wasn't bigger in the first place.... I used to set the partition sizes manually before this installation..

You don't need a /boot partition unless you are doing whole disk encryption or something. Just make a root (/) and a home (/home) partition would be sufficient.

  Since you already have a separate /home you don't really need to access it with gui or otherwise. First use gparted in the live usb to merge the /boot and / partitions. Then when install (choose "something else") make the new / to be the old combined partition and use the old /home as the new /home and don't format it. All your data should be safe and it takes you about 15 minutes to reinstall.

---

### Post by grahammechanical on 2015-12-31
As regards the folders that you cannot access, are they system folders? Is it necessary to access them to back up your data?

I am glad that you can decrypt /home to access those files. Not having any experience with encryption I did not know if it was possible from a live session. I have never tried re-installing with an existing encrypted /home partition. So, I cannot advise on what to expect.

It seems I have found an area of Ubuntu that I need to experiment with to improve my education. :)

Regards.

---

