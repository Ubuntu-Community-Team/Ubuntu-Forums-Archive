---
title: "Banshee not opening"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by fillmont on 2011-10-14
So, after upgrading to 11.10, everything has been hunky dory, except Banshee refuses to open. In the launcher, the icon simply pulses a few times before...nothing happens.

Any ideas how to diagnose this? No other program seems to be choking like this. 

Is the best solution to just uninstall and reinstall?

---

### Post by dniMretsaM on 2011-10-14
Open banshee from terminal and post the output.
```
banshee
```

---

### Post by fillmont on 2011-10-14
Here we go:

```
Missing method System.Reflection.Assembly::op_Inequality(Assembly,Assembly) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll
Missing method System.Reflection.Assembly::op_Inequality(Assembly,Assembly) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll
[Info  12:38:40.333] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
Missing method System.Reflection.Assembly::op_Equality(Assembly,Assembly) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/Mono.Addins/0.6.0.0__0738eb9f132ed756/Mono.Addins.dll
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.MissingMethodException: Method not found: 'System.Reflection.Assembly.op_Equality'.
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
Missing method System.Type::op_Inequality(Type,Type) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll

Unhandled Exception: System.MissingMethodException: Method not found: 'System.Type.op_Inequality'.
  at Hyena.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] (System.String[] args) [0x00000] in <filename unknown>:0 
  at Nereid.Client.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.MissingMethodException: Method not found: 'System.Type.op_Inequality'.
  at Hyena.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] (System.String[] args) [0x00000] in <filename unknown>:0 
  at Nereid.Client.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 

```

---

### Post by dniMretsaM on 2011-10-14
One thing you might try is updating to the latest stable version of Banshee (2.2.0-1). Add [this]("https://launchpad.net/%7Ebanshee-team/+archive/ppa") PPA in USC or run this in terminal:
```
sudo add-apt-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

