---
title: "[SOLVED] How do I forced emptied Trach Can?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Muhammad on 2008-06-30
I dunno lol
but srsly I need to know

---

### Post by fatality_uk on 2008-06-30
Sounds like you have a file or directory in the "trash" that you don't have rights to delete. Check in the trash and see if this is the case.

---

### Post by aeiah on 2008-06-30
your trash folder is called .username-trash, i believe. in hardy though it was changed to .local/share/Trash. a folder with a . infront of it is hidden, so in nautilus press ctrl+h to unhide your hidden files and folders and find where your trash folder is. it'll be on the partition which you deleted the file from.

once found, access this via sudo and remove it either from the command line
```
sudo rm /path/
```
or by launching root nautilus and navigating to your problem file in the trash folder.
```
gksudo nautilus
```

---

### Post by Muhammad on 2008-06-30
> **fatality_uk said:**
> Sounds like you have a file or directory in the "trash" that you don't have rights to delete. Check in the trash and see if this is the case.
This may sound freaky!
But there is no .trash in the home directory and yes I have unhidden the files!

---

### Post by WRDN on 2008-06-30
To delete things, you can do one of 2 things (that I know of).

The first option is to enter the terminal and change the directory to the following location:

```
cd /home/[username]/.local/share/Trash
```

Then type:

```
sudo rm -r files
```

and

```
sudo rm -r info
```

This will delete the "files" and "info" folder (where all trash is) and all of its contents.

You could also use the command:

```
gksudo nautilus
```

This way, you can navigate to, and delete the folders in the file browser.

It is safe to delete the folders, and when you delete something now, the folders will be created again.

---

### Post by lukjad on 2008-06-30
> **Muhammad said:**
> This may sound freaky!
But there is no .trash in the home directory and yes I have unhidden the files!

This is what worked for me. I have the exact same problem and this is what works. I can't open the trash bin or say delete trash except with this command. Go to Applications->Accessories->Terminal and type:
```

sudo rm -r ~/.local/share/Trash/files/
```
This should do it!

---

### Post by Muhammad on 2008-06-30
Thank you WRDN for giving me those useful command and the actual location of .trash

And thank you lukjad for the swift and quick solution

One more thing I wonder though
What is the difference between gksudo and normal sudo?

---

### Post by ayenack on 2008-06-30
gksu/gksudo are if you want to open graphic apps such Gedit, whereas sudo is used for non-graphic apps or commands. There can be some permissions issues when opening graphical apps with sudo instead of gksu or gksudo apparently.

BTW. This is what I use in Ubuntu 8.04 to clear stubborn trash. In terminal.

**sudo rm -rf ~/.local/share/Trash/files/***

Will get rid of everything in trash.

---

### Post by lukjad on 2008-06-30
Remember to show that this is solved (assuming it is) by going to "Thread Tools" and clicking on "Mark Thread as Solved".

---

### Post by ayenack on 2008-06-30
@lukjad007

Who's right? ;)

---

### Post by Inxsible on 2008-06-30
> **Muhammad said:**
> .....[snip]One more thing I wonder though
What is the difference between gksudo and normal sudo?


Here's a link that explains the difference

[Graphical Sudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

