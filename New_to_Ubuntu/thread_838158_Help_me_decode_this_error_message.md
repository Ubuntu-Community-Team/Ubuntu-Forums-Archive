---
title: "Help me decode this error message"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-23
I am asking this because the folks in this forum helped me create a script I thought would by-pass this problem but it has only made it slightly more manageable.  I used to get a complete system crash when I attempted to run World of Warcraft in Wine without a fresh Config.wtf file in the WTF folder.  The script we created automated the process of deleting the Config.wtf and moving a fresh backed up copy over to the WTF folder.

The problem still occurs, but now at least I can get something from the terminal window.

Please let me know if any of you can make sense of this and figure out what the issue is:
> 
fixme:shdocvw:PersistStreamInit_Load (0x131fb8)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x131fb8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x131fb8)->(0)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8dda08, overlapped 0x7d8dd9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x132054)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x132054)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x132cd8)->(L"" L"" 0 0x32be40)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x132054)
fixme:shdocvw:ClientSite_GetContainer (0x132054)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x132054)->(0xb7e7f6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 26 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x132054)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x131fb8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14bc08)->((nil))
fixme:shdocvw:OleObject_Close (0x131fb8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
jason@timmy:~/Games$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
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
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x136728): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  611
  Current serial number in output stream:  611
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7e969767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x7e96981e]
#2 /usr/lib/libX11.so.6 [0x7ea52518]
#3 /usr/lib/libGL.so.1 [0x7e9e0a75]
#4 [0xb7d12b28]
#5 [0xb7d12b28]
#6 [0xb7d12b28]
#7 [0xb7d12b28]
#8 [0xb7d12b28]
#9 [0xb7d12b28]
#10 [0xb7d12b28]
#11 [0xb7d12b28]


Thank you so much to whomever can make anything out of that and may be able to help me fix it.

---

### Post by adam_kimber on 2008-06-23
> **jasontu said:**
> X Error of failed request: GLXBadDrawable
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 5 (X_GLXMakeCurrent).

Well I am no Wine expert but I know GLX is an extension that needs to be loaded in the starting of X to get things like games to work. Here is my checklist for eliminating some easily overlooked problems (for nvidia only)

1) make sure 3D acceleration is enabled. Do this by using the "nvidia" driver, rather than the "nv" driver, in the xorg.conf file, this can be done in various ways these days, you can use the restricted drivers dialog box to do all this for you. Neat! Just check use the nVidia driver. (probably a similar method for ATI)
2) Make sure the glx module is loaded in the xorg.conf file 
3) Run glxgears, if it works, then try gltron (nice game btw). If they both work more complex things like WOW through wine can be attempted

Some people have suggested that running the program in a virtual desktop in wine can fix the above error. 

Lastly upgrade wine! Things are being fixed all the time. 

Hope this is not too generic. Shout if you need more help!

---

### Post by jasontu on 2008-06-23
Wow... I barely understand, but I'll give it a shot.  lol.  

I have a couple of questions:


1.  I am running EnvyNG for the nVidia driver.  If I check the restricted drivers box will that mess things up at all?  Will have to uninstall my current driver or anything?

2.  How would I make sure that I am running the glx module in my xorg.conf?

3.  What is glxgears?

4.  Whenever Ubuntu tells me it has upgrades I upgrade.  I'm not sure if there is anymore I'm supposed to be doing to keep things up-to-date.

Lastly, thank you so much for your help.

---

### Post by adam_kimber on 2008-06-23
Apologies if I was either / vague / too technical. Did not know how clued up you were! :P 

1) Don't worry Envy should have everything running.... so lets not mess things up by running restricted drivers over the top of Envy. 

2) Run the following command in a terminal ```
less /etc/X11/xorg.conf | grep glx
``` All that does is display the xorg.conf file and then find a particular line (grep is useful for that sort of thing). You should get a line like the following ```
Load           "glx"
``` If not I will tell you how to put it in.

3) glxgears is a little program that is used to test if direct rending, glx and other things are working properly. Its not foolproof by any means. However if it crashes then there is something awry. Just open a termainl and type ```
glxgears -info
``` Then paste me the top lines from the output. I don't need the extensions bit :D I have 

```
adam@zia:~$ glxgears -info
GL_RENDERER   = GeForce 8800 GT/PCI/SSE2
GL_VERSION    = 2.1.2 NVIDIA 169.12
GL_VENDOR     = NVIDIA Corporation

```

