---
title: "monodevelop to work on 6.10 edgy"
date: 2006-10-26
forum: Programming Talk
---

### Post by rammy22 on 2006-10-26
I uograded to 6.10 edgy and monodevelop doesn't seem to work.  WHen I click on Applications->Programming->Mnoodevelop from previous 6.60 installation nothing happens. I ran the command to upgrade all the mono files
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop
but that doesn't seem to work.
Running from terminal (bash shell) I type "monodevelop" and get output

** (./MonoDevelop.exe:6036): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   log4net    (assemblyref_index=5)
     Version:    1.2.9.0
     Public Key: a5715cc6d5c3540b
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (./MonoDevelop.exe:6036): WARNING **: Could not load file or assembly 'log4net, Version=1.2.9.0, Culture=neutral, PublicKeyToken=a5715cc6d5c3540b' or one of its dependencies.

** (./MonoDevelop.exe:6036): WARNING **: Missing method Configure in assembly /usr/lib/monodevelop/bin/MonoDevelop.Core.dll, type log4net.Config.XmlConfigurator

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'log4net, Version=1.2.9.0, Culture=neutral, PublicKeyToken=a5715cc6d5c3540b' or one of its dependencies.
  at <0x00000> <unknown method>
  at MonoDevelop.Core.Runtime.get_LoggingService () [0x00000] 
  at MonoDevelop.Core.ServiceManager.FetchService (System.Type serviceType) [0x00000] 
  at MonoDevelop.Core.ServiceManager.GetService (System.Type serviceType) [0x00000] 
  at MonoDevelop.Core.AddIns.Setup.SetupService..ctor () [0x00000] 
  at MonoDevelop.Core.Runtime.get_SetupService () [0x00000] 
  at MonoDevelop.Core.AddIns.AddInService.Initialize () [0x00000] 
Does anyone understand the error, and how to get monodevelop to run on 6.10 Edgy
Thanks for help

---

