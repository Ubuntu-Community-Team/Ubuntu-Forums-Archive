---
title: "Sharing folders"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by GreenfieldMark on 2008-06-06
I seem to be unable to share the folders I want to share over the network. Every time I select the folder I want to share, right-click and select 'sharing option,'and try to create a share, I get the following error: 
> 'net usershare' returned error 255: net usershare add: failed to add share public. Error was Operation not permitted

Any ideas on what to do about this?

---

### Post by spiderbatdad on 2008-06-06
Try running ```
gksu nautilus
```from the terminal. This will open a graphical file browser with admin privileges. Then navigate to the folders you want to share, right click, and select the various options.

Be careful using gksu nautilus, especially if you get into browsing root files. Changing the wrong things will break your system.

---

### Post by GreenfieldMark on 2008-06-07
Okay, I did that and from my main computer everything looks fine, but the other computers on the network (an Asus eee PC and an Ubuntu laptop) can't seem to see them. They see the computer, but that's it. 

I feel like I'm missing something here, but I'm not sure what. Could really use some help.

---

### Post by buntunub on 2008-06-07
If your trying to share your Ubuntu files with other Windows boxes and likewise, then you will be using Samba. Reference the Samba Wiki on Ubuntu Wiki for how to configure this. Samba is no easy beast to deal with often times, so I suggest you check out that guide. If your trying to share with other Linux boxes then you have a large array of options that are much simpler to deal with like NFS, SSH, and Fuse. You can setup SSH with your Windows boxes using PUTTY, or you can struggle with Samba.

---

