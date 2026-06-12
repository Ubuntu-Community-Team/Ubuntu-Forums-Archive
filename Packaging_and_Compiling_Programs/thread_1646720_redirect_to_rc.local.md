---
title: "redirect to rc.local"
date: 2010-12-16
forum: Packaging and Compiling Programs
---

### Post by my_abousamra on 2010-12-16
hi all,

I was writing a script and I needed to redirect a command into rc.local but the redirecting process always put it at the end of the rc.local. is there any way to redirect this command at the head or at least before the last line in rc.local (exit 0)?

---

### Post by SevenMachines on 2010-12-17
Not quite sure what you're trying to do but if you mean 'insert a line of text into a file somewhere' then i imagine sed or awk would be the things you want maybe. 

Example with sed, inserting or appending text at line 3...

test.txt:
> # Some sort of comment
first entry
second entry
third entryYou can then use sed using line numbers with 'i' to insert text before the specified line and 'a' to append it, eg
> $ sed '3i\New Text\' test.txt 

# Some sort of comment
first entry
New Text
second entry
third entry

$ sed '3a\New Text\' test.txt 

# Some sort of comment
first entry
second entry
New Text
third entry
Note, to make changes 'in place', so that the file is actually changed you would use pass the '-i' parameter

I dont know much about awk but apparently its used for this sort of thing in scripts too

---

### Post by my_abousamra on 2010-12-19
Thank u, This is something near to what I'm going to do

---

### Post by SevenMachines on 2010-12-19
Just as a side note, if you're needing to have your script run in a certain order compared to other ones in rc.*, depending on what you're trying to do it might be worth also looking at using an upstart script instead. since its its event based you can have the script wait on the service you need rather than trying to make sure that everythings in the right order

---

