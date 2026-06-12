---
title: "Using MonoDevelop to take user Input in external console"
date: 2014-04-13
forum: Programming Talk
---

### Post by WinterMadness on 2014-04-13
Hey guys, anyone have the solution to this? As some of you may know, in Monodevelop its console windows is read only. So I want to run it in an external console window so I can debug more efficiently.

I goto Project>[Project Name] options>General> and then I check run in external console

when I run it I get the following error:

File name has not been set
System.InvalidOperationException: File name has not been set
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start () [0x00000] in <filename unknown>:0 
  at MonoDevelop.Core.Execution.ProcessWrapper.Start () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) MonoDevelop.Core.Execution.ProcessWrapper:Start ()
  at MonoDevelop.Platform.GnomePlatform.StartConsoleProcess (System.String command, System.String arguments, System.String workingDirectory, IDictionary`2 environmentVariables, System.String title, Boolean pauseWhenFinished) [0x00000] in <filename unknown>:0 
  at MonoDevelop.Core.Execution.ProcessService.StartConsoleProcess (System.String command, System.String arguments, System.String workingDirectory, IDictionary`2 environmentVariables, IConsole console, System.EventHandler exited) [0x00000] in <filename unknown>:0 
  at MonoDevelop.Debugger.Soft.SoftDebuggerEngine+<CreateDebuggerStartInfo>c__AnonStorey1.<>m__6 (System.Diagnostics.ProcessStartInfo info) [0x00000] in <filename unknown>:0 
  at Mono.Debugger.Soft.VirtualMachineManager.BeginLaunch (System.Diagnostics.ProcessStartInfo info, System.AsyncCallback callback, Mono.Debugger.Soft.LaunchOptions options) [0x00000] in <filename unknown>:0 
  at Mono.Debugging.Soft.SoftDebuggerSession.StartLaunching (Mono.Debugging.Soft.SoftDebuggerStartInfo dsi) [0x00000] in <filename unknown>:0 
  at Mono.Debugging.Soft.SoftDebuggerSession.OnRun (Mono.Debugging.Client.DebuggerStartInfo startInfo) [0x00000] in <filename unknown>:0 
  at Mono.Debugging.Client.DebuggerSession+<Run>c__AnonStorey6.<>m__3 () [0x00000] in <filename unknown>:0 

I dont know what thats about. Theres a text box that says parameters. Perhaps I need to send it directly to "Konsole?" I dont know how to do that.

---

