---
title: "Ubuntu Menu Folder Heriarchy"
date: 2009-10-09
forum: Programming Talk
---

### Post by ioan1k on 2009-10-09
Hello,

I am looking to create a Menu Item in the Main Menu that will contain a Hierarchy of a folder system created/updated automatically

For example I would like to be able to do the following structure

```

|- Work
  |- Client 1
      |- Sub Client
         | - Web Files
             | - html
             | - python
  | - Client 2
      | - Project A
          | - Assets
              | - PSD's
          | - Web Files
              | - php
              | - js

```

etc etc...  

Which would allow me to rollover each folder and either click and the location open in nautilus or it expand with the sub folders under it.


I know this would be possible if I modified the config menu XML files themselves by writing a python cron job to update the menus every so often but I would like to know if this has already been accomplished before I spent the time doing so.

If no one has done this before, does anyone have some documentation on how exactly the Menu System works to point me in the correct direction for writing the code on this.

Thnx!

---

### Post by ioan1k on 2009-10-12
Anyone have some information or help on this subject?

---

### Post by ioan1k on 2009-10-30
If no one has any advice on menu modifications, how about creating a Menu tree from a Python Applet?

I know how to create a python applet with the gnome panel, only question is for this is how would I do it so I can make the hierarchy of folders?

---

### Post by benj1 on 2009-10-30
building a tree is pretty simple

```

def tree(dir, padding):
    print padding[:-1] + '+-' + os.path.basename(os.path.abspath(dir))
    padding = padding + ' '
    files = [x for x in os.listdir(dir) if os.path.isdir(os.path.join(dir,x))]
    for count,file in enumerate(files):
        count += 1
        path = dir + os.sep + file
        if os.path.isdir(path):
            if count == len(files):
                tree(path, padding + ' ')
            else:
                tree(path, padding + '|')
        else:
            print padding + '+-' + file


```
or a no printing version
```

def file_walk(dir):
    files = os.listdir(dir)
    files.sort()
    for file in files:
        path = os.path.join(dir,file)
        if os.path.isdir(path):
            file_walk(path)
        else:
            filelist.append(os.path.abspath(os.path.join(dir,file)))

```
cant offer any further advice in using that in the gnome menu tho.

---

