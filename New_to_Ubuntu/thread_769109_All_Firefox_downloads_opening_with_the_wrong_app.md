---
title: "All Firefox downloads opening with the wrong app"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by belovedmonster on 2008-04-26
Everytime I was downloading a file with Firefox 3 in Xubuntu 8.04 it was asking me to pick what I wanted to open the file. I assumed this meant the individual app for that particular file type so with this file being a zip I picked fileroller. 

Now I find every thing I download wants to open with Fileroller. Which for most file types results in an error message.

How do I fix this? I tried looking through the preferences but I cant seem to find any mention of Fileroller to change.

---

### Post by sdennie on 2008-04-26
I think you can adjust the settings you are interested in by going to Edit->Preferences->Applications in Firefox.

---

### Post by belovedmonster on 2008-04-26
Well maybe this is the problem, but going to that section shows no programs to alter the settings of. :confused:

---

### Post by belovedmonster on 2008-04-26
Even clicking the option "Open Containing Folder" is bringing up Fileroller. Someone please help :(

---

### Post by belovedmonster on 2008-04-26
Problem solved. I deleted the mimeTypes.rdf file as discussed here:

[http://forums.mozillazine.org/viewtopic.php?p=3352489#3352489](http://forums.mozillazine.org/viewtopic.php?p=3352489#3352489)

---

