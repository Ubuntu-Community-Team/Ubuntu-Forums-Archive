---
title: "Deleting a Movie File"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-08-03
I dragged the Video TS file and Audio TS File off of a DVD onto my desktop, however I am having issues deleting it and I don't know why. It's a fairly large file, but I have a screen shot of what's happening with it. Any help on how to delete this file? Maybe a command line trick?

Armaniboy :KS

---

### Post by sharks on 2008-08-03
select the file and press shift+delete. it will permanently delete the file. if it says any error post it here.

---

### Post by drs305 on 2008-08-03
> **Armaniboy said:**
> I dragged the Video TS file and Audio TS File off of a DVD onto my desktop, however I am having issues deleting it and I don't know why. It's a fairly large file, but I have a screen shot of what's happening with it. Any help on how to delete this file? Maybe a command line trick?

Armaniboy :KS

The DVD files are owned by 'root'. Open your favorite file browser as 'root', then delete the files. 

If you have 'root' trash that won't delete, also go to ~/.local/share/Trash and delete the 'files' and 'info' folders, as well as /root/.local/share/Trash and delete the 'files' and 'info' folders there.
```
gksu nautilus $HOME/Desktop
```

---

### Post by magnus0 on 2008-08-03
They are folders? Aren't they?

try: ```
cd Desktop && rm -rf VIDEO_TS && rm -rf AUDIO_TS
```
or, if that doesn't work, try:
```
sudo rm -rf VIDEO_TS && sudo rm -rf AUDIO_TS
```

---

### Post by sisco311 on 2008-08-03
> **Armaniboy said:**
> I dragged the Video TS file and Audio TS File off of a DVD onto my desktop, however I am having issues deleting it and I don't know why. It's a fairly large file, but I have a screen shot of what's happening with it. Any help on how to delete this file? Maybe a command line trick?

Armaniboy :KS
change the owner of the files:
```
sudo chown -R $USERNAME: ~/Desktop
```
then try again.

---

### Post by Armaniboy on 2008-08-03
This is the screenshot I get when I tried to do shift + delete...

---

### Post by ace007 on 2008-08-03
the easiest way maybe launching nautilus (file explorer) with root permissions and navigating to the Desktop.

```

sudo nautilus

```

Use the window that just opened and go delete the file.  Also, the advice given to you above by other members is all good advice, try it.

---

### Post by drs305 on 2008-08-03
> **Armaniboy said:**
> This is the screenshot I get when I tried to do shift + delete...

Shift-delete may send folders/files into oblivion, bypassing the trash folders, but it still won't allow a normal user to delete files owned by root. Try some of the other methods, and if you are going to run gui-based apps, 'gksu' or 'gksudo' is preferable to 'sudo', which is used for command-line operations.[Runnibng Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Ru$$i@N on 2008-08-03
yeah man, like mangus0 said, go with
```

sudo rm -rf /path/to/the/file

```
where path/to/the/file is the path to the file, that you're trying to delet :)
sudo will ask you for your password (that gives you root privileges)
rm is remove
-rf are the options (r - recursive, deletes the  folder and the content of it; f - forced, no questions like "are you sure?")

---

### Post by Armaniboy on 2008-08-03
I tried using the nautalis command, but there wasn't a file under desktop.... but I can see it on the desktop... the name of the file is 

:confused:Video_TS

---

### Post by sisco311 on 2008-08-03
> **Armaniboy said:**
> I tried using the nautalis command, but there wasn't a file under desktop.... but I can see it on the desktop... the name of the file is 

:confused:Video_TS
try:
```
gksu nautilus ~/Desktop
```

---

