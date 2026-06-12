---
title: "Nautilus &quot;search for files&quot; doesn't show path"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by timandjulz on 2008-07-03
I used Nautilus to search for duplicate files.  e.g. I search for "Taxes*.doc".  It comes back with two documents but I cannot tell what the paths are so I don't know which is the duplicate I want to delete.

There is no way to set "path" as a visible column and the properties box chops off long paths.  :confused:  Opening each document is out of the question because it can take a long time... and sometimes there is no file association.

Is there a way to do this in Nautilus?  If not, where can I report this for fixing/adding?

Thanks,
Tim

---

### Post by swisscow on 2008-07-03
Right click on the file in the search result, properties. (Doesn't help OP)

---

### Post by swisscow on 2008-07-03
> **swisscow said:**
> Right click on the file in the search result, properties.

Sorry, didn't read it in detail. Please ignore me

---

### Post by chrisccoulson on 2008-07-03
You can resize the properties box in Nautilus to see more of the path, but it isn't obvious really. Just hover over the right hand side to see the grab handle. Obviously, if the path is too long then you may be restricted by the horizontal size of your screen.

Hope that helps

---

### Post by jeffimperial on 2008-07-03
> **timandjulz said:**
> I used Nautilus to search for duplicate files.  e.g. I search for "Taxes*.doc".  It comes back with two documents but I cannot tell what the paths are so I don't know which is the duplicate I want to delete.

There is no way to set "path" as a visible column and the properties box chops off long paths.  :confused:  Opening each document is out of the question because it can take a long time... and sometimes there is no file association.

Is there a way to do this in Nautilus?  If not, where can I report this for fixing/adding?

Thanks,
Tim
You can use fdupes

In a terminal, do: ```
$fdupes -r ./stuff > dupes.txt
```

You could easily identify the offending files and be sure that you're getting the right "duplicates" because it identifies each file's unique md5 hash.

Also, if you want a nice GUI for this, you can use [fsflint]("http://www.pixelbeat.org/fslint/") ```
sudo apt-get install fslint
```

---

### Post by ghostdog74 on 2008-07-03
> **timandjulz said:**
> I used Nautilus to search for duplicate files.  e.g. I search for "Taxes*.doc".  It comes back with two documents but I cannot tell what the paths are so I don't know which is the duplicate I want to delete.
use the command line.:mad:

```

find / -name "Taxes*doc" -print

```

---

### Post by silkstone on 2008-07-03
Have you tried using the Tracker Search Tool to do the search? That seems to display the full path below each file.

---

### Post by timandjulz on 2008-07-03
> **silkstone said:**
> Have you tried using the Tracker Search Tool to do the search? That seems to display the full path below each file.

I haven't used Tracker.  I loaded it but it won't find anything.  I searched for keywords, dates, etc.  And there is no help in it.  I am probably doing something wrong but without help it is pretty useless.

---

### Post by silkstone on 2008-07-04
You have to enable Tracker and set it up in Preferences > Search and Indexing. It can take a long time to do the initial indexing. A magnifying glass icon should then appear at the right hand side of the top panel.

You should be able to search for filenames or any part of a filename. I've not tried other things, but that does work very well.

---

### Post by hippo31 on 2008-08-22
Hi,

Like *timandjulz* initially did, i'm also looking on how to display the full path of my seach results, but in nautilus and not using some other third part app.
ie. neither through **tracker** i've desactivated, nor via "[FONT="Courier New"]**find**[/FONT]" CLI command that i use often in my work enough to need some more friendly and simplier interface at home ...

I've disactivated tracker from my system because i don't want a daemon to run permanently indexing all my files. Most of the time i know where they are.
And when i don't know, the search function included in nautilus serves well most of my needs.
Except for diplaying the full path.

Maybe some dark, hidden gconf key can make the trick.
And if this actually exists and one here have heard about, it should be nice to let us know about it

---

### Post by philinux on 2008-08-22
Places>Search For Files

The results show the file name then the full path.

This is different from the nautilus search and I think better.

---

### Post by r0g on 2008-09-05
Damn this is SO needed in Nautilus it hurts, as is 'Open containing folder'. I just switched from XP a few days ago, mainly on the strength of Ubuntu looking like it had a good file manager at last, and indeed for the most part it's excellent but I hadn't noticed this omission til today. The main (possibly only) thing Windows has always done better is file management IMHO, there's seemingly still nothing to beat Explorer and although I'm impressed with Wine I'd be very surprised if it didn't choke instantly on explorer.exe ;-)

I guess I should brush up on my C++ and become a contributor eh!

Roger Heathcote

---

### Post by gkkg on 2009-12-13
Here is my solution to add an option 'Open containing folder' in the context menu in Nautilus:

