---
title: "[SOLVED] bin files"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by 1scorpio on 2008-05-29
how do I open and/or Install a bin file?

---

### Post by Xerp on 2008-05-29
Find out what the binary file is first:

 file filename.bin

You'll then be in more of a position to use an application that can handle that form of binary data.

---

### Post by spiderbatdad on 2008-05-29
bin files are executable file types...or programs. They need to be made executable with the command:```
chmod a+x filename.sh
```If the file is owned by root, use sudo: sudo chmod a+x....

To run:```
./file_name.sh
```

---

### Post by kwacka on 2008-05-29
Firstly make sure its executable with ```
chmod a+x file.bin
```

Then, using a terminal enter the filename, e.g. /home/john/downloads/file.bin

---

