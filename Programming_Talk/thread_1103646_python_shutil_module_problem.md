---
title: "python shutil module problem"
date: 2009-03-22
forum: Programming Talk
---

### Post by KLIA on 2009-03-22
Hey guys
i am trying to copy file using shutil module but i am have problem copying a file to directory using this 

shutil.copyfile (src, des) but there's an error saying that the destination is a directory and not a filename which i have to give a name for my file in destination in order to be copied..

the question how to copy a file to a directory without having to rename the file?

---

### Post by cabalas on 2009-03-22
what about using:

```
shutil.copy(src, dest + "/" + os.path.basename(src))
```

That way the file does not need to be renamed.

---

### Post by cabalas on 2009-03-22
After having a quick look at the docs (which I should have done first) at [http://docs.python.org/library/shutil.html](http://docs.python.org/library/shutil.html) I noticed that copy file requires the file name, but if you just use plain old copy do don't have to supply the destination file name.

---

### Post by KLIA on 2009-03-22
Thanks for replaying

I did the following but i still have error

shutil.copyfile(self.lwitem.text(), '/home/waseem/desktop/PhotosDB/1.JPG' + "/" + os.path.basename(self.lwitem.text()))

---

### Post by geirha on 2009-03-23
Do you really have a directory named 1.JPG? Anyway, use shutil.copy instead of shutil.copyfile.
```

shutil.copy(source_file, destination_directory)

```

---

