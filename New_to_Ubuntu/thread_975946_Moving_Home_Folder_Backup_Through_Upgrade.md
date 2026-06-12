---
title: "Moving Home Folder Backup Through Upgrade"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by geekchicohio on 2008-11-08
Somewhat against my better judgment I attempted today to "Upgrade" from 8.04 to 8.10 using the update dialog box. Somewhere in the midst of this process (after all the files were downloaded but before any were installed) I got some sort of buffer error and suddenly had an un-upgraded machine on which most of my applications (including nautilus) didn't work. Upon re-start, 8.04 failed to startup.
I used a live CD to backup my entire Home Folder to an external Harddrive and intend now to do a fresh install, preferrably of 8.10.

My questions are:

1. Is it true I can essentially copy my Home folder backup over the fresh install's Home folder and get back most of my settings etc?

2. Is it possible that doing so would bring back whatever errors/problems are resulting in my system's having been rendered unusable to begin with?

3. Would there be any issues I need to know about before copying my home folder settings, established on a Hardy install, over to an Intrepid install?

4. Am I looking at this entire thing the wrong way, and what might you recommend I do instead, if so?

Thank you all so much for any help you can provide!

---

### Post by handydan918 on 2008-11-08
> **geekchicohio said:**
> Somewhat against my better judgment I attempted today to "Upgrade" from 8.04 to 8.10 using the update dialog box. Somewhere in the midst of this process (after all the files were downloaded but before any were installed) I got some sort of buffer error and suddenly had an un-upgraded machine on which most of my applications (including nautilus) didn't work. Upon re-start, 8.04 failed to startup.
I used a live CD to backup my entire Home Folder to an external Harddrive and intend now to do a fresh install, preferrably of 8.10.

My questions are:

1. Is it true I can essentially copy my Home folder backup over the fresh install's Home folder and get back most of my settings etc?
Yes.Although you may have to rename it, or change the ownership, (chown).> 
2. Is it possible that doing so would bring back whatever errors/problems are resulting in my system's having been rendered unusable to begin with?
Possible, depending on what those issues were. If they were merely config errors on the user level, yes. If they were actually system errors, not likely.> 
3. Would there be any issues I need to know about before copying my home folder settings, established on a Hardy install, over to an Intrepid install?

 Heh. That's the 64 dollar question...but youshould be OK, in the vast majority of cases. > 

4. Am I looking at this entire thing the wrong way, and what might you recommend I do instead, if so?
Nope! I think your approach is quite reasonable, and might only be improved by researching the use of symlinks to facilitate the re-insertion of /home.> 
Thank you all so much for any help you can provide!

Pleasure. Hope it helped.

---

### Post by geekchicohio on 2008-11-09
Thanks so much for the help. Presumably, once I've got my fresh Intrepid installation up and running, I would just be able to move the home backup into my root directory copying over the new one? Or move all the backup's contents into the new one?
I guess I know what I want to do, but I'm less certain of the exact process I'd need to use to do it.
And I'm not sure the exact command for changing ownership, if that should need to happen (though I intend to use the same username this time out as I did before).

---

### Post by mapes12 on 2008-11-09
Best practice is to keep /home on a separate partition for the reasons you have experienced. If you have now got your system back to life and want to move /home then take a look at this HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

