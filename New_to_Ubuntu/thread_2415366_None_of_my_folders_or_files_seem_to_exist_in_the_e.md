---
title: "None of my folders or files seem to exist in the eyes of my terminal?"
date: 2019-03-24
forum: New to Ubuntu
---

### Post by retsek2 on 2019-03-24
Whenever I try to change directory it tells me that the directory doesn't exist, even when I have simply typed cd and then dragged the folder into the terminal and removed the apostrophes it still believes that the directory doesn't exist. This also happens when I try to run a python script. Below I have pasted the console output.

kester@kester-desktop:~$ pwd
/home/kester
kester@kester-desktop:~$ ls
Desktop    Downloads  Pictures  PycharmProjects  Templates
Documents  Music      Public    snap             Videos
kester@kester-desktop:~$ cd /PycharmProjects
bash: cd: /PycharmProjects: No such file or directory
kester@kester-desktop:~$ cd /PycharmProjects/
bash: cd: /PycharmProjects/: No such file or directory
kester@kester-desktop:~$ python3 selection_sort.py
python3: can't open file 'selection_sort.py': [Errno 2] No such file or directory

[ATTACH=CONFIG]282846[/ATTACH]

---

### Post by CatKiller on 2019-03-25
Putting that erroneous / at the start means that you're telling the shell to find that path from the root directory rather than the current directory.

---

### Post by Impavidus on 2019-03-25
You have found the difference between absolute paths and relative paths. When you start the path to your file/directory with a / or some something that's shorthand for an absolute path (like ~/, which is short for your home directory /home/kester/), it's an absolute path, interpreted relative to the root directory. Whenever your path starts with something else, it's a relative path, interpreted relative to the current directory.

---

