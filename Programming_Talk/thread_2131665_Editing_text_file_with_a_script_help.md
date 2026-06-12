---
title: "Editing text file with a script help"
date: 2013-04-02
forum: Programming Talk
---

### Post by bball2601 on 2013-04-02
Hey,

I'm trying to write a script that would loop through the files of a directory and add the names of each file to a text file.

I'm relatively new to writing scripts and have no idea how I would be able to edit the text file from bash.
Any help would be appreciate.
Thanks.

---

### Post by r-senior on 2013-04-02
> **bball2601 said:**
> I'm trying to write a script that would loop through the files of a directory and add the names of each file to a text file.
Could you just do this?

```
ls -1 > files.txt
```

The '>' is called redirection. You can use it to redirect the output of any command to a file. The 'ls -1' command is just a directory listing with one column of filenames.

---

### Post by bball2601 on 2013-04-02
> **r-senior said:**
> Could you just do this?

```
ls -1 > files.txt
```

Thanks, that works.

Just out of curiosity, do you know how I would be able to edit a text file via scripting?
Would it be by using sed, and if so how?

---

### Post by r-senior on 2013-04-02
Yes, sed would often be the tool for editing from a script. For example:

```
$ cat henry.txt 
So shaken as we are, so wan with care.
Find we a time for [COLOR="#0000FF"]frightened[/COLOR] peace to pant.
$ sed -i 's/[COLOR="#0000FF"]frightened[/COLOR]/[COLOR="#FF0000"]frighted[/COLOR]/' henry.txt 
$ cat henry.txt 
So shaken as we are, so wan with care.
Find we a time for [COLOR="#FF0000"]frighted[/COLOR] peace to pant.
```

There are lots of other things to be done with sed -- regular expressions, global replace, deletions, etc. It's well worth learning a little of even if you only remember how to do simple search/replace as above. Awk, sed and grep are three related tools that are all well worth exploring.

---

### Post by schragge on 2013-04-03
If both your questions are interconnected, i.e. you want to prepare a list of files, then make some automated edits on each, the first step is superfluous as *sed* is able to process several files in one command:
```
sed -i 's/old/new/' path/to/directory/*
```

---

