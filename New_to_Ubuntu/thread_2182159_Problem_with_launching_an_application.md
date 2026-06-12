---
title: "Problem with launching an application"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by AlisN1dlan on 2013-10-20
I need this app for school and followed the instructions here: 

[h=1]Installing FirstClass - Graphical Style[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Download [the Debian package]("http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb") from FirstClass' website. Then double-click it.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]There should be a launcher for it in your applications menu, but you won't have a direct command to launch the application unless you specify the full path to the executable: /opt/firstclass/fcc

Ihave an icon now But it won't launch and I don't know how to "specify the full path etc. etc." (I presume that's the problem?)

Thanks
Carol[/FONT][/COLOR]

---

### Post by howefield on 2013-10-20
Try launching from a terminal, either by using fcc or /opt/firstclass/fcc

This might give you a clue what the problem is.

---

### Post by AlisN1dlan on 2013-10-20
no - neither of those commands work. (not found)

---

### Post by howefield on 2013-10-20
I installed into a virtual machine, seems fine.

What version of Ubuntu are you using ?

---

### Post by AlisN1dlan on 2013-10-20
Churbuntu - 12.04. I'm a real newbie, but I gather that just because it's an Ubuntu app doesn't mean it will run well on all versions or flavors or whatever they're called? For example, I installed Okular and although it runs, none of the features I installed it for work and it's missing all the help files because I guess it's supposed to be for KDCE? Anyway. I can make do with another PDF reader, but I really need this first class thing to work. Not sure I have the expertise to start messing around with virtual environments :(

---

### Post by Jonathan Precise on 2013-10-20
> **AlisN1dlan said:**
> Chrubuntu - 12.04

Looks like that's ARM. AFAIK, first class doesn't support ARM :( (at least the deb is not for ARM)

---

### Post by AlisN1dlan on 2013-10-20
Well if Churbuntu 12.04 is for an ARM processor, it's running fine on my intel. But maybe that's the problem with First Class. I can see this is going to be a real steep learning curve - I REALLY don't know what I'm doing here . . .Thanks for the help though :)

---

