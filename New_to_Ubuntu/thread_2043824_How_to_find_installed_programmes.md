---
title: "How to find installed programmes"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by Ellio on 2012-08-17
Hi there, I am very new to Ubuntu having just installed it after Windows XP died on me.  I have been through the Ubuntu Software centre and found an app called GNU recovery which I want to use to recover the files on the crashed windows system.  It appears to install OK but then I can't find it anywhere to run.  Can any one help.  Perhaps this isn't the right programmed so any advice would be appreciated.

Apart from that so far Ubuntu is great!

---

### Post by Futant on 2012-08-17
Hello, and welcome to the wonderful world of Ubuntu! Anything you have installed will appear when you search for it in the dash (top button in the launcher). Have fun!

---

### Post by nyamina on 2012-08-17
Either press the Windows button on your keyboard, or the top button in the launcher on the left and type the name of the program you are after. If, for some reason it isn't there, I would start by logging out and then back in, but it's also possible that it could be a command-line program tool, although I haven't actually used that program. 

If you're just trying to get files from an unresponsive Windows XP system, I would use a live CD or USB to transfer the files off. If you have already installed Ubuntu over Windows XP, there is probably no way of getting your files back, as Windows XP will have been erased.

---

### Post by irv on 2012-08-17
I think the app you are referring to is gddrescue. Yes, you can do a search for it. It is the GNU data recovery tool and I found it in the package manager. I am not sure what you are trying to do and I am not familiar with this program.

---

### Post by oldos2er on 2012-08-17
gddrescue is a CLI app, so you won't find it in a GUI menu. Open a terminal (Ctrl-Alt-t) and type ```
gddrescue
``` It may need to be run as root, but I'm not certain of that.

---

### Post by ajgreeny on 2012-08-17
As your windows crashed you may have some difficulty mounting the partition in order to get the files off it.  Come back again if that's the situation.

---

### Post by gordintoronto on 2012-08-17
Your real desire is to recover your Windows files. Just run the file manager, which is called Nautilus. Your Windows partition should appear near the top-left, as "164 GB Filesystem," or whatever size it is. From there, you can write to a DVD or flash drive.

---

