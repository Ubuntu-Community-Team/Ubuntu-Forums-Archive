---
title: "How do you unmount an external harddrive thats stuck?"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by CrimpJiggler on 2011-12-18
My external harddrive won't unmount at the moment so I tried diagnosing the problem with the terminal and heres what it said:
> crimpjiggler@laptop:/var/log$ sudo umount /dev/sdb1
umount: /media/Verbatim: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8\) or fuser(1))
NOTE: ^^ I had to add a \ after the 8 because the forum kept converting it into a smiley. 

Then I tried running umount -f but I got the same "device is busy" error message. I tried running lsof(8\) but it gave me a syntax error so the terminal obviously wasn't telling me to run the  (8\) part. What does the terminal mean when it adds (8\) after the command like that? 

So I learned a bit about this lsof command and ran it on the external harddrive and heres what happened:
> crimpjiggler@laptop:/var/log$ sudo lsof /dev/sdb1
[sudo] password for crimpjiggler: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/crimpjiggler/.gvfs
      Output information may be incomplete.
I don't know what any of that means. I don't know if that even gives me any info about why the harddrive won't mount or if thats just an error with the lsof command itself. I just tried running "fuser -m /dev/sdb1" but it didn't do anything. 

Can anyone inform me as to how to deal with a situation like this where your external harddrive won't unmount normally? Normally I'd just physically unplug it but that seems like a destructive way to do it so I'd prefer to do it properly. I'm guessing I just need to find out what program is preventing me from unmounting it then killing it. How do I find out what program is using the drive though?


UPDATE: I just remembered that when I was transferring a video to the external harddrive, it got stuck half way. Thats obviously the problem so I ran "pgrep nautilus" and see that it is still running despite me not using it at the moment. I tried running "kill 1723" and also tried "pkill nautilus" but they won't do anything for some reason. I get no error message but when I run pgrep nautilus again, I see its still running. How can I force a process to shutdown?

---

### Post by TeoBigusGeekus on 2011-12-18
```
killall -9 nautilus
```
It will send the 9 signal (SIGKILL) to nautilus.

---

### Post by CrimpJiggler on 2011-12-18
I restarted my computer but I'll try that next time, thanks.

---

### Post by TeoBigusGeekus on 2011-12-18
You're welcome. I hope there was no data loss.

---

