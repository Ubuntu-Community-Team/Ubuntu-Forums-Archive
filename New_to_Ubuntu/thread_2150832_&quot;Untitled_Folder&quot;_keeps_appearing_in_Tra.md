---
title: "&quot;Untitled Folder&quot; keeps appearing in Trash bin"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by altirisx on 2013-06-02
A folder called "Untitled Folder" keeps appearing in my trash folder, I try emptying the trash and nothing happens. The folder seems to have root permission, I tried removing the folder as root but then "Untitled Folder.2" comes up. I am running Ubuntu 13.04 is this a new glitch?

---

### Post by ibjsb4 on 2013-06-02
Right click on it and go to properties.  Where is it coming from?  Maybe you have recently install software that generates it.

---

### Post by ShadowVegan on 2013-06-02
When you say it keeps appearing and nothing happens when you delete it, do you mean that you successfully delete it but it comes back, or that you are unable to delete it? If you are unable to delete it, does it give you an error message, and if so what does the message say?

---

### Post by DogMatix on 2013-06-02
Have you tried running Nautilus as root and deleting it that way:

ie:

```
gksudo nautilus
```

navigating to Trash and see what is there.

Makes me cringe a bit but running Nautilus this way has solved similar issues for me in the past when my terminal abilities have *abandoned* me.

---

### Post by altirisx on 2013-06-03
I went into .local/share/Trash/info and I found where the file was coming from, It was from a bash script I tried making in X11 to lower sensitivity on my mouse upon bootup.

---

