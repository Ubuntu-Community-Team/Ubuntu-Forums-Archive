---
title: "file type preferences (open with)"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-12-02
Please tell me how to change file open with preferences to make a particular file open with a particular program.

---

### Post by drs305 on 2008-12-02
> **melrokz said:**
> Please tell me how to change file open with preferences to make a particular file open with a particular program.

Open nautilus, right click on the type of file you are interested in, select Properties, Open With and a list of possible applications will be presented.

Added later, after OP responded: This will associate the selected file *type* with the selected application.

---

### Post by melrokz on 2008-12-02
Thanks, but i know that. I need to change the default program to open a particular file. How is that?

---

### Post by -Zeus- on 2008-12-02
what are you talking about?  what he told you is how you change it.

---

### Post by drs305 on 2008-12-02
> **melrokz said:**
> Thanks, but i know that. I need to change the default program to open a particular file. How is that?

Particular *file* or *particular file type*. The latter was discussed above. As to the former, a lot of programs can be opened by the command followed by the file name, if that is what you mean. Here is an example:
```
openoffice /home/xxx/Desktop/08.ods
gimp /home/xxx/Desktop/Screenshot.png

```
You would make a launcher on the desktop  or panel or make a simple bash script. For a launcher, right click on a panel, select "Custom Application Launcher" and put the command and filename in the command block. Try it in terminal first to see if the combination works. If it doesn't, the error code may give you enough information to tweak it.

---

### Post by Hakanu on 2008-12-02
Are you trying to say you want to associate a file type/extension with a specific application (e.g. mp3 with totem)?

If so, it's automatically associated when you change it once.

---

### Post by richg on 2008-12-02
Open the File Manager. Right click on the file, select Properties, select Open With. Select which application you want.
I just found that after a recent 8.04 update that PDFs would no longer open with the default application that came with 8.04. I had to select Adobe Reader 8 to open all PDFs now.
I had to change photo files to open with Gimp.
Now I left click on a file and it opens with the application I prefer.

Rich

---

