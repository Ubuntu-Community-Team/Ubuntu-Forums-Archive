---
title: "shell script program"
date: 2009-02-05
forum: Programming Talk
---

### Post by phanipalagummi on 2009-02-05
please give me the solution for the below program

Display directory in the present directory

---

### Post by Tek-E on 2009-02-05
I "might" be able to help.....But I dont cleary understand what exactley your asking for... :/

---

### Post by croto on 2009-02-06
pwd?

---

### Post by hamzah2096 on 2009-02-06
I think maybe he is saying to make something like ls or dir/w.

---

### Post by |{urse on 2009-02-06
what shell? Bash?

```

#!/bin/bash
pwd && ls -l
```copy that into your favorite text editor, i suggest gedit if you arent familiar with vi or nano. Save it.

then navigate your way to wherever you saved the file and either 

> chmod +x filename

or just right click on the file and set the file to executable under the permissions tab. 

now either 2x click the file to run it 

or run it from the terminal with 

> ./filenameor 

> sh filename
easy peasy

---

