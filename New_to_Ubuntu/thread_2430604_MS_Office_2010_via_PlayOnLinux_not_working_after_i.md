---
title: "MS Office 2010 via PlayOnLinux not working after installation"
date: 2019-11-04
forum: New to Ubuntu
---

### Post by alanralph on 2019-11-04
I am new to Lubuntu.

This thread - [https://ubuntuforums.org/showthread.php?t=2369334&highlight=office+2010](https://ubuntuforums.org/showthread.php?t=2369334&highlight=office+2010) - was closed but I have a similar question. 

I installed MS Office 2010 (only PP, Excel, Word) from an old DVD I have. I have a valid working Product Key. Yet none of the 3 applications will open. It starts to, then gets hung up, and I have to Ctrl-Alt-Del and kill it.  

I have a log file that PlayOnLinux generated but I have no idea what any of it means.

In the closed thread linked above, there was one answer mentioning "32 bit wine prefix". How is this installed, and did it need to be installed prior to MS Office via PlayOnLinux?  Finally, if I just want to uninstall it, is that possible? I thought I did so via PlayOnLinux when I "removed" the application but it didn't remove anything other than the icon in PlayOnLinux! (*I tried the installation twice and on the second time I was asked if I wanted to copy over the same virtual directory*).

This forum won't let me attach the log file, so here is a copy of the text:

```
[TABLE="width: 500"]
[TR]
[TD][11/04/19 14:54:50] - Running wine-3.0.2 --version (Working directory : /home/alanralph/.PlayOnLinux/shortcuts)
wine-3.0.2

PlayOnLinux logfile
-------------------
Date: 11/04/19 14:54:50


> PlayOnLinux Version
  4.3.4
> uname -a
  Linux alan-s120-linux 5.0.0-32-generic #34-Ubuntu SMP Wed Oct 2 02:06:48 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
> lsb_release -a
  
> wine --version
  wine-3.0.2
> POL_WINEVERSION
  3.0.2
> WINEPREFIX
  /home/alanralph/.PlayOnLinux//wineprefix/Office2010
> Distribution
  Ubuntu 19.04
> glxinfo \| grep rendering
  direct rendering: Yes
> glxinfo \| grep renderer
      GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 500 (Broxton 2x6) 
> OpenGL libs (Direct rendering testing)
  check_dd_x86 missing, test skipped
  check_dd_amd64 missing, test skipped

[11/04/19 14:55:12] - Running wine-3.0.2 cmd /c echo %ProgramFiles% (Working directory : /home/alanralph/.PlayOnLinux/shortcuts)
0025:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
0025:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 31
C:\Program Files
[11/04/19 14:55:16] - Running wine-3.0.2 /home/alanralph/Downloads/en_office_professional_plus_2010_x86_515486.exe (Working directory : /home/alanralph/.PlayOnLinux/shortcuts)
0026:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
0026:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 31
002e:fixme:ntdll:EtwEventRegister ({8736922d-e8b2-47eb-8564-23e77e728cf3}, 0x2e034ec1, 0x2e0b3d78, 0x2e0b3d70) stub.
002e:fixmeprocess:GetSystemDEPPolicy stub
002e:fixmeprocess:SetProcessDEPPolicy (1): stub
002e:fixme:ntdll:EtwEventRegister ({8736922d-e8b2-47eb-8564-23e77e728cf3}, 0x101f57e7, 0x103a5908, 0x103a5900) stub.
002e:fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
002e:fixme:richedit:REExtendedRegisterClass semi stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002f:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
002e:fixme:richedit:ME_HandleMessage EM_SETEDITSTYLE: stub
002e:fixme:richedit:ME_HandleMessage EM_SETBIDIOPTIONS: stub
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0030:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0033:fixme:ole:CoInitializeSecurity (0x69b2e0,-1,(nil),(nil),2,3,(nil),0,(nil)) - stub!
0033:fixme:ole:NdrCorrelationInitialize (0x16adc54, 0x16add30, 1024, 0x0): semi-stub
0033:fixme:ole:NdrCorrelationInitialize (0x16adc34, 0x16add10, 1024, 0x0): semi-stub
0033:fixme:ole:NdrCorrelationInitialize (0x16adc14, 0x16adcf0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16adc14): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16adc94, 0x16add70, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16adc94): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad894, 0x16ad970, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad894): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad894, 0x16ad970, 1024, 0x0): semi-stub
003f:fixme:ole:NdrCorrelationInitialize (0x87f704, 0x87f7e0, 1024, 0x0): semi-stub
003f:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003f:fixme:ole:NdrCorrelationFree (0x87f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad894): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad8a4, 0x16ad980, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad8a4): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad824, 0x16ad900, 1024, 0x0): semi-stub
003f:fixme:ole:NdrCorrelationInitialize (0x87f704, 0x87f7e0, 1024, 0x0): semi-stub
003f:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003f:fixme:ole:NdrCorrelationFree (0x87f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad824): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad864, 0x16ad940, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad864): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ad7b4, 0x16ad890, 1024, 0x0): semi-stub
003f:fixme:ole:NdrCorrelationInitialize (0x87f704, 0x87f7e0, 1024, 0x0): semi-stub
003f:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003f:fixme:ole:NdrCorrelationFree (0x87f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ad7b4): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ac144, 0x16ac220, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ac144): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ac3c4, 0x16ac4a0, 1024, 0x0): semi-stub
003f:fixme:ole:NdrCorrelationInitialize (0x87f704, 0x87f7e0, 1024, 0x0): semi-stub
003f:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003f:fixme:ole:NdrCorrelationFree (0x87f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ac3c4): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16ac3c4, 0x16ac4a0, 1024, 0x0): semi-stub
003e:fixme:ole:NdrCorrelationInitialize (0x76f704, 0x76f7e0, 1024, 0x0): semi-stub
003e:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
003e:fixme:ole:NdrCorrelationFree (0x76f704): stub
0033:fixme:ole:NdrCorrelationFree (0x16ac3c4): stub
0033:fixme:ole:NdrCorrelationInitialize (0x16aac14, 0x16aacf0, 1024, 0x0): semi-stub
.
.
(tons more of the same lines about 'stub' and 'semi-stub')
.
.
0033:fixme:ole:NdrCorrelationFree (0x16aafe4): stub0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0167:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0173:fixme:service:SERV_QueryServiceObjectSecurity 0xb62d020 4 (nil) 0 0xe88fa70 - semi-stub
0173:fixme:service:SERV_QueryServiceObjectSecurity 0xb62d020 4 0xb625870 28 0xe88fa74 - semi-stub
017f:fixme:hnetcfg:fwpolicy2_get_CurrentProfileTypes 0xb62e438 0xeaafba4
017f:fixme:hnetcfg:fw_apps_Remove 0xb62b080, L"C:\\Program Files\\Microsoft Office\\Office14\\onenote.exe"
0181:fixme:hnetcfg:fwpolicy2_get_CurrentProfileTypes 0xb62f778 0xeaafba4
0181:fixme:hnetcfg:fw_apps_Remove 0xb6258c8, L"C:\\Program Files\\Microsoft Office\\Office14\\outlook.exe"
0033:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0033:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0033:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0033:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0033:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xb5ab400 4 (nil) 0 0xedffa50 - semi-stub
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xb5ab400 4 0xb5ab3d8 28 0xedffa54 - semi-stub
019e:fixme:advapi:SetSecurityInfo stub: Service objects are not supported at this time.
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xbe23058 4 (nil) 0 0xedffa50 - semi-stub
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xbe23058 4 0xbe23030 28 0xedffa54 - semi-stub
019e:fixme:advapi:SetSecurityInfo stub: Service objects are not supported at this time.
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xbe23180 4 (nil) 0 0xedffa50 - semi-stub
019e:fixme:service:SERV_QueryServiceObjectSecurity 0xbe23180 4 0xbe230a0 28 0xedffa54 - semi-stub
019e:fixme:advapi:SetSecurityInfo stub: Service objects are not supported at this time.
01aa:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
01aa:fixme:heap:RtlSetHeapInformation 0x110000 0 0x33fe38 4 stub
01aa:fixme:ntdll:EtwRegisterTraceGuidsW (0x1043d32, 0x14277e8, {bf3736e4-23ae-47c3-b472-a03c2c3550fe}, 1, 0x33fe20, (null), (null), 0x14277f0): stub
01aa:fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {bf3736e4-23ae-47c3-b472-a03c2c3550fe}
01aa:fixme:ntdll:EtwRegisterTraceGuidsW (0x1043d32, 0x1427808, {ff1671c8-2eea-42b3-8143-a8da2634c369}, 1, 0x33fe20, (null), (null), 0x1427810): stub
01aa:fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {ff1671c8-2eea-42b3-8143-a8da2634c369}
01aa:fixme:ntdll:EtwEventRegister ({4c45ee69-2afe-4f15-9204-97fb58edfabd}, (nil), (nil), 0x1427850) stub.
01aa:fixmeole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
01ad:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002800): stub
01ad:fixme:advapi:RegisterEventSourceW ((null),L"Office Software Protection Platform Service"): stub
01ad:fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x40000384,(nil),0x0000,0x00000000,(nil),(nil)): stub
01ad:fixme:advapi:DeregisterEventSource (0xcafe4242) stub
01b0:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002820): stub
01ad:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002810): stub
01b0:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002840): stub
01b0:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002850): stub
01b0:fixme:advapi:RegisterEventSourceW ((null),L"Office Software Protection Platform Service"): stub
01b0:fixme:advapi:ReportEventW (0xcafe4242,0x0000,0x0000,0x40000386,(nil),0x0001,0x00000000,0x126448,(nil)): stub
01b0:fixme:advapi:DeregisterEventSource (0xcafe4242) stub
01b0:fixme:ntdll:EtwEventEnabled (deadbeef, 0x1002830): stub
01b3:fixme:ole:NdrCorrelationInitialize (0xeacec94, 0xeaced70, 1024, 0x0): semi-stub
01b0:fixme:ole:NdrCorrelationInitialize (0x98f704, 0x98f7e0, 1024, 0x0): semi-stub
01b0:fixme:ole:NdrCorrelationFree (0x98f704): stub
01b3:fixme:ole:NdrCorrelationFree (0xeacec94): stub
01b3:fixme:ole:NdrCorrelationInitialize (0xeacee64, 0xeacef40, 1024, 0x0): semi-stub
01b0:fixme:ole:NdrCorrelationInitialize (0x98f704, 0x98f7e0, 1024, 0x0): semi-stub
01b0:fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
01b0:fixme:ntdll:EtwRegisterTraceGuidsW (0x6f01b6a5, 0x6f15e4a8, {bf3736e4-23ae-47c3-b472-a03c2c3550fe}, 1, 0x98ee60, (null), (null), 0x6f15e4b0): stub
01b0:fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {bf3736e4-23ae-47c3-b472-a03c2c3550fe}
01b0:fixme:ntdll:EtwRegisterTraceGuidsW (0x6f01b6a5, 0x6f15e4c8, {ff1671c8-2eea-42b3-8143-a8da2634c369}, 1, 0x98ee60, (null), (null), 0x6f15e4d0): stub
01b0:fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {ff1671c8-2eea-42b3-8143-a8da2634c369}
01b0:fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
.
.
(more of the same)
.
.
01af:fixme:advapi:RegisterEventSourceW ((null),L"Office Software Protection Platform Service"): stub
01af:fixme:advapi:ReportEventW (0xcafe4242,0x0000,0x0000,0x40000387,(nil),0x0000,0x00000000,0x87fd14,(nil)): stub
01af:fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[11/04/19 15:04:44] - ----- Starting function POL_Install_dotnet20 -----
[11/04/19 15:04:44] - Running wine-3.0.2 uninstaller --remove {E45D8920-A758-4088-B6C6-31DBB276992E} (Working directory : /home/alanralph/.PlayOnLinux/tmp)
002a:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
002a:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 31
0038:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
0038:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 5)
0038:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 5)
[11/04/19 15:04:48] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/regkey.reg (Working directory : /home/alanralph/.PlayOnLinux/tmp)
[11/04/19 15:04:48] - Content of /home/alanralph/.PlayOnLinux//tmp/regkey.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine]
"Version"="win2k"
-----------
[11/04/19 15:04:49] - Running wine-3.0.2 regedit dotnet20_fix.reg (Working directory : /home/alanralph/.PlayOnLinux/tmp)
[11/04/19 15:04:49] - Content of dotnet20_fix.reg
-----------
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion]
"ProductName"="Microsoft Windows 2000"
"CSDVersion"=""
"CurrentVersion"="5.0"
"CurrentBuildNumber"="2195"
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Windows]
"CSDVersion"=dword:00000000
-----------
[11/04/19 15:04:50] - ----- Starting function POL_Install_corefonts -----
[11/04/19 15:04:50] - ----- Starting function POL_Internal_InstallFonts -----
[11/04/19 15:04:50] - ----- Ending function POL_Internal_InstallFonts -----
[11/04/19 15:04:51] - ----- Ending function POL_Install_corefonts -----
[11/04/19 15:04:51] - Running wine-3.0.2 dotnetfx.exe /q /c:install.exe /q (Working directory : /home/alanralph/.PlayOnLinux/ressources/dotnet20)
0043:fixme:advapi:DecryptFileA ("C:\\users\\alanralph\\Temp\\IXP000.TMP\\", 00000000): stub
004c:fixme:advapi:LsaOpenPolicy ((null),0x33f358,0x00000001,0x33f344) stub
004c:fixme:advapi:LsaClose (0xcafe) stub
004c:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\cscomp.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsn.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorwks.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\system32\\mscoree.dll", "C:\\windows\\system32\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorjit.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorpe.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\vbc.exe", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
004d:fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\diasymreader.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub
0077:err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
 077:err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
 0077:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
 0077:err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
007b:fixme:mofcomp:wmain stub
00b3:err:Ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
00b3:err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
00b3:err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
00b3:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
00b3:err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
00b3:fixme:advapi:RegisterEventSourceW ((null),L"ASP.NET 2.0.50727.0"): stub
00b3:fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0001,0x400003f9,(nil),0x0002,0x00000000,0x33ed3c,(nil)): stub
00b3:fixme:advapi:DeregisterEventSource (0xcafe4242) stub
00b3:fixme:loadperf:UnloadPerfCounterTextStringsW (L"u \"ASP.NET_2.0.50727\"", 1): stub
00bc:fixme:mofcomp:wmain stub
00b3:fixme:advapi:LsaOpenPolicy ((null),0x33e8e0,0x000f0fff,0x33e920) stub
00b3:fixme:advapi:LsaStorePrivateData (0xcafe,0x33e914,(nil)) stub
00b3:fixme:advapi:LsaClose (0xcafe) stub
00b3:fixme:loadperf:LoadPerfCounterTextStringsW (L"l \"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\aspnet_state_perf.ini\"", 1): stub
00b0:fixme:service:svcctl_ChangeServiceConfig2W SERVICE_CONFIG_FAILURE_ACTIONS not implemented: period 86400 msg (null) cmd (null)
00af:fixme:service:svcctl_ChangeServiceConfigW Setting password not supported
.
(more of the same)
.

[11/04/19 15:06:10] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/regkey.reg (Working directory : /home/alanralph/.PlayOnLinux/ressources/dotnet20)
[11/04/19 15:06:10] - Content of /home/alanralph/.PlayOnLinux//tmp/regkey.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine]
"Version"="winxp"
-----------
0037:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
0037:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 31
[11/04/19 15:06:11] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/setos.reg (Working directory : /home/alanralph/.PlayOnLinux/ressources/dotnet20)
[11/04/19 15:06:11] - Content of /home/alanralph/.PlayOnLinux//tmp/setos.reg
-----------
REGEDIT4

[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion]
"CSDVersion"="Service Pack 3"
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Windows]
"CSDVersion"=dword:00000300
-----------
[11/04/19 15:06:11] - Running wine-3.0.2 regedit Default_OS_Version.reg (Working directory : /home/alanralph/.PlayOnLinux/ressources/dotnet20)
[11/04/19 15:06:11] - Content of Default_OS_Version.reg
-----------
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion]
"ProductName"="Microsoft Windows XP"
"CSDVersion"="Service Pack 3"
"CurrentVersion"="5.3"
"CurrentBuildNumber"="2600"
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Windows]
"CSDVersion"=dword:00000300
-----------
[11/04/19 15:06:11] - ----- Ending function POL_Install_dotnet20 -----
[11/04/19 15:06:12] - ----- Starting function POL_Install_gecko -----
[11/04/19 15:06:12] - ----- Ending function POL_Install_gecko -----
[11/04/19 15:06:13] - ----- Starting function POL_Install_corefonts -----
[11/04/19 15:06:13] - ----- Starting function POL_Internal_InstallFonts -----
[11/04/19 15:06:13] - ----- Ending function POL_Internal_InstallFonts -----
[11/04/19 15:06:13] - ----- Ending function POL_Install_corefonts -----
[11/04/19 15:06:14] - ----- Starting function POL_Install_gdiplus -----
[11/04/19 15:06:14] - Running wine-3.0.2 WindowsXP-KB975337-x86-ENU.exe /extract:C:\Tmp /q (Working directory : /home/alanralph/.PlayOnLinux/ressources)
0049:fixme:advapi:DecryptFileA ("C:\\Tmp\\", 00000000): stub
[11/04/19 15:06:16] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/Tmp)
[11/04/19 15:06:16] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*gdiplus"="native"
-----------
[11/04/19 15:06:16] - ----- Ending function POL_Install_gdiplus -----
[11/04/19 15:06:17] - ----- Starting function POL_Install_riched20 -----
[11/04/19 15:06:18] - ----- Starting function POL_SP2_Extract -----
[11/04/19 15:06:21] - ----- Ending function POL_SP2_Extract -----
[11/04/19 15:06:21] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:21] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*riched20"="native,builtin"
-----------
[11/04/19 15:06:21] - ----- Ending function POL_Install_riched20 -----
[11/04/19 15:06:22] - ----- Starting function POL_Install_riched30 -----
[11/04/19 15:06:22] - ----- Starting function POL_Install_riched20 -----
[11/04/19 15:06:23] - ----- Starting function POL_SP2_Extract -----
0012:fixme:msvcrt:__clean_type_info_names_internal (0x64083a50) stub
[11/04/19 15:06:25] - ----- Ending function POL_SP2_Extract -----
[11/04/19 15:06:25] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:25] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*riched20"="native,builtin"
-----------
0019:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb24 0x95fb1c
0038:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
0038:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 31
[11/04/19 15:06:26] - ----- Ending function POL_Install_riched20 -----
[11/04/19 15:06:26] - ----- Ending function POL_Install_riched30 -----
[11/04/19 15:06:27] - ----- Starting function POL_Install_msxml6 -----
[11/04/19 15:06:27] - Running wine-3.0.2 msiexec /i msxml6_x86.msi /q (Working directory : /home/alanralph/.PlayOnLinux/ressources)
0045:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
[11/04/19 15:06:28] - ----- Ending function POL_Install_msxml6 -----
[11/04/19 15:06:29] - ----- Starting function POL_Install_mspatcha -----
[11/04/19 15:06:29] - ----- Starting function POL_SP2_Extract -----
0019:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb20 0x95fb18
[11/04/19 15:06:31] - ----- Ending function POL_SP2_Extract -----
[11/04/19 15:06:31] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:31] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*mspatcha"="native,builtin"
-----------
[11/04/19 15:06:32] - ----- Ending function POL_Install_mspatcha -----
[11/04/19 15:06:32] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:32] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*riched20"="native,builtin"
-----------
0019:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb20 0x95fb18
0019:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb64 0x95fb5c
0019:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb24 0x95fb1c
[11/04/19 15:06:33] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:33] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*riched30"="native,builtin"
-----------
[11/04/19 15:06:33] - Running wine-3.0.2 regedit /home/alanralph/.PlayOnLinux//tmp/override-dll.reg (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/windows/system32)
[11/04/19 15:06:33] - Content of /home/alanralph/.PlayOnLinux//tmp/override-dll.reg
-----------
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*gdiplus"="native,builtin"
-----------
[11/04/19 15:06:34] - Running wine-3.0.2 winepath -u C:\\users\\alanralph\\Desktop (Working directory : /home/alanralph/.local/share/applications)
/home/alanralph/.PlayOnLinux//wineprefix/Office2010/dosdevices/c:/users/alanralph/Desktop
[11/04/19 15:06:35] - Running wine-3.0.2 winepath -u C:\\users\\alanralph\\Desktop (Working directory : /home/alanralph/.local/share/applications)
/home/alanralph/.PlayOnLinux//wineprefix/Office2010/dosdevices/c:/users/alanralph/Desktop
[11/04/19 15:06:35] - Running wine-3.0.2 winepath -u C:\\users\\alanralph\\Desktop (Working directory : /home/alanralph/.local/share/applications)
/home/alanralph/.PlayOnLinux//wineprefix/Office2010/dosdevices/c:/users/alanralph/Desktop
0012:fixme:msvcrt:__clean_type_info_names_internal (0x64083a50) stub
[11/04/19 15:07:51] - Running wine-3.0.2 WINWORD.EXE (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/Program Files/Microsoft Office/Office14)
wine: Unhandled exception 0xc0000417 in thread 84 at address 0x7e490023:0x102f7ba1 (thread 0084), starting debugger...
[11/04/19 15:09:37] - Running wine-3.0.2 WINWORD.EXE (Working directory : /home/alanralph/.PlayOnLinux/wineprefix/Office2010/drive_c/Program Files/Microsoft Office/Office14)
0017:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb24 0x95fb1c
0031:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
.
.
.

007d:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
007d:fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
0070:fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
wine: Unhandled exception 0xc0000417 in thread 70 at address 0x330023:0x102f7ba1 (thread 0070), starting debugger...
0017:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb20 0x95fb18
0017:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb64 0x95fb5c
0017:fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x95fb24 0x95fb1c
007a:fixme:ole:NdrCorrelationFree (0x6daf994): stub
007a:err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be
0009:err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be
0009:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
0012:fixme:msvcrt:__clean_type_info_names_internal (0x64083a50) stub
004c:fixme:ntdll:EtwUnregisterTraceGuids deadbeef: stub
004c:fixme:ntdll:EtwUnregisterTraceGuids deadbeef: stub
004c:fixme:advapi:RegisterEventSourceW ((null),L"Office Software Protection Platform Service"): stub
004c:fixme:advapi:ReportEventW (0xcafe4242,0x0000,0x0000,0x40000387,(nil),0x0000,0x00000000,0x87fd14,(nil)): stub
004c:fixme:advapi:DeregisterEventSource (0xcafe4242) stub[/TD]
[/TR]
[/TABLE]
```

(SORRY, even this redacted version WAS VERY LONG)

THANKS!

---

### Post by uRock on 2019-11-04
Don't forget to stop by and let these guys know if their information helped you. [https://ubuntuforums.org/showthread.php?t=2430541](https://ubuntuforums.org/showthread.php?t=2430541)

---

### Post by jon-carmicheal on 2019-11-06
It looks like the root cause of the failure is: "libudev.so.0: cannot open shared object file: No such file or directory"

You  should be able to follow this guide to install that missing file:  [https://linuxconfig.org/how-to-fix-cannot-open-shared-object-file-libudev-so-0-error-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-fix-cannot-open-shared-object-file-libudev-so-0-error-on-ubuntu-18-04-bionic-beaver-linux)

The specific steps for your issue should be as follows (enter these commands in the terminal):

```
sudo apt install gdebi-core

wget http://mirrors.kernel.org/ubuntu/pool/main/u/udev/libudev0_175-0ubuntu9_amd64.deb
sudo gdebi libudev0_175-0ubuntu9_amd64.deb
```

---

### Post by alanralph on 2019-11-07
Thanks for the help, I will try this as soon as I get a chance!

---

### Post by mastablasta on 2019-11-07
> **alanralph said:**
> 
In the closed thread linked above, there was one answer mentioning "32 bit wine prefix". How is this installed, and did it need to be installed prior to MS Office via PlayOnLinux? 

When you create the virtual drive you should have the option to create a 32bit one: 
[https://askubuntu.com/questions/1021163/how-use-a-preset-wine-prefix-during-the-installation-on-pol](https://askubuntu.com/questions/1021163/how-use-a-preset-wine-prefix-during-the-installation-on-pol)

this creates a 32 bit prefix. it should offer better compatibility. 2010 works well in wine/playonlinux. however in today's standards it is quite old (10 years). and it doesn't have good compatibility with new format anyway. so i stopped using it on linux especially with alternatives available.


For "uninstall" - just delete the prefix.



other alternatives to try (random order): WPS office, Libre Office, Apache Open office, Caligra suite, Softmaker/Free Office, Only office, Zoho (?!). ++ Office365 works in browser on any OS.

---

### Post by jon-carmicheal on 2019-11-07
I agree with mastablasta that there are several Linux-friendly alternatives that are worth trying.  I use Libre Office almost daily as a MS Office alternative.

---

### Post by alanralph on 2019-11-07
Thank you both for the help... @jon-carmichael, the 'libudev' install worked! Office 2010 is working now!

I have LibreOffice as it came with Lubuntu. On my primary Windows machine, I use Office 2010, and am just used to using it. 

FWIW, I created a Lubuntu machine to use for my traveling. It is a light, small, travel-friendly machine, and the last big Windows update is too large for its 32gb eMMC HD, so I dumped Windows for a lite Ubuntu. I will need daily use of my spreadsheet, so the plan was to use Excel as I normally do at home, but also try LibreOffice as a backup to make sure it works well too. If all is well, then I might just remove the Office 2010 at some point!

@mastablasta re: the uninstall I was referring to, it was the uninstall of Office 2010, not the "32bit prefix (which I don't actual know if I have installed). I may not have worded that properly....

---

### Post by mastablasta on 2019-11-08
> **alanralph said:**
> 
@mastablasta re: the uninstall I was referring to, it was the uninstall of Office 2010, not the "32bit prefix (which I don't actual know if I have installed). I may not have worded that properly....

just delete the prefix and create new one. the install is not really a system install but made within the prefix so you are not actually installing to the OS you are just installing to a pretend OS which is wine. to simply it - wine tricks the programs into thinking they are installing and running on windows OS. and this is all done within what the call prefix. so removing that prefix would remove the app as well as the "fake pretend OS". 
then you just create new one and reinstall.


it is possible to install or reinstall to the same prefix, but as you found out the uninstall is sometimes not working.

good to know you got it working. also libre office now has a ribbon as well, but IMO it is not implemented as good as in MS office. needs to be refined quite a bit more. also they still do not have live changes like in office when you select different type of letters etc. (the theme) - the changes are immediately seen live in text for a preview.

still for the most part libre office is a descent replacement. but needs more work on the UI.

---

