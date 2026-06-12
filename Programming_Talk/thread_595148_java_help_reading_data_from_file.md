---
title: "java help: reading data from file"
date: 2007-10-28
forum: Programming Talk
---

### Post by dbbolton on 2007-10-28
i need a little help with a java programming assignment. i have to write a program that reads a file such as:

```

Smith 85 83 77 91 76 
Jones 87 90 88 91 94

```

and outputs something like:

```

Student Test1 Test2 Test3 Test4 Test5 Average Grade
Smith 85 83 77 91 76 82.4 B
...

```

i need help getting the program to read the data from the file using loops. could someone help me with this?

---

### Post by Ramses de Norre on 2007-10-28
Use a Scanner, if the file is named *text_file.txt* you do like this:
```

Scanner scanner=new Scanner(new FileInputStream(new File("text_file.txt")));

```

And then you can read out the file with the methods **next{,Int,Line}**, use as needed and read up on scanner [here](http://java.sun.com/javase/6/docs/api/java/util/Scanner.html).

---

### Post by dbbolton on 2007-10-28
thanks!

how do i loop it to read the whole file and get the data for each student?

---

### Post by \Oo._.oO/ on 2007-10-28
Assuming that the file contains one line for each student and the number of students is not defined you need something like this:

[INDENT]// read the whole file one line at a time
while(scanner.hasNextLine()) {
[INDENT]// read students name
for (int i=0; i<5; i++) {
[INDENT]// read the i:th exam score[/INDENT]
}[/INDENT]
}[/INDENT]

---

### Post by pmasiar on 2007-10-29
Here is why I prefer Python over java: I can open, read and parse file in 3 lines of code without consulting manual
[php]
for line in open('path/to/input/file'):
    parts = line.split(' ')
    name, grades = parts[0], parts[1:]
    # calculations, output etc
[/php]

---

### Post by Ramses de Norre on 2007-10-29
> **pmasiar said:**
> Here is why I prefer Python over java: I can open, read and parse file in 3 lines of code without consulting manual
[php]
for line in open('path/to/input/file'):
    parts = line.split(' ')
    name, grades = parts[0], parts[1:]
    # calculations, output etc
[/php]

He's asking about something specifically in java, python is no option here...

---

### Post by dbbolton on 2007-10-29
i'm sure that my CS prof would be amused if i turned in a python program for my java assignment

---

