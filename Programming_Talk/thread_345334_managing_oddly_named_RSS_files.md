---
title: "managing oddly named RSS files"
date: 2007-01-24
forum: Programming Talk
---

### Post by bvmou on 2007-01-24
I am trying to create a couple of tools to manage podcasts on a generic mp3 player.  As of now I have a script for a sync-like feature with rhythmbox, generally working.  There is one problem, which I think is that some RSS feeds name files with things that happen to also be bash arguments, like colons, and I can't handle them with a straight copy.  here is what I'm getting:

```
cp: cannot create regular file `/media/usbdisk/podcasts/KCRW\'s Politics of Culture/pc070123Will_Redevelopment_D.mp3?1169601287': Invalid argument
cp: cannot create regular file `/media/usbdisk/podcasts/KCRW\'s Le Show (Harry Shearer)/ls070121le_Show_-_January_21.mp3?1169419424': Invalid argument
cp: cannot create directory `/media/usbdisk/podcasts/NPR: On Point with Tom Ashbrook': Invalid argument
```

Is there any way to rename these things?  I'm not sure I understand how Rhythmbox or Linux generally handle oddly named files and directories, and am totally green in general.  Thanks in advance

---

### Post by jblebrun on 2007-01-24
> **bvmou said:**
> I am trying to create a couple of tools to manage podcasts on a generic mp3 player.  As of now I have a script for a sync-like feature with rhythmbox, generally working.  There is one problem, which I think is that some RSS feeds name files with things that happen to also be bash arguments, like colons, and I can't handle them with a straight copy.  here is what I'm getting:

```
cp: cannot create regular file `/media/usbdisk/podcasts/KCRW\'s Politics of Culture/pc070123Will_Redevelopment_D.mp3?1169601287': Invalid argument
cp: cannot create regular file `/media/usbdisk/podcasts/KCRW\'s Le Show (Harry Shearer)/ls070121le_Show_-_January_21.mp3?1169419424': Invalid argument
cp: cannot create directory `/media/usbdisk/podcasts/NPR: On Point with Tom Ashbrook': Invalid argument
```

Is there any way to rename these things?  I'm not sure I understand how Rhythmbox or Linux generally handle oddly named files and directories, and am totally green in general.  Thanks in advance


How are you handling the filenames? In Linux, "special" characters, like space, colon, quote, and a few others, are handled by placing a backslash in front of the character. So a file called 
Cool Feed.xml

would be

Cool\ Feed.xml

You can avoid some backslashes by single quoting the file.

---

### Post by ansi on 2007-01-24
Or you can also wrap you filename to single quotes, like this:
```
cp 'file with long name.txt' /tmp/normal_file.txt
```


[COLOR="Silver"]
[SIZE="1"]
Upd: Sorry, I didn't notice the text:
> You can avoid some backslashes by single quoting the file.[/SIZE][/COLOR]

---

### Post by bvmou on 2007-01-24
It may be the case that even if I change the names, future episodes will present the same problem.  I was thinking it may be easiest (for the "cannot create directory" issue) to do something like 

```
find ~/music/podcasts -mindepth 2  -exec cp -u /media/usbdisk/podcasts/orphans
```

but does update in this case only update the things that weren't copied in some way onto the usbdisk, or will I get a folder full of everything that is also in the subdirectories named by rhythmbox?

Is there a way to do something like:

1.  find all the .mp3 podcast files on the harddisk folder
2.  check if they were copied into the appropriate folders on the flash media by the recursive update copy
3.  if not, copy them into a separate folder.
4.  if the file names are leading to error messages, change them, maybe with a date time variable, and move them as above


It's likely I'm missing something obvious, feel free to point that out if so.  Does anyone know of a command line RSS tool, BTW?

---

### Post by jblebrun on 2007-01-24
Maybe what you want to try doing is doing a search/replace on the filename, and replace all invalid characters with underscores. 

As for command-line RSS... if all you want to do is fetch the RSS feed, you can just use wget.

---

