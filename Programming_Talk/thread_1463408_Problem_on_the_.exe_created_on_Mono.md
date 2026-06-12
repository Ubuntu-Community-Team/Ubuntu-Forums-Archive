---
title: "Problem on the .exe created on Mono"
date: 2010-04-26
forum: Programming Talk
---

### Post by satimis on 2010-04-26
Hi folks,


I'm now learning mono/GTK# on mono making a cross platform .exe.  The shell.exe which I'm testing is only a test sample created/compiled by me on mono.

It works on Linux without problem.  On console run;

```

$ mono /path/to/shell.exe

```


starts a small window.  On its top box type:```

firefox www.mono-project.com

```

start mono webpage


On Window Vista "Command Prompt"
```

C:>@start "" /b "C:\Program Files\Internet Explorer\iexplore.exe" %*

```

IE started without problem.


On Mono-2.6.3 Command Prompt run;```

C:>mono \path\to\shell.exe

```

It starts the small window. 

On the said window run;```

@start "" /b "C:\Program Files\Internet Explorer\iexplore.exe" %*

OR
@start "" /b "C:\Program Files\Internet Explorer\iexplore.exe" www.mono-project.com

```


The small window crashes with following warnings printed on Mono Command Prompt:-```

Marshaling clicked signal
Exception in Gtk# callback delegate
Note: Applications can use GLib.ExceptionManager.UnhandledException to handle
the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the ta
rget of an invocation. ---> System.ComponentModel.Win32Exception: ApplicationNam
e='@start', CommandLine='""', CurrentDirectory=''
at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartIn
fo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown
>:0
at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInf
o startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>
:0
at System.Diagnostics.Process.Start () [0x00000] in <filename unknown>:0
at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
at MainWindow.onButtonRunClicked (System.Object sender, System.EventArgs e) [0
x00000] in <filename unknown>:0
at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (ob
ject,object[],System.Exception&)
at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invoke
Attr, System.Reflection.Binder binder, System.Object[] parameters, System.Global
ization.CultureInfo culture) [0x00000] in <filename unknown>:0
--- End of inner exception stack trace ---
at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invoke
Attr, System.Reflection.Binder binder, System.Object[] parameters, System.Global
ization.CultureInfo culture) [0x00000] in <filename unknown>:0
at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] par
ameters) [0x00000] in <filename unknown>:0
at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <file
name unknown>:0
at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000]
in <filename unknown>:0
at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename
unknown>:0
at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args
) [0x00000] in <filename unknown>:0
at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <file
name unknown>:0
at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val,
UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal
_data) [0x00000] in <filename unknown>:0
at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean
is_terminal)
at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val,
UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal
_data)
at Gtk.Application.gtk_main()
at Gtk.Application.Run()
at shell.MainClass.Main(System.String[] args)

```

Please help.  TIA


B.R.
satimis

---

### Post by phrostbyte on 2010-04-26
I am assuming you are using Process.Start ?

If so, please omit the "@start", it will work on Windows only. start is a Windows binary that resolves protocols. But it is not needed.

This will also work too:

Process.Start("http://www.blahblah.com");

and it should work on Windows AND Linux.

---

### Post by satimis on 2010-04-27
Hi phrostbyte,

Thanks for your advice.

> **phrostbyte said:**
> I am assuming you are using Process.Start ?

If so, please omit the "@start", it will work on Windows only. start is a Windows binary that resolves protocols. But it is not needed.

This will also work too:

Process.Start("http://www.blahblah.com");


Sorry I don't follow. Please explain in more detail how to make it?  On the codes?


My small program works 100% on Linux.  It also works on Windows Vista with the commands for "Command Prompt" window.


Example:
notepad
calc
etc.

They works 100% on the small program starting Notepad and Calculator respectively on Vista.

I have not idea to start IE with a command on "Command Prompt" window NOT a command line.

Do you know the command to start IE on on "Command Prompt" window?  TIA


B.R.
satimis

---

