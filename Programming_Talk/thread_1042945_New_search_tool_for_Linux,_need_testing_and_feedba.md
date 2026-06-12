---
title: "New search tool for Linux, need testing and feedback"
date: 2009-01-18
forum: Programming Talk
---

### Post by buixuanduong1983 on 2009-01-18
Hello everybody, I have just finished a new search tool for Linux, called QuickSearch ([http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")). The ideal for this new tool is inspired from PDFind (a search tool of PowerDesk package). Among many search tools available nowadays for Linux, I found that all of them index the file system, including file content into a database, this is done when computer is not doing other thing (correct me if I'm wrong). But, normally user only need to search for file name, and they (in most case) only need to search in a specific folder, not all filesystem.

So my SearchTool use a different way: it uses 'ls' command to list content of searched folder, then does the search on that output. This way search speed is very fast (except for the first time it has to make the 'ls' output).

This is the first (pre-beta) of this tool. It is written by Gambas2, and depends on gambas2-runtime package. At this release I only tested it in Ubuntu 8.10. It is still very simple, so I am looking forward for your comment and advise:
- how can I improve it?
- how do you think about it?
- if it is OK then how can I spread it?

Thanks in advance and looking forward to hearing from you.

---

### Post by NE Key on 2009-01-18
I entered a file name, pressed "Find Now" and it came back with "Search Folder is Empty".

What does that mean ?

---

### Post by NE Key on 2009-01-18
I pressed the "Browse" button and a sub window opened - which I cannot close.


Still cannot find a file.

---

### Post by buixuanduong1983 on 2009-01-18
Thanks for fast reply, you are the first user of QuickSearch. Congratulation! :-)
- please fill in Path
- you can close that sub-window by clicking Browser again (double-click a folder inside this sub-window to select that folder to search). Should I change the way this button is?

And by some reason which I don't know yet, sometime I just cannot search. I close QuickSearch and open it again, it works. Maybe some problems with gambas runtime.

---

### Post by NE Key on 2009-01-18
OK, working now. The Browser "On/Off" toggle is not intuitive but is good once you know how it works.

It is a good search routine. A search for the file "area" in the home folder produced results for "areas.txt", "area1.txt" "SearchAreas.class" and others in all the sub folders.

That I like. No need to use wild cards - they are assumed.

The window cannot be resized - it would be good it it could be opened out.

Finally, where is the source code ?

Added - I really like this routine - It is a quick and simple of finding a file from only a part of its file name - I am always losing files in my home directory and forgetting where I put them, which sub-directory or older version.

Added again - I also like the way that a double click on a found file opens the file browser nautilus.


This tool is growing on me - I am beginning to think it will become my "default option".

---

### Post by buixuanduong1983 on 2009-01-18
Thank you very much for your comment. I still continue to improve it. This is what I think I'll have to do:
- Resize the window
- Make QuickSearch available for other distribution
- Cumstomise (or automatically find) the default browser (Nautilus, Konqueror, ...)
- Find by file type, file size, date...

I will upload the source code, please check again.

---

### Post by NE Key on 2009-01-18
I have just used your routine "for real".

I wanted to quickly find a version of a paper I wrote last year - which was somewhere in the many sub-directories of my Documents folder.

I had forgotten the exact name of the document (and where it was stored) but used a "key word" from the title.

I immediately found the original and subsequent versions. A click on it brought up the file browser. 

Your routine is very useful - I like it. Now smooth off the rough edges, make it pretty and you have a very useful utility.

---

### Post by buixuanduong1983 on 2009-01-19
I have a problem with resize the form: I don't want the form too small: ie if user resize my form, if form width and height is less than a value then the form stay at its smallest prefixed size. How can I do that? I tried:

PUBLIC SUB form_Resize()
  
  IF ME.Width <= 532 THEN ME.Width = 532
  
END

but it does not work.

---

### Post by buixuanduong1983 on 2009-01-19
Hi again, I have just update QuickSearch to version 2009-01-19. Have a look!
([http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")).

In this release:
- now you can resize its window
- press Escape key when browser sub-window is opened will close it
- fixed the error of duplicate entry in Path combo box
- store window setting on exit

---

### Post by NE Key on 2009-01-25
I am "playing" with your latest version and to be to honest; I like it and it is useful utility. - Your latest version is good.

I commend this utility to the house.

However - I think there is a bug. If the search path is "/" then there the program is "overloaded" and goes grey.
Also - it needs a "Searching....." response - this solves the problem of "still searching" or "nothing found".

---

### Post by TooRight on 2009-04-16
Just wanted to let you know that I downloaded your program and gave it a try... wowwwww!! I loveeeee it!! It now has a permanent spot on my panel. Such a handy little tool, and sooo fast!! :D Thank you!!

---

### Post by buixuanduong1983 on 2009-05-11
Thank you all for your testing and comment. I would improve my program as it is a lesson and like a hobby. Anyway now we have a very good search tool included, in Places/Search for Files... menu. And for anyone would read this, we have the fredom of choices, and that is what I love of open source software.

Thanks all once again!

---

### Post by ghostdog74 on 2009-05-11
how is your tool different from what the normal command line find utility?

---

### Post by buixuanduong1983 on 2009-05-11
I don't know for sure how find work, but is is a CLI tool, and (I guess) it goes through whole directory again when you search second time in the same directory. 
QuickSearch is a GUI tool, it make a temporary list of all file in desired location, then do the search on that list. So it only take a bit longer time to make the list first time, then from second search it only search text in text file ---> faster. This idea come from actual use situation, that normally you only want to search in 1 place, but many times.

---

### Post by ghostdog74 on 2009-05-11
i hope you can play with the find utility and find out the difference between them. it will help you to improve on your utility.

---

### Post by LewRockwellFAN on 2011-01-22
Thanks. A better file search tool is sorely needed. I couldn't get the browse-to-a-path-to-search function to work but I could paste in a path to get around that. But unless I'm missing something it won't search recursively in subdirectories, just in the one directory. Is that correct? Been trying all day to find a decent file search program and so far the one that came by default is as good (bad) as any for me but it won't let me select more than one file at a time from the search results to do something with. For instance it won't let me select all files or all files beginning with "a" or all files over 1 miB in the results and copy them to another directory. That truly sucks. Next I'm going to try installing some windows search programs under wine. One of the reasons I got disgusted with Windows is the dumbing down of the default file search utility in 7 vs. what came with W2k.

---

### Post by hakermania on 2011-01-23
It is very nice program. For a reason, I can't find it in my ubuntu menu (i am running ubuntu 10.10). Also, I tried to locate quicksearch.gambas, but the first Q is capital. Anyway, I extracted the deb file and finally found the executable name. I have to inform you that it's very rare to have capital letters in a executable. :P I am wondering if this project, after so many months is still being developed. I find it very good by the way. It is very easy to use ls and pipe to grep in order to find files. Very clever.
If you would like your package to be included to ubuntu you should have a check at lintian errors (I get many when I run it to the deb file) and upload it to [REVU.]("http://revu.ubuntuwire.com/")
I have attached the lintian errors I get with  lintian -I -i package.deb
Nice prog.

---

### Post by slavik on 2011-01-23
> **buixuanduong1983 said:**
> Hello everybody, I have just finished a new search tool for Linux, called QuickSearch ([http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")). The ideal for this new tool is inspired from PDFind (a search tool of PowerDesk package). Among many search tools available nowadays for Linux, I found that all of them index the file system, including file content into a database, this is done when computer is not doing other thing (correct me if I'm wrong). But, normally user only need to search for file name, and they (in most case) only need to search in a specific folder, not all filesystem.

So my SearchTool use a different way: it uses 'ls' command to list content of searched folder, then does the search on that output. This way search speed is very fast (except for the first time it has to make the 'ls' output).

This is the first (pre-beta) of this tool. It is written by Gambas2, and depends on gambas2-runtime package. At this release I only tested it in Ubuntu 8.10. It is still very simple, so I am looking forward for your comment and advise:
- how can I improve it?
- how do you think about it?
- if it is OK then how can I spread it?

Thanks in advance and looking forward to hearing from you.
so, your program can be replaced by locate ... find is even more powerful though.

---

