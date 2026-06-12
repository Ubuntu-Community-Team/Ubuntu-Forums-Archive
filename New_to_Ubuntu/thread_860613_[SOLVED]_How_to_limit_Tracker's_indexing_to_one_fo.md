---
title: "[SOLVED] How to limit Tracker's indexing to one folder inside the Home directory?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by swarup on 2008-07-15
In Tracker->Indexer Preferences->Files, I unchecked "Index and watch my home directory", and in the "add" window, selected the pathway to a particular folder in my home directory. But when I do searches, Tracker continues to give me results from throughout the entire home directory. I want it to limit its purview to one particular folder which I have specified. I don't want Tracker watching my entire home directory and giving me extraneous results from the entire home directory. What do I have to do to limit its search and index to the one particular folder inside my home directory?

---

### Post by joshsmith on 2008-07-18
i guess you just need to delete your old index
which is stored in ~/.cache/tracker

then it will reindex at some point, and everything will work

also check the config file in ~/.config/tracker to check the gui and the config file both think you are monitoring the same folder

---

### Post by swarup on 2008-07-20
I see. Perhaps that is what would be needed. 
I thought that after resetting the indexer preferences to the one folder inside my home directory, I had then requested a "re-index" to be done. But I'll give it another shot and see what happens. And if it doesn't work, then I'll try deleting the index as you suggest, and trying again. Thanks very much for the suggestion. :)

Edit (2 hrs later): Somehow the first time I didn't not get a proper re-indexing done, I don't know why. This time it worked perfectly. I didn't have to delete the old index. I just reset the index parameters, then requested a re-indexing. At first Tracker went into pause and didn't want to do the re-index, but then when I requested again it did the re-index and now it is working perfectly. Thanks again for your help. I can see you actively sought out a two-day-old request for help which had been yet unanswered, and I really appreciate that. :)

---

