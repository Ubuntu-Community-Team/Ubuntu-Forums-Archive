---
title: "Grub Rescue error Ubuntu 13.04 Dual Boot"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by eduseeker on 2013-07-09
i'm a newbie to Linux and had install Ubuntu 12.10 dual  booted with Windows8. But the ubuntu several times showed some wierd  kind of errors (which I've never heard of, like it got hanged and  freezed). So I decided to upgrade to 13.04.
  **What I did**: I wanted to increase the space allocated  for the disk on which ubuntu was installed, so I shrinked one disk  (using Windows Partion Manager) and ***deleted the one in which Ubuntu(12.10) was installed.***
  So when I restarted it, it showed "Grub rescue" kind of error. I  tried to install ubuntu (by live cd), it does not show any partition. It  shows the whole hard disk as a single partition.
  Moreover, when I tried to mount any of the partition (of total of 5),  it says something like "cannot mount, the file system is not in fine  state ... shutdown windows and try again".
  When I tried to boot windows Xp (the only cd I have atm), it stuck at "Examining disk at bus 0 ..." something.
  I searched and have installed Boot-Repair, whose log is [http://paste.ubuntu.com/5857634/](http://paste.ubuntu.com/5857634/) 
  Somebody Please guide me as I don't want all my data be erased.  ps: I've about 4-5 hours to run it otherwise my brother won't let me live at peace. :/
  (Sorry if the question has already been asked. I searched but  couldn't find any topic with exactly the same question, and moreover I  have to save the data on the disk; I can't take risks).
  thanks

---

### Post by westie457 on 2013-07-09
> **eduseeker said:**
> i'm a newbie to Linux and had install Ubuntu 12.10 dual  booted with Windows8. But the ubuntu several times showed some wierd  kind of errors (which I've never heard of, like it got hanged and  freezed). So I decided to upgrade to 13.04.
  **What I did**: I wanted to increase the space allocated  for the disk on which ubuntu was installed, so I shrinked one disk  (using Windows Partion Manager) and ***deleted the one in which Ubuntu(12.10) was installed.***
  So when I restarted it, it showed "Grub rescue" kind of error. I  tried to install ubuntu (by live cd), it does not show any partition. It  shows the whole hard disk as a single partition.
  Moreover, when I tried to mount any of the partition (of total of 5),  it says something like "cannot mount, the file system is not in fine  state ... shutdown windows and try again".
  When I tried to boot windows Xp (the only cd I have atm), it stuck at "Examining disk at bus 0 ..." something.
  I searched and have installed Boot-Repair, whose log is [http://paste.ubuntu.com/5857634/](http://paste.ubuntu.com/5857634/) 
  Somebody Please guide me as I don't want all my data be erased.  ps: I've about 4-5 hours to run it otherwise my brother won't let me live at peace. :/
  (Sorry if the question has already been asked. I searched but  couldn't find any topic with exactly the same question, and moreover I  have to save the data on the disk; I can't take risks).
  thanks




Hi.
If no one has already said, welcome to the forum.

Have looked at your 'Boot info' results and a couple of things are apparent.

You are using the 32-bit version of 13.04 when you should be using the 64-bit version which is necessary if Windows is pre-installed to a hard drive with a GPT partition table. The 32-bit version does not normally work with a GPT table and secure boot which is probably why the Boot-info is only showing the USB stick as your only hard drive (Sda). I could be mis-informed on this and if incorrect I apologise in advance.


Does Windows 8 still boot? Try it and let it run any necessary repairs. 

The Grub error is caused because the installed partition has been deleted but Grub has not been removed from the hard drive. To get Windows to boot you might have to press F12 or whatever button the computer manufacturer has decided on to get to the one-time boot options and choose the Windows Boot Manager.

Once you have Windows running again you will have to go into the power settings and disable the fast shut down (hybrid sleep). Cannot remember exactly how to get to those screens.

After that go into the UEFI/BIOS and disable 'Fast Boot'.

If you still want to use the 32-bit version disable 'Secue Boot' as well. Then post another 'Boot-info' report so we can see what is happening.

Thank you.

---

### Post by eduseeker on 2013-07-09
> **westie457 said:**
> Hi.
If no one has already said, welcome to the forum.

Have looked at your 'Boot info' results and a couple of things are apparent.

You are using the 32-bit version of 13.04 when you should be using the 64-bit version which is necessary if Windows is pre-installed to a hard drive with a GPT partition table. The 32-bit version does not normally work with a GPT table and secure boot which is probably why the Boot-info is only showing the USB stick as your only hard drive (Sda). I could be mis-informed on this and if incorrect I apologise in advance.


Does Windows 8 still boot? Try it and let it run any necessary repairs. 

The Grub error is caused because the installed partition has been deleted but Grub has not been removed from the hard drive. To get Windows to boot you might have to press F12 or whatever button the computer manufacturer has decided on to get to the one-time boot options and choose the Windows Boot Manager.

Once you have Windows running again you will have to go into the power settings and disable the fast shut down (hybrid sleep). Cannot remember exactly how to get to those screens.

After that go into the UEFI/BIOS and disable 'Fast Boot'.

If you still want to use the 32-bit version disable 'Secue Boot' as well. Then post another 'Boot-info' report so we can see what is happening.

Thank you.

Thank you very much sir!
Actually, the power cables of the hard disk were loose so I tighten them a bit and then Xp found them. I deleted both the partitions - one, in which Ubuntu was installed earlier and the other, the SWAP.

Now I can login to Windows without any problem.

But it took time to me to understand that it was a hardware related problem (after somebody at askubuntu replied), because when Ubuntu did not identify the partitions (on installing by Live cd) and it then run the Live Session, Ubuntu showed all the 5 partitions but could not mount any of them with that error (File System error something).


I'm really very sorry but I did not get any of your point (being a noob). Some question on basis of your answers:
1. How do I know if mine has GPT partition table?
2. Where is Grub info stored (considering the fact that I deleted the drive in which Ubuntu was installed but still Grub info was there)?
> If you still want to use the 32-bit version disable 'Secue Boot' as  well. Then post another 'Boot-info' report so we can see what is  happening.
3. Could you please tell me how to do this?

Thanks again.

---

### Post by westie457 on 2013-07-09
Secure Boot is an option in the UEFI/BIOS, what a computer runs through before booting an operating system.

To disable Secure Boot, power on the computer and rapidly press F2 or whatever key the manufacturer has designated, after a few seconds you will get screen appearing showing some basic info.

[COLOR=#ff0000]Be careful what you change in these screens because it is very possible to cause it not to start at all.[/COLOR]

Using the cursor/arrow keys move to the advanced tab or check each screen looking for 'Secure Boot'. Arrow down to that and hit Enter, select disabled and hit Enter again.

Hit F10 to save the changes and exit the UEFI/BIOS. This will cause the computer to reboot.

As the computer restarts you might see a warning that 'Secure Boot' is disabled, however it should continue to boot into whatever is the first declared starting device, usually 'Windows Boot Manager' unless you have set it to boot from something else. eg the CD/DVD drive.

On the same screen as the options for Secure Boot is a section for Uefi OS. In here might be Uefi OS, Legacy or something with CSM and Uefi/Legacy. I use the Uefi/Legacy one because I am booting an OS installed to an USB external drive.

Grub is stored in a UEFI Boot partition at the start of a hard drive when using a GPT partitioned drive. On a normal MBR/Msdos it is stored in the MBR - master boot record.

Secure Boot is usually enabled by default for a GPT partitioned hard drive.

Hope this helps.


Ps no need to apologise for being a noob, the vast majority of us here have come from using Windows and are still learning how to use Linux.

---

### Post by oldfred on 2013-07-09
Your bootinfo report only showed the flash drive and no hard drive, so that indicated some sort of hardware or BIOS type issue.
So we do not know what your configuration really is.

All BIOS based systems install a small bit of boot code into the MBR, with Windows that starts Windows but needs a lot of code in the Windows partition. With Ubuntu it is grub, but it needs the rest of grub and kernels in the Ubuntu partition. So when you uninstalled Ubuntu you deleted grub, but did not update the MBR with a Windows boot loader.

---

