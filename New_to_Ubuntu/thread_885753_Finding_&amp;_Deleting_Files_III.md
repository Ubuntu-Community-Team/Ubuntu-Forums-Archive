---
title: "Finding &amp; Deleting Files III"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-10
[Slight] Repost


  I'm extremely new to the [linux/xubuntu] operating system [and,comps too for that matter] & I need to know how to find a couple of files that I downloaded from the internet & delete them.
 
 If it helps...I [have] found these 2 downloads in firefox under tools/downloads.When I right-click them,"open","open containing folder" & "go to download page" cannot be selected.In other words,those 3 options are greyed out.

Thanks much,
J.Garcia.

:guitar:

---

### Post by SuperSonic4 on 2008-08-10
temporary downloads are usually put into [COLOR="Red"]/tmp[/COLOR]
if not look in firefox's settings, it should say where downloads go

---

### Post by cdtech on 2008-08-10
If you know where they are located just open a terminal and cd /intothatdir and use sudo rm ./downloadedfile

---

### Post by bpowell2005 on 2008-08-10
> **faron45 said:**
> [Slight] Repost


  I'm extremely new to the [linux/xubuntu] operating system [and,comps too for that matter] & I need to know how to find a couple of files that I downloaded from the internet & delete them.
 
 If it helps...I [have] found these 2 downloads in firefox under tools/downloads.When I right-click them,"open","open containing folder" & "go to download page" cannot be selected.In other words,those 3 options are greyed out.

Thanks much,
J.Garcia.

:guitar:

In Firefox go to Edit, Preferences, click the "Main" tab and look for the "Downloads" header...Look for the "Save Files To..." make sure that's checked and note where it's saving the files (I have mine go to the Desktop so I don't forget about them after download!)

---

### Post by faron45 on 2008-08-10
SS..I've looked at the tmp files before.There are some files there but,nothing that looks similar to the things I downloaded.When I downloaded these files I wrote everything down that was placed before my eyes,.So,I should have all the relevant info to find these files.But...hmph !
  
 Tech..As I said,I'm very new to comps..I'M SCARED of the terminal.Heh,heh.NO idea how to use that thing.I've tried to play with it a couple of times but,again,...hmph ! I will try again though.Thanks.

 bp..funny thing...that IS where all my dl's are supposed to be going.Hmmm.Thanks.

---

### Post by cdtech on 2008-08-10
The long approach would be to use "find" on a command line (open a terminal and type):
```
find "nameoffiledownloaded"
```
this will perform a search through your directories.

---

### Post by faron45 on 2008-08-10
Tech..thanks.I will try "the terminal" again when I come back.I have to run out for a couple of hours now though.

  Thanks very much everybody...

---

### Post by cdtech on 2008-08-10
your welcome......

---

### Post by HotCupOfJava on 2008-08-10
Yeah - the default is for the dowloads to go to the Desktop. If they aren't there, perhaps your downloads didn't complete?

---

