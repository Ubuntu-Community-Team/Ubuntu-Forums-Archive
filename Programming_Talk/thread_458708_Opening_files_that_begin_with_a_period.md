---
title: "Opening files that begin with a period"
date: 2007-05-29
forum: Programming Talk
---

### Post by LeeU on 2007-05-29
Using an editor, how do I open a file the begins with a period, e.g., ".htaccess"?

---

### Post by Medieval_Creations on 2007-05-29
Any file or directory with a . infront of it just means it's hidden.
You should be able to open it like any other file.

```
pico .htaccess
```

Depending on the file you may need to use sudo.  Also if you're using a GUI when you click on Open File, most have an option that shows hidden.

---

### Post by LeeU on 2007-05-29
> **Medieval_Creations said:**
> Any file or directory with a . infront of it just means it's hidden.
You should be able to open it like any other file.

```
pico .htaccess
```

Depending on the file you may need to use sudo.  Also if you're using a GUI when you click on Open File, most have an option that shows hidden.

In the case I mentioned, the editors I use (i.e., Cream version of vim) don't have an option to show hidden files.

---

### Post by xtacocorex on 2007-05-30
Sometimes when I need a GUI editor to open a hidden file I'll open it from the terminal.
```
gedit ~/.bashrc &
```

---

### Post by LeeU on 2007-05-30
Thanks, I'll give it a try. I just thought there was something I could do so i could just open it from the program itself. I use n editor under Wine and was trying to do it that way also.

---

### Post by bukwirm on 2007-05-30
In vim, ":e *filename*" opens any file, as long as you have permission to do so (and have the filename correct).

---

