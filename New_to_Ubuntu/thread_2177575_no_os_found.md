---
title: "no o/s found"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by c_blascsok on 2013-09-29
Feeble cry for help! I accidentally deleted the hidden files on my laptop that carried the reset information to ubunto 12.4. I was trying to delete the main partition so I could reformat into ntfs to load windows 7. Now I keep getting a screen that says "no operating system found, no bootable devices"
 I downloaded a copy of ubunto and tried installing it via usb and a dvd but with no luck. It still can't find any bootable devices. (I reset the bios to allow them to go first ). 
So now I'm stuck. Windows won't load because it doesn't recognize the format, ubuntu won't load because ????????
Help?

---

### Post by Petro Dawg on 2013-09-29
Sounds like a good candidate for Boot-Repair,  try it first...

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by whitesmith on 2013-09-29
+1 to Petro Dawg. Boot repair will provide you with a URL when it finishes running. Post it here for analysis.

---

### Post by c_blascsok on 2013-09-29
Downloaded boot repair to a usb, system still asks for a bootable device. In other words, I can't get it to load.

---

### Post by Petro Dawg on 2013-09-29
Can you boot a live CD (or USB) of Ubuntu, just like you did when you installed Ubuntu?

If you can get a live version of Ubuntu running, you can then install and run boot-repair from there.

---

### Post by c_blascsok on 2013-09-29
Thanks for replying. Ubuntu came pre-installed. I've tried installing a downloaded version but it won't load. There were 3 partitions on the pc originally. the first was the hidden one (about 11gb) The second was the main hardrive (485gb) and the third is 4 gb with ubuntu files. 
I wanted to format the second drive so I could load windows. Ubuntu wouldn't let me format it as it was in use at the time. There was a delete option available so I tried that, but somehow in the process it deleted the first drive by mistake. I haven't been able to load anything on the machine since. It won't even let partitioning tools from a usb load. 
It will, however, let windows7 setup as far as the partitions window, where it can't go any further. Why won't it let ubuntu on as that's what the hard drives are still formatted for?

---

### Post by Petro Dawg on 2013-09-29
It seems we need to start ruling out some things...

First, how exactly are you making the Ubuntu or Boot-repair disks/USB?  Are you using Unetbootin or something else?

If you are making USBs perhaps you are missing a step somewhere to make it bootable.  I suggest the simplest solution of downloading an [Ubuntu12.04 32 or 64 bit]("http://www.ubuntu.com/download/desktop") (which ever is appropriate for your system) or [Boot-repair disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") ISO image and burn it directly to a CD.

---

### Post by c_blascsok on 2013-09-29
The ubuntu was downloaded on my other computer (windows) as a zip file first to a dvd. This didn't work so I  unzipped the files, put them in a new folder then burned that folder to a new dvd using a programme called Express Burn. 

That didn't work either - wouldn't boot. The boot repair I downloaded , unzipped the files, then transferred the new folder to a usb stick - still wouldn't boot. I unzipped the files because I thought that with no operating system present, the computer wouldn't be able to get the files unzipped without a rar programme. (or can it?)

At this point I would be happy to be able to completely reformat my hard drive then try a new installation (it's a new machine so there is nothing on it), but I can't find a way to delete the ubuntu coded partitions to reformat into nfts, and it's not allowing anything to boot (like a partition manager style programme).

---

### Post by Petro Dawg on 2013-09-29
I don't believe simply transferring unzipped folders to a USB drive will work.  These downloads should be just ISO image files, nothing more, nothing less.

If you are dead set on using a USB, boot-repair suggests using [Unetbootin]("http://unetbootin.sourceforge.net/") to create the bootable USB from the ISO image.

---

### Post by c_blascsok on 2013-09-30
Okay it's fixed. I managed to burn the boot repair iso image direct to a dvd. created a new partition, formated, then installed a new o/s.

Thanls Petro Dawg for your help and patience.

---

