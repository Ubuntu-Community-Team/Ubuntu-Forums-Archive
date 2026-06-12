---
title: "How to run .exe programs using wine"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by ellalan on 2008-08-14
Hi
I have downloaded a program (sidebarb 116.exe) and trying to install and run using wine. This is what I have done:
1.Downloaded the program.
2.Installed wine using synaptics.
3.When I type "wine /home/user/Desktop/sidebarb.116.exe" in the terminal I get this:
fixme:reg:GetNativeSystemInfo (0x33f3fc) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x12e4a8 0x33f33c) stub!
fixme:advapi:LookupAccountNameW (null) L"vignes" (nil) 0x33efe8 (nil) 0x33efec 0x33efe0 - stub
fixme:advapi:LookupAccountNameW (null) L"vignes" 0x14c1d8 0x33efe8 0x138058 0x33efec 0x33efe0 - stub
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 4 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 3 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 4 ignored L"Shortcut" table values
Successfully registered DLL C:\Program Files\\Desktop Sidebar\basicpanels.dll
Successfully registered DLL C:\Program Files\\Desktop Sidebar\outlookpanels.dll
Successfully registered DLL C:\Program Files\\Desktop Sidebar\sbhelp.dll
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly

Could someone please tell me now how to run the program please, I am running Hardy Heron.
Thank you in Advance.

---

### Post by starcannon on 2008-08-14
what is sidebarb 116.exe?

---

### Post by ellalan on 2008-08-14
Hi
It is a sidebar utility program with which you can install sidebar and modify it to suit your liking. Thank you for the quick response.

---

### Post by starcannon on 2008-08-14
If its a sidebar for windows, it likely won't work as intended in linux, however there are sidebars for linux, a really sweet one available for free is from google.

[http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html)

I use those and enjoy them alot.

---

