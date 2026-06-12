---
title: "Set variables from a text file"
date: 2011-01-17
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-17
I am trying to have a script go through a text file that has names in it (e.g.  Preferences, Backgrounder) each on its own line.  I can set a basename for this file.

I would want to copy the apropriate file along with it into this directory.
something like this...

```

cp /Applications/$Textfilewithdiffdirectorynames/$icon name.



```
This is for iphone themeing, via the terminal emulator. 

I am trying to make it cat all the icons into a text file

```

cat /icons > list.txt

```

 then sed that file into another one that doesn't have the .png
```

sed 's/.png//' < list.txt >names.txt

```

Does this make sense?
So it would match the names of the first file to one of the second file, using each line as a variable, to copy the images over one by one into the apropriate directories.

Thanks!

---

### Post by psusi on 2011-01-17
> **bcooperizcool said:**
> 
I am trying to make it cat all the icons into a text file


This makes no sense.  Maybe you mean *ls* the files, not cat.

---

### Post by geirha on 2011-01-18
So you have two files with the same ammount of lines, one file contains directory names, and the other, corresponding icon filenames? (if not, sample files would help)

And then output the basenames, without extensions, of the icons, to a new file?

---

