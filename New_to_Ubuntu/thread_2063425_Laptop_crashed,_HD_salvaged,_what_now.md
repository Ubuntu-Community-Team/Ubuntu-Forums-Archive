---
title: "Laptop crashed, HD salvaged, what now?"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by mudjee on 2012-09-27
Hi 

Recently my old laptop blew up (mother board I think) but I have salvaged the HD and have installed it in a external HD case. I was running ubuntu 12.04 on a HP pavilion tx1000. I used to have vista on it (nuff said), it crashed so much and thats why I recovered it with ubuntu. 

I have just upgraded to a ASUS Eee PC netbook with windows 7 ultimate (2 GB ram, AMD E-450 APU with Radeon HD graphics, 1.65 Ghz) and to tell the truth I am glad to be back on a system where everything works as it should as I had no end of problems trying to get everything to work in linux, mic, vga out etc etc on the old HP

So my question is: I would like to get my info back off the HD but assume I need to install ubuntu as a dual boot to access the external HD because it wont show up under 'my computer' in windows. I have seen some tutorials on youtube and it seems straightforward enough, I would probably install it on a flashdrive and boot from there to keep my windows OS separated. 
So
-Is there a method of retrieving the files without installing ubuntu?
-If I do install ubuntu to retrieve the files, how do I get them into a format that suits windows? (at the moment I cant access the HD, windows wont recognise the device)
-Is there a better option for a netbook, such as Linux mint maybe, I researched that OS and it looks like it may be more laptop friendly......

Thanks for any help, I just want my info back!

cheers

Dean

---

### Post by shreepads on 2012-09-27
- Create a bootable USB stick with Xubuntu 12.04.1
- Boot into Live session with that. DO NOT start the install process at any time
- Connect your external HD with the old disk, should automount if USB, Else will need to mount by clicking the relevant icon in Nautilus
- Mount the local windows HD (NTFS) again by clicking the relevant icon in Nautilus (NB: This needs the ntfs-3g package, install from software centre/ synaptic if not already installed in the Live session)
- Copy relevant files from old to new using Nautilus/ command line cp/ rsync

WARNING: Win 7 partitions mounted via ntfs-3g and written to, need to be safely unmounted and may develop errors

Failsafe way:
- If you have another external HD with same or more capacity, boot Win 7, format that to NTFS. Then boot Xubunti 12.04 live session, mount both old and new external HD (again this needs ntfs-3g) and copy necessary files
- Boot Win 7, copy from new external HD to Win 7 HD

---

### Post by mips on 2012-09-27
Install this [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) in windows7 and it will give you read access to your hard drive and allow you to copy files across. It's the fastest/simplest way I can think of doing it right now.

---

