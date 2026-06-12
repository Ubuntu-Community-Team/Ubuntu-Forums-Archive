---
title: "Samba networking issues (filelocks)?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-21
I have setup a Ubuntu box at my work, one this box I have 1 Samba share, this samba share, share's a proprietary piece of software with multiple XP boxes, the software is based on [Visual FoxPro]("http://msdn.microsoft.com/en-us/vfoxpro/default.aspx").  

Before I setup the Ubuntu box this software was hosted on an XP machine via a Samba Share to the rest of the XP machines and all was well.  But now that I've moved the software to an Ubuntu box and setup a Samba Share on the ubuntu box, some of the clients are receiving an error message
```
invalid seek offset
```
After investigation of this problem ([Google]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&q=%22invalid+seek+offset%22&btnG=Search") ;) )  it is a network related issue.

So my samba share setup on my Ubuntu box is different than the old samba share on my XP box (for what ever reason, I don't know)?
Like I said this data is being accessed by multiple clients (3 at the most) at the same time, and I notice this error when multiple clients are connected.  So my assumption is there is a possible file lock issue where Samba is locking files that are being accessed by 1 computer which locks out the other users (but I could be very wrong)?

Are there any settings w/in Samba that might help me alleviate this problem?
TiA for any/all help,
-BassKozz

---

### Post by BassKozz on 2008-10-21
Question Moved: [http://ubuntuforums.org/showthread.php?p=6007123#post6007123](http://ubuntuforums.org/showthread.php?p=6007123#post6007123)

---

