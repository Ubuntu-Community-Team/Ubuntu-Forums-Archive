---
title: "file deletion"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by rfbeck on 2008-08-21
I'm trying to delete my bookmarks.html file. I'm doing this through the terminal and using the sudo command. I am embarrassed to admit the I don't know what the delete command is. Is it "delete"? If so it's not working.
Thanks.
Robert

---

### Post by kpatz on 2008-08-21
"rm"... as in **rm bookmarks.html**

You don't need to use sudo if the file is in your home directory, and thus owned by you.

---

### Post by ByteJuggler on 2008-08-21
It's "rm", in lieu of "remove".

---

### Post by tuxxy on 2008-08-21
Its not delete its rm, but I advise you read this before using the command as it could be harmful, 

[https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html#rm](https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html#rm)

why cant you delete it via a **gksu nautilus** anyway?

---

### Post by pauper on 2008-08-21
tuxxi, could you elaborate on why you consider taking over your filesystem as
root ("gksudo nautilus") is a safer way (I imply--you didn't say that) opposed
to deleting a single file ("sudo rm /path/to/file")?

Confused.

---

### Post by kpatz on 2008-08-21
The bookmarks.html file is located in $HOME/.mozilla/firefox/*.default/bookmarks.html.

It's owned by the user, so there's no need to use sudo at all.

Just use the rm command straight out, no sudo.

---

