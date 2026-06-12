---
title: "Install program to Windows 7 from within Ubuntu"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by sixfearstheseven on 2011-11-30
Hello everybody. I'm not new to Ubuntu but I haven't used it in some time and was never an expert by any means. As you can see from the title of this thread, what I'm asking is pretty straight-forward: using Wine, is it possible to run an exe installer and have it install on my Windows 7 partition so that when I boot into Windows, I can run the program normally?

When I run the exe with Wine, it runs fine and installs, but this particular installer doesn't ask what directory I want to install to, so I have no idea where it's installing. I tried putting the exe in my Windows Program Files directory and running it from there, but no new folders show up. Where on my Ubuntu partition are these files going, and how can I make them install to Windows if the installer doesn't ask what directory I want to install to?

Thanks in advance, and I apologize if this is a stupid question, or if the answer is obvious: it can't be done.

---

### Post by Jacobonbuntu on 2011-11-30
> **sixfearstheseven said:**
> Hello everybody. I'm not new to Ubuntu but I haven't used it in some time and was never an expert by any means. As you can see from the title of this thread, what I'm asking is pretty straight-forward: using Wine, is it possible to run an exe installer and have it install on my Windows 7 partition so that when I boot into Windows, I can run the program normally?

When I run the exe with Wine, it runs fine and installs, but this particular installer doesn't ask what directory I want to install to, so I have no idea where it's installing. I tried putting the exe in my Windows Program Files directory and running it from there, but no new folders show up. Where on my Ubuntu partition are these files going, and how can I make them install to Windows if the installer doesn't ask what directory I want to install to?

Thanks in advance, and I apologize if this is a stupid question, or if the answer is obvious: it can't be done.

No question is stupid I think :)
but Wine installs in the /home/yourname/.wine/drive_c/Program files -directory (invisible until you press ctrl+h), not on your Windows partition! to do that, you will have to boot up in Windows :) (I guess you have dual boot)

---

### Post by Mark Phelps on 2011-11-30
> **sixfearstheseven said:**
> ...using Wine, is it possible to run an exe installer and have it install on my Windows 7 partition so that when I boot into Windows, I can run the program normally.

Quick answer ... NO.

---

### Post by BC59 on 2011-11-30
Wine has two ways of working.

First install a program and run it.

Second to run it directly if the program is simple.

When it's installing a program, is using to install it a "virtual" Windows c:/Program Files drive in the ~/home/.wine folder. To run it needs some basic windows files and libraries, installed on the "virtual" c:/Windows of the same .wine folder.

So the Windows part of your HDD, has nothing to do with this operation.

---

### Post by farrinux on 2011-11-30
I do not believe it is possible to install a windows program into windows from ubuntu, the biggest reason is that ubuntu would not be able to write to the windows registry or what ever win 7 uses now.

---

### Post by sixfearstheseven on 2011-11-30
That all makes sense. Thanks to all of you for taking the time to answer anyway.

---

