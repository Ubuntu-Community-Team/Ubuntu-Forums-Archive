---
title: "Brasero error"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by jdwaugh on 2013-02-03
Ok, so I want to make a backup of a disc, so I open up brasero, click disc copy, and have it set so the source and destination are the same, and hit copy and I get an error saying "Installing packages by files isn't supported: This method hasn't been implemented yet."

What does that mean?  I just want to make a copy of a program disc so I have a backup

---

### Post by marcus3 on 2013-08-15
If you check out the package description for Brasero it says: > The following packages, if installed, will provide Brasero with added
functionality:
 * cdrdao to burn combined data/audio CDs and for byte-to-byte copy

I got the same error while trying to copy a CD, then installed the cdrdao and cue2toc packages, and could then successfully copy CDs.

You would think the developers would provide a more helpful error message rather than tacking the info on to the end of the package description.

---

