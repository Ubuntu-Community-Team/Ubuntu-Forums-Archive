---
title: "launching guest operating system"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-09-20
i have installed windows xp in virtualbox in hardy.how do i make virtualbox launch windows xp,from the terminal?

---

### Post by stonecoldjha on 2008-09-20
i want to know the command so as to create a launcher to launch xp directly,rather than opening virtualbox first and then double-clicking xp.

---

### Post by howefield on 2008-09-20
In terminal type

```
VBoxManage startvm WindowsXP
```

WindowsXP is the name of my xp virtual machine, subsitute with the name of yours.

---

### Post by stonecoldjha on 2008-09-20
it didn't do the job,the output was:

sonu@sonu-desktop:~$ VBoxManage startvm windows xp
VirtualBox Command Line Management Interface Version 2.0.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling virtualBox->FindMachine(Bstr(argv[0]), machine.asOutParam()) at line 5620!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Could not find a registered machine named 'windows'
[!] Component   = VirtualBox, Interface: IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
[!] Callee      = IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
sonu@sonu-desktop:~$

---

### Post by Mornedhel on 2008-09-20
Try putting 'windows xp' between quotes.

Otherwise it's passed to VBoxManager as two separate arguments, one with "windows", the other with "xp".

Disclaimer : I am not familiar with VBoxManager, but this is pretty much standard behavior.

---

### Post by howefield on 2008-09-20
Hmmm, works perfectly for me. You sure you typed correctly, it is case sensitive.

You could sub the name the vm with its UUID if you can get it, I'm not sure how you do that.

---

### Post by howefield on 2008-09-20
> **Mornedhel said:**
> Try putting 'windows xp' between quotes.

+1

yep, I'd guess that is it, never thought to mention that.

---

### Post by stonecoldjha on 2008-09-20
ok its working now,but its only launching the virtualbox.i want xp to be launched straightaway.

---

### Post by howefield on 2008-09-20
sorry not sure what to suggest now, the command works on my box without launching the Virtualbox window itself, it goes straight into loading the vm.

One last long shot, is it the name of the .vdi you are using or the name of the vm to type the command ?

---

### Post by stonecoldjha on 2008-09-23
excuse me ,but i did not quite get that.

---

