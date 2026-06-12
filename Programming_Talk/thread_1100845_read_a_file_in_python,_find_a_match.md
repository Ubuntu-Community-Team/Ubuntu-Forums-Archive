---
title: "read a file in python, find a match"
date: 2009-03-19
forum: Programming Talk
---

### Post by trypeace2day on 2009-03-19
I have a file of paired attributes. Something like:

abc,12345
asdf,23456
qwe,098765

In python, I want to add my two arguments and see if they are in this file. 

so, say I my arguments are asdf and 23456. I want to iterate through my file and find it. If I find it, I'll do some more processing. If it's not in the file, then I'll end my program.

Any suggestions?

Dorothy

---

### Post by macphisto on 2009-03-19
Do you mean something like:
```
#!/usr/bin/env python
#
# match

param_name  = "abc";
param_value = "12345";
param_file  = "testfile"


f = open(param_file, "r");
array = f.readlines();

match_text = param_name + "," + param_value + "\n";

if match_text in array:
    print "Found it!";
else:
    print "No: " + match_text;
```

If you are starting with Python, you might want to look at the official tutorial: [http://docs.python.org/tutorial/]("http://docs.python.org/tutorial/")

---

### Post by trypeace2day on 2009-03-19
I figured it out... Here's what I used:

> 

```
read_file = open(inFile,"r")

for line in read_file:
    linesp = line.split(',',3)
    fileWRD_ID = str(linesp[0])
    fileHUC = str(linesp[1])
    gp.addmessage(str(fileWRD_ID))
    gp.addmessage(str(fileHUC))

    if WRD_ID == fileWRD_ID:
        if huc_code == fileHUC:
           gp.addmessage(WRD_ID)
           gp.addmessage(huc_code)
           gp.addmessage("This is a major river. Additional HUCs will be merged.\n")
        else:
            gp.addmessage("The WRD_ID matched but the HUC did not. \n")
    else:
        gp.addmessage("This is NOT a major river. No additional HUC will be merged.")
    
read_file.close()
```


Note: the gp.addmessage is another software's version of print. (gp is geoprocessing for ESRI GIS software).:popcorn:

---

