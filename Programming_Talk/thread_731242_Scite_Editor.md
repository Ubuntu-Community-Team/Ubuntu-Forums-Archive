---
title: "Scite Editor?"
date: 2008-03-21
forum: Programming Talk
---

### Post by DaveGiant on 2008-03-21
Does anyone use this? It says it is supported by the Ubuntu community. I am not sure what that means.

Anyway.

Does anyone know how when I click on open files it shows all files by default instead of source files. I want to open .php files but these never show up be default.

---

### Post by maddog39 on 2008-03-21
If its supported by the ubuntu community then that means that people or someone within the Ubuntu community maintains and updates the Ubuntu package for Scite. As far as the default open file format. I dont know of a text editor that lets you choose the default, however the Open File dialog should give you the option to only show php files in your case.

---

### Post by LaRoza on 2008-03-21
I know some people on this forum (experienced programmers) use it.

---

### Post by happycoder on 2008-03-21
I've used it on XP for years. I don't have it installed under Ubuntu yet, but here is how I configured v1.66 to do what you ask.

Open the Options menu and select 'Open Global Options File' (you may need root access to save it, in which case start it using gksudo). You could open the local file if you don't want to make global changes.

Search the file for open.filter. Make $(all.files)\ the first entry instead of the source entry that is there now.

You'll probably notice just how configurable the editor is when you are scrolling around. I recommend saving your configuration so you don't lose it when you upgrade.

If you are editing the colors, there is no GUI, you have to know what RBG values you want.

---

### Post by pmasiar on 2008-03-21
I use SciTE on both Windows and Linux. It rocks! And I see your problems are solved by happycoder?

---

