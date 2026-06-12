---
title: "windows '07 1st version vista"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Soccroxanne on 2012-03-08
Hi, I have a question. Does ubuntu work for first version windows vista? If i download this software, will it absolutely work? Has anyone had problems with this? If it doesnt work, will my computer files be deleted with my computer no longer working? Thanks so much if you have the answer.

---

### Post by sikander3786 on 2012-03-08
Welcome to the UF! :)

If I understand you correctly, you want to dual-boot Windows Vista and Ubuntu, right? If yes, yes it would work regardless of which version (Service Pack) of Vista you've got.

First of all, you need to find if Ubuntu is compatible with your hardware. In most cases, Ubuntu (or any other Linux for that matter) work out of the box with almost all the hardware but there can be a few problems with your Wireless card, graphics card etc. For testing your hardware, you can create an Ubuntu Live CD/USB and boot from it. It won't make any changes to your existing setup and will give you the normal Ubuntu desktop where you can test all your hardware and also test Ubuntu if you come to like it.

Now if you want to install it, you need an empty partition where you'll be installing Ubuntu. I would recommend a minimum size of 15GB for this partition. If you've already got an empty partition, you are good to go. If not, you'll need to resize any of your existing partitions to create space for Ubuntu and then install it.

We can give you instructions on how to proceed. But before that, please download Ubuntu from here and create a Live CD or USB. Instruction are also on the same page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Then configure your computer's Bios to boot from the CD or USB (whichever you created) and boot Ubuntu. Continue with testing all your hardware. Additionally, if you then want to install Ubuntu, press the <Super> (Windows logo) key from your keyboard and search for and start 'Terminal'. In the 'Terminal', please run and post the output of following command so that we can guide you with the partitioning process:

```
sudo fdisk -l
```

---

### Post by jerome1232 on 2012-03-08
> **Soccroxanne said:**
> Hi, I have a question. Does ubuntu work for first version windows vista? If i download this software, will it absolutely work? Has anyone had problems with this? If it doesnt work, will my computer files be deleted with my computer no longer working? Thanks so much if you have the answer.

I think you are a bit confused about what Ubuntu is. Ubuntu is it's own independent Operating System, it does not run on Windows, it replaces Windows. Alternatively it can be setup so that you can choose at boot time whether you would like to use Ubuntu, or Windows (called dual booting).

If you want to try Ubuntu and not mess with resizing and repartition (taken care of very well automatically by the Ubuntu installer, but can be risky none-the-less) there is the option of doing what's called a Wubi install, this is a special setup in which Ubuntu is installed on a virtual file system that lives in Windows, Ubuntu can be removed and installed as if it were a program within windows so it's ideal for new users who want to get their feet wet.

For more info Try Psychocats guide, it is really good. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by I2k4 on 2012-03-08
The best way for a first timer to get familiar with Ubuntu is to install Live USB on a 4GB or larger USB thumb drive (and set the PC to boot from USB.)  Here are bullet proof step by step instructions to try Ubuntu out _without any risk of installing stuff that interferes with the Windows system_:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Note that if you don't install "Persistence" with the Pendrive installer you will lose all your settings between reboots.  Also, my experience has been that these Live USB installations go wonky after a few weeks - but they are wonderful _risk-free_ way to get familiar with Ubuntu in different versions and decide  if you want to permanently install it.

---

