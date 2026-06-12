---
title: "wow graphics problem"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by trigsenior on 2008-06-28
hi,

I recently installed wow the eu trial version the install went fine.
However when the game started the grahics were weird the floor was see through . I have done all the necessary tweaks  from here.
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

here are some screen shots

[http://s281.photobucket.com/albums/kk210/trigsenior/?action=view&current=WoWScrnShot_062908_132447.jpg](http://s281.photobucket.com/albums/kk210/trigsenior/?action=view&current=WoWScrnShot_062908_132447.jpg) 


my grahics card -

Intel Corporation 82945G/GZ Integrated Graphics Controller

ubuntu hardy -

wine version-

wine-1.0

and not sure if this will help but this is game log from terminal


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
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8b6a08, overlapped 0x7d8b69ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x132db4)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x132db4)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x133258)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x132db4)
fixme:shdocvw:ClientSite_GetContainer (0x132db4)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x132db4)->(0xb7def6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132db4)->((null) 26 2 0x32e780 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
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
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x136b08): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Unable to read extra attributes: "Cache\Survey.mpq"
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x3004c, (nil), 16): stub

ok i know this is information over kill but this is the wtf.config file in wow ( all the settings)

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
SET particleDensity "1.000000"
SET M2UseShaders "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET realmName "Aszune"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "23"
SET gxCursor "0"
SET uiScale "0.74000000953674"
SET weatherDensity "0"
SET gxRefresh "60"
SET shadowLOD "0"
SET ffxDeath "0"
SET ffxGlow "0"
SET accountName "**********"
SET specular "1"



thanxs for trying to help aswell =)

---

### Post by trigsenior on 2008-06-28
any ideas ?

---

### Post by trigsenior on 2008-06-29
bump =(

---

