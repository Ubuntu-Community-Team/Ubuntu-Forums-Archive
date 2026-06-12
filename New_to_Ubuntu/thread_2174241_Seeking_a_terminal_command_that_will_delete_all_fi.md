---
title: "Seeking a terminal command that will delete all files that lack an extension"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by skitter on 2013-09-13
I have a directory that contains file that are named like this:

song1
song1.mp3
song2
song2.mp3

I'm trying to find a way to delete all of the 'non-mp3' files.  I know that I can do this easitly enough in the GUI, but would really like to automate this with a script, and would also like to get a better working in the terminal.

*edit- I should correct what I said about the file names. A more accurate discription is:

01-Song Title
01-Song Title.mp3
02-Another Title
02-Another Title.mp3

I suspect the spaces / dashes are preventing the suggestions below from working.

---

### Post by Lars Noodén on 2013-09-13
The program [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html) will probably do what you want.  You can try the example below and remove *echo* when it gives the output you want.

```

find . -type f ! -name '*.mp3' -maxdepth 1 -exec echo rm {} \;

```

That looks in the current directory (.) for all regular files that don't end in .mp3 without going into any subdirectories.

---

### Post by Pako Pako on 2013-09-13
Although if the directory only has song. and song.mp3 files, you can always just
```
rm  -i *.
```

The "-i" will prompt you for each removal. Omit this and it will auto delete all "song1." files from said directory.

---

### Post by skitter on 2013-09-13
> **Lars Noodén said:**
> The program [find]("http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html") will probably do what you want.  You can try the example below and remove *echo* when it gives the output you want.

```

find . -type f ! -name '*.mp3' -maxdepth 1 -exec echo rm {} \;

```

That looks in the current directory (.) for all regular files that don't end in .mp3 without going into any subdirectories.

Thanks, but I'm getting an error with that one- 

"find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments."

Since there are no subdirectories, I tried removing -maxdepth 1.  That command runs with out error, but nothing is deleted.

---

### Post by skitter on 2013-09-13
> **Pako Pako said:**
> Although if the directory only has song. and song.mp3 files, you can always just
```
rm  -i *.
```

The "-i" will prompt you for each removal. Omit this and it will auto delete all "song1." files from said directory.

Thanks, but this one isn't working for me, I'm getting a 'no such file or directory' error.

There are files there though.

skitter@mypc:~/test$ ls -l
total 0
-rw-rw-r-- 1 skitter skitter 0 Sep 13 14:50 blah
-rw-rw-r-- 1 skitter skitter 0 Sep 13 14:50 blah2
-rw-rw-r-- 1 skitter skitter 0 Sep 13 14:51 blah2.mp3
-rw-rw-r-- 1 skitter skitter 0 Sep 13 14:51 blah.mp3

skitter@mypc:~/test$ rm *.
rm: cannot remove `*.': No such file or directory

---

### Post by Lars Noodén on 2013-09-13
The warning is just a warning.  It will still run.  You could get rid of it by putting it first.

```

find . -maxdepth 1 -type f ! -name '*.conf' -exec echo rm {} \;

```

About it not deleting anything, that is by design.  You need to remove "echo" from the find options for it to actually delete anything, but only do that after you are satisfied with the output.

---

### Post by skitter on 2013-09-13
Thanks so much. You mentioned the echo point in the first reply, and I overlooked it. I'll be sure to read with my good eye next time :)

This does what I need, and more importantly,  I (mostly...) understand what it's doing.
```
find . -maxdepth 1  -type f ! -name '*.mp3' -exec  rm {} \;
```

---

### Post by Lars Noodén on 2013-09-13
Cool.   Glad it works.  As you noticed, find uses a logical AND between options by default.  Just in case it is handy to know at a future date, it can also be made to do logical ORs or combinations and groupings for complex matching.

---

### Post by sisco311 on 2013-09-13
find is probably the best tool for this job, but if you don't mind I would like to show some other examples. ;)

In addition to the traditional globs, Bash also offers extended globs. Extended globs aren't enabled by default, so we have to enable them with `shopt -s extglob'. Once they are enabled we can use !(pattern) to match anything except one of the given pattern. For more info check out:  [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

```
shopt -s extglob nocaseglob
echo rm -- !(*.mp3)
```

NOTE: rm by default does not remove directories, so there is no need to test if the files are dirs or not.

This method is less portable than using find but it can be very handy in an interactive Bash shell.

Here is another way to accomplish the same thing:

```
for file in *
do
    [ -f "$file" ] || continue #ignore non regular files (directories etc.)

    case $file in
        *.mp3|*.MP3)
            echo "do nothing"
            ;;
        *)
            echo rm -- "$file"
            ;;
    esac
 done
```

This looks a bit complicated for such a simple task. Right? Why is this method better than the first two? 

 Well, it should run in any POSIX shell, hence it's more portable than the one which uses extended globs. And it's expandable. You can add more patterns in order to do something with the .jpg files for example.

```

     case $file in
        *.mp3|*.MP3)
            echo "do something"
            ;;
       *.jpg|*.JPG)
            echo "do something else"
            ;;
       *)
            echo rm -- "$file"
            ;;
    esac

```

hth

---

### Post by Jonathan Precise on 2013-09-13
Please mark as solved by going to thread tools.

---

### Post by skitter on 2013-09-14
Thanks.  That's a lot to chew on, but I'll make a note of this and revisit it when I get better with the shell and scripting.

---

