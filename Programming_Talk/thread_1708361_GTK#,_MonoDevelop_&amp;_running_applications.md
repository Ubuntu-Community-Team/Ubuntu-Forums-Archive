---
title: "GTK#, MonoDevelop &amp; running applications"
date: 2011-03-16
forum: Programming Talk
---

### Post by ibito on 2011-03-16
I'm currently working with GTK# & Mono, and I can't get a list of running applications. I successfully listed the processes running using System.Diagnostics.Process.GetProcesses() but I don't know how to differentiate between background processes and "opened windows". 
The list I get doesn't show any MainWindowTitle or MainWindowHandle, any suggestions?

---

### Post by ve4cib on 2011-03-16
The process name should match whatever the name of the .exe you compiled is.  So if your executable is named "MyFirstMonoApplication.exe" then you should have that name appear somewhere in your list of processes.

Alternatively you could look at the command lines used to execute each process.  Guaranteed your executable's name will be there, even if the process runs under a different name.

Also, you should be aware that a single process can have multiple windows.  Take GIMP for example; by default it has at least 3 windows associated with the gimp process.  Each window may be handled by a separate thread within a process, but it's pretty rare for every single window within an application to be a separate process.

---

### Post by directhex on 2011-03-16
> **ibito said:**
> I'm currently working with GTK# & Mono, and I can't get a list of running applications. I successfully listed the processes running using System.Diagnostics.Process.GetProcesses() but I don't know how to differentiate between background processes and "opened windows". 
The list I get doesn't show any MainWindowTitle or MainWindowHandle, any suggestions?

I don't think anything in System will help you here. It assumes WinForms-style constructs (such as MainWindowHandle) which may not exist.

It's also sorta not possible to extract this info from the X server.

What are you trying to achieve?

---

