---
title: "Just installed Ubuntu in dual boot with xp but cant select iso on boot"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by bill38 on 2014-04-22
Hello

I am new to the forum and quite new to linux. I just installed ubuntu 12.04 lts in dual boot mode but cant get the boot menu to display on startup. Holding the shift key doesnt work, I tried modifying some of the parameters in grub, that doesnt work. I was able to set the image it boots from to xp but now it only boots from xp and I cant get ubuntu to boot now. I tried ireboot and easybcd but no relief there. Is there a way to rebootthe  ubuntu image from xp? I'm trying to get this all working so I eventually port over to ubuntu permenantly.

Thanks for any help
Bill

---

### Post by nns2006 on 2014-04-22
Is this a side by side installation or ubuntu under windows? Can you explain how have you installed and how you have done till now. That will help pin point your problem.

---

### Post by stalkingwolf on 2014-04-22
you will probably have to use the grub boot repair disk ( the easiest way ive found)  . once booted choose advanced options, grub options, the the uncomment option. then just follow the on screen out.

---

### Post by oldfred on 2014-04-22
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or you can try booting with Supergrub to get into your Ubuntu install. 

 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

I have both as repairCD or flash drives and several other repair tools.

---

