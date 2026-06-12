---
title: "What does 'refresh' bascially do?"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by T.exe on 2011-11-27
When I started with computers back in the days with Windows 98, I always used to love the 'refresh' option provided by Windows.
In browsers ofcourse, refreshing is necessary to load the updated contents of a website. But, what is the purpose of 'refreshing'? When I moved to Linux, my curiosity grew even more when I found that Linux did not provide a 'refresh' option.

I have read in numerous forums that it updates the caches, icons etc. many even said it is useless (I find it hard to believe though).

Please help me understand the technical details behind the refresh option, and since Linux does not offer this facility, how is it handled in Linux???

Enlighten me!!!!

---

### Post by coffeecat on 2011-11-27
> **T.exe said:**
> But, what is the purpose of 'refreshing'?

If you're talking about refreshing the desktop, it's a mostly pointless ritual dating from early Windows days. On those rare occasions when you need to refresh the gnome/Unity desktop, try F5. Whatever you do, don't double right-click on the desktop! This is a habit some Windows veterans have for repeatedly and unnecessarily refreshing their desktops. If you do this in Ubuntu (and move the mouse fractionally between clicks) you'll cover your desktop in folders named "Untitled Folder", "Untitled Folder2", and so on. :)

---

### Post by CryptAck on 2011-11-27
I do think that a refresh option would be nice...even if I never use it. Nostalgia...

---

### Post by navaleshubham10 on 2011-11-27
i think refresh is used to give some rest to computer so tat it computer can work properly like we refresh ourselves with some water on our face

---

### Post by T.exe on 2011-11-27
What might be the point of having a 'refresh' option then??
(*confused*)

---

### Post by shubham1 on 2011-11-27
refersh actually means reload to do that task again same as in rowsers to update the status

---

### Post by 3rdalbum on 2011-11-27
> **T.exe said:**
> When I started with computers back in the days with Windows 98, I always used to love the 'refresh' option provided by Windows.
In browsers ofcourse, refreshing is necessary to load the updated contents of a website. But, what is the purpose of 'refreshing'? When I moved to Linux, my curiosity grew even more when I found that Linux did not provide a 'refresh' option.

I have read in numerous forums that it updates the caches, icons etc. many even said it is useless (I find it hard to believe though).

Please help me understand the technical details behind the refresh option, and since Linux does not offer this facility, how is it handled in Linux???

Enlighten me!!!!

It's simple.

With ye olde Windows, if you open up a folder, the folder's contents are ONLY read when you actually open the folder. Anything added to the folder after you open it will not appear in the window, unless you Refresh. The Refresh option just reads the folder contents again and redraws the icons.

That's a bit silly, if you ask me. There's no valid reason* why it couldn't just periodically check if the folder's contents have changed, or better yet, be informed by the kernel when the folder's contents are modified. That's the approach used by Linux and newer versions of Windows. And every version of Mac OS, I believe since System 1 in 1984.

So, T.exe, it's actually really similar to a Refresh option in your web browser. The web page is only read when you open it, and any changes since made will not automatically appear in your browser unless you Refresh, which re-reads the page from the site.

No, naval, the Refresh option does not give the computer a virtual splash of water. It appears to be a common misconception in some parts of the world. The Refresh option when you right-click the desktop ONLY re-reads the actual desktop contents and redraws the desktop. It doesn't garbage-collect the RAM or make the CPU run faster or anything like that.

*I imagine the original reason was to reduce the load on early CPUs and early disks, especially floppies, from polling them to find out if anything has changed. However, the Mac OS has NEVER had a Refresh button - it has always automatically detected any folder changes and redrawn icons when needed, even when running on a 16 MHz CPU with 2 MiB of RAM. The "reduce load from polling" reason just doesn't stack up.

---

### Post by The Cog on 2011-11-27
It is still useful when looking at mapped drives. Frinstance if I map a drive to a windows share, it doesn't update periodically. You have to use refresh to see when new files appear, or files get written to so their timestamp changes.

---

### Post by T.exe on 2011-11-27
**@3rdalbum**

Your post is fantastic...!!!!!!!!!!!!!!

THANK YOU! :D

---

### Post by CryptAck on 2011-11-27
> **3rdalbum said:**
> 
That's a bit silly, if you ask me. There's no valid reason* why it couldn't just periodically check if the folder's contents have changed, or better yet, be informed by the kernel when the folder's contents are modified. That's the approach used by Linux and newer versions of Windows. And every version of Mac OS, I believe since System 1 in 1984.

Depends on the duration of "periodically". Some times after a process moves a file from one directory to another, I immediately want to execute/edit the file. With the polling concept, if the duration is too long (i.e. human noticeable) then a refresh option may come in handy. 

I do agree, if the file browser works off kernel events for file system changes, that is ideal. It saves processing cycles (polling the directory) and handles the refresh for you.

I'm not familiar with the methods employed by Nautilus today. I do recall having to use the F5 technique recently; I believe it was for a remote file transfer to a local directory.

---

