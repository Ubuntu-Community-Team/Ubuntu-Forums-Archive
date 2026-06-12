---
title: "[SOLVED] Force mount"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-06-05
hi i was wondering if anyone could help me here - my friends windows machine crashed and now his windows os wont boot when the computer is put on.

i was wondering if i could use the ubuntu live cd(which does boot in his computer)to load his internal hdd so he can get his data onto an external hdd and then reboot his machine.

if someone could help me with this i would b very grateful!

---

### Post by Paqman on 2008-06-05
Yep, very doable indeed.

Just boot into the LiveCD and mount the Windows drive (Places > Computer) and you'll be able to copy data over to your external drive.

---

### Post by rraj.be on 2008-06-05
Yes.

You can.Just get into live cd and mount windows partition.

Then you can copy any thing from it including the personal my documents if they are not destroyed by windows.

---

### Post by Xiong Chiamiov on 2008-06-05
A distro called Knoppix got really popular (and boosted the idea of Live CDs) by being a live CD filled with all sorts of recovery tools.  That's one of the nice things about not having to verify your OS with the manufacturer - you can run it completely off of a CD/flashdrive/floppy/RAM/toaster.

Good luck!  I know losing access to data is a very hard thing indeed, but at least it's not lost, yes?

---

### Post by betterthanjordan79 on 2008-06-05
yh i tried that but when i do that i get an error like

"cant mount media"

and goes on to tell me about how windows had a bad shut down etc...

---

### Post by betterthanjordan79 on 2008-06-05
> **Xiong Chiamiov said:**
> A distro called Knoppix got really popular (and boosted the idea of Live CDs) by being a live CD filled with all sorts of recovery tools.  That's one of the nice things about not having to verify your OS with the manufacturer - you can run it completely off of a CD/flashdrive/floppy/RAM/toaster.

Good luck!  I know losing access to data is a very hard thing indeed, but at least it's not lost, yes?

ok so if i download it will it force mount the hdd so i can read the data off it.

and yes it is there because its only wen windows it loadin it crashes meanin that the data is not all lost

---

### Post by Xiong Chiamiov on 2008-06-05
Hmm, sounds like some interesting things are going on with your filesystem.  I haven't had to deal with that, really, so I can't tell you anything definitive.

If you have a windows disk from Microsoft, many things can be fixed by doing a repair install.

---

### Post by rraj.be on 2008-06-05
Try force monut using this

```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
```

---

### Post by Paqman on 2008-06-05
> **betterthanjordan79 said:**
> yh i tried that but when i do that i get an error like

"cant mount media"

and goes on to tell me about how windows had a bad shut down etc...

If you read through that whole error message, it gives you a command that you can throw into the terminal to force that NTFS partition to mount.

---

### Post by betterthanjordan79 on 2008-06-05
> **Xiong Chiamiov said:**
> Hmm, sounds like some interesting things are going on with your filesystem.  I haven't had to deal with that, really, so I can't tell you anything definitive.

If you have a windows disk from Microsoft, many things can be fixed by doing a repair install.

i did try this aswell with the repair install but i had no luck with it all all. i no ya can force mount usb hdds by puttin in

> sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

is there anything similar i can do for internal hard drives?

---

### Post by pmlxuser on 2008-06-05
Use the windows OS disk to start to the recovery console do
"chkdsk  /f " or something like that. it repairs the errors that the hard disk might have. or just do chkdsk ? / something like that am forgeting the windows commands but within the recovery console there are ways to get al the command that you can perfome using chkdsk.

---

### Post by rraj.be on 2008-06-05
The same can be used for any drive whether its internal or external just by mentioning the device path correctly.

---

### Post by rraj.be on 2008-06-05
Its not safe to repair a system that was crashed without having backed up the data
because

```
It may lead to further more disaster
```

Than trying to repair the system that was crashed just try to 

```
Back up your data first
```

Because you can reinstall a OS back in hour.

But very difficult to  retrive data thats lost.

---

### Post by betterthanjordan79 on 2008-06-05
> **rraj.be said:**
> Try force monut using this

```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
```

hi man-i just tried that and it worked 100%!!

thank you so much man-ur the best!!

---

### Post by rraj.be on 2008-06-05
There are many Geeks here but i am not.If any post is really help full and if you want to thank any one just you can click the medal symbol at the  bottom right of each posts.

If any Problem is solved then

```
MARK IT AS SOLVED.
```

To mark solved go to 

```
Thread tools at the top and click it and select MARK THIS THREAD AS SOLVED.
```

Mark it always when your problem is solved.

See my signature for more info.

---

### Post by betterthanjordan79 on 2008-06-05
all is done rraj.be!! thanks again!!

---

