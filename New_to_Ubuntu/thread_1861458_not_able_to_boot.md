---
title: "not able to boot"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by yogeshasd on 2011-10-15
Hello everyone,

I use unix in my research and usually have support from experts. To learn unix, I decided to  partition my lenovo T60p and loaded ubuntu 10.04 LTS. Since it was asking me to update, I did update to 10.10 and then tried 11.04. But during this some thing happened and system is not rebooting. When I choose 10.10 or 10.04, I got in to this screen msg

init: udevtrigger mainprocess (461) terminated with status 1
init: udevtrigger post-stop porcess (464) terminated with status 1
init: udevmonitor main process (460) killed by TERM signal.
The disk drive for  / is not ready yet or not present 
Continue to wait: or Press S to skip mounting or M for manual recovery
If i choose latest 11.04, a long msg started with

"[ 0.909620] Kernel panic - not syncing: VFS : Unable to mount root fs unknown-block (0.0)
[ 0.909671] pid: 1, comm: swapper not tainted 2.6.38-11-generic #50-ubuntu
[ 0.909617] call trace:................
.......................
 
I want to fix this and go back to 10.04 LTS or 101.10. I have installed lots of research related software and I have spent lot of time to install them as I am slowly learning unix. I have lot of data as well. I dont have backup. Could you please help me to fix this problem.

I did lockup for some information on Google but couldn't figure out which one is right.

I highly appreciate your time to help me.

Thanks
Yogi

---

### Post by oldfred on 2011-10-15
Welcome to the forums.

Anytime you make major system changes you need to have good backups. Plus hard drives fail, usually just before you planned a major backup.

Post this from a liveCD. 

sudo fdisk -lu

Did you do a multiple upgrade and did it work in between? Or did you do multiple installs?

---

### Post by critin on 2011-10-15
*<<Since it was asking me to update, I did>>*

I want to say 'just say NO! here' because regretfully,  I've done the same thing one time.  I haven't upgraded to 11.10 though.  When I do it'll be to a separate partition or disk all its own for testing.
 [I]
<<I did update to 10.10 and then tried 11.04>>[/I]

When you upgrade to the next os, you are basically writing over the os you're using, so there is a chance you'll lose your work.  Always back up and save it safely somewhere.  (I learned that the hard way too.)

It sounds like the first upgrade to 10.10 was successful, but the second to 11.10 was cut short somehow.  I'd bet Grub was lost/corrupted in the process.  I would try boot-repair via live usb/cd at this point.  It comes in very handy for me.

We learn best by our mistakes.

Good luck,  I'm sure your work is still there.  
critin

---

### Post by yogeshasd on 2011-10-15
Thank you both for the suggestions. I dont want to reformat. Critin, I have a CD od 10.04 LTS CD, is it possible to rescue the data. If so  could you please advise me in detail. This would save lot of data and time for me.

Thanks
Yogi

---

### Post by oldfred on 2011-10-15
It depends on where you are at and what is or is not installed. Can you currently mount the partition(s) from your liveCD?

If just a boot issue this may fix it or we can review boot script which boot repair will run or you can just download boot_info-script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

