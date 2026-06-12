---
title: "somehow put all icons from home folder on desktop"
date: 2020-05-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-05-12
running 20.04. note just want to delete them off desktop except for my home folder "ray" and trash link. any idea how to do in one command or have to remove individually. /tks

---

### Post by ajgreeny on 2020-05-12
I'm not sure what you mean by "all icons from home folder" but I suspect somehow you have either moved all the files and folders normally in the /home/username folder to the /home/username/Desktop folder or you have somehow created links from those files and folders to the Desktop.

In terminal show us the output of command ```
ls -la
``` and then ```
ls -la Desktop
```
The first should list all files and folders in your home line by line, the second may show some launchers (.desktop files) if you use any on the desktop or maybe nothing if you do not normally place files on the desktop.  If links have been created the output will show that they are all links and can therefore be deleted but come back here with the output first and we can help you more.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by &amp;KyT$0P# on 2020-05-12
Also could you please post the output from running this command in Terminal -
```
cat ~/.config/user-dirs.dirs
```

---

### Post by rburkartjo on 2020-05-12
hal

---

### Post by rburkartjo on 2020-05-12
looks like i need to change first line to read

XDG_DESKTOP_DIR="$HOME/Desktop"
  

how would i do that in terminal/tks

---

### Post by Impavidus on 2020-05-12
~/.config/user-dirs.dirs is a plain text file. You can use any text editor you like. If you want to do it in terminal, I suggest nano or vim.

Most config on Linux is in plain text files.

---

### Post by rburkartjo on 2020-05-12
tks ya'll got it fixed

---

