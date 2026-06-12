---
title: "New kernel not showing up in grub2?"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by scruffyeagle on 2012-03-23
I have a project machine w/ 4 different versions of Linux; each, in its own partition. I'm working w/ the Ubuntu v10.04LTS 32-bit OS today in partition sda5. I used the Update Manager today, and it didn't find anything. On a whim, I clicked on search, and it found a long list. I told it to install everything. Within that list, were items named "2.6.32.40-generic". Anyway, the system required rebooting right after the update was completed, so I did. When the grub2 screen came up, there wasn't any ".40" item listed for the partition. There was only the 4 items that had been there previously: ".39", ".39" for troubleshooting, the original kernel #, & that original for troubleshooting. What happened to the ".40" kernel?

TIA!

---

### Post by oldfred on 2012-03-23
Is the partition you updated the partition you boot from?

Post boot info script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

or run it directly (this is test/git version that has some fixes):

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

### Post by bogan on 2012-03-24
Hi!, **Scruffyeagle,**

I am running 10.04 LTS and 11.10 on two desktops and exactly the same thing happened to me when I rebooted after updating 10.04 to 2.6.32-40 on one machine but not on the other.

I reran update-grub and Grub Customizer from 11.10 - the default entry, -  and then everything was as I had set it up.

Chao!, **bogan**

---

### Post by scruffyeagle on 2012-03-26
> **scruffyeagle said:**
> I have a project machine w/ 4 different versions of Linux; each, in its own partition. <snipped> When the grub2 screen came up, there wasn't any ".40" item listed for the partition. <snipped> What happened to the ".40" kernel?


I hadn't read the posts here yet, but I figured out this mystery. What happened was the result of the fact that I'd installed the Xubuntu last. Since I had NOT used a "boot partition" for Grub's needs, Grub installed its files within the partition of the OS which was currently being installed. I now understand, that in the course of installing 4 different OS's into 4 separate partitions, Grub was installed 4 times. The sequence was Debian, Ubuntu, Kubuntu, then Xubuntu. The last installation of Grub is the location of Grub's files. Messing with installations of Grub within the other partitions will only mess things up, because the current installation of Grub knows where its home should be - within the Xubuntu partition.

Today, I did updates of all 4 OS's. I followed the order in which I'd installed them. Debian managed to update the grub2 screen w/ info about the new kernel w/o adding a new entry line. Ubuntu & Kubuntu showed no change in kernel lines; i.e., no new entry lines. However, when Xubuntu updated to the .40 kernel, it all came due & showed up in the grub2 boot selections screen. I believe that in the process of updating the grub2 boot data to show the new kernel option within Xubuntu, the program also scanned the other partitions - and updated the boot screen entries showing the .40 kernels. This only happened during the Xubuntu kernel update, because that was where grub2's files were residing. I'm sure the other updates triggered boot options updates - but, the grub2 boot screen installed only loods in the Xubuntu partition, and the other grub updates stored their info into their OWN partitions, not the Xubuntu partition.

---

### Post by oldfred on 2012-03-26
Yes, with 4 systems and update to the 3 that are not the one in the MBR will not be in the boot version until you do a sudo update-grub in the partition you boot.

You may also have to be aware that grub remembers where it installed. A major update to the grub2 files themselves sometimes triggers a total reinstall and that install will then take over as it is then installed into the MBR.

You can check where grub reinstalls to and by unselecting prevent it from reinstalling.

You can do this in all you Ubuntu based installs:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

They all will probably show the drive that is sda.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you do want anther install to be in charge you can run the above and select that install to be in the MBR.

I like to run the boot info script as it shows which grub is in the MBR plus it documents system configuration in case you have to recover it.

---

