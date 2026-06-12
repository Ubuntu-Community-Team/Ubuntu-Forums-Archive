---
title: "Help with getting files to show in Home directory"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-10
My Home directory (in the GUI) is showing a different set of files than the directory listing in Terminal (even when I tell the GUI to show hidden files). When I issue the command (in Terminal) "open &disown filename" I get the following message: "Couldn't get a file descriptor referring to the console"

I'd like to open the file that Terminal says is sitting there (and the GUI can't see). I'd appreciate it if anyone could tell me why the two interfaces show different sets of files, and neither of them will allow me to open the file (which is a downloaded PDF). 

Thanks.

---

### Post by deadflowr on 2013-06-10
Don't know what version your on, don't think it would matter, but try
```
evince filename
```

Evince is the document viewer you use to read PDFs in Ubuntu.

Don't know what open does, let alone open & disown...

Can't help distinguishing between what's in the terminal output and what's in the nautilus output without more info on what commands your typing in the terminal.

---

### Post by Cheesemill on 2013-06-10
Can you post a screenshot of your home folder from the file manager as well as the output of...
```
pwd && ls -lha
```

Also what are you expecting the 'open' command to do? It probably has a different meaning to what you think it does.

---

### Post by steeldriver on 2013-06-10
... maybe you want

```
**xdg-**open *filename* **& disown**
```

---

### Post by jps2012 on 2013-06-10
Deadflowr: That did it. I didn't know about "evince." 

I made an assumption about "open." I assumed that if it opened an application, it would open a file. Oh, so wrong. 

I tried "xdg-open *filename* & disown," interestingly, it doesn't open the file, but it does open a "home folder" window and highlights the file. So, while it won't open a file, it could be used to find it (which worries me; the command isn't supposed to behave that way, right?). 

Cheesemill: I'd post a screenshot of my home directory, but one of the files is called "my_plans_to_overthrown_liberia" and I was planning to make it a surprise. (But thanks for the offer.)

---

### Post by ajgreeny on 2013-06-10
If you are in the folder containing a file both xdg-open and exo-open followed by the filename should open it.  I have no idea why your use opened a filemanager window, unlerss of course, you used xdg-open <*foldername*>

---

### Post by deadflowr on 2013-06-10
As I recall, xdg-open opens the file with whatever the default application for the file/filetype is.
If it doesn't have a default then the file manager will open.

---

### Post by jps2012 on 2013-06-10
ajgreeny: Nope, I issued the filename, not the directory name. Pretty weird, I know. 

I tested it on another file: xdg-open filename2" 

I got the same behavior. It opened a "finder-type" window and highlighted the filename. Now that command is my new filefinder. 

Deadflowr: I've got four applications that can and/or edit PDFs, so it's not that there's no application associated with the command. The PDF (once I found it) opens fine.

---

### Post by ajgreeny on 2013-06-12
> **jps2012 said:**
> The PDF (once I found it) opens fine.
But does it open from your file manager with a double click, or do you have to right click and choose "open with"?

---

### Post by jps2012 on 2013-06-12
ajgreeny: It opens with a double-click. I have PDF CHAIN, PDF MOD, PDF EDITOR and gPDFText Editor installed.

---

