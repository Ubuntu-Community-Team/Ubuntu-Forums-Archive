---
title: "Can I Access my Existing Files Through the Installation Disc?"
date: 2017-04-05
forum: New to Ubuntu
---

### Post by random turnip on 2017-04-05
I have an old HDD plugged into a working laptop with the Ubuntu installation DVD.  Can I access the files on the HDD through this DVD's 'Try Ubuntu' mode?

I'm looking at File/Computer, but not sure which of the many folders would be right to check?

I'm planning on installing Ubuntu on here anyway, but would like to try and save a few pictures ect. on here first.

Thanks in advance.

---

### Post by ajgreeny on 2017-04-05
The partitions on that old disk should show in the left hand pane of the file-manager as separate volumes or Places, but I am not sure how they would be named, they may just show as **##GB-volume** or using the partitions' labels, if they were labelled. They may also show on the desktop of your live OS, depending on which DE it uses.

You will probably be able to read most but not all the files on the disk, but if you need to copy any of them to, for example another USB drive, you will have to do so as root I believe.

---

### Post by random turnip on 2017-04-05
It seems I've not got access to get into the root.  How do I change this?  I'm pretty rusty on using Ubuntu.

I found a bit of a guide but none of the commands to do with Nautilus (i'm not even sure what this is to be fair) don't seem to be working.


Tried all commands in this thread to no avail...
[https://ubuntuforums.org/showthread.php?t=1773244](https://ubuntuforums.org/showthread.php?t=1773244)

---

### Post by random turnip on 2017-04-05
OK, so I've stopped being stupid and appear to have gotten into the Root folder, but it's just a link back to the desktop, WTF?

Is this something to do with not having GKSU installed?  I can't seem to install it if it is.

---

### Post by cmcanulty on 2017-04-05
Install gparted to see all the drive locations and what  files systems. Also pmount is a useful tool to mount drives without sudo.as long as they are mounted RWX you should be able to deal with them easily I think the command is pmountb then the path to the drive like /def/sdb1 or similar once mounted it should be easy to access the files

---

### Post by random turnip on 2017-04-05
Thanks for the response.
I;ve loaded GParted and it seems to think the HDD has only 1.45gb.

How can I save a screenshot as a file and upload?  What would be the equivalent of Paint?

---

### Post by yancek on 2017-04-05
Nautilus is the file manager in a standard Ubuntu install.  If you want to copy files/pictures from the installed hard drive, why do you think you would need to be root?  If you want to write to the HDD you would need it but not to simply copy from.  Drive partitions should be available under the /media/ubuntu directory by UUID.  You'll just have to look at the different ones to find the one you want.

To get a screenshot with standard Ubuntu, click on the Dash and type in screenshot or type it in a terminal and hit enter to see if it opens.  I'm not  really sure if it is on the install DVD but I'm pretty sure it is.  Try it.

---

### Post by random turnip on 2017-04-05
Under media I only have a folder called cdrom

So these are what I have in files and GParted...[ATTACH=CONFIG]274443[/ATTACH][ATTACH=CONFIG]274444[/ATTACH]

I'm starting to wonder if the HDD is working properly...

---

### Post by yancek on 2017-04-05
The image you posted of GParted is only showing the DVD so you need to click the down arrow in the upper right next to /dev/sr0 to see if your hard drive is seen.  If you don't see anything besides the DVD, then your hard drive is not being detected for whatever reason.  In Nautilus, you should see a link to cdrom plus an ubuntu directory with sub-directories for partitions under /media/ubuntu.  Also on the left panel in Nautilus, you should see Devices which would show your drive partitions.

---

### Post by random turnip on 2017-04-06
Ah, all there was in the drop-down was the cd Rom. I did swap the hdd with another, so i'll check its in properly when I'm home, but surprised I'd be able to shut it all up if it wasn't in properly though. Annoying i spent all that time last night trying to make that work when it was probably just not plugged in properly.

Thanks for the help.

---

### Post by yancek on 2017-04-06
Checking connections is usually the first thing to check when you're moving or attaching different dirves.  Easier with a Desktop than a laptop though.

---

### Post by random turnip on 2017-04-07
It was indeed not plugged in properly, kinda silly of me.  Plugged it in properly, booted up and not only recognised the HDD but let me boot into the existing Ubuntu partition on there no problem, so can easily rescue my files and format.  Pity it's still on a really old version so I can't even update directly.

Thanks for all the help guys, will mark this as solved.

---

