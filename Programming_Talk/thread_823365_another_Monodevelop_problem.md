---
title: "another Monodevelop problem"
date: 2008-06-09
forum: Programming Talk
---

### Post by x88a on 2008-06-09
Unhandled Exception: System.EntryPointNotFoundException: GetCurrentThreadId

how do i solve this?

tq

---

### Post by Lau_of_DK on 2008-06-09
> **x88a said:**
> Unhandled Exception: System.EntryPointNotFoundException: GetCurrentThreadId

how do i solve this?

tq

What caused it to be thrown? Other relevant details?

/Lau

---

### Post by x88a on 2008-06-09
here is the complete log

Unhandled Exception: System.EntryPointNotFoundException: GetCurrentThreadId
  at (wrapper managed-to-native) WeifenLuo.WinFormsUI.Docking.NativeMethods:GetCurrentThreadId ()
  at WeifenLuo.WinFormsUI.Docking.DockPanel+FocusManagerImpl+LocalWindowsHook.Install () [0x00000] 
  at WeifenLuo.WinFormsUI.Docking.DockPanel+FocusManagerImpl..ctor (WeifenLuo.WinFormsUI.Docking.DockPanel dockPanel) [0x00000] 
  at (wrapper remoting-invoke-with-check) FocusManagerImpl:.ctor (WeifenLuo.WinFormsUI.Docking.DockPanel)
  at WeifenLuo.WinFormsUI.Docking.DockPanel..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) WeifenLuo.WinFormsUI.Docking.DockPanel:.ctor ()
  at ECamTools.ECamViewer.InitializeComponent () [0x00170] in /home/jdwm/Desktop/ECamTools/ECamViewer/ECamViewer.Designer.cs:64 
  at ECamTools.ECamViewer..ctor (System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) ECamTools.ECamViewer:.ctor (string[])
  at ECamTools.Program.Main (System.String[] args) [0x0000b] in /home/jdwm/Desktop/ECamTools/ECamViewer/Program.cs:14 


tq

---

### Post by x88a on 2008-06-09
anyone out there can help me???
pls pls plssssss

---

### Post by Vadi on 2008-06-09
[http://www.monodevelop.com/Help_%26_Contact](http://www.monodevelop.com/Help_%26_Contact)

I think you're asking for a *bit* too much free support here.

---

### Post by kragen on 2008-06-09
> 
EntryPointNotFoundException

I think that says it all - your application needs an entry point.

Should be relatively easy to fix :)

---

### Post by Lau_of_DK on 2008-06-09
> **Vadi said:**
> [http://www.monodevelop.com/Help_%26_Contact](http://www.monodevelop.com/Help_%26_Contact)

I think you're asking for a *bit* too much free support here.

I disagree, I think its good that we can help each other out.

At OP: You need to make an entrypoint - For specific details its a good idea to hang out a #monodevelop to get instant answers.

/Lau

---

### Post by x88a on 2008-06-10
> **kragen said:**
> I think that says it all - your application needs an entry point.

Should be relatively easy to fix :)

i googled "Unhandled Exception: System.EntryPointNotFoundException: GetCurrentThreadId" and got this result.
[http://mail.python.org/pipermail/pythondotnet/2007-October/000681.html](http://mail.python.org/pipermail/pythondotnet/2007-October/000681.html)

i downloaded "DockPanel_2_2_Bin.zip" and attached "WeifenLuo.WinFormsUI.Docking.dll" to the references

my source code also comes with its own "WeifenLuo.WinFormsUI.Docking.dll". That doesnt work too.

what should i do?

tq

---

### Post by Lau_of_DK on 2008-06-10
> **x88a said:**
> i googled "Unhandled Exception: System.EntryPointNotFoundException: GetCurrentThreadId" and got this result.
[http://mail.python.org/pipermail/pythondotnet/2007-October/000681.html](http://mail.python.org/pipermail/pythondotnet/2007-October/000681.html)

i downloaded "DockPanel_2_2_Bin.zip" and attached "WeifenLuo.WinFormsUI.Docking.dll" to the references

my source code also comes with its own "WeifenLuo.WinFormsUI.Docking.dll". That doesnt work too.

what should i do?

tq

Like I said, I think it would be good for you to come hang out at #monodevelop and get straight answers from the experts. I'd love to help, but honestly I dont know whats up :(

/Lau

---

### Post by x88a on 2008-06-10
the website you gave me seem to be down now.
can you access the website?

---

### Post by scourge on 2008-06-10
This would be so much easier if you could show us the relevant code...

---

