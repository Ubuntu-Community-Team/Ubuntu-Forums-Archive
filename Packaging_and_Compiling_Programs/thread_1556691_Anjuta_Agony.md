---
title: "Anjuta Agony"
date: 2010-08-19
forum: Packaging and Compiling Programs
---

### Post by Cilph on 2010-08-19
I'm trying to switch to the GNOME Anjuta IDE and thus far it has been nothing but a big headache for the following reason. I've created a simple Generic C++ project and wish to add a few already existing source files to the project. I've created several groups (/src/XX/YY) in which 'YY' contains the files. After that, I add the files to the project under the main target (same as project name). This adds the files to the project but when I look under the Project tab I can see the target, with main.cc associated to it. It also shows the files I added, except it looks like it is expecting them in the /src directory because there is no file 'icon' next to the text and doubleclicking on it gives a 'no file found'. Naturally, the project also refuses to compile with a
```

make[3]: *** No rule to make target `----.o', needed by `----'.  Stop.

```(---- replaces filenames)

Basicly, it refuses to compile the files in my subfolder, while I have added both the folder and the files to the project.

Can anyone please tell me what I'm doing wrong? I'd rather not use gEdit+make because of the complexity of what I'm making and Eclipse has far too many features for me.

---

