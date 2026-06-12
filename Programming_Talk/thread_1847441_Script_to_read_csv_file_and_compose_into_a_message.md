---
title: "Script to read csv file and compose into a message"
date: 2011-09-20
forum: Programming Talk
---

### Post by caja0710 on 2011-09-20
Hi All,

I am new to the shell scripting and need your help.

I have an csv file that is needed to be read the data and plug the data into below fields below marked with letters (A, B, C, D, E).  This will be in loop until it reach to the end of the csv file.  The plug in data will be accumulated into one output file.  How can I achieve it?  Any help will be appreciated.

csv data
Aland_Islands,Aland Islands,358,Aland_Islands,Aland_Islands
Anguilla,Anguilla,261,Anguilla,Anguilla
Antigua_And_Barbuda,Antigua And Barbuda,268,Antigua_And_Barbuda,Antigua_And_Barbuda
Armenia,Armenia,374,Armenia,Armenia
Azerbaijan,Azerbaijan,994,Azerbaijan,Azerbaijan

File used to be plug into:
OBJECT  TYPE="country", NAME=<A>
   name ="<B>";
   code=<C>;
   ref_id ="<D>";
END_OBJECT  NAME=<E>

---

### Post by Smart Viking on 2011-09-20
Shell scripting isn't optimal for this.

Rather use a language like Python which is good at string manipulation.

I don't understand what the output file is gonna look like, Can you make an example output file or something?

What is this for? Sure you have to do this?

---

### Post by caja0710 on 2011-09-20
The output will look like this in a single file.  Basically this is to prepare to import the data back to the database using a specific tool (a must).  Since there is couple hundreds of records, I am thinking of using a script to compose this data file will save my time.


OBJECT TYPE="country", NAME=Aland_Islands
name ="Aland Islands";
code=358;
ref_id ="Aland_Islands";
END_OBJECT NAME=Aland_Islands

OBJECT TYPE="country", NAME=Anguilla
name ="Anguilla";
code=261;
ref_id ="Anguilla";
END_OBJECT NAME=Anguilla

OBJECT TYPE="country", NAME=Antigua_And_Barbuda
name ="Antigua And Barbuda";
code=268;
ref_id ="Antigua_And_Barbuda";
END_OBJECT NAME=Antigua_And_Barbuda

OBJECT TYPE="country", NAME=Azerbaijan
name ="Azerbaijan";
code=994;
ref_id ="Azerbaijan";
END_OBJECT NAME=Azerbaijan

---

### Post by Smart Viking on 2011-09-20
Try this out:
```

import csv

f = open("omg.csv")

read = csv.reader(f)
for line in read:
  try:
    print "OBJECT TYPE=\"country\", NAME="+line[0]
    print "name=\""+line[1]+"\";"
    print "code="+line[2]+";"
    print "ref_id=\""+line[3]+"\";"
    print "END_OBJECT NAME="+line[4]+"\n"
  except IndexError:
    pass #empty line, probably.




```It's a python script. Name it "script.py" (or something else), If you change "file.csv" to the name of the file, and launch this script in the same directory as the csv file it will spit out the correct data. Launch with:
```
$ python script.py
```EDIT:
To save it in a text file, just run:
```
$ python script.py > file.txt
```

---

### Post by Vaphell on 2011-09-20
same thing in bash
```
#!/bin/bash

while IFS=, read -a arr
do
  if [[ ${#arr[@]} -ne 5 ]]; then continue; fi
  echo "OBJECT TYPE=\"country\", NAME=${arr[0]}"
  echo "name=\"${arr[1]}\";"
  echo "code=${arr[2]};"
  echo "ref_id=\"${arr[3]}\";"
  echo "END_OBJECT_NAME=${arr[4]}"
  echo
done < in.csv
```

```
bash script.sh > out.txt
```

---

### Post by caja0710 on 2011-09-29
Thanks both.  Does it have any limit of how many rows it can read?  I created a 3 rows data with 13 parameters and it only created the file for the first 2 rows.  Do I put too much parameters?

---

