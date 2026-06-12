---
title: "How to delete locked files."
date: 2024-05-19
forum: New to Ubuntu
---

### Post by rifqilubis on 2024-05-19
wanna delete this files.

---

### Post by MAFoElffen on 2024-05-19
If you are sure... Do this
```

sudo rm -rf '/etc/apt/trusted.gpg.d/codeblocks-dev-ubuntu-release.gpg*'

```

---

### Post by rifqilubis on 2024-05-26
still there [IMG]https://ibb.co.com/jy2BQbm[/IMG]

---

### Post by rifqilubis on 2024-05-26
[[img]https://i.ibb.co.com/k4fkw5j/linuxtermcodeblocksgpg.png[/img]](https://ibb.co.com/jy2BQbm)

---

### Post by currentshaft on 2024-05-26
Please don't use screenshots to paste terminal output, or any text for that matter: it makes it extremely difficult for people with disabilities to understand your post.

Files owned by root can be deleted as root, as MAFoElffen pointed out. If the file is still there, something is probably putting it back.

---

### Post by Impavidus on 2024-05-26
You use sudo su to start a root shell, then use sudo rm to remove the file. No need to become root twice. You could have skipped the sudo su.

rm -r is used to remove directories with contents. You don't need -r to remove files, but it won't harm.

rm -f is used to remove write protected files without being prompted. You don't need it to for files with write permission or if you don't mind giving confirmation, but it won't harm. (To remove a file, you need write permission on the directory. Write permission on the file itself isn't needed, but if you don't have that, rm provides another saveguard.)

You have the filenames enclosed in single quotes. This means that the * character isn't expanded by the shell; rm lookes for a file that has an actual * in its name. There doesn't appear to be such a file in your first screenshot, but the command gives no error in your second screenshot, suggesting such a file exists. There are no spaces or other special characters in the filename, so you could remove the single quote characters. Then it should work.

---

### Post by MAFoElffen on 2024-05-27
Also... (Additional Notes to clear up some details)

1.) Using -r for recursive doesn't hurt anyting if a just a file and will just be ignored, but still execute.

2.) Before deleting, or it it doesn't delete when asked... Make sure the file is not locked open by a running process.

To do that, I use this script, burrowed from the URL I noted in the script... (Good read there on that.)
```

#!/usr/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com>, 2024.03.20
# Code derived from: https://www.baeldung.com/linux/find-process-file-is-busy
# Find if file is opened by a process
# Takes an argument of a filename
# SYNTAX: mylsof <filename>
# To check "files" and use filters, I came up with this example:
#   mylsof . | grep -v 'dev\|snap\|run\|db'
# Note that the filename can be a regedit pattern match, compatible with grep

for pid in /proc/{0..9}*; do
  i=$(basename "$pid")
  for file in "$pid"/fd/*; do
    link=$(readlink -e "$file")
    if [ "$link" ]; then
      echo "PID $i: $link"
    fi
  done
done | grep $1

```
But that will not tell you if a file is opened in an Editor. File Editors are a different animal (and an exception), because of how they work. They will open a file temporarily for read, while it is being read into the editor, then close it. Then when you go to save, it will again open it for write to save it, then close it again. Editors don't keep a file opened. So those will not show up as being in an "opened/locked" state.

3.) With some files that are locked, look at the lock or temp file first. Deleted that file first... I normally clean up temp files (of closed files) that were orphaned. Then, if desired, deleted the original file itself.

---

