---
title: "WinXP Batch Scripting"
date: 2007-06-18
forum: Other OS Talk
---

### Post by Kodfish on 2007-06-18
OK. Windows XP's batch scripting engine sucks. A lot. I'm working on converting a perl script into a batch script for work, and i can't figure out for the life of me how the variable system works. I thought i'd come to you guys for help, since i know there are a ton of people on here that must have been forced to write some batch scripts at some time in their life. 

I need to figure out how to do the same thing as 
```
$tar = <STDIN>;
chomp $tar;
```
in batch script format. I tried using set /p but that just gives me a loop. 

Thanks, UbuntuForums!

---

### Post by Kodfish on 2007-06-18
Whoo, i found a really bad way to do it. you need 2 files. one is a .vbs:
```
strUserIn = InputBox("Target's IP Adress")
Set fs = CreateObject("Scripting.FileSystemObject")
strFileName = fs.BuildPath(Wscript.ScriptFullName & "\..", "ip.bat")
strFileName = fs.GetAbsolutePathName(strFileName)
Set ts = fs.OpenTextFile(strFileName, 2, True)
ts.WriteLine "set target=" & strUserIn
ts.Close

```
the other is the .bat:
```
@echo off
call ip.vbs
pause
call ip.bat
shutdown -r -m \\%target%
echo Will now ping target until upped, when you receive a ping reply hit control c, come back to this window, and press any key.
pause
start ping -t %target%
pause
telnet %target%

```

if you find a better way to do it, please tell me!

---

### Post by LaRoza on 2007-06-19
Batch is limited, why not use Perl?

[http://www.activestate.com/](http://www.activestate.com/)

-if you can install on the computer, this would probably be better.

---

