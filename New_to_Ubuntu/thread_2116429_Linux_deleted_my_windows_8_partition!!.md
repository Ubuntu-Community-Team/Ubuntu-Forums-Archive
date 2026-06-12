---
title: "Linux deleted my windows 8 partition!!"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Linuxxkid on 2013-02-15
Hello, 
Today I have tried to install Linux and what happened was that it restarted, when It restarted the screen was orange and started to flicker. I. Tried to boot into windows 8 and then I could not find it on the boot uefi and the only thing there is ubuntu which doesn't work! I was wondering how you could fix this.
Thanks,
Linuxxkid
Ps. I was using 12.10 ubuntu

---

### Post by cariboo on 2013-02-15
Are you sure, that your windows install is gone? Boot whatever media you used to install Ubuntu, and once at the desktop, press Alt-F2 and type:

```
gksu gparted
```

This will open the Ubuntu partitioning tool, to check and see if indeed your windows partition have been overwritten. I don't have a windows installation on this system, but the screen shot should give you an idea to look for.

Once you've run gparted, come back and tell us what you found, so that we know where to go from there in helping you get your system up and running again

---

### Post by Linuxxkid on 2013-02-15
Well, I have found that all my partitions are all intact! :D but i looked at the one labeled os and then I clicked Information and saw that it was unmounted so now I need to remount it :???:

---

### Post by Linuxxkid on 2013-02-15
Here are the screenshots I took.

---

### Post by Linuxxkid on 2013-02-16
Just a quick question, 
Is there a way to dual boot windows 8 and ubuntu? Like when I start up the computer, I will be presented with an option to either pick windows 8 or Ubuntu?

---

