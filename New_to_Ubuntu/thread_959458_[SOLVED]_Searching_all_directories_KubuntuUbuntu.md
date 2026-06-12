---
title: "[SOLVED] Searching all directories Kubuntu/Ubuntu"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by burnetbj on 2008-10-26
Hi there

What would be the easiest way to find a file you are not sure of the directory? I seem to have miss placed a file and I have no idea where I could have put it. I am using 8.04 with Kubuntu/Ubuntu hybrid, its really a messy install and I intend on re-installing on the 30th to Ibex but until then.  

Thanks to all that help

---

### Post by Xiong Chiamiov on 2008-10-26
Use the "locate" command:
```

locate [filename]

```

You may have to update the database first:
```

sudo updatedb

```

---

### Post by burnetbj on 2008-10-26
Thanks for the responce

Tried locate ....didnt get anything 

Trying to updatedb curser flashing not sure how long to wait will give it a few, its a 500Gb drive

---

### Post by Xiong Chiamiov on 2008-10-26
I'm not sure how it works on Ubuntu, but normally updatedb gets run by cron during system downtime.  If the database hasn't been built at all, then it will take a while, since it's indexing *all* of the files on your computer.  Searches use something similar to an sql database, though, so once indexed, it is rather fast.

---

### Post by burnetbj on 2008-10-26
Dang 

After command it doesnt seem to do anything, heh

Example 
After command input it just goes to a ready state again without doing anything

system acted like it completed updatedb as it reverted to a ready state

---

### Post by Xiong Chiamiov on 2008-10-26
Updatedb doesn't give you any output.  When it's finished, locate will find any file that's on your computer.  If you try locate and don't get anything, then no files match that search.

---

### Post by burnetbj on 2008-10-26
Well I am actually trying to find a folder 


Is there a command to locate a folder with generic search such as Windows search *Rancid* and search within C:?

Thanks for the help

---

### Post by burnetbj on 2008-10-26
Wierd the post made a smiley out of colon question


Any how the question was can I search for folder with generic query like Windows

Search C colon and *filename * 

Thanks

---

### Post by Xiong Chiamiov on 2008-10-26
> **burnetbj said:**
> Well I am actually trying to find a folder 


Is there a command to locate a folder with generic search such as Windows search *Rancid* and search within C:?

Thanks for the help
[Gnome has a built-in search]("http://linux.die.net/man/1/gnome-search-tool").

EDIT:
> **burnetbj said:**
> Wierd the post made a smiley out of colon question


Any how the question was can I search for folder with generic query like Windows

Search C colon and *filename * 

Thanks
If you're in the full reply-editor, the 3rd checkbox under "Additional Options" will avoid parsing things as smilies.

---

### Post by burnetbj on 2008-10-26
Hurray!!

Found the file by shear luck

Thanks for all the help.

One last thing ......cant remember how to change thread to solved

---

### Post by burnetbj on 2008-10-26
Got it

---

### Post by Xiong Chiamiov on 2008-10-26
> **burnetbj said:**
> Hurray!!

Found the file by shear luck

Thanks for all the help.

One last thing ......cant remember how to change thread to solved
It used to be under thread tools, in the top-right.  I don't know if they've reintegrated it yet.

---

