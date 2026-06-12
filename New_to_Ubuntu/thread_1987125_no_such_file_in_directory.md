---
title: "no such file in directory"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by CQCnotBLT on 2012-05-25
I'm trying to run this emulator on Wine. I moved the file to the Desktop and entered everything right in the terminal, but when i enter this

cody@cody-laptop:~/Desktop$ wine no$gba-w.2.6a.exe

it says this

wine: cannot find L"C:\\windows\\system32\\no.exe"
I'm sure the file is on the desktop, and everything should be in right.

---

### Post by papibe on 2012-05-25
Hi CQCnotBLT.

The '$' is a special character. Either you need to escape it like this:
```
wine no\$gba-w.2.6a.exe
```
or you got the wrong filename.

Could you post the result of this command?
```
ls ~/Desktop
```
Regards.

---

### Post by CQCnotBLT on 2012-05-26
When i entered the first one it did this

cody@cody-laptop:~/Desktop$ wine no\$gba-w.2.6a.exe
wine: cannot find L"C:\\windows\\system32\\no$gba-w.2.6a.exe

and the second one was

cody@cody-laptop:~/Desktop$ ls ~/Desktop
NO$GBA.EXE

---

### Post by papibe on 2012-05-26
Thanks.

Another feature of the command line is that is 'case sensitive' :D

Your best friend is a feature called 'auto completion'. It complete the name of the arguments (filename in this case) if there's no doubt about it.

For example, write wine, and then just the capital N:
```
wine N
```
then press the 'tab' key, it would expand the complete name of the file (probable NO\$GBA.EXE)

Tell us how it goes.
Regards.

---

### Post by CQCnotBLT on 2012-05-26
Awesome! that fixed that problem. 
But what did the capital N have to do with anything?

---

### Post by papibe on 2012-05-26
):P Great!

Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.
Regards.

BTW, the N is because your file starts with a capital N :)

---