1)install nautilus-actions (with synaptic or apt-get)
2)System>Preferences>Nautilus Actions Configuration
3)click on 'Add'
4)label= Open containing folder', path= nautilus, parameters= %d
5)OK and exit

Then simply right-click on the search result and select Open containing folder.
Now, I'd be interested to know if I can open the containing folder in a new tab rather than a new window. Is there an option one can add to the nautilus command?

---

### Post by ronewolf on 2009-12-29
> **r0g said:**
> Damn this is SO needed in Nautilus it hurts, as is 'Open containing folder'. 
On Hardy (and I assume thereafter?) the open containing folder option seems to be in the base install.

I agree with you that showing the path of the found files in the file browser search is a _must have_ feature. Puzzled as to why its not an option... Maybe its that the old-time Unix folks can do all of this from the command line and are more than satisfied with that. For the rest of us its a basic and expected feature of file browsing. The lack of simple stuff like this is one more detriment to the adoption of Unix.

---

### Post by Morbius1 on 2009-12-29
Open **Terminal**
Type **gnome-search-tool**

Click on "Select more options"

You can search by file name, file type, text within files, date, etc...

So you can search for all .txt files that contain the word ubuntu and it will display the name of the file and it's path.

You can create a launcher for it, put it on the panel, and even create a nautilus-script for it.

---

### Post by ronewolf on 2010-01-02
> **Morbius1 said:**
> Open **Terminal**
Type **gnome-search-tool**

Click on "Select more options"

You can search by file name, file type, text within files, date, etc...

So you can search for all .txt files that contain the word ubuntu and it will display the name of the file and it's path.

You can create a launcher for it, put it on the panel, and even create a nautilus-script for it.

at least with Hardy, the gnome-search-tool is found in the *Places* menu as *Search for Files*. so what you suggest is redundant.

in any case the gnome-search-tool also has many short falls. for instance its not integrated with Nautilus, so using it as you suggest (or from the *Places->Search for Files* menu as i suggest) still means that i have to separately navigate to the directory that i want to search from. 

but that's easily addressed,i added a one line Nautilus script that i called search. the one line is, duh, ```
gnome-search-tool

```

now in the folder that i want to search from, i 'only' have to right click, mouse to scripts, mouse to search. well, its a start.

btw, to do this i had to remember where Nautilus scripts reside - i didn't because they aren't in .nautilus... ugg.... so i searched for them (ha ha the ole recursive joke there)... and yikes, there they are in the gnome2 directory. not a very intuitive location....

still, the remaining issues are many. for instance the gnome-search-tool won't display icons/images only file lists. i could go on....

the helpfulness of the Ubuntu community makes up for many of Ubuntu's and Linux's usability shortfalls, but why have these shortfalls at all? this is not rocket science...

---

### Post by Morbius1 on 2010-01-02
> at least with Hardy, the gnome-search-tool is found in the *Places* menu as *Search for Files*. so what you suggest is redundant.

in any case the gnome-search-tool also has many short falls. for instance its not integrated with Nautilus, so using it as you suggest (or from the *Places->Search for Files* menu as i suggest) still means that i have to separately navigate to the directory that i want to search from. 
but that's easily addressed,i added a one line Nautilus script that i called search. the one line is, duh,  	Code:
 	gnome-search-tool 


As I said in my original post you can create a nautilus script for it as you have done. I do think your script has a problem however , it won't search properly if you select a directory that contains a space in its name.

I think this will work better:
```
gnome-search-tool --hidden --allmounts --contains= --path="$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)"
```In 9.10 the **allmounts** parameter is now the default so it should be removed from the script above.

---

### Post by jadonchristensen on 2010-06-29
> **gkkg said:**
> Here is my solution to add an option 'Open containing folder' in the context menu in Nautilus:

1)install nautilus-actions (with synaptic or apt-get)
2)System>Preferences>Nautilus Actions Configuration
3)click on 'Add'
4)label= Open containing folder', path= nautilus, parameters= %d
5)OK and exit

Then simply right-click on the search result and select Open containing folder.
Now, I'd be interested to know if I can open the containing folder in a new tab rather than a new window. Is there an option one can add to the nautilus command?

Thanks for this tip. Also to note, I had to logout/login to Ubuntu to see the change on the menu.

---

### Post by jcoles on 2011-10-22
In 11.10, you can add Location as one of the Visible Columns (see View menu). The column is initially sized as wide as the longest path. Depending on the path length and your screen, you might need to scroll horizontally. An obvious solution for content that's too wide for a column would be a tool tip to show the entire content. Do the Nautilus developers not know that common GUI feature? 

The Properties dialog for a file has a fixed width field for the Location. It does not expand when you resize the dialog. If the path is long it is truncated, ending with "..." In many cases, the truncated path is useless. Really, we need full path or nothing.

---

