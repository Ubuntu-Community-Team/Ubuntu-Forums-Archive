---
title: "Search by date modified."
date: 2011-07-01
forum: Programming Talk
---

### Post by conradin on 2011-07-01
Hi all,  
I have a directory with 52,000 sub-directories. Each sub-directory has numerous files. What I need to do is search each sub-directory, and find out if any of the files are newer than june, sixth, 2006. 

if any file is older than 6.6.06, I can move to the next sub-directory. 
if all the files are older, I can delete them all, and that sub-directory. 

So, I am looking at the find command, and think that it could do most of the work I need it to do with the command:
```
find -newerXY
```
But I cant seem to get it to work, and I haven't found any examples how to use the -newerXY option. 

Does anyone have any ideas how I can get this done, or a functional code example?

---

### Post by zobayer1 on 2011-07-01
If you try to see the man page for find, you will see -newerXY and other options are discussed there in pretty much details...
```

$ man find

```

However, writing your own depth first search procedure may give you a lot of flexibility than using find. To get various status, you can use stat program.

---

### Post by ratcheer on 2011-07-01
I haven't needed to do this in Ubuntu, but the way I used to do it at work on Solaris was, e.g.,

find . -mtime +11  (would find everything more than 10 days old)

-11 would find things less than 11 days old, or something like that. I never understood exactly what the numbers meant, I just learned to get along with whatever they were doing.

Tim

---

### Post by conradin on 2011-07-04
ratcheer, that post was helpful.
I tried to figure something out for a bash script but I was unable. The computer with 52000 files & folders is a directory on a windows 2003 server, inside a closed source CMS, which doesn't track users, creation dates, and doesn't even have a delete function. Ah, so I sorted the ancient files in windows and put them in a folder. (folder names are usernames) I removed the old folder after backing it up on a external drive. 
Then I dumped the usernames to a file using 
```

ls FilesToDelete/DataFiles/ > ../Desktop/UsersToDelete.txt

```

Then I placed a generic date after all the users Which are scheduled to be removed.. 6.6.2006. Any users before then we just don't care about. 
This cleared up 512MB of space and Identified 1017 users who I can safely remove.

---

### Post by ratcheer on 2011-07-05
Good. I'm glad I could help.

Tim

---

