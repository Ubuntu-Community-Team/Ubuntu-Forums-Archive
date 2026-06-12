---
title: "How do I get Ubuntu installed on its own partition"
date: 2020-10-21
forum: New to Ubuntu
---

### Post by Odense on 2020-10-21
Please also see the attached screenshots.

I have a computer with a 500 gb HD with Windows 10.
I have created a second partition with 400gb so there is 100 gb left on the windows partition.
I want to install Ubuntu on the second partition with a grub boot menu so I can choose to boot from the partition with Windows 10 or the partition with Ubuntu.
But I dont see that option (in the screenshots).

So - what can I do to achieve my goal?

---

### Post by oldfred on 2020-10-21
You cannot install Ubuntu to Microsoft formats like NTFS, default is ext4, but other Linux formats can be used.
So select change, use ext4 and use as / (root). Optional is to split space and add a /home partition which should be the largest part.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Installer will auto find your existing ESP - efi system partition and will create a swap file. So only / (root) required.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

---

### Post by Impavidus on 2020-10-21
Ubuntu can't be installed in a Windows partition, which is what NTFS is. If you first delete that /dev/sda5, the install alongside option will probably do what you want. You can also use something else, select /dev/sda5 for mountpoint / and format to ext4 (or some other Linux filesystem if you really want).

Some other options that you may find interesting:
Instead of a single large partition for Ubuntu, you could have a separate partition for /home, or some other way to separate your data from the OS. That will make it easier to reinstall while keeping your data.
By default Ubuntu now uses a swap file, but you could use a swap partition if you like.
If you want to share files between Ubuntu and Windows, it's best to make an NTFS partition for data, separate from your Windows C partition.
Make sure FastStartup has been disabled in Windows (although I think it already is).

---

### Post by Odense on 2020-10-21
> **Impavidus said:**
> Ubuntu can't be installed in a Windows partition, which is what NTFS is. If you first delete that /dev/sda5, the install alongside option will probably do what you want. You can also use something else, select /dev/sda5 for mountpoint / and format to ext4 (or some other Linux filesystem if you really want).

Some other options that you may find interesting:
Instead of a single large partition for Ubuntu, you could have a separate partition for /home, or some other way to separate your data from the OS. That will make it easier to reinstall while keeping your data.
By default Ubuntu now uses a swap file, but you could use a swap partition if you like.
If you want to share files between Ubuntu and Windows, it's best to make an NTFS partition for data, separate from your Windows C partition.
Make sure FastStartup has been disabled in Windows (although I think it already is).

I actually tried installing Ubuntu on the empty space before formatting it but that was not possible.
Then I formatted it to ntfs and that was wrong.

I just formatted it to ext4 but it did not seem to change much?

I think it is a good idea to reduce the Ubuntu (and the Windows) partitions and make a bigger document partition - how many gb is good for a Ubuntu partition (and how many gb for a Win10 partition)?

---

### Post by oldfred on 2020-10-21
Partitioning is unique for every person.
It depends on your use & how much data you want to save and where you are saving it.

Windows NTFS needs 30% free to work well. At 10% free, it becomes very slow and you just about cannot do a defrag as no working room.
Linux does need some working space but not as much.

If new user better to use just /, if not very large partition,  or have separate /home.
More advanced is data partition(s), but then you have to set mount point and give yourself ownership & permissions to use it.
I keep /home inside /, but have large data partition as ext4. Back when I still had Windows XP, I also had a NTFS data partition. But as I used Windows less & less, data grew in ext4 data partition, so had to resize. Now no NTFS partitions. :)

Typical desktop is usually ok in 25 to 30GB, but if you add server applications and then a large data base, you either need a larger / or move those apps to another location.

---

### Post by ajgreeny on 2020-10-21
Having created the free space, which you say you have tried already, you then need to use the "Something Else" (Noget andet) option at the disk preparation stage, select that unallocated space and choose to create new partition or partitions as you want by clicking on the + sign below.

As you have already made an ext4 partition you can also choose that in the installer and click on "Change", then choose what you want to do with it from there, which will depend on how you want to use that 400GB space; one partition for the complete OS or one for / (root) the OS itself and a second for /home or data.
A / and /home partition can be created at installation with the appropriate mountpoints given them; a data partition will have to be made then dealt with after the OS installation has been performed.

---

### Post by Odense on 2020-10-21
> **ajgreeny said:**
> Having created the free space, which you say you have tried already, you then need to use the "Something Else" (Noget andet) option at the disk preparation stage, select that unallocated space and choose to create new partition or partitions as you want by clicking on the + sign below.

As you have already made an ext4 partition you can also choose that in the installer and click on "Change", then choose what you want to do with it from there, which will depend on how you want to use that 400GB space; one partition for the complete OS or one for / (root) the OS itself and a second for /home or data.
A / and /home partition can be created at installation with the appropriate mountpoints given them; a data partition will have to be made then dealt with after the OS installation has been performed.

Please see the new screenshots.

I would have thought that too but I really dont see how I can pick the ext4 partition I just created for Ubuntu. (sda4 Win10  sda5 Ubuntu sda6  shared data disk)

But as shown in the screenshot it seem it want to split up sda6 into 6 and 7 and that is not what I want.

How can I install Ubuntu on sda5 and use sda6 as a data disk shared between Ubuntu and Win10?

