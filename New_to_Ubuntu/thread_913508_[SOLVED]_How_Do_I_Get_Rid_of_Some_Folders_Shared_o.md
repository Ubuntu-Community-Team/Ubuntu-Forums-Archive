---
title: "[SOLVED] How Do I Get Rid of Some Folders Shared on a Windows Network?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-07
Here's my problem... I was messing around trying to share my Ubuntu desktop so my wife could see it from her Windows 2000 PC. In the process I "shared" my desktop twice - and I gave it two different share names. I finally got my desktop shared so she can see it from her Windows PC, but I have it shared with two different names - and they BOTH appear on the list of folders she can access. 

When you share the same folder twice - with 2 different names - how do you get rid of one of them?

Thanks!

---

### Post by bobsmith2 on 2008-09-08
Can someone help with this? I'm unclear if this type of question should be in the "absolute beginners" forum. I'm an advanced user in Windows, but a beginner with Linux. Should this be posted on another forum?

---

### Post by whitethorn on 2008-09-08
I'm guessing you used samba to share the folders.  Try looking at your smb.conf

```
gksudo gedit /etc/samba/smb.conf
```

Look at the end and see if your shares are in there, if they are then you can just remove the one line.  

If not, open Nautilus right click on your Desktop folder go to the share tab and remove the share, this should get rid of one.  If nothing shows up, then try starting nautilus as root

```
gksudo nautilus 
```  repeat above.

---

### Post by bobsmith2 on 2008-09-08
Whitehorn you are awesome! That's twice you have dug me out of a problem today. You're solution worked perfectly and is something I wouldn't have  come close to figuring out myself. I am extremely grateful.

Actually I ended up using BOTH of your suggestions. Sure enough, at the bottom of the smb.conf file was one of them. I blew it away and it disappeared. I actually had a desktop shared under root too - and when I did as you suggested, I was able to "unshare" it and it went away too. So now I'm set.

Thanks again.

---

