---
title: "Changing Directories"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by RayArdia on 2014-05-29
I want to cd to Program Files and then to Sketchup, which I know exists but however I try I get -

ray@ray-Aspire-5735:~$ cd .wine/drive_c
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ ls
Program Files  users  windows
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ cd Program-files
bash: cd: Program-files: No such file or directory
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ cd ProgramfFiles
bash: cd: ProgramfFiles: No such file or directory
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ ^C
[email]ray@ray-Aspire-5735:~/.wine[/email]/drive_c$ find Program Files
find: `Program': No such file or directory
find: `Files': No such file or directory

Clearly _I _ must be doing something wrong, but Just _what_?

---

### Post by Impavidus on 2014-05-29
cd "Program Files"
cd Program\ Files

should work.

---

### Post by RayArdia on 2014-05-29
Thank you, both work fine.

---

### Post by jakke1975 on 2014-05-29
Please mark the thread as solved (in thread tools)

---

### Post by oldos2er on 2014-05-29
You can save yourself some typing by using the Tab key ```
cd .wi[Tab]

cd dr[Tab]

cd Pr[Tab]
``` and let the shell add the escape character "\" for you.

---