---

### Post by ajgreeny on 2020-10-21
You have not shown us the screenshot after choosing the "Something Else" option.

DO NOT choose to install "alongside Windows Boot Manager", which is something I know nothing about as I do not use Windows any more, and of course, do not use the second option to erase disk as that will remove all of the existing Windows.

Try again the Something Else option and show us what appears; it will help clarify the situation and we can then give you more exact suggestions.

---

### Post by oldfred on 2020-10-21
Along side will  take some random partiiton and try to shrink it enough to squeeze in a new / partition.
That is not what you want once you have already created partitions.
You want Something Else and choose (change button) which partition is / & which is /home and format (even if already formatted).
But if reusing a /home that has data, never check the format box as that would erase all your data. 
Do not forget as I have accidentally picked the wrong one. Installer screen is different than gparted screen.

---

### Post by Odense on 2020-10-22
> **oldfred said:**
> Along side will  take some random partiiton and try to shrink it enough to squeeze in a new / partition.
That is not what you want once you have already created partitions.
You want Something Else and choose (change button) which partition is / & which is /home and format (even if already formatted).
But if reusing a /home that has data, never check the format box as that would erase all your data. 
Do not forget as I have accidentally picked the wrong one. Installer screen is different than gparted screen.

Thank you oldfred - you are naturally right.
So - which of the options should I choose_
It is a royal PITA that if I choose English language then alt-prtscr does not work - so this is a photo from my old phone.

---

### Post by oldfred on 2020-10-22
Scroll all the way up & choose ext4. 
That is the normal default for Ubuntu.
Then choose use as / (root) for your / and choose other partition set ext4 and use as /home.
Again only check the format box if new install. If reusing a /home with data, never check format box.

If UEFI install, it will  auto find the existing ESP from Windows on gpt drive, if first drive.
Old instructions had adding swap partition, but now a swap file is used by default, so no swap partition required.

---

### Post by Odense on 2020-10-22
> **oldfred said:**
> Scroll all the way up & choose ext4. 
That is the normal default for Ubuntu.
Then choose use as / (root) for your / and choose other partition set ext4 and use as /home.
Again only check the format box if new install. If reusing a /home with data, never check format box.

If UEFI install, it will  auto find the existing ESP from Windows on gpt drive, if first drive.
Old instructions had adding swap partition, but now a swap file is used by default, so no swap partition required.

Thank you for answering.
I do however not understand the answer.
There is only one ext4 partition on the HD. I took a 500 GB SSD with Win10 preinstalled and shrunk the partition with Win10 to 90 GB There are some small partitions that Win10 installation must have created. I had for a short period the rest on the HD partitioned as ext4 but I can see it will be nice to have a Data partition that both Ubuntu and Win10 can work on so I reduced the ext4 partition to 50 GB and made a data partition formated to ntfs.
So I CAN choose ext4 for the Ubuntu installation but it is not at the top of the list as the screenshot should show - I think it is sda5 or sda6. When I double-click on ext4 i get a list of what it should be used for. I do however not see neither home nor root on that list - so what should I select?
When I want to use the last - ntfs formatted - partition as a data disk I think that is where home should be - but again I don't see home in the list of choices?

The partitons are freshly formated so I don't need that even if there is also no home folder on the partitions yet.
I have set the bios to UEFI only.

---

### Post by tea for one on 2020-10-22
Have a look at the screenshots under Step 6 on this web page

[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

Any help?

---

### Post by Odense on 2020-10-22
> **tea for one said:**
> Have a look at the screenshots under Step 6 on this web page

[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

Any help?

Yes - thank you very much - apart from the description of the creation of the swapfile which I think oldfred wrote I did not need. But I will try following that page.

For some reason I had the impression I could place the /home folder on a data partition that is ntfs formatted so it could be used by both my Ubuntu and my Win10 partition.
I deleted the ext4 and the ntfs partitions previously created and followed the guide. It works well but there is no option to use ntfs for the home partition. So I guess I cannot have the home partition on a "shared" partition?

---

### Post by tea for one on 2020-10-22
Ubuntu will automatically create a swapfile during the installation process.

One less thing to think about ;)

---

### Post by Odense on 2020-10-22
> **tea for one said:**
> Ubuntu will automatically create a swapfile during the installation process.

One less thing to think about ;)

You might think so - but not really - can I just skip that step and move to the creation of the /home folder?

---

### Post by CelticWarrior on 2020-10-22
> [COLOR=#000000]So I guess I cannot have the home partition on a "shared" partition?[/COLOR]
Indeed, you can't.

> [COLOR=#000000]can I just skip that step and move to the creation of the /home folder?[/COLOR]
Indeed you can. A swapfile is created automatically. There's no need to make a swap partition currently.

---

### Post by tea for one on 2020-10-22
You've edited post 14 so I do not know how far you have progressed? The chronology of the thread becomes difficult to follow.

Which step do you want to skip?

Ooh, I think CelticWarrior has cracked it.

---

### Post by Odense on 2020-10-22
> **tea for one said:**
> You've edited post 14 so I do not know how far you have progressed? The chronology of the thread becomes difficult to follow.

Which step do you want to skip?

The step with the swap file

---

### Post by Odense on 2020-10-22
And it seems to work now - thank you gentlemen :)

---

