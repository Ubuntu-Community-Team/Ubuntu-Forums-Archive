---
title: "Mono/GTKsharp issue in Jaunty"
date: 2009-04-15
forum: Programming Talk
---

### Post by lykwydchykyn on 2009-04-15
Not sure if I'm asking in the right place but I figure you guys would know what my next step is here.

I have a piece of software we use at work written in Mono/GTKsharp.  Most users use it on Windows, but I have it installed a few places on Kubuntu or Debian -- most notably, my own workstation.

The program has worked fine in Debian, Suse, and various other distros for several years.  It has worked fine in Kubuntu since I switched to it on my workstation a few releases ago (Gutsy, maybe?).

It also works fine on Windows using either the version of Mono it was written with (1.2.5) or the latest version of Mono (2.4).

It's not working on Jaunty, though.  I get a crash after running it like this:
> 
** (StaffClientv2:9127): WARNING **: Missing method .ctor in assembly /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll, type System.Runtime.CompilerServices.RuntimeCompatibilityAttribute                                                                                                                  

** (StaffClientv2:9127): WARNING **: The class System.Runtime.CompilerServices.RuntimeCompatibilityAttribute could not be loaded, used in gtk-sharp

** (StaffClientv2:9127): WARNING **: Can't find custom attr constructor image: /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll mtoken: 0x0a000119                                                                                                                                                          
Marshaling clicked signal                                                                                                                                       
Exception in Gtk# callback delegate                                                                                                                             
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.                                                                  
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.TypeLoadException: Could not load type 'System.Runtime.CompilerServices.RuntimeCompatibilityAttribute' from assembly 'gtk-sharp'.                                                                            
  at (wrapper managed-to-native) System.MonoCustomAttrs:GetCustomAttributesInternal (System.Reflection.ICustomAttributeProvider,System.Type,bool)               
  at System.MonoCustomAttrs.GetCustomAttributesBase (ICustomAttributeProvider obj, System.Type attributeType) [0x00000]                                         
  at System.MonoCustomAttrs.GetCustomAttributes (ICustomAttributeProvider obj, System.Type attributeType, Boolean inherit) [0x00000]                            
  at System.MonoCustomAttrs.RetrieveAttributeUsage (System.Type attributeType) [0x00000]                                                                        
  at System.MonoCustomAttrs.IsDefined (ICustomAttributeProvider obj, System.Type attributeType, Boolean inherit) [0x00000]
  at System.Reflection.MonoMethod.IsDefined (System.Type attributeType, Boolean inherit) [0x00000]
  at GLib.Object.InvokeClassInitializers (GType gtype, System.Type t) [0x00000]
  at GLib.Object.RegisterGType (System.Type t) [0x00000]
  at GLib.Object.LookupGType (System.Type t) [0x00000]
  at GLib.Object.LookupGType () [0x00000]
  at GLib.Object.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000]
  at Gtk.Object.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000]
  at Gtk.Widget.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000]
  at Gtk.Menu..ctor () [0x00000]
  at StaffClientv2.TicketListPopupMenu..ctor () [0x00000]
  at StaffClientv2.MainWindow.LoadGUIUnclaimedIconView () [0x00000]
  at StaffClientv2.MainWindow.LoadGUIElements () [0x00000]
  at StaffClientv2.MainWindow..ctor () [0x00000]
  at StaffClientv2.LoginWindow.OnLoginClicked (System.Object o, System.EventArgs args) [0x00000]
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000]
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000]
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000]
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000]
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000]
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000]
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000]
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000]
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000]
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at StaffClientv2.MainClass.Main(System.String[] args)


I have tried in both 32 and 64 bit Jaunty, and I get the same results.  I've tried googling what seem to be the relevant parts of the backtrace, and I can't find much other than some odd bug reports with no responses.

The person who wrote this app is long gone, I do have the code but it is not documented well and I don't grok C#.  I've managed to recompile it on my Intrepid box, but my recompiled versions do the same thing.  

I am using Kubuntu, so this app is the only thing I really need mono for.

Any advice?  Should I report a bug against gtk-sharp?  Can I install a newer mono on Jaunty?

---