### Post by Ravi5kumar on 2013-02-16
Maybe this thread will help you: [http://ubuntuforums.org/showthread.php?t=2088425](http://ubuntuforums.org/showthread.php?t=2088425)

---

### Post by cariboo on 2013-02-16
If you are up to doing some work in a terminal, it looks like grub didn't install properly. Boot from whatever media you used to do the installation, and once at the desktop open a terminal, then once at the prompt type the following command, and press enter after each one:

```
sudo mount /dev/sda7 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

Next re-install grub:

```
sudo grub-isntall /dev/sda
```

then

```
sudo update-grub
```

you should see a listing of your installed operating systems, plus memtest. Press Ctrl-d twice, then reboot.

This should solve your problem.

---

### Post by carl4926 on 2013-02-16
> **Linuxxkid said:**
> Here are the screenshots I took.

Whoever partitioned that HD needs good poke.
Horrible !

+1 to @cariboo907 comments

---

### Post by Cbbwasott on 2013-02-16
You probably installed it over windows 8 by accident.

---

### Post by carl4926 on 2013-02-16
> **Cbbwasott said:**
> You probably installed it over windows 8 by accident.

No
Windows is still there

---

### Post by Linuxxkid on 2013-02-16
Ill try that when I get home but on a side note, how is the partition bad?

---

### Post by carl4926 on 2013-02-16
> **Linuxxkid said:**
> Ill try that when I get home but on a side note, how is the partition bad?

If you mean my comment

I just mean it's so messy and a very poor example.
Look at my netbook
[http://dl.dropbox.com/u/10573557/12.3_install_complete/12.3_install/eeepc-gparted.png](http://dl.dropbox.com/u/10573557/12.3_install_complete/12.3_install/eeepc-gparted.png)

My point is more or less an aesthetic one
Though you do have unallocated chunks and for the life of me I can't see the extended space listed

---

### Post by oldfred on 2013-02-16
STOP!

While the advice you are getting is good if you have a BIOS/MBR install, you have an efi partition first. So you almost for sure have the new UEFI install.

And Windows needs several extra partitions, vendors add partitions. With gpt there is no more 4 partition limit so everyone is creating partitions. There is no extended partition nor logical partitions.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by carl4926 on 2013-02-16
I did wonder if it was GPT
I hadn't noticed if that had been clarified yet ?
But that does seem most likely given what we see

---

### Post by Bartender on 2013-02-16
> **cariboo907 said:**
> 

```
sudo grub-isntall /dev/sda
```



Cariboo, shouldn't that be "grub-install"?

---

### Post by Linuxxkid on 2013-02-16
> **cariboo907 said:**
> If you are up to doing some work in a terminal, it looks like grub didn't install properly. Boot from whatever media you used to do the installation, and once at the desktop open a terminal, then once at the prompt type the following command, and press enter after each one:

```
sudo mount /dev/sda7 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```Next re-install grub:

```
sudo grub-isntall /dev/sda
```then

```
sudo update-grub
```you should see a listing of your installed operating systems, plus memtest. Press Ctrl-d twice, then reboot.

This should solve your problem.
I have tried that one and this shows up. When I tried this happened. Isnt there supposed to be something that says the command has been done? like for example when I inputed sudo mount /dev/sda7 /mnt isn't there supposed to be something happening like it did when i typed in sudo grub-install /dev/sda? Sorry if this is confusing.

---

### Post by oldos2er on 2013-02-16
Apropos of post #19

[s]Should be **grub-install**[/s]

Normally bash only gives feedback if there is a problem with a command. If a command is successfully executed it will return to a command prompt.

---

### Post by oldfred on 2013-02-16
Please go back to post #13 before you cause more issues.

With UEFI you do not use grub-pc but have grub-efi. And you do not install grub to MBR, but use grub-efi and install to the efi partition.

---

### Post by Linuxxkid on 2013-02-16
[http://paste.ubuntu.com/1665006/](http://paste.ubuntu.com/1665006/) 
This is the boot repair info.

---

### Post by oldfred on 2013-02-16
You are not showing any Windows boot files. Your efi partition is empty. And your Windows OS system partition is not showing the Windows boot file either. (but sometimes script misses it). Your Windows is in UEFI mode as drive is gpt, first partition is efi, and you have the Microsoft reserved partition. But the Windows specification says that must be just before main install and the next partition you have is the recovery?? Not sure if that will work. Did you rearrange partitions somehow or is that how the vendor did it. All other systems with Windows 8 have the MSR just before the OS as per spec.

But Boot-Repair seems to have backups of at least some of the Windows files that it can reinstall and will install the Ubuntu efi files.

I would run Boot_Repair and see what it recovers.

---

### Post by Linuxxkid on 2013-02-16
I ran boot_repair. [http://paste.ubuntu.com/1665904/](http://paste.ubuntu.com/1665904/)

---

### Post by Linuxxkid on 2013-02-16
So it told me that i could restart it but sínar i left the House, i was wondering of i was supposed to boot into try ubuntu or if i was supposed to boot into my actual ubuntu install.

---

### Post by oldfred on 2013-02-16
You should from the UEFI menu of your system boot ubuntu entry. 

You can try Windows only from grub menu, but I am not sure it Boot-Repair restores a BCD and you need that. You probably need a Windows repair flash drive and run bcdEdit.

       Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)

---

### Post by Linuxxkid on 2013-02-16
Well I will have to try that but I got into windows 8. I just have to go through Grub menu to boot though which for me I'snt that bad of an option but the thing is, I need my usb drive in the computer everytime I need to boot :(. I will also need to make a flash drive to make the repair disk. But, for now it is working.

EDIT: I got it and also now I boot from that drive and try to repair it?

---

### Post by Linuxxkid on 2013-02-19
I am able to run Windows 8 now but I want to delete the partition for ubuntu but I am afraid that it will mess up windows 8 because right now in the uefi, it says that I am automatically booting from windows boot manager but I think that is from the linux partition.

---

### Post by oldfred on 2013-02-20
Depending on settings you have done in Boot-Repair you may have renamed Windows boot files.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

Also some are reporting that even when deleting Ubuntu and removing grub files from efi partition UEFI remembers the entries. So you also have to go into the UEFI menu and do edits.

---

