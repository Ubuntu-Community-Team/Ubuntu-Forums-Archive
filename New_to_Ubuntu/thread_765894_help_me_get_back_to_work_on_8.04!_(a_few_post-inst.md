---
title: "help me get back to work on 8.04! (a few post-installation bugaboos)"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by eDRoaCH on 2008-04-24
Been waiting anxiously for Hardy for a couple weeks now. Didnt get the beta because I use my laptop for web dev and wanted to keep it stable. However, I messed up my mounting a bit when I re-partitioned my fat32 data drive so I thought a format was best. Anyway, on to my questions/issues

1. I don tsee a www-data group. In 7.10 I added my user to this acct so I could live-edit my site. What is the fix?

2. My fat32 data drive (And all others) do not auto mount and require passwords the first time I access them. I want to eliminate this.

3. I have a x3100 card that compiz doesnt like, but in 7.10 I was able to have it ignore it and it worked just fine.  I cant get emerald or compiz-settings-manager to save their settings no matter what I do. I've never even seen the emerald theme engaged. Did they change how to disable the check? (I used [http://ubuntuforums.org/showthread.php?t=707473](http://ubuntuforums.org/showthread.php?t=707473) ) The apperance settings go back to normal on their own.

I did go from a 32bit to a 64bit os as well. Anyone got input on these?

---

### Post by eDRoaCH on 2008-04-25
alright people, got the 3d stuff working. i had an error downloading a lib (probably due to the busy servers) right after install, so i reinstalled. compiz seems to be working now except a strange bug with scale (try out compiz --replace in terminal to see it, seems a default option is wrong)

to get emerald working, I had to add "emerald --replace &" to system->administration->session manager

I created a group called www-data and chowned it to 775 which seems to give me my edit ability (still owned by root) I still need to re-import my database to see if things are working properly.

so far thats what I got, further help appreciated.

Oh, I also have no wifi card anymore, I will have to boot into vista at some point to find out its name (i forget)

---

