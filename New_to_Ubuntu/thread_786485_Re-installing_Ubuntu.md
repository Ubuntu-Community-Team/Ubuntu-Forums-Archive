---
title: "Re-installing Ubuntu?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Ghaarnok on 2008-05-08
Well, I decided to upgrade to Hardy Heron from Gutsy Gibbon via the Software Update Manager last night, it had a few random errors in doing so and now Ubuntu doesn't seem to be working correctly.

Anyway, I was thinking of rather than trying to solve the issues that I should just re-install Ubuntu. What is the best way to do this? So far a couple of options seem to be open to me...

Format the partition using partition magic and then re-install.
..or..
Delete the partition and then re-create one during the Ubuntu installation.

However, the main query I have is about the GRUB bootloader. How will it be affected by the above actions?

Ubuntu is installed on a different drive to my Windows XP installation. HOWEVER, the drive on which Ubuntu is installed does have a NTFS partition on it which contains data (music etc) so I'd like to keep that data. I've set BIOS to boot from this drive first (thus initiating GRUB on boot). So I was also wondering how trying to remove GRUB would affect all this.

What do you think I should do?

---

### Post by talsemgeest on 2008-05-08
Just back up your data to a partition that you are not going to install ubuntu to, download the .iso and burn it to a cd. Then start it up, and install it to the partition of your choice. The grub will be reconfigured, and it will be written to the MBR.

Hope this helps :)

---

### Post by Ghaarnok on 2008-05-08
Thanks for the response.

The only problem is that I can't move the data from the NTFS partition to another drive as I haven't sufficient space anywhere else (and it would take me hours to burn it all to DVD).

Perhaps removing GRUB from the drive first, then formating the partition may be better?

Problem is, how do I get rid of GRUB and how will it affect the NTFS partition?

---

### Post by indytim on 2008-05-08
When you come to the partition section of the re-installation, select the "Manual" option.  Install your fresh Ubuntu right over the existing installation.  Don't forget to flag THAT partition as "Format".  Also, identify any other partitions you want mounted with the Ubuntu ops bootup.

IndyTim

---

### Post by talsemgeest on 2008-05-08
You don't need to stick it on another drive. When you install ubuntu, it will only touch the partition that you are installing it to. As long as there is nothing on there that you don't mind being deleted, you are good to go.

---

### Post by Ghaarnok on 2008-05-08
So there's no need to format the partition previous to running the installer? Interesting.

Sorry, I'm still used to the Windows way of doing things.

Also, I've yet to decide whether I'll install Hardy Heron or Gutsy Gibbon too. Gutsy Gibbon was working fine but after trying to update to Hardy Heron and having issues I'm a little wary of it.

---

### Post by drsox1899 on 2008-05-08
See if there is an answer in this guide :

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

In general the wisdom seems to be to reinstall rather than upgrade, but ensure you have separate /home partition so that this can be untouched in any new install.  
It also makes for an easy place to find the stuff that you might want to backup.

Luck

PS Yes, you can format prior to installing but you will need to do it yourself.
I have found PMagic to work v well - it runs as a live CD. It's easy to use.

---

### Post by talsemgeest on 2008-05-08
When you do an upgrade it tends to go wrong. It is a lot safer to just do the cleans install, it should all go smoothly.

And another thing, when you tell ubuntu which partition to install to, it formats it prior to installing itself onto it.

---

### Post by muteXe on 2008-05-08
I've never really trusted an upgrade, I've always done a fresh install.

---

### Post by Ghaarnok on 2008-05-08
Thanks for all the feedback so far.

I'll just do fresh installs in future I think. However, if you do a fresh install won't that get rid of all the programs etc that you set up on the previous version?

One of my pet hates is re-installing software on a fresh XP install, especially when you have a large catalogue. It's not too much of an issue with XP though as I only need to re-install about once every 2 years. With Ubuntu though, new versions are coming out on a much more frequent basis.

For future reference, is there any way you can preserve what software you have installed in Ubuntu when installing a new version? (this is why I took the upgrade route rather than doing a fresh install)

---

### Post by Sef on 2008-05-08
> I'll just do fresh installs in future I think. However, if you do a fresh install won't that get rid of all the programs etc that you set up on the previous version?


Yes, you will have to reinstall all your programs.

---

### Post by Ghaarnok on 2008-05-08
> **Sef said:**
> Yes, you will have to reinstall all your programs.

Ah, that is what I thought. But I also thought that there may have been some way to export a list of what packages you have installed and then import the list into the package manager when you re-install ubuntu so that it will download and install everything you had previously.

It would be a useful piece of functionality as reinstalling everything is what puts me off upgrading, especially since I'm a noob and it takes a long time to find out what software I need to be using and then installing it.

---

### Post by drsox1899 on 2008-05-08
> **Ghaarnok said:**
> Ah, that is what I thought. But I also thought that there may have been some way to export a list of what packages you have installed and then import the list into the package manager when you re-install ubuntu so that it will download and install everything you had previously.

It would be a useful piece of functionality as reinstalling everything is what puts me off upgrading, especially since I'm a noob and it takes a long time to find out what software I need to be using and then installing it.

Unfortunately it doesn't always work like that. Each new version of Ubuntu usually installs newer versions of some dependencies (think dll's in WinSpeak). Most apps that are installed by Ubuntu package managers will install newer versions when reinstalled to deal with this.

If you have found and installed an app from somewhere else, then you may have to look for a newer version from the original site (e.g. Sourceforge) or you may have to edit the install.

A favourite problem seems to be the updating of the lib packages in /lib that breaks the dependency (e.g. there was libxyz.1.1.1 and now you find  that this has been replaced by libxyz.1.2.0).  What you need to do is just to create a link IN the /lib directory that points all references to 1.1.1 to the new 1.2.0.  Not difficult but needs to be done in the Terminal as root.

---

### Post by talsemgeest on 2008-05-08
You can always back up the packages that you downloaded, then put them back after. They are located at /var/cache/apt/

Hope this helps :)

---

### Post by A$h X on 2008-05-10
I am considering doing the same thing (re-installing gutsy over hardy) and was wondering if there is a way to add a /home partition (ATM it's just a directory on my hardy partition) so my settings and added apps will still be there after a fresh install. Or is this not possible? 

Oh and in var/cache/apt does that contain any programs which I have installed manually (ie by clicking a .deb package and not via synaptic)? How do I go about re-installing all these programs from my var/cache/apt backup after a fresh install?

---

### Post by talsemgeest on 2008-05-10
As for the home partition, make a new partition and copy everything from your old home to here. When you are installing, tell it to mount the partition as /home.

For the apt thing, I don't think it has the manual installers. As for installing what you have there, you can either double click the package, or you can install it through synaptic.

---

