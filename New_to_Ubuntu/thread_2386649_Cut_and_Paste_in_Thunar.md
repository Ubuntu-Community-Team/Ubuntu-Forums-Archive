---
title: "Cut and Paste in Thunar"
date: 2018-03-08
forum: New to Ubuntu
---

### Post by xipho2 on 2018-03-08
Hello, 

I cut a folder from a flashdrive (a), and want to paste it into a flashdrive(b). At first I tried that via mouse over the b-icon on the left pane, "paste". Impossible. I opened b, but there are folders. But I did not want to paste the folder into a folder. Impossible, too. How to get that done? As a first aid, I created a folder and pasted the folder into that folder. 
Further: How to display "Properties" via context menue?
Thanks for your hints!

---

### Post by #&amp;thj^% on 2018-03-08
Do you mean to say that right click on the folder/file dose not show properties as an option?
And you can also view more information with:
"stat <your folder/filename>"
IE:
```
stat Videos
  File: Videos
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 18087946    Links: 2
Access: (0755/drwxr-xr-x)  Uid: ( 1001/      me)   Gid: ( 1001/      me)
Access: 2018-02-02 18:02:15.261878101 -0700
Modify: 2018-03-07 10:22:04.599332415 -0700
Change: 2018-03-07 10:22:04.599332415 -0700
 Birth: -

```
And what Version of Xubuntu being used?
```
lsb_release -a
```
I suspect possibly a read/write issue with the USB drive or Drives
If you could be less vague and more descriptive, it would help you to draw more users to help you. :)

---

### Post by xipho2 on 2018-03-08
16.04.4 LTS. I tried the right click for the flash drive icon on the left pane. I wanted to know how much space is left. Did not work. Just by dumb luck I found a mouse over is doing the trick. Nevertheless: Are there other ways? Just a click...?

---

### Post by #&amp;thj^% on 2018-03-08
> **xipho2 said:**
> 16.04.4 LTS. I tried the right click for the flash drive icon on the left pane. I wanted to know how much space is left. Did not work. Just by dumb luck I found a mouse over is doing the trick. Nevertheless: Are there other ways? Just a click...?

Assuming your using thunar as the file manager click or mount the USB and at the bottom it will show remaining space.
And using the Disk Utility will also show the same
See Screenshot.
EDIT: BTW if the USB is formatted to fat32 and the folder your trying to move or copy over to the next USB drive is over or around 5Gigs that will cause you to see errors. (That's a known limitation with Vfat or fat 32)

---

