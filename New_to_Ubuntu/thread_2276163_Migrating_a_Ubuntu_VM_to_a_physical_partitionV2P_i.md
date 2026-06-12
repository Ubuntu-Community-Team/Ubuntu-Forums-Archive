---
title: "Migrating a Ubuntu VM to a physical partition/V2P is it possible?"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by diego38 on 2015-04-30
Hello everyone! I'm new to this community, i tried searching for what i'm looking for, but i didn't found the answers to this exact case:

Actually i'm using Windows 7, and i have a Ubuntu 14.04 installed on a Virtual Machine [which i use the software VirtualBox to run it]. My HD is already partitioned, and does have an partition for Ubuntu [where i have an older and unsupported version of Ubuntu] and a swap partition, also i have the grub on the boot...

My question is: Is there a way where i can substitute my older Ubuntu version that is on a physical partition with the Ubuntu 15.04 that runs in a vm on my Windows partition? I don't need to backup anything from my linux phisycal partition, can i move my VM to there?

Thank you!

---

### Post by sudodus on 2015-04-30
Welcome to the Ubuntu Forums :-)

Ubuntu is portable between computers if you are not using any proprietary drivers. I'm not sure about the virtualbox guest additions. Maybe you should uninstall them.

Then you can make a [compressed] image of the system. Maybe you can find a converter from the file, where it is stored now, the [SIZE=3]**vdi**[/SIZE] file. Otherwise you can use for example ***tar*** or ***Clonezilla*** to create an image. You need another drive to store the image, either in virtualbox or via the local network (or the internet).

I would use the One Button Installer to create a tarball (compressed tar file), or Clonezilla.

---

