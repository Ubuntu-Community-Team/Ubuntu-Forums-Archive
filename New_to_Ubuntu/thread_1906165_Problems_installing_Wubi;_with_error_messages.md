---
title: "Problems installing Wubi; with error messages"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by mitsulancer91 on 2012-01-08
I'm trying to install ubuntu on my laptop which is running windows xp 32 bit, i have 705mb of ram. my issue is that when i use the windows installer that is provided all goes well until i reboot my dual boot window pops up and gives me the option of windows or ubuntu. I have tryed installing it twice, i get the same error messages with the second time i installed having a little more detail.... my first time went like this: Try (Hd 0,0) NTFS5 error "prefix" not set..... then it went in to a grub command prompt thing and i had to shut down and re boot in to windows. i un and re installed ubuntu but before i reinstalled i ran chkdsk c:/f amd chkdsk c:/r.... than i reinstalled ubuntu and tried to run it in the dual boot menu and this is what i got........ NTFS5 error "prefix" not set uncompression error _ _ system Halted:confused::confused::confused: i have no idea what to do and i really want a new OS since windows in giving XP the bird in 123 or so days, so no more updates:(

---

### Post by Rubi1200 on 2012-01-08
> **mitsulancer91 said:**
> I'm trying to install ubuntu on my laptop which is running windows xp 32 bit, i have 705mb of ram. my issue is that when i use the windows installer that is provided all goes well until i reboot my dual boot window pops up and gives me the option of windows or ubuntu. I have tryed installing it twice, i get the same error messages with the second time i installed having a little more detail.... my first time went like this: Try (Hd 0,0) NTFS5 error "prefix" not set..... then it went in to a grub command prompt thing and i had to shut down and re boot in to windows. i un and re installed ubuntu but before i reinstalled i ran chkdsk c:/f amd chkdsk c:/r.... than i reinstalled ubuntu and tried to run it in the dual boot menu and this is what i got........ NTFS5 error "prefix" not set uncompression error _ _ system Halted:confused::confused::confused: i have no idea what to do and i really want a new OS since windows in giving XP the bird in 123 or so days, so no more updates:(
Hi and welcome to the forums :-)

Please start your own thread in future since no two problems are exactly alike and it makes it much harder for us to provide help.

Thread moved and thanks for understanding.

---

### Post by bcbc on 2012-01-08
> **mitsulancer91 said:**
> I'm trying to install ubuntu on my laptop which is running windows xp 32 bit, i have 705mb of ram. my issue is that when i use the windows installer that is provided all goes well until i reboot my dual boot window pops up and gives me the option of windows or ubuntu. I have tryed installing it twice, i get the same error messages with the second time i installed having a little more detail.... my first time went like this: Try (Hd 0,0) NTFS5 error "prefix" not set..... then it went in to a grub command prompt thing and i had to shut down and re boot in to windows. i un and re installed ubuntu but before i reinstalled i ran chkdsk c:/f amd chkdsk c:/r.... than i reinstalled ubuntu and tried to run it in the dual boot menu and this is what i got........ NTFS5 error "prefix" not set uncompression error _ _ system Halted:confused::confused::confused: i have no idea what to do and i really want a new OS since windows in giving XP the bird in 123 or so days, so no more updates:(
From searching the forums it appears that this error may be caused by some bad RAM. You could rule this out by running memtest86 from an Ubuntu CD.

---

### Post by mitsulancer91 on 2012-01-08
> **bcbc said:**
> From searching the forums it appears that this error may be caused by some bad RAM. You could rule this out by running memtest86 from an Ubuntu CD. i dont have a ubuntu cd plus i just bought a brand new 512 ram card and the 246 something ram card work(S)ed fine, any other ideas?

---

### Post by halitech on 2012-01-08
personally, forget about wubi. Unless it has gotten vastly better then they were, not worth the time (and yes I know it is officially supported)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

once you have the iso downloaded, burn it as slow as possible, Defrag windows a few times then reboot from the cd and choose along side windows

---

### Post by bcbc on 2012-01-08
> **mitsulancer91 said:**
> i dont have a ubuntu cd plus i just bought a brand new 512 ram card and the 246 something ram card work(S)ed fine, any other ideas?

If you just added RAM then it's definitely worth checking. You can download an Ubuntu CD ISO from that link *halitech* provided and then create either a CD or bootable USB from which to run the check.

---

