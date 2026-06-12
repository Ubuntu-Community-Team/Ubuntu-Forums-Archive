---
title: "How can I code applications with GUI in windows"
date: 2009-01-07
forum: Programming Talk
---

### Post by iampriteshdesai on 2009-01-07
I had C++ in this semester and I'd like to code my first app. We havent done GUI yet.Can anybody plz tell me how?
I use Codeblocks.
I'll code GTH later. School requires windows

---

### Post by Rocket2DMn on 2009-01-07
Moved to Programming Talk.

---

### Post by Mr. Picklesworth on 2009-01-07
You just need to utilize the appropriate API, just like with any other code thing :/
GUI stuff is abstracted to the point that you don't need to think about anything special. I forgot the particulars for Windows GUIs, except that they are horribly painful to make, which is why I yanked them from memory. (Granted, at the time I was working with the really lame API based on set coordinates instead of fluid layouts. I understand winforms in .Net received a bit more love. Never quite figured out if that love spread over to other APIs).

With GUIs, it is worth noting that everything is a window. The operating system (in our case with the X window system - similar deal in Windows) manages thousands of little windows that are essentially little areas that can be drawn on and which are set up to handle certain events (eg: mouse clicks). A button is a window, just handled by a different function / program from a text box or a toplevel window.
For some reason people occasionally teach this stuff as if every widget is a specific beast implemented from the bottom up, but at some (generally fairly nearby) level they all follow the same rules under the same technology.

It *is* possible to use GTK on Windows, or Qt or WXWidgets, if they'll let you. They're much more enjoyable to work with.
Otherwise, I believe WinForms is the one to look for.

---

### Post by Majorix on 2009-01-07
Have a look at Visual C++ 2008. It comes with Visual Studio 2008.

---

