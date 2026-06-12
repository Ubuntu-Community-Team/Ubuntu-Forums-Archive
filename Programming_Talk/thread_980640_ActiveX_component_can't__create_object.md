---
title: "ActiveX component can't  create object"
date: 2008-11-13
forum: Programming Talk
---

### Post by rabbitCode on 2008-11-13
Can somebody please help. I'm tryin to write to a .txt file from a web page. The error is: ActiveX component can't  create object:"Scripting.FileSystemObject". My code is as follows:

Sub writeToFile()
Dim Stuff, myFSO, WriteStuff

Stuff = "Whatever you want written"

Set myFSO = CreateObject("Scripting.FileSystemObject")
Set WriteStuff = myFSO.OpenTextFile("yourtextfile.txt", 8, True)
WriteStuff.WriteLine(Stuff)
WriteStuff.Close
SET WriteStuff = NOTHING
SET myFSO = NOTHING
End Sub

---

