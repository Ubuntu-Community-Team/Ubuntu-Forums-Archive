---
title: "Copy a folder with gnomevfs-copy?"
date: 2007-09-18
forum: Programming Talk
---

### Post by wayanwolvie on 2007-09-18
Does anyone know how to copy a folder (with files inside) using 'gnonevfs-copy' in terminal?

---

### Post by unrar on 2007-11-17
i just used this command to rescue data from an old os x hard drive i thought was dead! it's really easy...

gnomevfs-copy /yourfolder/ /destination/

if you are having trouble with the source and destination you can just drag and drop the source and destination into the terminal window and it will pin them down for you. i had a problem with recovering folders with spaces in them. to make it even more complicated, the folder was inside another folder with locked permissions from os x. i used the su command to gain root access, then i navigated inside the locked folder. i then used the ls command to show me the files and folders inside. my folder i needed to recover was named "apartment before 7-7-7". so to copy this my commands were this:

 gnomevfs-copy apartment\ before\ 7-7-7/ /home/unrar/recovery/

you have to use the \ before the spaces in the folder name, otherwise it can't find it. 

p.s. the autocomplete feature in terminal is great! just press tab after a few keys and it does the rest for you!

---

