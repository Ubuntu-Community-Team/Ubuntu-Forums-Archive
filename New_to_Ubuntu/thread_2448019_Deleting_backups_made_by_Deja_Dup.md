---
title: "Deleting backups made by Deja Dup"
date: 2020-07-30
forum: New to Ubuntu
---

### Post by bkscroggs on 2020-07-30
I have my Deja Dup backup to my Google Drive online and am noticing my space on the Google Drive starting to dwindle down. I like to have it backup pretty often so I'd like to start deleting the older recovery versions. Can't I in theory delete everything and then immediately do a backup to what I have now? I have a couple of hard drives that will be failing soon and want to make sure I can restore.

Thanks!:P

---

### Post by deadflowr on 2020-07-31
Deja Dup will automatically remove the oldest backup when it sees the space is running too low.

Beyond that you can set the scheduling to remove backups that are older than a certain time.
Deja Dup gives only 3 option in the program gui (1 year, 6 months, or forever)
But you can set it even shorter (or longer) using the program called dconf editor (would need to be installed.)
In dconf editor the deja dup settings are located in org > gnome > deja dup.
The setting is called delete-after.
Here you can set anytime for older backups to be deleted.

> Can't I in theory delete everything and then immediately do a backup to what I have now?
If you want to nuke it then you can do that the same as you would normally, no need to run any deja dup command.
Once empty, then sure, you can just start doing your backups again.

---

### Post by bkscroggs on 2020-07-31
Awesome! Thank you so much! I'll definitely give that a go.

---

### Post by bkscroggs on 2020-07-31
It WORKED! Thank you. How do I make this thread [SOLVED]?

---

