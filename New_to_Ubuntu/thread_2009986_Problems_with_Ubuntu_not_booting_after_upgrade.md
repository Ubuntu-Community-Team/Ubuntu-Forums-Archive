---
title: "Problems with Ubuntu not booting after upgrade"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Maggie229 on 2012-06-25
Hi

I am new to this so please be patient and understanding. I have a duel OS system. On Saturday I did an upgrade from Ubuntu 11 to Ubunto 12.04 (not too sure of the version numbers but the point is I did an upgrade). I think there may have been a problem because my computer after the upgrade was giving even more trouble than normal ( sticking and constantly going dark and then getting bright). I decided to restart my  machine and when I did after choosing to load Ubuntu my screen goes to a purple screen and stays there.So after doing some research I decided to load it in a previous version. The same problem persisted. Then I tried recovery mode and yet the same problem persisted. I did however, tried typing in a command when I was in the grub menu and I was given the error message "Kernel not loaded". So I am assuming this is the source of my problem. How do I fix it? I am using an HP laptop which is a 32bit processsor.

Thanks

---

### Post by oldfred on 2012-06-26
Welcome to the forums.

Not sure with changes you have done where you are at. Can you boot to a grub menu. You may have to hold shift key from BIOS until grub menu appears.

If you cannot get to grub menu download a Ubuntu liveCD or USB of 12.04. Repairs generally need to be same version of grub now with grub 1.99.

You can then download into the liveCD or from this site download a repairCD. Post the link to Boot-Info report.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.


If you do get to grub menu above report may not help much. What video card/chip do you have. Often issues are video related, but could be other issues that require a different boot parameter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mapes12 on 2012-06-26
Oldfred is well respected on this Forum and his advise is solid.

You don't say what you are dual booting with. I'm guessing it's windoze. The first thing to do is to backup all the stuff you want to keep in case everything goes wrong. If you don't have your original windoze installation media then image it using something like Macrium. An Ubu live CD should let you access your ubu partition and export your stuff to external media from the CD session.

Others on this Forum have reported problems by going down the upgrade route. I personally go for a clean install. The reason for this in my opinion is that there are loads of hidden folders (Ctrl + h to see them) in your /home folder and I'm not convinced that some critical ones get updated via the upgrade route. But a fresh install will overwrite everything with the correct version files. Once you have your system tweaked how you want it then consider creating a custom installation disk with Remastersys. Then if it all falls over it's a breeze to get your system up and running again without having to load all your favourite packages again.

---

