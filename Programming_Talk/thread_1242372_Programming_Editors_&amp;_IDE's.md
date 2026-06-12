---
title: "Programming Editors &amp; IDE's"
date: 2009-08-17
forum: Programming Talk
---

### Post by Yansky on 2009-08-17
Does anyone know of an editor or IDE for linux that highlights *all* instances of a variable/function name when one instance is highlighted manually? This is the default behaviour for Notepad++ under windows, but I have yet to find an editor in linux that will do this.

I've tried:
Editra
Kate
Eclipse
Geany
jEdit
Scite

---

### Post by jimmio on 2009-08-17
Code::Blocks might do it.. if not by default, with option changes. 

```
sudo apt-get install codeblocks
```

Code::Blocks uses the same text control as Notepad++ (Scintilla I believe it is), so it should work.

-Jim

---

### Post by jimi_hendrix on 2009-08-17
the latest qt-creator (check the site, repo is out of date) is great

eclipse-cdt is what i used before, and was sturdy

---

### Post by kpkeerthi on 2009-08-17
Eclipse does it (for Java)

---

### Post by nvteighen on 2009-08-17
The new Emacs23 is quite impressive, actually. It now opens PDF, images, etc...

---

### Post by pepperphd on 2009-08-17
I know that Kdevelop has a "Find in Files" feature that will bring up a list of the occurrences of a string, line numbers, and the context it was found in. Clicking on each entry will bring you to it. I think this is close to what you are asking for. Also, once Kdevelop 4 is released it will have a full declaration-usage-chain modeling system (like Visual Studio) which is going to be awesome.

---

### Post by hyperAura on 2009-08-17
i think this depends also on which programming language ur willing to use.. not rly sure though.. for example ive been using nedit for java and gedit for C to get the right indexing and highlighting..

---

### Post by Mirge on 2009-08-17
> **Yansky said:**
> Does anyone know of an editor or IDE for linux that highlights *all* instances of a variable/function name when one instance is highlighted manually? This is the default behaviour for Notepad++ under windows, but I have yet to find an editor in linux that will do this.

I've tried:
Editra
Kate
**Eclipse**
Geany
jEdit
Scite

Strange, because I use Eclipse everyday & it does it for me. It's called "Mark Occurrences"... might not be enabled by default, but it's just a button on the toolbar that toggles it on/off.

---

### Post by bostonaholic on 2009-08-17
> **hyperAura said:**
> i think this depends also on which programming language ur willing to use.. not rly sure though.. for example ive been using nedit for java and gedit for C to get the right indexing and highlighting..

> **kpkeerthi said:**
> Eclipse does it (for Java)

^^ what he said.

Have you tried NetBeans?

---

### Post by Jimleko211 on 2009-08-17
Netbeans does it, for Java.

---

