---
title: "Feisty 7.04 server is hosed, need reinstall upgrade advice"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Hopworks on 2008-05-18
I've been putting it off, but now ready to reinstall my Ubuntu, but going with Hardy 8.04 server.

My current install is trashed big time, and it's not the OS's fault, it's mine. I changed all the hardware, all the way down to the core of the platform, and the OS still worked, but it's slow, and now I have a monster load of errors when I do anything with apt-get.

Problem is, I have been tweaking this feisty server for a very long time, as a LAMP server, and I still use it a lot, for everything. I was wondering if it is possible to install a fresh Hardy server 8.04 in a dual boot and STILL have my other install accessible. Then I can go back and forth, configuring all those tweaks I did.

Not sure what is entailed. Do I have to create another partition? Can I use the existing ones my current install uses? I downloaded the ISO, and have it on my flash drive.

Sorry to ask such an 'ADVICE INTENSIVE' question, but I don't want to lose anything I've accomplished, but I really need to upgrade and fix my errors.

Thanks for your time!

Hop

---

### Post by jbrown96 on 2008-05-18
> **Hopworks said:**
> I've been putting it off, but now ready to reinstall my Ubuntu, but going with Hardy 8.04 server.

My current install is trashed big time, and it's not the OS's fault, it's mine. I changed all the hardware, all the way down to the core of the platform, and the OS still worked, but it's slow, and now I have a monster load of errors when I do anything with apt-get.

Problem is, I have been tweaking this feisty server for a very long time, as a LAMP server, and I still use it a lot, for everything. I was wondering if it is possible to install a fresh Hardy server 8.04 in a dual boot and STILL have my other install accessible. Then I can go back and forth, configuring all those tweaks I did.

Not sure what is entailed. Do I have to create another partition? Can I use the existing ones my current install uses? I downloaded the ISO, and have it on my flash drive.

Sorry to ask such an 'ADVICE INTENSIVE' question, but I don't want to lose anything I've accomplished, but I really need to upgrade and fix my errors.

Thanks for your time!

Hop

You will need to create another partition for Hardy Heron, but there are a couple of things to keep in mind. I don't think more than 5 primary partitions (better double check) can exist on a single hard drive; jfs and xfs partitions cannot be shrunk, although xfs isn't bootable, so you're probably not using it. I didn't have any problems installing Hardy (desktop) after another version of it or any other linux distro. 
When you install hardy, I would suggest you make create mount points (in the partition editor) for all your partitions (greatly simplifies accessing them -- mount is always works too). Also be sure that Feisty is still listed in the grub configuration (last step of install) or else you should make a backup of your /boot/grub/menu.lst (not a bad idea anyway).

I think the only risk of going dual-boot, then transitioning to singl-boot, is a loss of disk usage. It may be difficult and risky to grow the Hardy partition to use the Feisty space after you have made your tweaks, but if you don't have another backup option, then that's what you have to do. 

Best of luck

---

### Post by Hopworks on 2008-05-19
I want it clean, with the best chance of being error free and not so limited, so I made a full backup of settings in Webmin. I don't know how that will affect MySQL, or Apache2, or even PHP, or finally my LAMP configuration in Hardy at all, so I was wondering if it would be as simple as that, importing those settings back in using webmin after I install Hardy 8.04 server CLEAN.

I've spent the last few hours researching how to backup my databases, my samba settings, etc. Not sure if I covered all the bases. My biggest problem with my Feisty is that it was my first Linux experience, and I failed to take good notes. I want to make sure I do that this time. Some suggested a wiki type page for my LAMP server, so maybe I should wait until I can take good notes this time.

At least I can search my posts here, and trace down all the research I did. Kind of a refresher course I guess. I've spent countless hours researching XFS, MythTV, SSH/SSL, Webmin settings, Samba for access from my windows machines, TightVNC, Putty. The thought of not being able to go command line from my laptop or main windows machines is unbearable! =)

Again, Thank you for your valuable time. I made sure to thank you. =)

A Ubuntu Linux LAMP server has been so amazingly valuable to me though, so it's not just for fun anymore, it's a real necessity.

---

