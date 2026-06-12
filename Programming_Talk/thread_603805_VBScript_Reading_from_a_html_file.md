---
title: "VBScript: Reading from a html file"
date: 2007-11-05
forum: Programming Talk
---

### Post by Het Irv on 2007-11-05
I can't find anywhere online that gives me a good anwser.  If anyone knows of a better forums to post this in please tell me.

I am trying to write a Logon Script for my network that will display a HTML file every two hours (for security reasons).  What I have so far will only read .txt files.


```
'Declares varibles
Dim objFSO, objFile, strCharacters

'Open the file
Set objFSO = CreateObject("Scripting.FileSystemObject")
Set objFile = objFSO.OpenTextFile("C:\test.txt", 1)
	'To change the file change the path in the line above

'Read the file
Do Until objFile.AtEndOfStream
    strCharacters = strCharacters & objFile.Read(1)
Loop

'Display the file in a message box every 2 hours.
Do
	Wscript.Echo strCharacters
	WScript.sleep(7200*1000)
		'To change the amount of time change the first number in 
		'the line above to the number of seconds needed.
Loop
```

I don't know much about programming, most of this code has been copied from other places.  Any help you can give will be much apreciatied.

---

### Post by cwaldbieser on 2007-11-05
I am not too clear what you are trying to do.  Are you trying to read an HTML file and then-- what?  Display it in a message box?  Could you please explain a little more in depth what you are trying to accomplish?

---

### Post by Het Irv on 2007-11-06
> **cwaldbieser said:**
> I am not too clear what you are trying to do.  Are you trying to read an HTML file and then-- what?  Display it in a message box?  Could you please explain a little more in depth what you are trying to accomplish?
Sorry, Yeah that is about it. Really all I am trying to acomplish is to display the file every 2 hours. I'm not real picky on how the file is displayed.  I just don't want to use alot of system resources so I would like for this to work as simply as possible. The message box was the first thing that came to mind on this project.

---

### Post by cwaldbieser on 2007-11-06
> **Het Irv said:**
> Sorry, Yeah that is about it. Really all I am trying to acomplish is to display the file every 2 hours. I'm not real picky on how the file is displayed.  I just don't want to use alot of system resources so I would like for this to work as simply as possible. The message box was the first thing that came to mind on this project.

An HTML file is a text file.  I am not sure why your program wouldn't work on one.
Do you want to render the markup like a browser does?  Or is the trouble that you want to read the HTML from a URL rather than a filesystem path?

---

### Post by Het Irv on 2007-11-07
It does display the HTML but it also displays the HTML tags, which I don't want.  I just want the formating to display

---

### Post by cwaldbieser on 2007-11-07
> **Het Irv said:**
> It does display the HTML but it also displays the HTML tags, which I don't want.  I just want the formating to display

You probably want to use something like the web browser control to render the HTML.
[http://www.aspfree.com/c/a/VB.NET/Displaying-HTML-Content-with-a-Web-Browser-Control-in-Visual-Basic/]("http://www.aspfree.com/c/a/VB.NET/Displaying-HTML-Content-with-a-Web-Browser-Control-in-Visual-Basic/")

---

