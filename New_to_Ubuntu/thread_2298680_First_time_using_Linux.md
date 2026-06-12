---
title: "First time using Linux"
date: 2015-10-13
forum: New to Ubuntu
---

### Post by Oscar_Estrada on 2015-10-13
Hello, I'm interested in changing my OS from Win7 to Ubuntu and I ran into a problem and I can't seem to find what my problem is because it looks different than what I am getting when I search it. So what I did was download the latest version of Ubuntu from the website, made my usb into a bootable USB and got as far as to installing the new OS, logging in, and it gave me a error while verifying the installation saying "No root file system defined Linux ubuntu, Please partition something something from partition menu". I can't open a partition menu of any sorts because when I press ok, seconds later the same error pops up and theres no option to open up a partition menu. Sadly I'll have to wait till the weekend to play around with it again because I'm trying to put it on my weekend computer. If need be I can clarify more. I have two hdd's so I'm putting it on the one I don't use.

---

### Post by The Cog on 2015-10-13
I thnk you needed to press Back to get back to the partitioning menu.
Since you have a whole hard disk to play with, the easiest thing to do is to choose to use the option to use the entire disk. t will create the partitions itself, using reasonable default configuration.
Unplug your windows disk to avoid confusion/accidents.

---

### Post by grahammechanical on 2015-10-13
You have choosen to use the Something Elase option. At the page where we get the layout of all the partitions we need to select a partition to install ubuntu on and a partition you use as a swap partition and we need to tell the installer what we want it to do with those 2 partitions.

We select the intended Ubuntu partition and we click Change. In the next dialog we go to the panel labelled Use As and from the dropdown menu we select Ext4. Then we tick the box labelled format the partition. Still need to define what in Lunux is called a mount point and there is a panel and a dropdown menu where we can do that. We select /. Then we click OK and we find ourselves back at the screen with all the partitions and our changes are accected.

We then select the partition to be used as Swap. We click change. We get the same dialog but this time we do things a little different. The mount point this time will be /swap. Every other setting should be the same as for the Ubuntu partition. Now when we click OK we get back to the screen with the partition layout without seeing that error message.

The installer will default to installing the boot loader into the first hard disk (sda) but we can change that if we need to in the panel just underneath the box showing the partitions. So double check that things will be installed where you want them to be and them click Install. And off you go.

But the Erase disk & install Ubuntu or the Install Alongside options are the simple options.

Regards

---

