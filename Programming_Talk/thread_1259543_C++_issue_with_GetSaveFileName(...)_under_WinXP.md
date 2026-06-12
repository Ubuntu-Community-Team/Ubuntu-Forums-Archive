---
title: "C++ issue with GetSaveFileName(...) under WinXP"
date: 2009-09-06
forum: Programming Talk
---

### Post by Wug on 2009-09-06
a program im working on uses the GetSaveFileName WinAPI function.  The dialog displays fine and properly, and allows me to select a file ad use all of its controls and whatnot.  However, when I close it IN ANY WAY (including clicking the save button) It always reports an error.  Calling GetDlgExtendedError indicates that the dialog failed due to user dismissal (a.k.a. clicked cancel button)
I most assuredly did not click the cancel button.  Also, even though it reports an error, the lpstrFile member of the OPENFILENAME object is correctly updated.
I could work around and ignore errors, as it is just saying there is one while there isnt, but thats a bad idea.
WHY is GetSaveFileName misbehaving?
GetDlgExtendedError only ever returns 0 (user dismissal of dialog w/o choice)
OPENFILENAME object updates correctly with chosen name.
Im using Dev-Cpp (MinGW compiler for WinXP)

help?

---

### Post by cszikszoy on 2009-09-06
This might help:
[http://msdn.microsoft.com/en-us/library/ms646928(VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms646928(VS.85).aspx)

How about a code sample?  It's pretty impossible to help when we can't see the code you're using.

---

