---
title: "search for a term and copy the sentence shell scripting"
date: 2013-10-06
forum: Programming Talk
---

### Post by aadil7 on 2013-10-06
hello everyone

I am trying to search for a specific term in another file and extract that whole sentence til the end of the line.
I am clueless of whether to use grep or cut or find or a combination of these commands.

more detail
i want the script to search for any term i input in.

the script will look in a specified file where there is data. this data is one long string and things are separated by being on a new line.
the data in the file will look like:
feenzy343223right/on/point/feeno
madagascar343233right/on/point/parting

i want it so if I search for feeno the whole sentence "feenzy343223right/on/point/feeno" gets put into a variable which I can then manipulate.

I am thinking of combining the "/" with the input of feeno so it can recognise it properly.

is this a possibility?
all responses are much appreciated!

---

### Post by Vaphell on 2013-10-06
```
result=$( grep "/$pattern" file )
```
maybe with $ sign at the end of pattern to make sure it matches only at the end of line.

---

