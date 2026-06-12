---
title: "Need a sollution to this problem."
date: 2008-01-06
forum: Programming Talk
---

### Post by chris062689 on 2008-01-06
(I'm running a windows system for this server, sorry.  But the server client that it runs on requires windows.)

I need a C++ developer to design two simple programs for me.

1) A exe file that executes a DreamDaemon based server, and returns the PID of that DreamDaemon.

(Basicly this is simply a command line application)

Usage (perhaps?) : startworld MYDMB.dmb PORT
Need to Return: PID

2) A exe file that gracefully shuts down a program based on it's PID.

This is because the current startup() and shutdown() procs are bugged. If anyone could help with this, I would be grateful.

[http://byond.com](http://byond.com)
If ANYONE could help me with this, I'd be grateful.

---

### Post by Martin Witte on 2008-01-06
for the second one: on linux and other unixes (unices?) the command to use is ' kill -15 <pid>' (sorry, I missed the windows part in your question, please ignore this)

---

### Post by amo-ej1 on 2008-01-07
So you need a C++ programmer to write two 2-line shell scripts ? ;)

---

### Post by ghostdog74 on 2008-01-07
you should post to a job advertisment site instead. you will get better response.

---

### Post by nathandelane on 2008-01-07
First off, does it have to be C++?

In windows you can use taskkill.exe to kill the process:

[PHP]
taskkill /F /IM firefox.exe
[/PHP]

Or you could use WMI with vbscript:

[PHP]
Rem killCertainProcs.vbs
Rem This script uses WMI to find and kill certain processes.
Rem This script requires one command line argument, that pertains to the process name.
Rem
Rem To run this script, type:
Rem   cscript killCertainProcs.vbs processName.exe
Rem
Rem @author Nathan Lane
Rem @date 01/07/2008
Rem

Option Explicit

Dim wmi, processes, computer, processName, process

computer = "."

Set wmi = GetObject("winmgmts:{impersonationLevel=impersonate}!//" & computer & "/root/cimv2")
Set processes = wmi.ExecQuery("select * from win32_process")

processName = WScript.Arguments.Item(0)

For Each process In processes
        If StrComp(processName, process.Name) = 0 Then
                WScript.Echo "Name: " & process.Name
                WScript.Echo "PID: " & process.ProcessId
                WScript.Echo "Terminating " & process.Name & " with PID " & process.ProcessId & "...."
                process.Terminate()
        End If
Next[/PHP]

Save the script in a file named killCertainProcs.vbs. Then use this line to execute it:

[PHP]
cscript killCertainProcs.vbs firefox.exe
[/PHP]

The VBScript solution is much more elegant than its C++ counterpart and it uses existing Windows 32-bit services, namely WMI (Windows Management Instrumentation). You should just be able to start the server with a batch file (however you do that) and using the name of the executable you can kill it with this vbscript or with taskkill.exe.

Nathan

---

