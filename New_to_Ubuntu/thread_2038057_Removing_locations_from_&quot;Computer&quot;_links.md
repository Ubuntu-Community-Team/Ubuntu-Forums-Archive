---
title: "Removing locations from &quot;Computer&quot; links in Nautilus"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by thexcguy on 2012-08-05
Hello!

I just completed a dual-boot of Ubuntu 12.04 and Windows 7, and I was wondering if/how I could remove some of the links in the "Computer" list in Nautilus.  Because I'm running a dual boot, I have all of my music/documents/photos/videos on a separate partition, so the links to ~/Documents, ~/Music, ~/Pictures, and ~/Videos aren't really necessary for me.  I'd really like to be able to remove them if possible, but when I right-click on them, the "remove" option is grayed out. I was able to remove what I think are the associated bookmarks in the "edit bookmarks" menu, but they still appear in the sidebar.

Thanks in advance for your help!  I'm really jazzed to be joining the Ubuntu community :D

---

### Post by NikTh on 2012-08-05
Hi , 
you can hide side bar with F9 . F9 again to unhide. 

If you want to remove those specific entries , I think it is not possible. 
Take a look here --> [http://askubuntu.com/questions/79150/how-to-remove-bookmarks-from-the-nautilus-sidebar](http://askubuntu.com/questions/79150/how-to-remove-bookmarks-from-the-nautilus-sidebar)

You must disable (delete) those entries all together.

Although the best option might be to create symlinks and eg Music folder point to you music folder at this separate partition where you have your music.  
Thanks

---

### Post by thexcguy on 2012-08-05
Thanks NikTh!  I actually ended up trying to use the solution suggested by Elfy in that page you linked to, and it worked smashingly.

---

