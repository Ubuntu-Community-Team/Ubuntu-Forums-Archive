---
title: "Problem in editing C++ text file."
date: 2014-04-29
forum: Programming Talk
---

### Post by tusharkoshti on 2014-04-29
Hi friends, 
I want to do C++ programming.  Following steps i am using. 

1) gedit program name.cpp 
2) g++ program name.cpp -o program name.cpp
3) ./program name.cpp

but problem is when I want to edit my program file I can't open it. ( I usually open it by double clicking on it).
Message is : 

There was a problem opening the file.
The file you opened has some invlaid characters , if you continue editing this file you could corrupt this document.
You can chooose another character encoding and try again. 
And there is character encoding " Current Locale (UTF-8)
How to solve this problem ? 
Please help.

---

### Post by slickymaster on 2014-04-29
Moved to the Programming Talk sub-forum.

---

### Post by steeldriver on 2014-04-29
> **tusharkoshti said:**
> 
1) gedit program name.cpp 
2) g++ program name.cpp **-o program name[COLOR=#ff0000].cpp[/COLOR]**
3) **./program name[COLOR=#ff0000].cpp[/COLOR]**


If you really gave the output (executable) file the same name as the source code file, then your g++ command overwrote the original file and it now contains binary data not text

You *may* be able to recover the original file from gedit's automatic backup (~) file

I'm assuming you didn't really use a name with unquoted spaces i.e. 'program name' is really something like 'program_name' or 'myprog'

---

### Post by tusharkoshti on 2014-04-29
I have used Triangle1.cpp in all the 3 steps.

---

### Post by The Cog on 2014-04-29
As steeldriver says, there may be a hidden file called ~Triangle1.cpp that is an auto-saved backup by gedit. In your file manager, press Ctrl-H to turn on showing hidden files.
Or just use the command:
```
cp '~Triange1.cpp' Triangle1.cpp
```
and hope the backup file is there to be recovered. And hope that the last edit wasn't too big, as the backup file will be a copy of the last-but-one version of the file.

Remember not to tell the compiler to output over the input file in future. The proper command would be:
```
g++ program Triangle1.cpp -o program Triangle1
``` which would create a program executable file called Triangle1.

---

