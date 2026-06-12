---
title: "Will i lose data?"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by Lucas_Winther on 2015-10-18
Hey. I have a computer i only use for school, and its running a little slow. I want to install ubuntu, but i dont yet know if i wanna delete windows. If i use the option to do the partition disk, will i permanently lose data? And if i choose to use windows/ubuntu Will i get the full DATA of my hard drive back?

---

### Post by Irihapeti on 2015-10-18
If you want to be sure that you won't lose data, do a backup first. Then if something goes wrong, at least your documents and so on are safe.

---

### Post by howefield on 2015-10-18
A properly set up dual booting of Ubuntu with Windows won't put your data at risk.

The risk is that you mess something up, so ensure that you have a copy of any data you do not want to lose, this is something you should be doing in any event, irrespective of what you are using for an operating system(s). Always have a back up strategy otherwise you are just a mistake waiting to happen.

Ubuntu will be able to read the Windows partition and files, but Windows won't see the Ubuntu partition or files (at least, not without a degree of effort).

Which version of Windows are you using ?

---

### Post by grahammechanical on 2015-10-18
When we install ubuntu we get these options early on in the priocess

1) Install Ubuntu alongside them [that is other operating systems]
2) Erase disk and install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Uase LVM with the new Ubuntu installation
5) Something Else - create & resize partitions for yourself or choose multiple partitions for Ubuntu.

If you choose option 2, Erase disk and Install Ubuntu, You know what will happen. Do you not? And yet some people to choose to erase the disk and then get a surprise that they have lost everything that was on the disk.

In preparation you should

a) Use Windows utilities to defrag the hard drive. Do this more than once and check that Windows loads correctly each time.
b) Use Windows utilities to resize or delete Windows partitions to create unallocated space for Ubuntu.

If that machine is old enough to have a BIOS/MBR boot system and not a UEFI/GPT boot system you may need to delete at least one of the present partitions. This is because with MBR partitioning we can only have 4 primary partitions and if both Microsoft and the manufacturer have used up the full allocation (4 primary) then there is no where for Ubuntu to go. The only option for the Ubuntu installer is to ask permission to Erase disk and install Ubuntu. Do not accept.

We need to delete 1 primary partition and then use the spare allocation ( 1 primary) to create an Extended partition in which we can put as many logical partitions as we need. Ubuntu will need two.

With GPT partitioning it is much more simple. We just need unallocated space to create the 2 partitions for Ubuntu. There is risk but with good preparation and a backup the risks can be minimized

Regards.

---

### Post by Lucas_Winther on 2015-10-18
Well, i mean will i lose overall hard drive space. I have 256 GB and if i pledge 125 and decide i wanna go back to windows 10(the system i use) Would i then lose 125 GB on my computer?

---

### Post by Lucas_Winther on 2015-10-18
After some deeper research i found my answer. Thanks for the replies!

---

### Post by HermanAB on 2015-10-18
Howdy,

In general, installing Linux on a Windows machine is very reliable and the only times I have lost data was when I was complacent and failed to make a backup first - Murphy's Law...

---

### Post by continuity2 on 2015-10-18
The answer to your question (as you have already discovered, but for  others reading) is No, you will not permanently loose the hard drive  space you partition off for Ubuntu. You can always chose to erase that  partition and expand the original partition back into the empty space.  That works both ways, so if you decide you like Ubuntu you also have the option of erasing the windows partition to recover the space for your Ubuntu install.

---

