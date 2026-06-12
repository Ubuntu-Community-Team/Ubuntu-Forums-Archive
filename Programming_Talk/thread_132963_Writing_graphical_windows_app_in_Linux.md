---
title: "Writing graphical windows app in Linux?"
date: 2006-02-19
forum: Programming Talk
---

### Post by Kimm on 2006-02-19
Hi,

I have a plan on making a CD containing software for Linux, FreeBSD, Mac OS X and windows. As windows has an autorun feature I think it would be bad not not use it. However I have a problem, I want to write the application in Linux preferably without using any windows APIs (one reason being: I dont know them...), can this be done?

I would like to use GTK, but as most windows computers dont have this installed I think it would be difficult to just write it as a normal GTK app and put it on the CD.

Can anyone come with suggestions?

---

### Post by dee.dw on 2006-02-19
If you want to have a GUI that is platform-independent I would recommend Java. Most computers habe Java Runtime installed and would work with autostart I think.

Greetings, Dee

---

### Post by Kimm on 2006-02-19
The idea crossed my mind, but I dont know Java. I would like to write it in something like C or C++.

I do know wxWidgets, but most computers dont have that eighter.

---

### Post by LordHunter317 on 2006-02-19
installing the GTK+ runtime on Windows is trivial.

---

### Post by Kimm on 2006-02-19
Perhaps, but then the CD would have to promt them to install GTK before the autorun program starts, something that may seem irritating to some.

---

### Post by dee.dw on 2006-02-19
You could programm with wxWidgets and link the code dynamically. Then you must create some dlls from wxWidgets and put them on the disc too. This should help...

Greetings, Dee

---

### Post by Kimm on 2006-02-19
That could work, thanks dee.dw

I havn't done this before... how would I go about doing it?

---

### Post by dee.dw on 2006-02-19
Hm... if I think about it: Dynamically linking would be no advantage because under Linux you must use .so and under Windows .dll... So you can link them statically and get some two executables for Linux and Windows separatly.

This means write your code in wxWidgets as normal and compile them for Windows and then for Linux and burn this on CD. (Hm, but I don't know about architectures and kernel versions. So I don't know if one executable for all Linux-Distris is enough.)

@all: If I talk nonsense please correct me! I have never linked something dynamically. :)

Greetings, Dee

---

### Post by LordHunter317 on 2006-02-19
[QUOTE=dee.dw]Hm... if I think about it: Dynamically linking would be no advantage because under Linux you must use .so and under Windows .dll... So you can link them statically and get some two executables for Linux and Windows separatly.[/quote]Except that most code won't work correctly if linked statically.

Link them dynmically and ship the libraries.  Not hard.  VMware does this, for example.

---

### Post by Kimm on 2006-02-19
The app was acctually not intended to run in Linux, only windows, for the simple reason that Linux users are usualy more experianced then windows users and since Linux has no CD autorun feature.

---

### Post by dee.dw on 2006-02-19
@LordHunter: What do you mean with "won't work correctly" exactly?

@Kimm: Hm, I thought from your first post that it shoudl be platform independet what you program. But as I see now you only meant the Win autostart. So I think there is no reason not using wxWidgets maybe with Bloodshed Dev-C++ under Windows!

Greetings, Dee

---

### Post by LordHunter317 on 2006-02-19
[QUOTE=dee.dw]@LordHunter: What do you mean with "won't work correctly" exactly?[/quote]Anything that depends on NSS switch, or PAM, would break outright.

Qt applications can't be safely statically linked in most situations (you have to code for it).  KDE can't be at all.

---

### Post by Kimm on 2006-02-19
> 
Hm, I thought from your first post that it shoudl be platform independet what you program. But as I see now you only meant the Win autostart. So I think there is no reason not using wxWidgets maybe with Bloodshed Dev-C++ under Windows!


That may work. Perhaps bloodshed could work in Wine...

---

### Post by dee.dw on 2006-02-19
Why use Wine? ;) A similar (or identical) IDE for C++ you can get at [http://www.parinyasoft.com/](http://www.parinyasoft.com/) called MinGW Developer Studio. Unfortunately I found this thing really instable and it crashed everytime I tried to compile something. Now I use [Code::Blocks](http://www.codeblocks.org/) which works really fine with wxWindows. (And Code::Blocks is for Windows too, so you can test it there.)

[quote=LordHunter317]Qt applications can't be safely statically linked in most situations (you have to code for it). KDE can't be at all.[/quote]Hm, may be... In my case everything works fine! :) Maybe I just had luck... But I think a for a simply frame with some buttons you do not need to link dynamically.

Greetings, Dee

---

### Post by LordHunter317 on 2006-02-19
[QUOTE=dee.dw]Hm, may be... In my case everything works fine! :) Maybe I just had luck... But I think a for a simply frame with some buttons you do not need to link dynamically.[/quote]You do know that unless you're asking for static linking, you're not getting it, right?

---

### Post by dee.dw on 2006-02-20
[QUOTE=LordHunter317]You do know that unless you're asking for static linking, you're not getting it, right?[/QUOTE]Hm, unfortunately I don't understand this sentence... So you're right: I don't get it! :(

But anyway if the answer is not related to the topic of Kimm it's not that important that I understand it. :)

Greetings, Dee

---

### Post by LordHunter317 on 2006-02-20
What I'm saying is that unless you explictly link -static, you don't ever static link on Linux.

---

### Post by dee.dw on 2006-02-20
Ah, thank you. Now I got it. :) I didn't know that linux link everything dynamically... Do not program that often there!

Thanks for explanation,
Dee

---

