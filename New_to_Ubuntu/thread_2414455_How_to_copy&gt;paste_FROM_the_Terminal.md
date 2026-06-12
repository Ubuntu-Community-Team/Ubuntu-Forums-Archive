---
title: "How to copy&gt;paste FROM the Terminal"
date: 2019-03-11
forum: New to Ubuntu
---

### Post by tazmo8448 on 2019-03-11
Saw an old closed post that was called 'SOLVED' (shows in Google as solved) an all they did was discuss things that didn't work. I would like to be able to copy something FROM the Terminal and put it in a folder/notepad but have yet to find a way.

---

### Post by Bashing-om on 2019-03-11
tazmo8448; Hello -

What terminal are you using ?
In my xterm I can left click with the mouse, hold and drag over what I want, and middle click to paste it where I want.

Your terminal emulator will make a difference.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by tazmo8448 on 2019-03-11
Root Terminal is what is showing on the top of the page. The icon shows Terminal Emulator.  I'm new to this stuff.

When I hi-lite the text am unable to do anything with it. I've tried all the shift control insert C's & V's but no luck.

Using the mouse it either hi-lights (which in this case actually darkens it) trying to drag it all that happens is it goes back to the way it was.

---

### Post by Impavidus on 2019-03-11
There are two buffers to be used for copy-paste that work across the GUI applications and the terminal emulator is a GUI application (in contrast to the programs running in the terminal). Some applications may have more copy-paste buffers for internal use.

The first can be used by first selecting the text, than pase it with a click of the middle mouse button. For most mice that means pressing the wheel. This works in most applications, including most terminals. No explicit copying is required.

The second buffer is what many new users are more familiar with. To use it, you select the text, then copy with right-click->copy or a key combination, than paste with right-click->paste or another key combination. Instead of the context menu from right-click, you can also use the edit menu. In most applications the key combination for copy is ctrl+c, for paste ctrl-v. In the terminal, it's ctrl+shift+c and ctrl+shift+v, because the former were already used to send signals to running processes.

There could be a complication from using a root terminal, as you're now trying to copy stuff from one user to another, but I think that should still work. Have you tried to copy text from a non-root terminal?

---

### Post by vinayakmadiwalar9 on 2019-03-11
To copy ctrl+shift+c
To paste ctrl+shift+P

---

### Post by Dennis N on 2019-03-11
Gnome Terminal has menus on a menu bar. Use the Edit menu to copy selected text to clipboard (Edit >Copy) , and paste (Edit>Paste) to place text from the clipboard into the cursor position.

Paste text from clipboard to Gnome's Text Editor:
In Text Editor (named gedit) window (has no menu bar or edit menu like the terminal), use right-click paste, or Ctrl+V to paste into cursor position.

---

### Post by oldrocker99 on 2019-03-11
The way to paste with CTRL-V in a terminal is to use SHIFT-CTRL-V. It was mentioned above that is you simply highlight the text, you can paste it with the middle mouse button. This is one feature of Linux that I most like.

---

