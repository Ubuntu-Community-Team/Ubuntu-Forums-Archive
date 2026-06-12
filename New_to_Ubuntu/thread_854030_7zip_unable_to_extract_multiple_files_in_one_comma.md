---
title: "7zip unable to extract multiple files in one command"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-09
for example, i have three zip files to extract, 
```
 7z x a.zip  b.zip  c.zip

7-Zip 4.51 beta  Copyright (c) 1999-2007 Igor Pavlov  2007-07-25
p7zip Version 4.51 (locale=en_HK.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Processing archive: a.zip


No files to process
```
thanks in advance.

---

### Post by sayakb on 2008-07-09
Not sure if multiple file arguments would work or not. So you could use this script instead.
Firstly, at a terminal:
```
sudo gedit /usr/bin/7zm
```
And type this script in gedit:
```
#!/bin/bash
C="y"
while [ "$C" == "y" ]
do
   echo Enter Filename:
   read fn
   CMD="7z x "$fn
   $CMD
   echo
   echo More - y or n?
   read C
done
```
Then do:
```
sudo chmod +x 7zm
```
Just type 7zm at a terminal to execute this script..

---

### Post by afeasfaerw23231233 on 2008-07-10
thanks

---

### Post by ytsestav on 2009-06-18
I've had the same sort of problems with different programs that don't accept multiple file inputs. Alternatively you could do the following:

```
> for fl in *.7z; do 7z x -y "$fl"; done
```

In the folder containing all your *.7z files, this will extract each file in turn. Essentially just looping through all the *.7z files one by one.

---

