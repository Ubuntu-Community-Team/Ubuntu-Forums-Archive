---
title: "[SOLVED] Can't delet files in Trash"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by captgadget on 2008-11-11
Sorry, could not display all the contents of "Documents": Operation not supported

Also get this error message: Sorry, could not display all the contents of "Documents": Operation not supported

Did gksudo in terminal and get this message: unable to add monitor:  Operation not supported

I also get this message in the terminal:--- Hash table keys for warning below:
--> trash:///media%252fdisk-1%252f.Trash-1000%252fcaptgadget/.local/share/Trash/files/Documents.4/Documents
--> trash:///
--> file:///home/captgadget
--> file:///root

(nautilus:8286): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 4 elements at quit time (keys above)

---

### Post by bumanie on 2008-11-11
This should remove the files from trash. Be aware this will **remove them permanently and it will remove all of them**, so if there are any files you are not 100% sure about removing, move them or copy them first.
> sudo rm -rf /home/yourusername/.local/share/Trash/files/*


---

### Post by captgadget on 2008-11-11
That didn't work. I still have locked files in the trash that won't delete.

---

### Post by Austin17 on 2008-11-11
I have 7.10, so you might want to verify the location of your Trash folder, but to do that operation for me the command would be:

```
sudo rm -rf /home/yourusername/.trash/*
```

Just substitute "yourusername" with your account's username.

---

### Post by captgadget on 2008-11-11
The files are gone in .local but the problem I'm having are in the trash can in the panel called Trash - file Browser that contains locked files that I can't delete.

---

### Post by philinux on 2008-11-11
Use this.

```
gksudo nautilus
```Browse to the trash files and delete them with nautilus.

---

### Post by captgadget on 2008-11-11
when i do I get this message and I don't know what or how to fix: ** (nautilus:10799): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:10799): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:10799): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-share extension
seahorse nautilus module shutdown

---

### Post by philinux on 2008-11-11
Try another method.

[http://www.arsgeek.com/2008/08/05/how-to-delete-stuck-folders-and-files-from-your-trash-in-ubuntu/](http://www.arsgeek.com/2008/08/05/how-to-delete-stuck-folders-and-files-from-your-trash-in-ubuntu/)

---

### Post by captgadget on 2008-11-11
That's what I don't understand. Home/.local/share/trash is empty. It's when I open the trash can it gives me files in there that are locked and I can't get to them to remove them.

Thanks for you  help.

---

### Post by captgadget on 2008-11-11
Hey, the files in trash - file browser are some of the same files in my home/documents folder. Is there a connection here?

---

### Post by captgadget on 2008-11-11
Don't know whose solution worked but the Trash - File Browser is now empty. I did a restart, checked and it was empty. Did a shut down, checked and it was empty. Did another restart, checked and it's still empty.

Thanks everyone

---

### Post by Jesua on 2009-01-12
> **bumanie said:**
> This should remove the files from trash. Be aware this will **remove them permanently and it will remove all of them**, so if there are any files you are not 100% sure about removing, move them or copy them first.

Thanks a lot, it worked... :guitar:

---

