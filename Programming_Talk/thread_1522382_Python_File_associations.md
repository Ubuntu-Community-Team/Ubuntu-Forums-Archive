---
title: "Python File associations"
date: 2010-07-02
forum: Programming Talk
---

### Post by DrTravia on 2010-07-02
I've recently installed a couple python programs such as todo manager, which is working whenever I open it with idle and run with f5. However, there are no file associations with the program itself so every time I want to start any python program, I am forced to open IDLE, then open that file and run with f5.

Is there any way to fix the file associations so that all I would need to do is double click the *.py files.

I've searched via google for file association fixes but unfortunately I've had no luck in finding a remedy to the problem.

Also, currently, if I double click a *.py file it comes up in gedit

---

### Post by Bodsda on 2010-07-02
> **DrTravia said:**
> I've recently installed a couple python programs such as todo manager, which is working whenever I open it with idle and run with f5. However, there are no file associations with the program itself so every time I want to start any python program, I am forced to open IDLE, then open that file and run with f5.
 
Is there any way to fix the file associations so that all I would need to do is double click the *.py files.
 
I've searched via google for file association fixes but unfortunately I've had no luck in finding a remedy to the problem.
 
Also, currently, if I double click a *.py file it comes up in gedit
 
IIRC, file extension association is set in the properties of the launcher. Right click > Properties > It's one of the tabs on here.
 
Bodsda

---

### Post by wmcbrine on 2010-07-02
If you set the executable bit on your .py file, then instead of it automatically coming up in gedit, you'll get a prompt asking if you want to run it or edit it. (For this to work, you also have to have the proper interpreter line at the top -- "#!/usr/bin/env python" or the like.)

Note that if it's a terminal app (using print, input, etc.), and you choose "Run in Terminal", the terminal will close automatically when the program ends.

To completely avoid the menu, and just launch the app, right-click on the desktop and select "Create launcher...", and follow the prompts.

Changing file associations is almost certainly not what you want to do.

---

### Post by DrTravia on 2010-07-03
> **Bodsda said:**
> IIRC, file extension association is set in the properties of the launcher. Right click > Properties > It's one of the tabs on here.
 
Bodsda

Ah, thank you this solved the problem.

I got used to windows, doing it with rightclick > open with > choose from list > always use this program.
Although, in hindsight, properties should have been the first place I looked lol.

---

