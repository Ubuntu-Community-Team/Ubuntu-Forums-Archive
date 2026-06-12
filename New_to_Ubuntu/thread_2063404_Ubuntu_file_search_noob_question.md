---
title: "Ubuntu file search noob question"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Paco62 on 2012-09-27
I have been using Ubuntu for some time now, but never really had the need to search for a specific file until recently.  I used nautilus browser set to 'file system' to attempt to search the entire drive.  The search lasted a second and turned up zero results.  I am guessing that it only searched the names of the 21 main folders (bin, boot, cdrom, dev etc.) and three files with shaded-out names and did not actually search the entire drive including subfolders, files etc. So I selected all of the 24 files and folders in the nautilus window and then searched, and that worked:  the search took some time and found the file I wanted.  But the search function in nautilus is very simple with no advanced options.  I tried gnome-search-tool, which has advanced options, set to search 'file system' but again the search lasted only a second and turned up zero results.  In "look in folder" I clicked "other" and came up with  a browse window with a sidebar.  Clicked 'file system' in the sidebar and there is a list of the 24 folders and files in the right side.  But they are in list format, not icon format and there seems to be no way to select them.  In the future, I might wish to to a search with advanced options, so is there anyway to get gnome-search-tool to actually search the whole drive including subfolders, files etc.?  Am I missing something obvious?

---

### Post by HiImTye on 2012-09-27
I tend to avoid graphical search tools. the two main console tools are 'locate' which uses an indexing service and therefore searches very quickly, so long as the file was created before it was last indexed, and 'find' which does a live search of the drive and can take some time, but will find any files (that the user has permissions to see). most graphical programs are just front ends for these tools. I would take a look at the man pages for them:
```
man find
man locate
```

---

### Post by s1baker on 2012-09-27
I use gnome-search-tool all the time and I can search all folders and sub folders with no problem.
When you select "look in folder", you have a number of choices, "file system" being one, or you can select "other".
If you select "other", navigate to the folder that you want to search and then select "open" in the bottom right hand corner of the
browse window.
This will bring you back to the Search for Files window and your ~where to search~ selection will be displayed in the "Look in folder" field.

Put the name of folder or file you are looking for in the "Name contains"
filed.

If you want to search for specific text in any of the files ( including the files that are in all sub-folders ), then put 
an asterisk * in the "Name contains" field, hit the "Select more options" tab, and in the "Contains the text" field,
put in the text you are looking for.

On the list of hits that you get, just double click on any one of them and you will be taken to where that file is located.

---

### Post by jerrrys on 2012-09-27
Your described method of nautilus filesystem search works for me.  And I am not finding any bug reports on this (there are bug reports about hidden folders searches).

---

### Post by centaurusa on 2012-09-27
> **Paco62 said:**
>  In the future, I might wish to to a search with advanced options, so is there anyway to get gnome-search-tool to actually search the whole drive including subfolders, files etc.? 

As one of the replies to your post indicated, the find and locate commands both do what you wish, but using somewhat different methods.  However, rather than just consulting the relevant man pages, there are two good posts about the use of these commands at:

Find files on Linux with the command locate
[http://linuxaria.com/howto/find-files-on-linux-with-the-command-locate?lang=en](http://linuxaria.com/howto/find-files-on-linux-with-the-command-locate?lang=en)
 

How-To: Find files on your computer with find
[http://www.debuntu.org/how-to-find-files-on-your-computer-with-find](http://www.debuntu.org/how-to-find-files-on-your-computer-with-find)


And, a post on using find through a bash script file at:

Find-ing Files
[http://linuxnorth.wordpress.com/2012/08/23/find-ing-files/](http://linuxnorth.wordpress.com/2012/08/23/find-ing-files/)

---

### Post by Puzzleman on 2012-09-27
Not sure what system you are using but in 12.04 you can use the "dash home" search feature. Upper left purple button.

I have found it quick and efficient. You can set it to search various areas such as applications, files & folders, music, video but I have found it is fast enough to just type in your search word and it will find your target very quickly.

If you aren't familiar with the feature download the 12.04 program manual.

I am new to Ubuntu and don't know when this feature was built into the system.

Puzzleman

---

### Post by Paco62 on 2012-09-27
I solved this by going into gconf-editor, apps-gnome search tool and clicking on 'disable-quick-search'

---

