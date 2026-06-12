---
title: "Include files determined at runtime with PHP/Python"
date: 2011-06-02
forum: Programming Talk
---

### Post by btindie on 2011-06-02
Below is an example shell script, I was wondering how you'd do the same in PHP/Python?

datafile:
```
VAR1="hello"
VAR2="world"
```script:
```
#!/bin/sh

FILE=$1
. ./$FILE
echo $VAR1 $VAR2
```Run with:```
$ ./script datafile
```We've got a webservice that dumps ticket information to text files in a directory. The intention is to use *incron* to monitor the directory then have that run a PHP/Python script passing the name of the newly created file containing the variable information. What would be nice is if it could be included in a similar fashion to the above bash script without having to parse the text file. The format in which the data is written to *datafile* can be changed. This script then processes the file in it's own time not blocking the ticketing system.

---

