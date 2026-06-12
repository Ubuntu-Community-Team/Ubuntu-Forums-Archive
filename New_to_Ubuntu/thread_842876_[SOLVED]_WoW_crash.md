---
title: "[SOLVED] WoW crash"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by trigsenior on 2008-06-27
I just installed WoW using wine on ubuntu 8.04 it is the eu trial version it starts fine , there is the little intro still fine , but soon as the intro finishes it crashes and messes up the seize of the desktop. I tryed running with out compriz , same effect .

If anyone has had this problem , or has a suggestion on how to fix please say.

many , many thanxs as usual 

:)

update: i managed to make it work using this 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

i used this commands

add to the wtf.config

SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"

should have looked earlyer many thanxs to Xerp and flytripper for their help =)

---

### Post by Xerp on 2008-06-27
Try running it from the command line, that way you get a bit of info on why it crashed... most of the time :)

---

### Post by trigsenior on 2008-06-27
here ran in terminal , does not mean much to me though 

env WINEPREFIX="/home/emilien/.wine" wine "C:\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x132d30)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x132d30)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x132d30)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x133370): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133350): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8bea08, overlapped 0x7d8be9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x132dcc)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x132dcc)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x133258)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x132dcc)
fixme:shdocvw:ClientSite_GetContainer (0x132dcc)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x132dcc)->(0xb7e466d5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 26 2 0x32e780 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132dcc)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x132d30)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14c060)->((nil))
fixme:shdocvw:OleObject_Close (0x132d30)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
emilien@emilien-desktop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x137e78) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x138630) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

---

### Post by Xerp on 2008-06-27
Hm. Which graphics card are you using and are you using a restricted driver for it?

---

### Post by trigsenior on 2008-06-27
hi again , i think this is my grachics card 

 lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

i dont think im using a restricted driver

---

### Post by Xerp on 2008-06-27
Yes, this one is:

Intel Corporation 82945G/GZ Integrated Graphics Controller

This should be able to run WoW (just!)

I have a feeling you're running the "Vesa" driver though - can look in /etc/X11/xorg.conf and see if you have something like this:


Section "Device"
Identifier "Intel Corporation 82945G/GZ Integrated Graphics Controller"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

---

### Post by flytripper on 2008-06-27
looks like you are using d3d and it doesnt like it

[COLOR="Red"]Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups[/COLOR]

try adding :    SET gxApi "opengl"   to your config.wtf file in /path to wow/config/config.wtf file



you may just be unlucky as you have integrated graphics and that is a bad thing like verrry bad...

hope this helps....   nuckchorris gnoom lock

---

### Post by trigsenior on 2008-06-27
ok mixed results it worked once then  i reboted and it didnt work this 
was arfter adding : SET gxApi "opengl" to your config.wtf file

env WINEPREFIX="/home/emilien/.wine" wine "C:\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x132d18)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x132d18)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x132d18)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x133370): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133350): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1336f0): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8b9a08, overlapped 0x7d8b99ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x132db4)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x132db4)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x133258)->(L"" L"" 0 0x32be40)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x132db4)
fixme:shdocvw:ClientSite_GetContainer (0x132db4)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x132db4)->(0xb7ec36d5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 26 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x132d18)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14c060)->((nil))
fixme:shdocvw:OleObject_Close (0x132d18)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
emilien@emilien-desktop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x136b00): stub
fixme:imm:ImmAssociateContextEx (0x3004c, (nil), 16): stub

i looked on /etc/X11/xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
EndSection

this what it said

also the wtf.config file now says

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET gxApi "opengl"
SET locale "enGB"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"

---

### Post by trigsenior on 2008-06-27
anyone any ideas ?

---

### Post by flytripper on 2008-06-28
you are going to need a graphics card methinks

---

