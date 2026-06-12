---
title: "remove sertain text from terminal output for nautilus script"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by Froylan on 2013-06-23
hi
so I am doing a nautilus script that uses a file to run a command in a directory but $NAUTILUS_SCRIPT_CURRENT_URI adds "file://" and I want to remove that, here is my script if it helps```
frmdata=$(yad --title "script 1" --entry --text="please incert the URL")
~/.aa\ sh\ tools/tumbdl.sh $frmdata $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

---

### Post by vipulkumar7 on 2013-06-23
Simple use rm -rf to delte the file :)

---

### Post by sudodus on 2013-06-23
Try

```
 ${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/file\:\/\/}
```

instead of

```
 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

---

### Post by Froylan on 2013-06-23
> **vipulkumar7 said:**
> Simple use rm -rf to delte the file :)

there is no file, it is a filepath

---

### Post by Froylan on 2013-06-23
neither worked :(

---

### Post by sudodus on 2013-06-23
I tested the method in post #3 like this and it worked.

```
$ NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=file://svammel
$ echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
file://svammel
$ echo  ${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/file\:\/\/}
svammel
```

Maybe there is some other error in your script.

---

### Post by Froylan on 2013-06-23
any way to see nautilus working in the terminal? watching what happens can help

---

### Post by sudodus on 2013-06-23
What do you want to do?

It is probably easier to help you this way. Maybe there is another way to do it.

---

