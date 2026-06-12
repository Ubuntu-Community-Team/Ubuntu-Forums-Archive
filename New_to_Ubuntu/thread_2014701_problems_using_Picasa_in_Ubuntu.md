---
title: "problems using Picasa in Ubuntu"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Phil Miller on 2012-07-02
I like using Picasa3 for editing and managing my photos.
However it seems that it is not entirely compatible with Ubuntu.
All I want to do is move my folders from my hard drive to an external hard drive.
In this way, when I delete the folders from the hard drive Picasa should be able to locate them on the external HD.
The procedure should be;
Right Click folder, select "move folder..."
Then I'm lost.
A window opens up in "wine" but I can't figure it out.
All suggestions welcome

---

### Post by oldfred on 2012-07-02
Welcome to the forums.

I use the Windows version of Picasa (I have version 39) as it is a bit more updated. I just install it into wine and add winetricks and fonts.

I have all our photos in separate data partitions and Picasa finds then without issue. I do set what folders to search in Picasa, so it is not searching entire system, but I do not try to move the folder in wine. When I install the new version of Ubuntu I reinstall Picasa and have had issues with edits that were only internal to Picasa, but have convinced my spouse to always save edited photos outside Picasa. That works for backups better anyway.

---

### Post by Lars Noodén on 2012-07-02
> **Phil Miller said:**
> A window opens up in "wine" but I can't figure it out.


That's because there isn't really a Linux native version of Picasa.  It runs in its own WINE wrapper.  Since it is running in WINE anyway, Oldfred's suggestion of using the other version might work. 

Or you could consider using Shotwell, Digikam or gThumb.

---

