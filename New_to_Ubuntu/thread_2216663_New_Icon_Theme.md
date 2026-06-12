---
title: "New Icon Theme"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by salmichaels on 2014-04-13
I have a folder full of nice new icons I'd like to use sitting on my desktop. Not sure hot to get them working though. 

I'm using Ubuntu 13.04 with gnome fallback. 

thanks!

---

### Post by Frogs Hair on 2014-04-13
First ,  Install a supported version of Ubuntu such as 13.10 rather than customizing an unsupported operating system . 

 Extract the package and place the folder on the desktop . 

Open  the terminal and and enter the following.  ```
gksudo nautilus 
```
Navigate to computer- usr- share-icons in the file browser. 

Drag the folder from the desktop to the icons folder and close.

A tool such as Unity Tweak or Gnome Tweak will be needed to apply the new icons.

---

### Post by salmichaels on 2014-04-13
> First ,  Install a supported version of Ubuntu such as 13.10 rather than customizing an unsupported operating system .

No. I tried 13.10 and I could not find a way to make Gnome 2 work on it. I don't like Unity, and Gnome 3 makes me wanna puke. So unless you can think of a way . . . and no, installing Gnome Fallback did not cut it. It kept reverting back to Gnome 3 or something 3ish, and that annoyed me so much I considered going back to Windows. 

Otherwise, thanks for your help.

---

### Post by Frogs Hair on 2014-04-13
There is security risk running 13.04 without updates and it is based on Gnome 3.6, so you must be referring to the fall-back session rather than Gnome 2. Perhaps you can try 14.04 when it is released  next week which is supported for 5 years . 14.04 has Mate based on Gnome 2 in the repository as an alternative desktop.

---

### Post by salmichaels on 2014-04-14
At the risk of steering this topic off course . . . lemme ask: is there any really serious security risk in running 13.04? I  mean given in %, what is the likelihood of a problem, based on actual  data? 

I had 13.10 installed but even Gnome Fallback was like . . . not the Gnome I know and love. I know there's a bicker about Gnome 3 going away from 1 and 2, and looking like a dang smartphone. If some people like that, it's fine. Truthfully, it's just as much about aesthetics as functionality for me. Is there any way to have the latest thing with good old Gnome?

I did try MATE. I just . . . didn't like it. 

BTW your icons advise worked famously, thank you.

---

### Post by MystaMax on 2014-04-14
off topic: well the recent SSL [heartbleed bug]("http://heartbleed.com/") is pretty serious. I'm not sure, but 13.04 probably won't get those updates since support ended in January 2014.

I think ~/.local/share/icons works as well, and you don't need root. I haven't tested this.

glad you got it working!

---

### Post by vasa1 on 2014-04-14
> **MystaMax said:**
> ...

I think ~/.local/share/icons works as well, and you don't need root. I haven't tested this. ...
I use **~/.icons**.

---

### Post by Frogs Hair on 2014-04-14
Glad the icons worked , .icons also works well also for a single user system.13.04 will not get updates for any software including Firefox and it's your choice what you want to use.

---

