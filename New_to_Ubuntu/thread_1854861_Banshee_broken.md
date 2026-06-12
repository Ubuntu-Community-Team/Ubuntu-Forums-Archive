---
title: "Banshee broken"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by l3vity on 2011-10-05
Since upgrading to 11.10 beta to try out the gnome-shell I have been unable to run banshee. Launching from terminal gives the error 

```
Missing method AddDefaultFile in assembly /usr/lib/banshee/Banshee.ThickClient.dll, type Gtk.Rc

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at Nereid.Client.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at Nereid.Client.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 

```Have tried updating, even with --fix-missing, still no luck. I have also installed all gtk# technical items etc, can anyone help?

---

