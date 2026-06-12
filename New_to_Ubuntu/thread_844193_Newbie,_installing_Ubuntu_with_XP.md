---
title: "Newbie, installing Ubuntu with XP"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Lycanthropy on 2008-06-29
Hi

I have a computer running XP SP2, and I'd like to try installing Ubuntu without affecting windows at all

I have tried running it from a Live CD, but would like to try running it from hard disk, to see it at full speed

I have two hard disk drives in the computer, each 60 Gb. 

I also have a 500 Gb external hard drive, which is attached to the computer by USB 2.0

If possible I'd like to install Ubuntu on the 2nd 60 Gb hard drive or the external as dual boot XP and Ubuntu without affecting the files on it, so that I could go back to a single boot XP, exactly the same as before, if I decided I wanted to do this.

Is it possible to do this and go back to the computer exactly the same as it was before setting up the dual boot?

Thanks for any help!

---

### Post by hyper_ch on 2008-06-29
If you want to use the whole 60 GB of the second drive, then repartition it and make it unformatted.

If you don't want to use the whol 60 GB, then resize the drive and make an empty, unformatted partition.

Then, during install, you can select "use largest continuous free space"

---

### Post by Lycanthropy on 2008-06-29
> **hyper_ch said:**
> If you want to use the whole 60 GB of the second drive, then repartition it and make it unformatted.

If you don't want to use the whol 60 GB, then resize the drive and make an empty, unformatted partition.

Then, during install, you can select "use largest continuous free space"

And would this affect the other files?

Would I be able to delete ubuntu and return to what I have now?

---

### Post by lukjad on 2008-06-29
> **Lycanthropy said:**
> Hi

I have a computer running XP SP2, and I'd like to try installing Ubuntu without affecting windows at all

I have tried running it from a Live CD, but would like to try running it from hard disk, to see it at full speed

I have two hard disk drives in the computer, each 60 Gb. 

I also have a 500 Gb external hard drive, which is attached to the computer by USB 2.0

If possible I'd like to install Ubuntu on the 2nd 60 Gb hard drive or the external as dual boot XP and Ubuntu without affecting the files on it, so that I could go back to a single boot XP, exactly the same as before, if I decided I wanted to do this.

Is it possible to do this and go back to the computer exactly the same as it was before setting up the dual boot?

Thanks for any help!

Yeeesssss... 
It is possible. You can install it on one 60G drive but be careful, you want to make sure that you don't have any data filed there. As for the USB external hard drive, I would not recommend it for two reasons. One, it will be slow. And, two, because if you forget to turn on your external hard drive before booting up you would then need to reboot the PC and turn on the external hard drive. For the Dual boot on the hard drives here are two links you might find useful.

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

[http://ubuntuforums.org/showthread.php?t=843767](http://ubuntuforums.org/showthread.php?t=843767)

Hope this helps

---

### Post by Canis familiaris on 2008-06-29
> **Lycanthropy said:**
> And would this affect the other files?

Would I be able to delete ubuntu and return to what I have now?

Most easily. But you would not need it;)

---

### Post by lukjad on 2008-06-29
> **Lycanthropy said:**
> And would this affect the other files?

Would I be able to delete ubuntu and return to what I have now?
[http://users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu](http://users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu)
This shows you how to get rid of Ubuntu. Is this what you were looking for?

---

### Post by Lycanthropy on 2008-06-29
> **lukjad007 said:**
> Yeeesssss... 
It is possible. You can install it on one 60G drive but be careful, you want to make sure that you don't have any data filed there. As for the USB external hard drive, I would not recommend it for two reasons. One, it will be slow. And, two, because if you forget to turn on your external hard drive before booting up you would then need to reboot the PC and turn on the external hard drive. For the Dual boot on the hard drives here are two links you might find useful.

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

[http://ubuntuforums.org/showthread.php?t=843767](http://ubuntuforums.org/showthread.php?t=843767)

Hope this helps

Ah okay, thanks.

I'll probably not bother, due to the fact that I was only going to test-run installing it on my parents computer before I bought my own laptop, but seeing as it would involve moving loads of data etc, I think I'll just wait

Thanks for the help everyone!

---

### Post by lukjad on 2008-06-29
> **Lycanthropy said:**
> Ah okay, thanks.

I'll probably not bother, due to the fact that I was only going to test-run installing it on my parents computer before I bought my own laptop, but seeing as it would involve moving loads of data etc, I think I'll just wait

Thanks for the help everyone!

It's always best to do an install AFTER you back up your data and on your PC. If something goes wrong (let's hope not) then will not have a) lost all your files, and b) ruined someone else's computer.

---

### Post by fahadsadah on 2008-06-29
You could always use Wubi and install Ubuntu in Windows.

---

### Post by lukjad on 2008-06-29
> **fahadsadah said:**
> You could always use Wubi and install Ubuntu in Windows.

True. I have been out of the Windows/Microsoft/Gates world so long that I forgot about that great feature. But on rereading the post, I seem to get the impression that he was and wanted to do a full install. Then again, maybe not.

---

### Post by mybunche on 2008-06-29
You can install in on the 500G USB drive, but as the post said above you need to make sure it's on. Anyway, a drive this size can be used as a backup drive. I have been running Ubuntu off a USB hard drive for the last 20 months as it's been perfect, yes probably a bit slower than a internal HD, but fine.

It's best to use your 60G internal drive to put Ubuntu on. You can configure Grub to choose which HD it will boot up from after a certain time or can manually choose which one. When installing be certain that you are installing Ubuntu on the spare drive.

If you need to get rid of Ubuntu, you need to boot up from the Windows drive and restore the MBR (Master Boor Record). Easy.
Boot up computer (from your windows drive) using your Windows install disc.
Choose repair or recover option by pressing R
Enter your Administrator password. Press enter if you have no password.
At  C:>windows>  type fixmbr then enter
Type Y. Type exit

---

### Post by lukjad on 2008-06-29
> **mybunche said:**
> You can install in on the 500G USB drive, but as the post said above you need to make sure it's on. Anyway, a drive this size can be used as a backup drive. I have been running Ubuntu off a USB hard drive for the last 20 months as it's been perfect, yes probably a bit slower than a internal HD, but fine.

It's best to use your 60G internal drive to put Ubuntu on. You can configure Grub to choose which HD it will boot up from after a certain time or can manually choose which one. When installing be certain that you are installing Ubuntu on the spare drive.

If you need to get rid of Ubuntu, you need to boot up from the Windows drive and restore the MBR (Master Boor Record). Easy.
Boot up computer (from your windows drive) using your Windows install disc.
Choose repair or recover option by pressing R
Enter your Administrator password. Press enter if you have no password.
At  C:>windows>  type fixmbr then enter
Type Y. Type exit

I'm pretty sure you could get Ubuntu running off of a USB key if it was large enough. The point is that it would be slower especially for running large and intensive programs such as games. As for the 60Gig hard drive, I wouldn't want him to delete some of his parent's files and get him in trouble. I have no way of knowing his technical experience, short of asking him. So, just to be safe, check if there are any files on that hard drive and THEN install Ubuntu on that drive.

---

