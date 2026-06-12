---
title: "How to perform command in terminal using C#(Mono)"
date: 2011-07-23
forum: Programming Talk
---

### Post by Hilgert on 2011-07-23
Hi all,

How can i open the terminal, perform some linux command and close terminal by my application. I write on C#, use Mono.

Thanks!

---

### Post by PaulM1985 on 2011-07-23
Use the process class.
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)

This is something that has been discussed alot on this forum recently.  I recommend actually using C# libraries rather than calling shell commands.
[http://ubuntuforums.org/showthread.php?t=1804818](http://ubuntuforums.org/showthread.php?t=1804818)

What do you want to run in the terminal?  Is there no way in C# to do this?

Paul

---

### Post by Hilgert on 2011-07-23
yes, its no way to do this in C#, its "cutter" command, C# cant kill external connection without special api like iphlpapi, wsock32 on windows.

---

### Post by Hilgert on 2011-07-23
i tryed to use ProcessStartInfo and Process to execute .sh script, but i always catch error:

> Unhandled Exception: System.ComponentModel.Win32Exception: ApplicationName='/media/3C54C11754C0D4B4/test/new/cold/trunk/Server/Server/bin/Debug/test.sh', CommandLine='', CurrentDirectory=''
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start (System.Diagnostics.ProcessStartInfo startInfo) [0x00000] in <filename unknown>:0 
  at Server.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

I check the test.sh path many times but always catching this error.

Code i using:
```
            ProcessStartInfo psi = new ProcessStartInfo(); 
            psi.FileName = "test.sh"; 
            psi.UseShellExecute = false; 
            psi.RedirectStandardOutput = true; 
         
            //psi.Arguments = "test"; 
            Process p = Process.Start(psi); 
            string strOutput = p.StandardOutput.ReadToEnd(); 
            p.WaitForExit(); 
            Console.WriteLine(strOutput);
```

---

### Post by Hilgert on 2011-07-23
yeee, i fix it

C# code:
```
            string command = "sh"; 
            string argss = "/home/roma/server/test.sh"; 
            string verb = " "; 
             
            ProcessStartInfo procInfo = new ProcessStartInfo(); 
            procInfo.WindowStyle = ProcessWindowStyle.Normal; 
            procInfo.UseShellExecute = false; 
            procInfo.FileName = command;   // 'sh' for bash 
            procInfo.Arguments = argss;        // The Script name 
            procInfo.Verb = verb;                 // ------------ 
            Process.Start(procInfo);              // Start that process.
```

---

### Post by MadCow108 on 2011-07-23
the script was probably not executable
```
chmod u+x test.sh
```

---

