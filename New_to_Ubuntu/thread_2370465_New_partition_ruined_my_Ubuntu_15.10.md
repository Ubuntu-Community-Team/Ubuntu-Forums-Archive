---
title: "New partition ruined my Ubuntu 15.10"
date: 2017-09-03
forum: New to Ubuntu
---

### Post by bertmung on 2017-09-03
I attempted to create a password protected partition in Ubuntu 15.10. The result was that usable space for Ubuntu was limited to the extent that doing anything at all created warnings that the hard drive was full. I got frustrated and went back to Windows 10 for awhile. Now I've even forgotten the password for logging in with Ubuntu. 

Can I just freshly install over the Ubuntu partitions starting from scratch?

---

### Post by wheatpenny2 on 2017-09-03
As far as I know you can. When you start the install process, select the option to erase the whole hard drive and install Ubuntu it should get did of whatever is on the hard drive, and the whole hard drive will be available under your new Ubuntu installation.

---

### Post by oldfred on 2017-09-04
Ubuntu 15.10 (Wily Werewolf) reached End of Life on July 28 2016  

Only install and use current versions of Ubuntu. 
Often best to use the LTS - long term support versions as they are good for 5 years.
      
 Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

If not wanting to erase entire drive only use Something Else install option. And you can reuse the existing / (root) as new / using the change button when on that partition.
Also the full drive encryption option is a erase entire drive as it uses the LVM install option.

       
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

