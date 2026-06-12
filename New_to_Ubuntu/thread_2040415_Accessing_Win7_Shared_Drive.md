---
title: "Accessing Win7 Shared Drive"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by kublait on 2012-08-11
Hi all,
I'm totally new to Linux.  I recently installed Lubuntu 12.04 on a 8 yrs old laptop and just love the performance.  

Here's what I'm trying to accomplish.  My primary computer is a Windows 7 Ultimate 64 bit with an attached external drive.  The Win7 box have a static IP of xxx.xxx.xxx.150 and I've also shared out external attached drive as "BlacX".

I'm trying to access the external drive on the Win7 box via my Lubuntu laptop. 

I used Alt+F2 and "smb://xxx.xxx.xxx.150/blacx".  The error message I got is:
Failed to execute child process "smb://xxx.xxx.xxx.150/blacx" (No such file or directory)

I'm not sure where to go from here.  Any help will be greatly appreciated.

---

### Post by daimaru on 2012-08-11
sorry dumb question here. did you try smb://xxx.xxx.xxx.150/ , login and then browse to blacX ?

---

### Post by Bashing-om on 2012-08-11
Hi! ;
 My experience with file sharing is rather limited ... but,
-the simplest things first-
 is file sharing enabled on your lubuntu box ? (right click your share folder and choose the share option)

---

### Post by kublait on 2012-08-11
Hi Daimaru - Thanks for the suggestion.  I tried to smb to just the IP address and received the same error message.  

Failed to execute child process "smb://xxx.xxx.xxx.150" (No such file or directory).

It's as if the Lubuntu laptop can't see the Win7 box.  I was able to successfully ping the Win7 box from the Lubuntu laptop and got replies.

---

### Post by kublait on 2012-08-11
Hi Bashing-om,
I don't have any files on the Lubuntu laptop that I'm trying to access.  It's the other way around.  I'm trying to access files on a Win7 box from the Lubuntu laptop.  The files on the Win7 box have all been shared out.

---

### Post by Bashing-om on 2012-08-11
kublait;
 Excuse me if I am in error. But does not SAMBA have to be enabled on the lumbutu laptop as client ? : As samba/server enabled on the windows box?
Have you looked at the community documentation [https://help.ubuntu.com/community/Samba/](https://help.ubuntu.com/community/Samba/) ?

---

### Post by Morbius1 on 2012-08-11
> I used Alt+F2 and "smb://xxx.xxx.xxx.150/blacx".  The error message I got is:
Failed to execute child process "smb://xxx.xxx.xxx.150/blacx" (No such file or directory)You're doing that as if you were running the equivalent from "Run" in Windows. It doesn't work that way in Linux.

Try this instead:

Alt+F2
pcmanfm smb://xxx.xxx.xxx.150/blacx

OR
pcmanfm smb://xxx.xxx.xxx.150

You need to invoke the file manager to interpret what a "smb://" means.

---

