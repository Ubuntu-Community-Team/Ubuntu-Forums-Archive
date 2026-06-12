---
title: "Linking Documents folder to Dropbox"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by mithen2 on 2013-10-29
I managed to link the Document folder to Dropbox via this method:

[LIST=1]
[*]Create "Make Link" of Document Folder (Creates "Link to Documents" Folder) 
[*]Insert "Link to Document Folder" into Dropbox Folder 
[/LIST]
It works and seems so simple and logical :P But I was curious are there any more logical methods to do this? Perhaps without using "Make Link" and maybe using the Terminal? I'm new to Linux/Ubuntu but I'm highly intrigued to learn more about using it :D

---

### Post by newb85 on 2013-10-29
If you use Ubuntu One instead of dropbox (same concept, different company) you can right-click any folder, click Ubuntu One, then click Synchronize this Folder.

Even simpler...

---

### Post by drmrgd on 2013-10-29
You might be better off moving your Documents folder to Dropbox and then putting the link on your local computer(s).  That way you'll be able to access your Documents folder from anywhere you have access to Dropbox, and it'll sort of act as a way to keep the folder backed up in case of disaster.  

If you want to do it from a terminal window, then you can use the **ln** command to create a softlink to the folder.  So, assuming the folder is in Dropbox and you want to put a link to it in your Home directory:

```

ln -s $HOME/Dropbox/Documents $HOME/Documents

```

The variable $HOME here refers to your home directory (/home/mithen2/ for example).

---

