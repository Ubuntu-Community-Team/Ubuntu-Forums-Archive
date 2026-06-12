---
title: "How to create a custom keyboard shortcut to then run a wGet HTTP command?"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by cwkid on 2013-08-09
Hello

I am looking for a way in Ubuntu Minimal (No desktop UI) to be able to create a custom keyboard shortcut like Ctrl+Alt+1 and then have it run a wGet HTTP command. 

To do this in Windows I would create a .cmd file that contains a wGET HTTP command like:

```
[COLOR=#000000][FONT=dejavu sans mono]wget --delete-after "http://192.168.1.100:3480/data_request?id=lu_action&output_format=xml&DeviceNum=3&serviceId=urn:upnp-org:serviceId:SwitchPower1&action=SetTarget&newTargetValue=1"[/FONT][/COLOR]
```

For example this HTTP command would tell my Home Automation system to do something, like turn on a light. 

In Windows I would then use AutoHotKey running in the system tray and a AutoHotKey script like:

```
[SIZE=3][COLOR=#000000][FONT=dejavu sans mono]^!1::[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]IfWinExist Untitled - Left Lamp On[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]WinActivate[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]else[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]Run C:\Lights\Lounge-On-Left.cmd[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]return[/FONT][/COLOR][/SIZE]
```

^!1 = Ctrl+Alt+1 and it then runs the command file C:\Lights\Lounge-On-Left.cmd. 

So when I pressed Ctrl+Alt+1 on the keyboard the Light would come on. I can then further program my Universal remote control, to send these custom keyboard shortcuts to the HTPC. So I can control my lights via my remote control. 

I have migrated away from Windows Media Center to Linux Ubuntu 12.10 minimal and XBMC. I am a Linux newbie and am looking for help on how I might do this under Linux?

Any help greatly appreciated

Thanks

---

### Post by d2btoo on 2013-08-09
Hello,
A quick search suggests 3 alternatives for AutoHotKey in Linux:
[http://alternativeto.net/software/AutoHotKey/?platform=linux](http://alternativeto.net/software/AutoHotKey/?platform=linux)

However I've never used them and also you are running "Ubuntu Minimal (No desktop UI)", so I've no idea if they are useful to you or not!  :-k

---

### Post by cwkid on 2013-08-09
Hi thanks for the reply! 
Yes I have done some searching and seen there are some Linux alternatives to Autohotkey but as I am running Ubuntu minimal and with my lack of general Linux know how I was really unsure where to begin with something like this.

Thanks

---

