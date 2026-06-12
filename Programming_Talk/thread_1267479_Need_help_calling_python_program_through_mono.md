---
title: "Need help calling python program through mono"
date: 2009-09-15
forum: Programming Talk
---

### Post by KPS1 on 2009-09-15
Need help I am trying to execute a python program using mono, but have been very unsuccessful. 
My program needs to open a new terminal window, when the user click a command button, and display/run the python program. When the python program has finished it will close out. Any advice would be greatly appreciated. 
 
**Currently this is what I have tried.**
 
Dim processStartInfo = New ProcessStartInfo("DISPLAY=:32 /root/rxvt -geometry 80x25+150+150+sb -fn 9x15 -e /path/ProgramName", param) 
 
processStartInfo.UseShellExecute = False 
processStartInfo.ErrorDialog = False 
processStartInfo.WindowStyle = ProcessWindowStyle.Normal 
processStartInfo.RedirectStandardError = True 
processStartInfo.RedirectStandardInput = True 
processStartInfo.RedirectStandardOutput = True 
processStartInfo.CreateNoWindow = False 
 
Dim process As New Process() 
process.StartInfo = processStartInfo

---

### Post by directhex on 2009-09-15
> **KPS1 said:**
> Need help I am trying to execute a python program using mono, but have been very unsuccessful. 
My program needs to open a new terminal window, when the user click a command button, and display/run the python program. When the python program has finished it will close out. Any advice would be greatly appreciated. 
 
**Currently this is what I have tried.**
 
Dim processStartInfo = New ProcessStartInfo("DISPLAY=:32 /root/rxvt -geometry 80x25+150+150+sb -fn 9x15 -e /path/ProgramName", param) 
 
processStartInfo.UseShellExecute = False 
processStartInfo.ErrorDialog = False 
processStartInfo.WindowStyle = ProcessWindowStyle.Normal 
processStartInfo.RedirectStandardError = True 
processStartInfo.RedirectStandardInput = True 
processStartInfo.RedirectStandardOutput = True 
processStartInfo.CreateNoWindow = False 
 
Dim process As New Process() 
process.StartInfo = processStartInfo

Um... you don't seem to have entirely grasped the purpose of the parameters of the ProcessStartInfo object's constructor.

From MSDN:
> ProcessStartInfo(String, String)	Initializes a new instance of the  ProcessStartInfo class, specifies an application file name with which to start the process, and specifies a set of command-line arguments to pass to the application.

Ignoring for now your desire to define an environment variable, this means you're doing exactly the opposite of what you should be:
```

Dim processStartInfo = New ProcessStartInfo("DISPLAY=:32 /root/rxvt -geometry 80x25+150+150+sb -fn 9x15 -e /path/ProgramName", param) 

```
should be
```

Dim processStartInfo = New ProcessStartInfo("/root/rxvt", "-geometry 80x25+150+150+sb -fn 9x15 -e /path/ProgramName") 

```

Now, the unresolved issue with the environment. Try Environment.SetEnvironmentVariable( "DISPLAY", ":32" );

---

### Post by KPS1 on 2009-09-16
Worked like a charm.... Thanks for your help

---

