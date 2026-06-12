---
title: "rsync - copy files within all subdirectories and with patterns"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by koosfoto.hu on 2013-06-19
Greetings!

There is a directory with several sub-dirs.
The sub-dirs all contain many files (hundreds of them).

There is a list of files in a text file. 

I would like to copy all files from within the first dir and its all sub-dirs into a new dir.

And I would need files with a given pattern, as well. (Like all files starting with P1234 and ending with .jpg)

How may I
- make rsync search for all sub-dirs?
- give the patterns in the list-file?

Thanks a lot, 

Tamás

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by koosfoto.hu on 2013-06-19
Thanks, ahallubuntu!

This is the command I tried now:

*rsync --archive  --files-from=/home/tamas/probalista.txt . /home/tamas/proba*

(Beforehands I made cd to the input dir, and created a probalista.txt file with the filenames, and created the folder proba)

When executed, it searches the files ONLY under the . directory, and sends error messages: 

*failed: No such file or directory (2)*


And at the end:

*rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]*


The files I need to copy can be in ANY of the subdirectories! 

Thanks,

Tamás

---

### Post by HiImTye on 2013-06-19
[quote=rsync man page]--include-from=FILE
    This option is related to the --include option, but it specifies a FILE that contains include patterns (one per line). Blank lines in the file and lines starting with oq;cq or oq#cq are ignored. If FILE is -, the list will be read from standard input.[/quote]that's the option you want
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Lars Noodén on 2013-06-19
The option --files-from only reads the files from an existing list.  If you want rsync to find what's there you can just point it to the source directory:

```

rsync -avl /home/koosfoto.hu/source/  /media/backup/koosfoto.hu/destination/

```

To keep cruft from accumulating in your backup directory, you can also use --delete.  But be careful with it.

```

rsync -avl --dry-run --delete /home/koosfoto.hu/source/  /media/backup/koosfoto.hu/destination/

```

---

### Post by koosfoto.hu on 2013-06-21
Thanks Lars Noodén and  HiImTye!


I make a fresh start. With less questions. :)

So... there is a folder, it has several subfolders. 
All subfolder contains many files (photos).
One filename is present only in one of the subfolders. 
I get a list of filenames. These files in the list are in one (any) of the subfolders.

I would like to copy all files indicated by the list-file into a new folder. 

If I cd into one of the subfolders and use the command:

rsync  --files-from=/home/tamas/probalista.txt . /home/tamas/proba

it works well, and copies all files requested by the "probalista" list-file from THIS specific subfolder.
So, if I repeat the abouve command under all subfolders ... I get what I need.

Now... I would like to issue the command once, from within the main folder... and would like it to go and check in all subfolders and copy the requested files it finds in all of these subfolders. 

I would think, that -r or -a should do the trick... however... none worked yet for me.
May be I just made syntax error?

So, I would need the command line to do the copy from all subfolders the files requested by the list-file. 

Thanks,

Tamás

---

### Post by Lars Noodén on 2013-06-21
The problem looks like your use of *--files-from*.  Don't use it. If you leave that out, then -a or --archive will recursively traverse your directories.  

```

rsync -a . /home/tamas/proba/

```

That assumes that the directories you are after are not starting with /home/tamas  If you are after those directories and still want the results in ~/proba then you have to use *--exclude*.

If you do not want all the files, then consider using *--include*  You can get a preview of what will happen if you use *--dry-run*.

If you still want to work using the* --files-from* option, then the question becomes one about your use of [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html) rather than rsync.

---

### Post by koosfoto.hu on 2013-06-21
Thanks, Lars.

YES, you are right! 
What I need is a "**find and copy**" function!
May be it should be something very different and NOT rsync, at all?

Yes, the goal is to collect in the destination folder all files defined by the list... wherever they are located within the subdirectories.

(The rsync command has been suggested to me long time ago...
[http://ubuntuforums.org/showthread.php?t=2009320]("http://ubuntuforums.org/showthread.php?t=2009320"))


Thanks,

Tamás

---

### Post by Lars Noodén on 2013-06-21
You could do it in two steps then.  First, use find to find the files and create the data file for use by rsync.  Second, use the datafile with rsync's --include-from option.

find is quite flexible in what it can include and exclude.  What files are you trying to find?

---

### Post by koosfoto.hu on 2013-06-21
As a photographer, I make photos at events. 
They are named sequentially, automatically be the camera. 
I keep them separeted by sub-events (subfolders).

When there is an order... I get the file names in a list. 
These are the files I need to find and copy into a new destination folder. 

So, I have a folder containing only subfolders... there are the subfolders with a lot of photos each, and there is a list of selected files to be copied into the new folder. 

THANKS,

Tamás

---

### Post by HiImTye on 2013-06-21
> --include-from=FILE
This option is related to the --include option, but it specifies a FILE that contains include patterns (one per line). Blank lines in the file and lines starting with oq;cq or oq#cq are ignored. If FILE is -, the list will be read from standard input.

```
rsync -a --include-from=/home/tamas/probalista.txt . /home/tamas/proba
``` [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by koosfoto.hu on 2013-06-23
Well, this one:
> rsync -a --include-from=/home/tamas/probalista.txt . /home/tamas/proba

copies ALL files (not only the ones defined in the txt file!), and the structure itslef, as well. :(

---

