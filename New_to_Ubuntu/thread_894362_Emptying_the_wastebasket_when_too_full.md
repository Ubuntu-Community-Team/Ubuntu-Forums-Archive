---
title: "Emptying the wastebasket when too full"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-08-19
I've noticed that the /tmp folder is automatically emptied.

However, my wastebasket just seems to grow and grow, so now I regularly go in and empty it.

Is there a way to instruct the wastebasket to delete everything older than a certain age, say five days? It would be nice not to empty everything.

Also, is it possible to order the wastebasket's listing by the date deleted?

---

### Post by LTFC2020 on 2008-08-19
not sure about the date thing but try

Open a Nautilus window and go Edit&#8594;Preferences. Go to the Behavior tab and under where it says Trash check the box for Include a Delete command that bypasses Trash.

---

### Post by Paddy Landau on 2008-08-19
Thanks for the reply.

I already have that preference ticked. I was after something that automatically deleted files from the wastebasket after some days (it's useful to have deleted files in the wastebasket for a couple of days in case of accidental deletion).

I will see if I can write something myself. If successful, I'll post it here.

---

### Post by limasierra on 2008-08-19
You can use a command that searches for old files in the wastebasket and then deletes them. Try this: go to "Main Menu > System > Preferences > Sessions". Once you opened the Sessions window click "Add", write a name for that program and for "Command" copy this:```
find /home/<username>/.local/share/Trash/ -atime +5 -delete
```
This command will search for files on your wastebasket older than five days and remove them. Don't forget to change <username> for your ubuntu username.

---

### Post by Paddy Landau on 2008-08-19
Thanks, that's great advice. I can put it into a script and run it automatically every time I log in!

It would be lovely if nautilus displayed the wastebasket by order of date deleted, and allowed selective restores to the original directory.

---

### Post by limasierra on 2008-08-19
Nautilus doesn't display the wastebasket files by order of date deleted but it can display them by order of acessed date. If you delete a file to wastebasket the acessed date of that file will be the date when you deleted the file. So unless you use that file again the date will remain the same and the file will be deleted after five days according to the command that I previously posted.

---

### Post by Paddy Landau on 2008-08-19
Hmm...

According to my nautilus, the date last accessed is **not** the date deleted!

Any clues?

---

