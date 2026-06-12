---
title: "explanation of colors of dir/file names"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-04
what is shown by each color of files/directories names in linux like blue are folders, green are exe files,,, what else like yellow, white, cyan and others????

---

### Post by taras.kuzyo on 2012-09-04
You can find it out by running:
```
file <item with some color>
```
which displays kind of the file.

---

### Post by spjackson on 2012-09-04
```

dircolors --print-database

```is the command to show you the defaults on your system. You can override these defaults.

On the system I am using right now, cyan is audio files, white is a "file that is setuid (u+s)" or a "dir with the sticky bit set (+t) and not other-writable", yellow is a pipe or a device.

---

### Post by sisco311 on 2012-09-04
D'oh! spjackson beat me to it.

You can colorize the output of *dircolors -p* :)
```

echo -e  "$(dircolors -p | sed -r -e 's/(([0-9][0-9];)+)([0-9][0-9])/\\e[\1\3m=> color: \1\3 \\e[00m/')"

```

---

### Post by syednasirraza on 2012-09-07
thnx alot dear friends...got the joke

---

