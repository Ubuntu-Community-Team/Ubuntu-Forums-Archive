---
title: "ie4linux ie6 not working"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by BillGod on 2008-05-19
Has anyone gotten internet explorer working with wine on Hardy?  I have 3 different PC's and have the same results on all of them.  I am using ie4linux as I have for a long long time.  I have never had any issues before until hardy. When I start it.  It comes up on the screen but if I type in google.com and hit enter or click the go button nothing happens.  then it just hangs.  If I run it from the command line I get this.

 wine .wine/drive_c/Program\ Files/Internet\ Explorer/iexplore.exe 
fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12beac)->((null) 1 0x32e27c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 25 2 0x32e290 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 26 2 0x32e290 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12beac)->(0x32e2cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e390 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e420)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12beac)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 26 2 0x32fc80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 29 2 0x32fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 28 2 0x32fbf8 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12beac)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12beac)->(0xb7e8b725)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 26 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12beac)->((null) 21 2 (nil) (nil))

---

### Post by philinux on 2008-05-19
It works from the shorcut on my desktop, but even though it said it had installed flash it dont work.

---

### Post by nirkir on 2008-05-19
Works great for me, including flash (although I always had problems with flickering while rendering flash content).

---

### Post by philinux on 2008-05-19
Well what do you know. I went to sky news website followed the link to install flash plugin, again!.

This time it worked. I upgraded wine to the RC1 today so it looks like its fixed.

---

