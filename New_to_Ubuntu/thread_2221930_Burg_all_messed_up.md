---
title: "Burg all messed up"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by gareth8 on 2014-05-04
Hello I am a new user to ubuntu as of yesterday but still a beginer in Linux but I pick up fast I have been tinkering round since last night had everything pretty much setup perfect burg bootloader included so I decided to see what a theme would look like with my own picture with Grub customizer and I restart with no success so as I try to switch to a previous theme and it now gives me the message (This theme doesn't contain a theme.txt. Please look for the config file and rename it to "theme.txt"!) I want to revert back to my themes I have been trying diffferent ways to fix tis lots of research online but have not been able to come up with a fix any help would be much appreciated Thankyou.

---

### Post by gareth8 on 2014-05-04
all that was changed was to theme custom settings and back again

---

### Post by oldfred on 2014-05-04
Not many of us use burg with adds its scripts.
And grub customizer creates its own scripts also.
Not then sure how they work together or not?

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by gareth8 on 2014-05-04
It did work perfect till I changed the background a lot of bother for a small change what would be my best way then if no one can help with to get the bootloader back to some type of default? Which was the Kali-linux bootloader Thanks

---

### Post by Bashing-om on 2014-05-04
gareth8; Yikes !

What operating system(S) do you have installed ?

As we are the more familiar and comfortable with the boot manager 'grub' would you consider installing 'grub' ?

See what then results .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by gareth8 on 2014-05-04
I am running Ubuntu and Kali Linux Thanks

---

### Post by gareth8 on 2014-05-04
Yes that is what I want now burg seems to be more bother than it's worth I just want to get rid of all existence of burg.

---

### Post by gareth8 on 2014-05-04
Think its time to bite the bullet and format and start again can someone just point me into the direction of changing my bootloader to something a little more pleasing to the eye thanks.

---

### Post by Bashing-om on 2014-05-04
gareth8; OK !

Let's install grub such that ubuntu becomes your primary operating system.

To know where to install the boot code, show what the partitioning is, and tell which partition is ubuntu installed onto:

From the liveDVD of ubuntu:
```

sudo fdisk -lu ## for the legacy partitioning scheme
sudo parted -l
##else for the new GPT partitioning:
sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb ##if additional disk other than the one apply.

```

Once known, can be done.

[INDENT][INDENT][INDENT]piece of cake
[/INDENT][/INDENT][/INDENT]

---

### Post by gareth8 on 2014-05-04
I'm pretty new to all of this so please excuse me wouldn't I get the same result by a fresh install.

---

### Post by Bashing-om on 2014-05-04
gareth8; Hey,

Nothing wrong with being new, None of us were born knowing what we know.

In this instance, all we are doing is making sure that the partitioning supports installing ubuntu's boot code to the (M)aster (B)oot (R)record sector of the hard drive, and not elsewhere.

And then from that liveDVD, will do the actual install of grub.

And Yes -- if you were to (RE-)install, the same thing we are going to do would be done by the installer.

[INDENT][INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT][/INDENT]

---

