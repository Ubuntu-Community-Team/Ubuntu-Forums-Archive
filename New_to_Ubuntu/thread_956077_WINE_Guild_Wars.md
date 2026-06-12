---
title: "WINE Guild Wars"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Arsin on 2008-10-22
So I installed WINE. and continued to install Guild Wars using wine, installed it completely and successfully. Now i try to play the game through wine and it starts up and then nothing happens but the resolution just gets all screwed up like its gonna go full screen and play but it doesn't it just stops. Any suggestions?

---

### Post by Zzl1xndd on 2008-10-22
Guess we should start from the top, what kind of Graphics card are you using? and If its an Nvidia or ATI have you installed the drivers?

---

### Post by Arsin on 2008-10-22
Integrated dell graphics card.

---

### Post by Arsin on 2008-10-23
Need some help still please

---

### Post by jamesrl on 2008-10-23
Have  you read:
[http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)

and
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)
?

---

### Post by Arsin on 2008-10-23
well thank you i didn't know those existed ill update this with my results



RESULTS:
Everything happened the same, but this time i noticed that the mouse changes to the Guild Wars cursor then it goes away too. I also tried running it in a window a window came up after the initial load box then the window went away.

Help is appreciated.

---

### Post by Arsin on 2008-10-23
still need help

---

### Post by HittingSmoke on 2008-10-23
Wish I could be more specific but I'm kind of a noob myself.

Any time I have a crashing issue, or almost any issue I run the program in a terminal so it will post any error output and I can post that in my request for help.

There is a certain command output to launch WINE apps in terminal but I dont remember it off the top of my head. I'm sure someone will post it here for you so you can get more info on what's causing your crashes and lockups

---

### Post by Arsin on 2008-10-24
That was a brilliant idea maybe someone can help now that they might have an idea whats going on.


Heres the output terminal gives me when I try to run Guildwars:

```
aaron@aaron-desktop:~$ wine "C:\Program Files\Guild Wars\Gw.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:winsock:WSACancelAsyncRequest (0xdeb3),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb4),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb5),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb6),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb7),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb8),stub
fixme:winsock:WSACancelAsyncRequest (0xdeb9),stub
aaron@aaron-desktop:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a418) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a418) Dialogs cannot be disabled yet
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x2592230,0x2bb1728): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e40720,0x28a2680): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1ee9e8,0x1e40a88): stub
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a418) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a418) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13a418) Dialogs cannot be disabled yet
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

```

---

### Post by Perfect Storm on 2008-10-24
Please don't bump your thread within 24 hours thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by Arsin on 2008-10-24
my apologize and please don't count this as a bump i just want to let you know im acknowledging your request.

---

### Post by Squish on 2008-10-24
Not sure if this would help you, but I have been getting tremendous results with wine ever since I used winetricks

Im not going to explain what it is, but I will accidentally leave a link here. Hopefully no one will use it~
[http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")

---

### Post by Arsin on 2008-10-24
Hmm definitely not going there to figure this out

---

### Post by Squish on 2008-10-24
Did you try winetricks?

It helped me run Fable, which was a direct x 9 game, pretty much flawlessly

---

### Post by Arsin on 2008-10-24
i can't figure it out i installed it and it didn't do anything

---

### Post by Squish on 2008-10-25
Really?
Did you run it, and selected it to install the directx stuff?

---

### Post by ehamman on 2008-11-24
Hi
I've got pretty much the same problem.
I've installed DirectX through winetricks, but still only get the music playing after the small Guildwars splashscreen disappears.
I got the following output.  Guess the last line should tell me something, but alas nothing that rings a bell.

 wine "/home/ale/NetworkData/Data/Programs/Games/Guild Wars/Gw.exe" -windowed -dx8 -noshaders
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec20,0x00000000), stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d1d0a08, overlapped 0x7d1d09ec): stub
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x339448) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x3394b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33916c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x3394b4,0x00000000), stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x7d6b3b18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x7d6b37d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7d6b3b18,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x144d38) : stub
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet

---

