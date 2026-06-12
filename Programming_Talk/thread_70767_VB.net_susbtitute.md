---
title: "VB.net susbtitute?"
date: 2005-10-01
forum: Programming Talk
---

### Post by bernardfrancois on 2005-10-01
Hi,

I need to program with VB.net (in Visual Studio) for school. Does anyone know a subsitute for that which I can use under Ubuntu? The syntax of the language should be the same. It should be possible, just some language on top of Xlib with the same syntax as VB.net... I don't feel like using window$...

Thanks in advance for anyone who can help me.

Bernard

---

### Post by Drakx on 2005-10-01
Yes

[http://www.realbasic.com/](http://www.realbasic.com/)

If you by the pro version you will have crossplatform ability :) is mac, lin and win

---

### Post by GentleHatemonger on 2005-10-01
Realbasic will not help you, as that more closely relates to VB 6 and not .NET

For Mono's implementation of VB.NET, check out [http://www.go-mono.com/mbas.html](http://www.go-mono.com/mbas.html)

It doesn't seem like it's ready quite yet, but it will be soon enough.

Sadly, you will have to reboot into Windows (or run a virtual machine like VMWare) in order to code in VB.NET

---

### Post by mostwanted on 2005-10-01
This link is a bit newer:

[http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)

Update your bookmarks gentlehatemonger ;)

---

### Post by bernardfrancois on 2005-10-03
Looks nice, but I can't find a drag-and-drop mode where you can drag buttons, labels, text input fields, etc to a window... is that available in mono?

---

### Post by bernardfrancois on 2005-11-16
I already noticed that those tools aren't implemented yet.

For now I'm using windows for those school tasks, but not with Visual Studio! I found a good free open source alternative (which uses the free .net runtime);sharp develop: [http://www.icsharpcode.net/OpenSource/SD/](http://www.icsharpcode.net/OpenSource/SD/)

It's a nice alternative while waiting for a linux version...

---

### Post by JuanC on 2005-11-16
These tools where available when Windows.Forms support for mono were complete.

> 
It's a nice alternative while waiting for a linux version...


Try [Monodevelop](http://www.monodevelop.org)

---

### Post by bernardfrancois on 2005-11-19
I don't have much time to install from source now. I tried, but I got some packages missing which are not in my repositories. I'll have to compile some more stuff myself.

But are you sure there's a form designer impelemted now? I want to drag controls graphically to the window, and double-click controls to start write code for an action on a control... Can you post a screenshot please? I don't see  such screenshots on the monodevelop website...

---

