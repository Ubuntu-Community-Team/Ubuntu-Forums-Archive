---
title: "[SOLVED] File and file labeling - a bit more than you think"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by SilverShadow118 on 2008-11-05
Hello, I've been running Ubuntu on my system for a little over a month. I've got to say: I love it. Though, I do have many questions. You see, theres a part of me that screams "WINDOWS", but I know that the logical part of me is in Ubuntu. The only problems I've had with Ubuntu is the transition. Mainly when it comes to file labeling and dev's. What does it all mean? Why is it I have a "cdrom" and "cdrom0" and a "floppy" and a "floppy0" when I don't even have a floppy drive installed? What partition is Ubuntu installed on (I messed up with labeling and got confused ^_^)? What are the folders labeled "opt", "srv", "proc", "initrd" ect. for? What purpose do they serve? Is there a purpose as to what these folders do and why they're labeled that way? Is there a cross-reference comparison for previous Windows users out there somewhere? Such as: What files are the equivalent to a .exe in Ubuntu? Any help is appreciated and loved. Thank you ^^

---

### Post by hashimoto on 2008-11-05
Maybe this will help:
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by hyper_ch on 2008-11-05
there is no equivalent of ".exe" in linux.

Linux does not care what file extension a file has to determine whether it is an executable. It all depends on the file permissions given to a file.

---

### Post by FrostyFlames on 2008-11-05
For the most part each one of those houses a specific kind of information.
/proc = virtual file system that holds information on the system, memory, and processes currently running 
/home/<username> = basicaly your "My Documents"
/dev = devices which include CD/DVD, hard drives, USB thumb drives, and other storage devices
/var = variable folder, mostly stuff that changes is put here
/tmp = temporary folder
/sbin = houses executable files for users (there are several places that hold these and this is just one, think of it like "Program Files")
/lib = library (equivalent would be .DLLs on windows)
/mnt = where devices are mounted (not to be confused with /dev which is the physical device)
/media = the newer place where stuff is mounted (USB drives, CD-ROMS, network shares, etc)
/boot = houses the GRUB boot information and the Linux Kernel
/etc = configuration folder (think of these as the .ini or .cfg files in windows)

---

### Post by SilverShadow118 on 2008-11-05
^_^ Thanks Guys

---

### Post by ad_267 on 2008-11-05
You don't really need to know any of that stuff just to use Ubuntu. To access your drives/devices just click on the Computer icon. Anything else should stay within your home directory. The package manager takes care of the rest of the file system.

---

### Post by Kellemora on 2008-11-05
Hi SS

It's actually much simpler than the DOZE!

If you've ever gone into your Windows hidden folders you will see thousands of files all jumbled together in one big mess.

In Linux, everything is Logically situated!

It does take only a short time to learn what each folder is for, but most of them, just like in the Doze, you will never have a need to get into.

I'm 61 years old and have picked up on Ubuntu fast enough in less than one month that I converted my whole office to Ubuntu except for one computer used in accounting.
Production levels have increased considerably as well, once everyone got used to the LOGICAL way of doing things.

If you NEVER used a computer or even a Word Processor before and had not already learned the Doze, you would find Ubuntu to be GREAT and easy to learn.

Look at msWORD as an example, if you wanted to reformat the page you are working on, where would you LOGICALLY look for the controls?

Would you Look Under Format (where formatting belongs) or under File (which has to do with handling the whole file system)?

Well in msWORD, you look under file to format your page settings.
In Open Office Writer, you look under Format, where one new to using a word processor would logically assume it should be.

So if you are used to some of the backwards things in the Doze, then YES it will take a little getting used to having things WHERE THEY BELONG, hi hi.......

BUT, by the same token, if you never used a word processor before, you would find that just thinking logically about where something should be, you can find it easily and quickly.

As far as files and file labeling, your original topic.
Think of /home/user with user (meaning you) as being the C Drive.
Other than System Files, everything else you create is in your User directory.  

In the Doze when you select My Computer, you see the drives installed in your computer.  Same thing with Linux, select Computer and you see the drives in the computer ALL OF THEM.  With one exception, in Linux each DEVICE is shown as a FOLDER in the /root directory.
In Windows, they are all hidden in the Windows System Directory.

Give it another month and you'll be on the way to becoming a PRO!!!!!

TTUL
Gary

---

### Post by harsh1kumar on 2008-11-05
Dont worry man about all the strange and different names you see in ubuntu. Just use your system for some time, you will come to know all.

If your problem is solved then please mark solved. :guitar:

---