### Post by directhex on 2009-04-15
Which compiler was this app compiled with? What does "gacutil --assemblyref foo.exe" return?

---

### Post by lykwydchykyn on 2009-04-15
> **directhex said:**
> Which compiler was this app compiled with? What does "gacutil --assemblyref foo.exe" return?

IIRC he wrote it on SimplyMepis 3.x using whatever monodevelop was current at the time.  That would be when etch was in testing.

My version of gacutil doesn't understand the --assemblyref switch and hasn't got anything similar to it.  It just says "unknown command".

---

### Post by directhex on 2009-04-15
> **lykwydchykyn said:**
> IIRC he wrote it on SimplyMepis 3.x using whatever monodevelop was current at the time.  That would be when etch was in testing.

My version of gacutil doesn't understand the --assemblyref switch and hasn't got anything similar to it.  It just says "unknown command".

Gah, sorry. **monodis** --assemblyref

---

### Post by lykwydchykyn on 2009-04-15
That worked:
```

AssemblyRef Table                                                    
1: Version=1.0.5000.0                                                
        Name=mscorlib                                                
        Flags=0x00000000                                             
        Public Key:                                                  
0x00000000: B7 7A 5C 56 19 34 E0 89                                  
2: Version=0.1.0.0                                                   
        Name=SimMySQL                                                
        Flags=0x00000000
        Zero sized public key
3: Version=2.8.0.0
        Name=gtk-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
4: Version=0.1.0.0
        Name=TicketLibrary
        Flags=0x00000000
        Zero sized public key
5: Version=2.8.0.0
        Name=glade-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
6: Version=2.8.0.0
        Name=gdk-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
7: Version=2.8.0.0
        Name=glib-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
8: Version=1.0.5000.0
        Name=System
        Flags=0x00000000
        Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89

```

BTW, the above is my output when running that command under intrepid.  Do you need the output on the Jaunty box?

---

### Post by directhex on 2009-04-15
> **lykwydchykyn said:**
> That worked:
```

AssemblyRef Table                                                    
1: Version=1.0.5000.0                                                
        Name=mscorlib                                                
        Flags=0x00000000                                             
        Public Key:                                                  
0x00000000: B7 7A 5C 56 19 34 E0 89                                  
2: Version=0.1.0.0                                                   
        Name=SimMySQL                                                
        Flags=0x00000000
        Zero sized public key
3: Version=2.8.0.0
        Name=gtk-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
4: Version=0.1.0.0
        Name=TicketLibrary
        Flags=0x00000000
        Zero sized public key
5: Version=2.8.0.0
        Name=glade-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
6: Version=2.8.0.0
        Name=gdk-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
7: Version=2.8.0.0
        Name=glib-sharp
        Flags=0x00000000
        Public Key:
0x00000000: 35 E1 01 95 DA B3 C9 9F
8: Version=1.0.5000.0
        Name=System
        Flags=0x00000000
        Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89

```

BTW, the above is my output when running that command under intrepid.  Do you need the output on the Jaunty box?

Try mono --runtime=v2.0.50727 program.exe

---

### Post by lykwydchykyn on 2009-04-15
> **directhex said:**
> Try mono --runtime=v2.0.50727 program.exe

Sweet! that worked!

What runtime did it use by default?

---

### Post by directhex on 2009-04-15
> **lykwydchykyn said:**
> Sweet! that worked!

What runtime did it use by default?

Your app is compiled against 1.0, as you can see from the version of the mscorlib dependency

We have deprecated 1.0 support in Jaunty.

---

### Post by lykwydchykyn on 2009-04-15
Is there an easy way for me to recompile the app against 2.0?  I recompiled it on Intrepid; if I recompile it on Jaunty, will it automatically use 2.0 or will I have to change the code in some way?

---

### Post by directhex on 2009-04-15
> **lykwydchykyn said:**
> Is there an easy way for me to recompile the app against 2.0?  I recompiled it on Intrepid; if I recompile it on Jaunty, will it automatically use 2.0 or will I have to change the code in some way?

Easy way: use "gmcs" instead of "mcs" to compile it

---

### Post by lykwydchykyn on 2009-04-15
Cool; Thanks again!

---

