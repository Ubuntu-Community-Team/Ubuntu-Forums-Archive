---
title: "Ubuntu not installing on Windows 7 system"
date: 2018-02-06
forum: New to Ubuntu
---

### Post by lyokoheros on 2018-02-06
I have similar problem though with Windows 7. 
I tried to install the same version of Ubuntu (or at least I think so I downloaded the newest LTS version) alongside with windows 7. I'd never done anything like that but I found some tutorial with a way which was told to be completely safe (for my data on the computer), and when I menaged to create bootable USB and boot system from it I tried to install Ubuntu, choose my language, and then I have too choose between formating the computer and erase all data to install Linux or "other". It was actually something different than in tutorial I found - it told about option "install alongside with Windows", but i though "ok, maybe I'll just need to chose it in the other option, considering it was done for instalation from CD", than i got to something like partitioning configuration, in which I was pretended to choose partition for Linux(tutorial said it was supposed to happen after choosing instalation alongside with Windows), but after I tried to decrease size of one of them I couldn't create a new partition with remaining free space. I tried to retreat from the instalation, but then to my surprise i get to something what look like already installed ubuntu(or it just seemed to me), though it seemed to not have any of my data from Windows! I tried to restart my computer and boot Windows anyway to find solution, but I found out it's impossible. I have just boot option to install Linux or try it without instalation. I decided to restart again and this time go to Bio to change boot option but it was all in vein...
Then on this uninstalled linux I find something what seemed to be solution, I mean page about Boot-Repair, I do the instructions from it, use Boot-Repair device hoping it solve the problem but all I can get was getting back to instalation menu (but fortunately information about used and all space on particion seem to suggest, that my data are still not deleted) and again I couldn't use remaining free space to create new partition for linux. 

I just don't know what to do... here is link to boot.rapair raport:
paste.ubuntu.com/26532519
My Bios is UEFI... 
I know You already wrote solution to case with Windows 10, but to be honest I don't understand exactly what i have to do(if solution in case of Windows 7 remain the same). I'm completely new to such modyfying the system etc. and reading about it in English, which isn't my native language, make it even harder. So if You could explain in easy steps, and easy way (I mean I could not know all technical term in English) what I'm suppose to do I would be very, very grateful.

---

### Post by oldfred on 2018-02-06
While a new install, you configuration is totally different, so you need separate thread.
Please do not hijack another thread as then it gets confusing on what answer applies to what problem.

You have the classic 4 primary partition problem with BIOS/MBR systems. (UEFI uses gpt which has a 128 partition (soft) limit).
MBR only allows 4 primary partitions. It originally only allowed 4 partitions when designed 35 yearts ago, but then they realized more partitions were needed.
So one primary must be converted to an extended partition which is just a container and then you can have an unlimited number of logical partitions inside the extended partition.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by lyokoheros on 2018-02-07
Sorry for that. It just... well in most forum I ever wrote i usually seen rather "Do not create unneeded new threads, ask in existing one", and that previous thread seem to be suitable...

Anyway thanks for answer and links, I hope they will help.

---

