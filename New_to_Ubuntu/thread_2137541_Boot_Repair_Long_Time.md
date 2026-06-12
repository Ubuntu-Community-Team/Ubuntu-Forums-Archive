---
title: "Boot Repair Long Time"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Pondweasel on 2013-04-21
Is the boot repair supposed to take 13minutes+? (still counting)

I ran into some boot issues and this was the recommend course of action and I have been watching it for a while,
am I just being inpatient or has something gone wrong?

---

### Post by oldfred on 2013-04-21
If the issue is a partition with corruption and it cannot mount it, it may stall. It should timeout and complete but there are cases where certain commands just do not end. Boot-Repair is really running a bunch of Linux commands an writing to log files. It also tries to write BootInfo report to Internet. So if it cannot write or get to Internet it may have issues also. I think Yann tried to fix most of those as it has occurred before and he has made some fixes for that type of issue. 
Did you let it update to the newest version?

I have lots of drives and many partitions and it does take a few minutes on my system, but I think you may have larger issues.

Were you just running BootInfo report or actual fixes?

You can try running just the bootinfoscript which is the first part of BootInfo report. It just saves to file on your system. But it may be the issue??
       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

