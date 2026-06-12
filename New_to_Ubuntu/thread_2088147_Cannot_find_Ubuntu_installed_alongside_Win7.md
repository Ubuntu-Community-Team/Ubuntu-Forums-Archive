---
title: "Cannot find Ubuntu installed alongside Win7"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by brainzz on 2012-11-25
Hello,
With help from the good people of this forum, I have **finally managed to install Ubuntu 12.10.** (i think)
This was my thread: **[http://ubuntuforums.org/showthread.php?t=2085292]("http://ubuntuforums.org/showthread.php?t=2085292")**

After installation, i did not see any menu that shows the option of booting into Ubuntu / Win7 (something called GRUB right?)

Everytime, my **machine directly boots into Win7**.
So, **where did Ubuntu go?**

I can see some new partitions created (see below)
-----

-----
**One other thing**,
I tried to install Ubuntu again (since i thought that it did not get installed) and saw that the **installer gives me an option to re-install Ubuntu.**

So i guess _that is proof that Ubuntu did really get installed?_

So, my question: **Where did Ubuntu go? How do i get it to show itself during boot?**

Kindly do help,
Thanks
~aki

---

### Post by newb85 on 2012-11-25
When you installed, where did you tell the installer to put the Boot Loader?

---

### Post by brainzz on 2012-11-25
I don't even know whether it asked for such a thing.

Could you tell me how to find out where the bootloader is installed?

**Extra Info:**
Oh, I used a pen drive to install Ubuntu 12.10.

I used the _USB boot disk creating software_ for Ubuntu (Linux) to extract the full ISO of 12.10 into the pen drive.

Is that where the bootloader has gone? How do i check it? How do i access it?

What if the bootloader is not in the pen drive?

**More Extra Info:**
The boot disk creating software asked me to give a size for the persistence file, and i gave the size close to somewhere around 4 GB.

Thanks,
~aki

---

### Post by Old_Grey_Wolf on 2012-11-25
What happens if you try booting from the USB pen drive?

Do you get the try Ubuntu or install Ubuntu when it starts?

Do you get options for booting Windows 7 and Ubuntu?

Edit: with a little more information, someone may be able to help you. If you did install Grub (bootloader) to the USB pen drive, it will not be hard to fix.

---

### Post by jumperkid400 on 2012-11-25
depending on how you did it you might have installed the os on the thumb drive.  i bet that if you boot with the thumb drive in it will work

---

### Post by NikTh on 2012-11-25
Hi , 
please use this tool => [boot - repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) to provide more info and maybe resolve your problem. 

Boot from Live-USB/DVD of Ubuntu , select "Try Ubuntu" and then follow the instructions on link to install and run boot-repair software. 
Click on [Recommended Repair] and do not forget to post here the link with info (if your problem not resolved). 

Thanks

---

### Post by oldfred on 2012-11-25
Moved Steavio99 to this as his issue is UEFI and totally different.

[http://ubuntuforums.org/showthread.php?t=2088205](http://ubuntuforums.org/showthread.php?t=2088205)

---

### Post by brainzz on 2012-11-26
@Old_Grey_Wolf:
Yes, I got "Try / Install Ubuntu" when i inserted my pen drive again. Does that tell you something? Kindly do let me know.

@NikTh:
I will put in my pen drive and see if i can connect to the internet after clicking "Try Ubuntu". I will install the software mentioned by you and paste the results here again.

@Everyone:
Thanks guys.
I will paste the results of 'boot - repair' as mentioned by 'NikTh'.

~aki

---

### Post by Pilot6 on 2012-11-26
This happens from time to time. Grub does not install automatically for some reason. This can be easily fixed.

1. Boot from LiveCD.
2. Find partititon, where linux root (/) is installed, i.g. /dev/sda3.
3. Run commands
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by Old_Grey_Wolf on 2012-11-26
> **brainzz said:**
> @Old_Grey_Wolf:
Yes, I got "Try / Install Ubuntu" when i inserted my pen drive again. Does that tell you something? Kindly do let me know.


That tells me you didn't install grub on the pen drive.

As NikTh said, use boot-repair. Boot-repair doesn't always work; so, be sure to write down the URL it gives you when it finishes.

---