4) Fair enough. 

Not a problem, we are here to help. 

Just out of interest, can you run the following in a terminal too and dump the results on here. 

```
glxinfo | grep NVIDIA
```
```
glxinfo | grep direct
```

I have 

```
[adam@zia:~$ glxinfo | grep NVIDIA
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.1.2 NVIDIA 169.12

```

```
adam@zia:~$ glxinfo | grep direct
direct rendering: Yes

```

Makes sure everything matches and is working.

---

### Post by jasontu on 2008-06-23
Output from
glxgears -info
> 
GL_RENDERER   = GeForce 6600 GT/PCI/SSE2
GL_VERSION    = 2.1.2 NVIDIA 173.14.05
GL_VENDOR     = NVIDIA Corporation

---

### Post by jasontu on 2008-06-23
Output from glxinfo | grep NVIDIA:
> 
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.1.2 NVIDIA 173.14.05

---

### Post by jasontu on 2008-06-23
Output from: glxinfo | grep direct
direct rendering: Yes

---

### Post by adam_kimber on 2008-06-24
Hmmmm. All seems to be fine there..... That's good news. Eliminated all of that. As wine and the nvidia drivers are very complex I am not sure what might be the problem. However.

Are you running 64bit (uname -a) will show you if you are unsure. 

Right now either try - we are going to swap to the restricted drivers (unfortunately not so new but might be more stable)

1) Different nvidia driver version 

- Run EnvyNG, select remove driver. It will do some stuff. Click no to reboot. Ubuntu --> System --> Hardware Drivers

Select the check box. Apply. OK. Now Restart. If that does not work.


2) Different wine version

Run in a terminal ```
sudo aptitude remove wine
```

Then goto here. [Wine Debs]("http://wine.budgetdedicated.com/archive/index.html") and select the one from the version of Ubuntu you are using, either 64bit or 386. Download and install by double clicking. You might get a warning about a newer version available. We will ignore that for now. 

Try your program again.

---

### Post by jasontu on 2008-06-24
Using the "Restricted Drivers" has never worked for me.  After using it, I will not direct rendering.

What will work, and I have determined that it is not a placebo effect, is deleting the Config.wtf file in the WoW/WTF folder and clicking and dragging a backed up copy of the file (I have mine saved in WoW/Unused WTF/Baseline Edit/Config.wtf) into the WoW/WTF.  This MUST be in the Gnome GUI.  This ALWAYS fixes the issue until the next time I restart the machine.  Doing the same thing via creating an executable to do the same thing via terminal:

> #before wine executes:
rm -f ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf
mv -f ~/.wine/drive_c/Program\ Files/WoW/Unused\ WTF/Baseline\ Edit/Config.wtf ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf
cp -f ~/.wine/drive_c/Program\ Files/WoW/WTF/Config.wtf ~/.wine/drive_c/Program\ Files/WoW/Unused\ WTF/Baseline\ Edit/Config.wtf

does not work.

Thanks for all your help!  It's bizarre.  Like you said, Adam, the relationship is complex, and maybe the issue will be corrected in a future update of Wine.  This never happened (that I recall) with my ATi card, but this issue is preferable to my inability to use the mini-map indoors in the game using the ATi drivers.

I think I will just post the details the AppDB in WineHQ so the Wine people will know about it.

---

### Post by adam_kimber on 2008-06-24
> **jasontu said:**
> Using the "Restricted Drivers" has never worked for me.  After using it, I will not direct rendering.

Hmmm. envy never used to work for me. Tried it this morning and it works fine. :confused: 

How about just copying the file over without removing first? i.e. overwriting using the terminal? That might work. Also try dropping the -f option. 

Other than that posting a AppDB reponse might help. 

OOOH Wine 1.0 is out woooo!

---

### Post by jasontu on 2008-06-24
Copying over without removing the file does not work.  I'll try it dropping the -f option.  (I have no idea what the -f option really does.)  I have no idea why this little ritual works in the GUI and how it differs from what I have encoded via this little terminal script.

---

### Post by adam_kimber on 2008-06-27
Hmmm maybe its a permissions thing. Have a look at the permissions on the file before and after running the program and befoer and after doing you gui routine. That might reveal something?!?

---

### Post by jasontu on 2008-06-30
I'll give it a shot... I thought about that, but I have no clue what would change between then and whenever I restart.

---

