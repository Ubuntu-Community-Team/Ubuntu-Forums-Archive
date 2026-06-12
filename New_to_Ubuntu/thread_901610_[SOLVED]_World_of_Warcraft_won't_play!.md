---
title: "[SOLVED] World of Warcraft won't play!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by pelle@xburk on 2008-08-26
I am running Ubuntu Hardy Heron 8.04 AMD64 with an AMD Athlon X2 64-bit dual core processor with an nVidia GeForce 7900 graphics card.

I installed World of Warcraft using Wine-doors, but when I run the launcher from the menu the graphics load very slow.  When I then press play to open the actual WoW.exe application, an error pops up.  Here's the terminal output when I tried to run the WoW.exe file directly, skipping the launcher:

```
pelle@XION:~$ wine /home/pelle/.wine/drive_c/Program\ Files/World\ of\ Warcraft\ Trial/WoW.exe
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:advapi:SetSecurityInfo stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
failed to open C:/Program Files/World of Warcraft Trial/Data/----
failed to open C:/Program Files/World of Warcraft Trial/Data/----
archive Data\Start.MPQ opened
archive Data\patch.MPQ opened
archive Data\interface.MPQ opened
archive Data\misc.MPQ opened
archive Data\model.MPQ opened
archive Data\texture.MPQ opened
archive Data\terrain.MPQ opened
archive Data\wmo.MPQ opened
archive Data\sound.MPQ opened
archive Data\fonts.MPQ opened
archive Data\dbc.MPQ opened
archive Data\speech.MPQ opened
fixme:powrprof:DllMain (0x7d0f0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d0f0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed9c,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

Also, these windows pop up:

[IMG]http://i38.tinypic.com/x3bya9.jpg[/IMG]

[IMG]http://i37.tinypic.com/2rp61d3.jpg[/IMG]

I also downloaded TryWoW.exe from Blizzards Website to try to install it without Wine-doors, just with wine, but it just launches the launcher window, and when I press play, I get the two windows again, but this error:

```
pelle@XION:~/Desktop$ wine TryWoW.exe
pelle@XION:~/Desktop$ fixme:shdocvw:PersistStreamInit_Load (0x131f10)->(0x33e524)
fixme:shdocvw:OleControl_FreezeEvents (0x131f10)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x131f10)->(0)
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d9faa08, overlapped 0x7d9fa9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x131fac)->((null) 1 0x33beec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 25 2 0x33bf00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 26 2 0x33bf00 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x131fac)->(0x33bf3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33c000 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x132e88)->(L"" L"" 0 0x33c038)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 29 2 0x33ec08 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x131fac)
fixme:shdocvw:ClientSite_GetContainer (0x131fac)->(0x33ea48)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x131fac)->(0xf7df6755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 25 2 0x33e97c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 26 2 0x33e97c (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131fac)->((null) 28 2 0x33eba8 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x131f10)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14bca0)->((nil))
fixme:shdocvw:OleObject_Close (0x131f10)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:advapi:SetSecurityInfo stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
```

I suspect that it can't connect to the internet or something.  It could also be the graphics drivers or something.  Because when I run:

```
glxinfo | grep rendering
```

I get the output:

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

I don't remember where I read it, but supposedly that no is supposed to be a yes...

Also, when I run **LIBGL_DEBUG=verbose** as it tells me to, there is no output.

Does anybody know how to fix this?  Why does 64 bit always have to be so complicated?

---

### Post by neurostu on 2008-08-27
Try posting in the wine area of the forums... they might be able to help you.

---

