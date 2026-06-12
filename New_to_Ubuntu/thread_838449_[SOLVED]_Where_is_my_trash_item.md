---
title: "[SOLVED] Where is my trash item?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by KingTermite on 2008-06-23
I deleted a directory a little bit ago, but I purposely brought up Nautilus in sudo mode and moved it to trash because I was not sure if I may need it after all.

I think now that I do need it, but when I go to the trash, I do not see it.

Where is it?

---

### Post by forestpixie on 2008-06-23
It's probably in root trash - if you deleted it as root.

Open nautilus as root and look in it's trash

---

### Post by KingTermite on 2008-06-23
> **forestpixie said:**
> It's probably in root trash - if you deleted it as root.

Open nautilus as root and look in it's trash

I thought that too, but still didn't see it.

I couldn't move to trash until I opened nautilus from command line with "sudo nautilus". Then I moved to trash. Now, no matter whether I open nautilus regular or with sudo, I don't see anything in the trash except for a link I deleted last week.

---

### Post by forestpixie on 2008-06-23
I've been scouting about and found that my root trash appears to be in my home hidden as .Trash-0 - maybe check there - I just found a bunch of my old deleted files from when I reinstalled.

---

### Post by gandaran on 2008-06-23
if you using ubuntu 8.04 and fully updated, you will find the root trash in file system » home » .trash-0 ( hidden folder) you have to be root to access it.
if your ubuntu 8.04 is not updated, you can find it in the hidden home .local folder.

---

### Post by KingTermite on 2008-06-23
Thanks for suggestions, but nothing worked.

I went in as root and there are no hidden directories in my /home directory. No .local or .trash-0. I'm using 7.10.

Anyway, I ended up reinstalling from my originals anyway, so at least the crisis is over.

---

### Post by gandaran on 2008-06-23
> **KingTermite said:**
> Thanks for suggestions, but nothing worked.

I went in as root and there are no hidden directories in my /home directory. No .local or .trash-0. I'm using 7.10.

Anyway, I ended up reinstalling from my originals anyway, so at least the crisis is over.

I beleive the trash folder in 7.10 is in file system » root folder, again the trash folder is always hidden, if its not in the root folder, look in other folders.

---

### Post by KingTermite on 2008-06-23
> **gandaran said:**
> I beleive the trash folder in 7.10 is in file system » root folder, again the trash folder is always hidden, if its not in the root folder, look in other folders.

You were right.....it was in /root/.Trash and the directory in question was there. I still don't understand why it didn't show up in nautilus.

Point is moot as I said I already reinstalled, but thanks for the location tip.

---

