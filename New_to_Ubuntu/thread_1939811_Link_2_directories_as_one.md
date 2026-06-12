---
title: "Link 2 directories as one"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Gourandle on 2012-03-12
Hi all

Im new to this forum and also new to ubuntu.
Been trying to get a directory to show all files on 2 separate locations, is it possible? if so how?
Ive tried symbolic links using ln -s but requires me to run the command every time there's new file in one of the directories.
Im trying to achieve like what Windows have with their Libraries Folder, allowing multiple locations to appear on one specific location.

sorry if this has been covered before, but been searching hours and found no solution.

Thanks all

---

### Post by TeoBigusGeekus on 2012-03-12
You can't do this I think.
See also [this]("http://stackoverflow.com/questions/423320/can-i-symlink-multiple-directories-into-one").

---

### Post by gdea73 on 2012-03-12
TBG's right, you can't symlink multiple directories with a single link. You would likely have to link to each *directory* containing each part of the total set of files. (i.e., "Music on PC-2", "Music on PC-3", "Local Music") to point to the different directories.

I'm trying to think of an alternative to the Win7 "Libraries" setup... one way you could sort of do this is, on 10.10 and before, you can drag directories into Nautilus' "Places" panel, which would then show up in the Places menu. I'm not sure how to do this in Unity though.

---

### Post by Gourandle on 2012-03-13
Thanks for the replies.

> **TeoBigusGeekus said:**
> You can't do this I think.
See also [this]("http://stackoverflow.com/questions/423320/can-i-symlink-multiple-directories-into-one").

thanks for the link. its great help. gone try figure something out with that. I wonder if its possible, instead of doing cron job that executes the commands periodically, the commands executes only when there are changes (i.e. new files, modified files, deleted files) in directories?


> **gdea73 said:**
> TBG's right, you can't symlink multiple directories with a single link. You would likely have to link to each *directory* containing each part of the total set of files. (i.e., "Music on PC-2", "Music on PC-3", "Local Music") to point to the different directories.

I'm trying to think of an alternative to the Win7 "Libraries" setup... one way you could sort of do this is, on 10.10 and before, you can drag directories into Nautilus' "Places" panel, which would then show up in the Places menu. I'm not sure how to do this in Unity though.

Never experienced previous versions so I'm unsure what you are referring to. Im currently on Ubuntu 11.10.
What I'm trying to achieve is to share this combined directories as one share name. This PC will be more used as a central storage rather than an everyday used PC.


I will leave this thread open if anybody has more suggestion and inputs.
Thanks :).

---

