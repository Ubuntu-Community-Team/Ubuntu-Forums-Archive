---
title: "automating some processes"
date: 2006-08-07
forum: Programming Talk
---

### Post by nbpetts on 2006-08-07
I would like to write a script that will open some files (one afeter another) and find a certin bit of text (a url) and out put that to a text file.

Any suggestions for the language/jumping off points/general comments?

---

### Post by mority on 2006-08-07
> **nbpetts said:**
> I would like to write a script that will open some files (one afeter another) and find a certin bit of text (a url) and out put that to a text file.

Any suggestions for the language/jumping off points/general comments?

I think you want to use "grep" to do this. In fact, with grep you can accomplish this task with just one line of bash, which I would hardly call a script.
Maybe try something like this:```
grep pattern directory > output_file
```
*pattern* is the URL you want to search for. *directory* is the directory where the files are in which you want to search and *output_file* is the filename where you want to store the results. The ">" causes the output to be written to a file instead of being printed to the screen.
For details have a look at ```
man grep
```

---

### Post by nbpetts on 2006-08-07
not a bad thought, thanks

what about dealing with many files and searching not for a specific url, but all lines beginning with or containing "http://"?

---

### Post by harisund on 2006-08-07
Still you could use grep. 

What is it that you want to do exactly?

---

### Post by mority on 2006-08-07
> **nbpetts said:**
> not a bad thought, thanks

what about dealing with many files and searching not for a specific url, but all lines beginning with or containing "http://"?

You can find any pattern with grep. grep is designed to accomplish much more complicated tasks then what you are planning to do, but it fits perfectly to your needs, too.

grep automatically searches all files in a given directory. If you want to search subdirectories too, use the -R option (for recursion). If the files you want to examine are scattered through all different directories, use the output of a "find" search as an argument for grep like this:
```
grep "http://" `find / -iname "foo_file"`
```

---

