---
title: "BASH: for each directory and get directory name"
date: 2007-10-07
forum: Programming Talk
---

### Post by .evan on 2007-10-07
I'm working on a backup script and want to break up the tar file into smaller chunks.  I've tried working out how to exclude directories from the tar process and it does not work  (I've seen many others on forums with the same problem)  and tarring my entire home directory fails with an error telling me that the tar file size limitation has been met.

So, I'm thinking that it would be cool to loop through every directory in my home path, get the name of the directory, and then tar/bzip2 that directory - using its name as the name of the .bz2 file.

can someone give me a few hints?

how to get the name of each directory...

how to loop through each directory in current working directory...


Thanks!
[http://www.hobbylobby.wordpress.com/](http://www.hobbylobby.wordpress.com/)

---

### Post by cwaldbieser on 2007-10-07
```

$ find . -maxdepth 1 -type d -exec echo tar '[options]' {} \;

```
This should give you some idea, I hope.

---

### Post by dwhitney67 on 2007-10-07
You can exclude directories (or files) using the --exclude option.

So for instance, if you want to back up a folder, but you do not want the subfolders beef and cafe, then something like this would work:

[FONT="Courier New"]$ tar cvf folder.tar folder --exclude beef --exclude cafe [/FONT]

You can also use wildcards; thus for example, to ignore all object files (those with a .o extension):

[FONT="Courier New"]$ tar cvf mySourceFolder.tar mySourceFolder --exclude *.o[/FONT]

Lastly, if you know which folder and sub-folders/files you want to backup, you can always list them into a text file.  Then tell tar to only backup those file listed in the text file with a command similar to this:

[FONT="Courier New"]$ tar cvf myCollection.tar -T myList.txt[/FONT]

---

### Post by .evan on 2007-10-08
thanks everyone!

I've experimented with --exclude in a tar command and got some advice on another thread ([http://ubuntuforums.org/showthread.php?p=3490966#post3490966](http://ubuntuforums.org/showthread.php?p=3490966#post3490966))
, but your advice was very helpful.

I really want to get my script working by looping through the directories in code so that I don't have to worry about keeping a reference file up to date as I make changes to my file structure.

 I'll work on these ideas more in the next few days.

.evan
[http://www.hobbylobby.wordpress.com/](http://www.hobbylobby.wordpress.com/)

---

