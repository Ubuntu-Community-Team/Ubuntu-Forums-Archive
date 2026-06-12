---
title: "Code Blocks File Error"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by Dying_Starman on 2016-01-16
Hello. I am new to Ubuntu. I want to learn c++, so I downloaded Code Blocks as a place to practice and learn. I downloaded it from the software center and started it. I can click "Create a new project", choose a template, name it and tell it where to store it, but when i click "finish", I get this message:
Couldn't create the project directory:
First/Hi/

Can someone please help me? I have Ubuntu 14.04.3 LTS 32-bit if that helps answer.

---

### Post by steeldriver on 2016-01-16
Where exactly (what directory / path) did you tell it to store the project directory? Remember that by default you will only be able to write to locations under your own home directory

---

### Post by Dying_Starman on 2016-01-16
The file name is "Hi" and the folder name is "First" so it said that the Filename is First/Hi/Hi.cbp

After that window is the final one, and it's just debugging and release options.

---

### Post by steeldriver on 2016-01-16
You need to choose an actual **existing** folder as the 'Folder to create project in', I think

e.g. create a folder called 'First' in your home directory and then browse to it (using the '..' chooser) or enter the full absolute path:

---

### Post by Dying_Starman on 2016-01-16
Thank you!!!! It saved it and I can now work in it!

---

### Post by steeldriver on 2016-01-16
You're welcome

IMHO IDEs like CodeBlocks can make complicated projects simpler to manage, but often make simple things more complicated than they need to be - you might do just as well by writing your code using a plain ol' text editor (gedit / geany or whatever)

---

