---
title: "/boot too small"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by d4ng3r on 2008-06-10
So I am running a dual boot Hardy/XP system, and to do this I followed some tutorial on the internet that told me to set up my partitions as:
Windows
/ for Ubuntu
Swap
/Boot - 50mb
So I did that, problem is today an update was released that apparently changes something with the boot, but 50mb is too small for this update, so it gives me an error and stops the update.  Now every time I try to run apt-get or something of the sort, it tells me 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'  and when I run that command it yet again tells me there is no space left on the drive.

Any thoughts?

Thanks
-Brian

---

### Post by immerohnegott on 2008-06-11
My guess is that it's trying to install a new kernel update, which places a kernel image and a few other files in the /boot directory. From looking at my /boot, each kernel added will take up about 20 mb of the /boot directory (a kernel image @ about 7 mb, a backup of that @ 7mb, a vmlinuz file @ about 2 meg and a system.map file @ about a meg, plus a smaller config file), which means a 50mb partition isn't going to cut it if you have more than one (maybe two) kernel(s) installed. If you've updated the kernel once, and the older one isn't being used, you should be able to delete the files associated with it to save some space. If not, then my ability to help sort of runs out, as I'm still kind of a noob myself.

You COULD theoretically delete the files referenced by your current kernel from /boot, then run the updater. It should then install a new kernel and update GRUB, but keep in mind if you try that and it fails, your system will not boot, as there won't be a kernel image to load. 

Personally, I've been dual-booting my systems since I first started using Ubuntu a few years back, and I've never used a /boot partition. Some people prefer it that way, but your system will still work fine if you have one partition for linux with a /boot folder in the main directory (the ubuntu installer sets this up for you automatically if you just choose the one "/" partition at install). If you don't have a lot invested in your Ubuntu install, you might consider reformatting your drive and either A) resizing the /boot partition to a couple-hundred meg, or B) deleting your /boot and / partitions and creating one new / partition to install to.

---

### Post by snkiz on 2008-06-11
Same thing happened to me. I deleted the old kernel and all the backups (Boot will regenerate the ones it needs.) Then run: sudo dpkg configre -a And next time be sure to uninstall old kernels before updates you should be ok. Btw 50mg is enough for 2 kernels

---

### Post by amanda on 2009-11-10
I'm  in the same boot boat. I don't have enough space and I'm anxious about what is essential and what is non-essential. I have 9 versions in there.

---

### Post by falconindy on 2009-11-10
If all you're running are the generic kernels that get passed down through the repos, you shouldn't need to keep more than the latest plus the one prior. If a few weeks go by and you haven't had any problems, you could even go as far as to only keep the current. You should **always** keep at least one vanilla kernel around if you roll your own.

---

