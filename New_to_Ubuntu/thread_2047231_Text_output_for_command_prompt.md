---
title: "Text output for command prompt"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by LAN1ACM on 2012-08-24
I have a situation where I am using the command prompt to run a perl script.

The perl script is in a batch file and is executed by an action command. 

Inside the batch file, the perl script converts a .xlsx file to .csv

This is what the syntax has been so far:

SYNTAX: perl_script.pl Input_file sheetname Output_file

EXAMPLE:
>perl_script.pl "Uniquefilename.xlsx" "sheetname" "Uniquefilename.csv"



The filename 'Uniquefilename' changes everyweek. The 'sheetname' doesn't. You will notice that the 'Uniquefilename' is the same for the input and the output file. The only thing that has changed is the extension. I have been making these changes manually everyweek when our xlsx file lands. But its now more feasible to automate this task. the only thing that changes everyweek is the filename. The file that lands is a .xlsx file. We have to keep the filename the same for the outputfile. 

And All I am trying to achieve is a line of text that can be executed at the command prompt that says the example above.

I dont know how exactly this will be done, but I would think that we would copy the 'Uniquefilename' from the .xlsx file in a variable and print it as 'Uniquefilename.csv' in the output text line.  

I have used sed before but it was only minor. I have been playing around with sed for several hours now on my windows maching but havent been able to figure out how I can run that line above in the command prompt. 

Any pointers or help will be much appreciated.

---

### Post by steeldriver on 2012-08-24
bash has some substitution capabilities that are perfect for this kind of thing, e.g.

```
infile="Uniquefilename.xlsx"

outfile="${infile%.xlsx}.csv"
```

[http://stackoverflow.com/questions/965053/extract-filename-and-extension-in-bash](http://stackoverflow.com/questions/965053/extract-filename-and-extension-in-bash)

[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

