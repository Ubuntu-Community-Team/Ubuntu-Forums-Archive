---
title: "Editing Virus"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by mrdosa on 2008-04-24
Hi guys! I am a newbie using a dual boot xp and ubuntu 7.10 system. Recently my windows was attacked by a virus [as usual] and I could locate the file using nautilus. Now,is there any way I can open it using gedit. I am getting an error saying cant open. Please let me know if its possible. 
Thanks!

---

### Post by the_darkside_986 on 2008-04-24
Is this a text file or a binary file? You might have better luck opening the file with ghex2. It is available in the "ghex" package (as in sudo apt-get install ghex).

---

### Post by mrdosa on 2008-04-24
Its a .exe file. SO I guess its a binary file. Can we open any windows programs too?

---

### Post by Bodsda on 2008-04-24
a .exe is a compiled binary package there is no way to determine the source from a compiled exe afaik

---

### Post by the_darkside_986 on 2008-04-24
Ghex2 should be able to handle opening any binary file, including *.exe.

Hex editors are probably not the best tool to use for opening exe's unless you are reading a guide to the Portable Executable format. I made a C++ program that reads all the header information from the first part of the file but I got bored so I didn't add the interesting stuff (reading code, data, etc.).

If you are trying to reverse engineer the virus, the WINE project might have some tools for that. WINE runs Windows applications in Unix. But you probably don't want to run a virus even in WINE with your normal user account. I would make a separate, unprivileged account just for that.

---

### Post by dasunst3r on 2008-04-24
Since you're on Ubuntu, you can always delete the virus that's giving you grief. ;)

---

### Post by mrdosa on 2008-04-24
Well, just wanted to know what makes up a virus. Its interesting. Can you post some links, where I can read more about such files, and how to edit them?
Thanks!

---

### Post by Chayak on 2008-04-24
> **mahender.mandala said:**
> Well, just wanted to know what makes up a virus. Its interesting. Can you post some links, where I can read more about such files, and how to edit them?
Thanks!

Then you really should be working in a virtual machine.  I normally use OLLYDBG, procmon, wireshark (on the host) and procexp.  You take a safe snapshot then you run the virus with OLLYDBG and watch what it does though a knowledge of assembly language will help a lot at that point.  You can then watch procmon and see what files and registry entries were written.  You can then monitor network traffic with wireshark and determine if it has any callbacks.  That's the basic behavioral analysis.  The in depth stuff is going through the assembly code and reverse engineering it.

---

### Post by mrdosa on 2008-04-24
Can you please provide some links where I can go through all that!? It would be great!

---

### Post by LaRoza on 2008-04-25
> **mahender.mandala said:**
> Can you please provide some links where I can go through all that!? It would be great!

You can open it with a hex editor (ghex for Ubuntu), but that won't tell you much.

What is the name of the file?

---

### Post by mrdosa on 2008-04-25
Its a .exe file. It has the same name as the folder in which it is. It came through a pen drive!

---

