---
title: "[Python] File writing at certain point in file"
date: 2011-09-21
forum: Programming Talk
---

### Post by ki4jgt on 2011-09-21
How do I write to a file at a certain point in the file without overwriting the entire file?

---

### Post by cgroza on 2011-09-21
Appending at the end is no problem, but you can't write in the middle of a file without overwriting what comes after that point.

This is similar to your case: [http://stackoverflow.com/questions/6065215/how-to-insert-a-newline-at-middle-of-a-file-in-python](http://stackoverflow.com/questions/6065215/how-to-insert-a-newline-at-middle-of-a-file-in-python)

---

### Post by ofnuts on 2011-09-22
> **ki4jgt said:**
> How do I write to a file at a certain point in the file without overwriting the entire file?Open it as 'r+', and then use the seek() method to position th cursor when you want to write.

 ```
-> echo "abcdefghijklmnop" > testfile                   
->cat testfile                                                            
***abcdefghijklmnop***
```pyseek contents:
```
#! /usr/bin/python
f = open('testfile', 'r+')
f.seek(5)
f.write('1234')
f.close()

```Result:
```

->./pyseek                                                                
->cat testfile                                                            
***abcde1234jklmnop       ***

```

---

