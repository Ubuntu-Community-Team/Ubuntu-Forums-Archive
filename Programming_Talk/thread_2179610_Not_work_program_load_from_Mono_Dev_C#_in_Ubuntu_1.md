---
title: "Not work program load from Mono Dev C# in Ubuntu 13.04"
date: 2013-10-09
forum: Programming Talk
---

### Post by Wn3nQEK on 2013-10-09
Hi!
I use Ubuntu 13.04 and Mono Develop

I read this post: [http://ubuntuforums.org/showthread.php?t=1804818](http://ubuntuforums.org/showthread.php?t=1804818)
but this is no help me!!

I wrote code:

```
private static void OnButtFlashRomReadClick (object sender, EventArgs args)
    {
         ProcessStartInfo psi = new ProcessStartInfo();
        psi.FileName = "/tmp/bash.sh";
        psi.UseShellExecute = false;
        psi.RedirectStandardOutput = true;

        psi.Arguments = "test";
            Process p = Process.Start(psi);
        string strOutput = p.StandardOutput.ReadToEnd();
        p.WaitForExit();
        Console.WriteLine(strOutput);


        return;
    }
```

But when programm go to **Process.Start(psi)** line, all crashed!

**I use:**
 GTK#
Mono Develop 3.0.3.2
Ubuntu 13.04.

**Program trace:**
Loaded assembly: /home/guard/MonoProj/EXAMPLE/bin/Debug/EXAMPLE.exe
Loaded assembly: /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll [External]
Loaded assembly: /usr/lib/mono/gac/glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll [External]
Loaded assembly: /usr/lib/mono/gac/atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll [External]
Loaded assembly: /usr/lib/mono/gac/System/4.0.0.0__b77a5c561934e089/System.dll [External]
Resolved pending breakpoint at '/home/guard/MonoProj/EXAMPLE/MainWindow.cs:137' to Void MainWindow:OnButtFlashRomReadEndProcess (Object, EventArgs) [0x00000].
Resolved pending breakpoint at '/home/guard/MonoProj/EXAMPLE/MainWindow.cs:122' to Void MainWindow:OnButtFlashRomReadClick (Object, EventArgs) [0x00000].
Resolved pending breakpoint at '/home/guard/MonoProj/EXAMPLE/MainWindow.cs:134' to Void MainWindow:OnButtFlashRomReadClick (Object, EventArgs) [0x00049].
Loaded assembly: /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll [External]
Loaded assembly: /usr/lib/mono/gac/Mono.Posix/4.0.0.0__0738eb9f132ed756/Mono.Posix.dll [External]
Marshaling clicked signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ComponentModel.Win32Exception: ApplicationName='/tmp/bash.sh', CommandLine='test', CurrentDirectory=''
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start (System.Diagnostics.ProcessStartInfo startInfo) [0x00000] in <filename unknown>:0 
  at MainWindow.OnButtFlashRomReadClick (System.Object sender, System.EventArgs args) [0x0002a] in /home/guard/MonoProj/EXAMPLE/MainWindow.cs:128 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (System.Reflection.MonoMethod,object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at EXAMPLE.MainClass.Main(System.String[] args) in /home/guard/MonoProj/EXAMPLE/Main.cs:line 26

---

### Post by Mr.Pytagoras on 2013-10-09
do you have your script that you are trying to run in /tmp/bash.sh? also make sure that the script is executable and/or whether you have the permisions to use it
```
chmod +x /tmp/bash.sh
```

---

