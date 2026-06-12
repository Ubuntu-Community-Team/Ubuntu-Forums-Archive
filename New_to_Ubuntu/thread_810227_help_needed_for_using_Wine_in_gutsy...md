---
title: "help needed for using Wine in gutsy.."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-05-28
i am using ubuntu gutsy. when i start some windows application using wine my system got hanged and none of the thing is working.., even my restart button is not not working..

I cannot able to restart my system , my system got totally freezed is use wine. my mouse point are not moving. 

I need to plug out my power then again switch on  to work again..

please help me out what is the problem.. and how i can fix this?

---

### Post by iaculallad on 2008-05-28
> **sxytrillian said:**
> i am using ubuntu gutsy. when i start some windows application using wine my system got hanged and none of the thing is working.., even my restart button is not not working..

I cannot able to restart my system , my system got totally freezed is use wine. my mouse point are not moving. 

I need to plug out my power then again switch on  to work again..

please help me out what is the problem.. and how i can fix this?


What windoze application are you trying to execute via WinE?

---

### Post by sxytrillian on 2008-05-28
winrar and some exe files.. even i cant able to use notepad..

---

### Post by sayakb on 2008-05-28
Why do you even need Winrar and notepad?
Goto Applications->Accessories->Text editor <- Much more efficient than notepad
For Winrar, open a terminal and type:
```
sudo apt-get install rar unrar
```You should be able to open and create RAR archives then.

Plus, which EXE files are you trying?

---

### Post by sxytrillian on 2008-05-28
Sp27213.exe file.

Its is an exe which will make an Usb pen drive bootable for window operating system...

---

### Post by sayakb on 2008-05-28
Why are you installing that on Wine. There is no way this should work with ubuntu. Btw, I don't get your point completely: "makes USB pen drive bootable for Windows", or does it create a bootable USB pendrive that boots to Windows/Command prompt? Anyway, either be the case, none would work with Wine. Here's a list of apps which work with Wine: [http://appdb.winehq.org](http://appdb.winehq.org)

EDIT: Please do read this also: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by iaculallad on 2008-05-28
> **sxytrillian said:**
> Sp27213.exe file.

Its is an exe which will make an Usb pen drive bootable for window operating system...

You could get away with that windoze file, there's actually a Linux utility (syslinux) that could do the same thing for you. Try reading this [link]("http://forum.x86-secret.com/showthread.php?t=6148"). It's rather long but we're here taking the road less traveled :)

---

