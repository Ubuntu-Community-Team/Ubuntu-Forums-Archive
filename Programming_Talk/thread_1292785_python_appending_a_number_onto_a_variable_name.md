---
title: "python appending a number onto a variable name?"
date: 2009-10-16
forum: Programming Talk
---

### Post by Mach1723 on 2009-10-16
pretty sure this isnt possible but if it is how would you append a number onto a variables name like ```

to_append = 1
varName+to_append = 1

```heres the code i am having the problem with(trouble code is bold), need a new variable for each pass of the while loop.
```
def GetFile():
    print GetFile ##
    print "Enter Converse File Name"

    work_dir = GetRelativeDir()
    con_file = raw_input()
    slash = "/"

    openfile = work_dir+slash+con_file #combine the three above variables
    openfile_s = open(openfile, "r") #load file into buffer

    file = openfile_s.readlines()
    start_lst = 0

    to_append = 1
    #TODO: figure out how to append "to_append" onto the end of "file_str

[B]    while start_lst < len(file):
        file_str = file[start_lst]
        file_str.replace("\n", "")

        start_lst += 1
        to_append += 1[/B]

```also, a link to the full file [http://code.google.com/p/machs-code-sandbox/source/browse/trunk/Mach/Converse/V0.2/file_con.py](http://code.google.com/p/machs-code-sandbox/source/browse/trunk/Mach/Converse/V0.2/file_con.py)

---

### Post by Arndt on 2009-10-16
> **Mach1723 said:**
> pretty sure this isnt possible but if it is how would you append a number onto a variables name like ```

to_append = 1
varName+to_append = 1

```heres the code i am having the problem with(trouble code is bold), need a new variable for each pass of the while loop.
```
def GetFile():
    print GetFile ##
    print "Enter Converse File Name"

    work_dir = GetRelativeDir()
    con_file = raw_input()
    slash = "/"

    openfile = work_dir+slash+con_file #combine the three above variables
    openfile_s = open(openfile, "r") #load file into buffer

    file = openfile_s.readlines()
    start_lst = 0

    to_append = 1
    #TODO: figure out how to append "to_append" onto the end of "file_str

[B]    while start_lst < len(file):
        file_str = file[start_lst]
        file_str.replace("\n", "")

        start_lst += 1
        to_append += 1[/B]

```also, a link to the full file [http://code.google.com/p/machs-code-sandbox/source/browse/trunk/Mach/Converse/V0.2/file_con.py](http://code.google.com/p/machs-code-sandbox/source/browse/trunk/Mach/Converse/V0.2/file_con.py)

Why would you need a new variable for each loop? The good things with variables is that they can vary; so they don't need to be used only once.

---

### Post by Mach1723 on 2009-10-16
i need each string in the list to have its own variable.
EDIT: Actually is there a way to dump a list to a string without all the extra stuff like brackets?

---

### Post by Arndt on 2009-10-16
> **Mach1723 said:**
> i need each string in the list to have its own variable.
EDIT: Actually is there a way to dump a list to a string without all the extra stuff like brackets?

But I don't think you do. When you have all these variables file_str1, file_str2, etc. what will you do with them? For handling an unspecified number of values, you can use an array, file_str[1], file_str[2], etc.

---

### Post by mobilediesel on 2009-10-16
> **Mach1723 said:**
> i need each string in the list to have its own variable.
EDIT: Actually is there a way to dump a list to a string without all the extra stuff like brackets?

> **Arndt said:**
> But I don't think you do. When you have all these variables file_str1, file_str2, etc. what will you do with them? For handling an unspecified number of values, you can use an array, file_str[1], file_str[2], etc.

Yes, the array is what you need here. No need to reinvent it.

---

### Post by Can+~ on 2009-10-16
> **Mach1723 said:**
> EDIT: Actually is there a way to dump a list to a string without all the extra stuff like brackets?

```
"".join(str(i) for i in alist)
```

---

