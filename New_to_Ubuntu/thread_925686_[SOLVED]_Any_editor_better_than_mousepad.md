---
title: "[SOLVED] Any editor better than mousepad?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ferral-cat on 2008-09-20
I have been using mousepad text editor here on Xubuntu Hardy Heron.  

Is there a way to create an alias for mousepad so that instead of typing

```
mousepad /boot/grub/menu.lst
```

I can type an abbreviation for mousepad such as:

```
mp /boot/grub/menu.lst
```

I know it sounds stupid but I really wish I didnt have to type so much.  

I am tempted to install kate text editor but dont want to add all the KDE libraries and bloat just for this purpose.

---

### Post by ladr0n on 2008-09-20
I assume that you are using bash (the default command shell in Ubuntu).
Use the command "mousepad .bashrc" (ironic enough for you?) to open your bash configuration file for editing.
At the bottom, add an alias line or two.  Here is what I would use:
```

alias mp='mousepad'
alias smp='sudo mousepad'

```
Now when you type 'mp' the terminal interprets it as 'mousepad' and when you type 'smp' the terminal interprets it as 'sudo mousepad' (for editing system-wide config files).  
You can add aliases to do basically anything else using the same method.  For example, one of my most-used aliases is la='ls -a', which allows easy access to viewing hidden files.  Hopefully that will make you life just a little bit easier.

---

### Post by barbedsaber on 2008-09-20
whoa, thats really cool, I learned something new.
(goes and adds aliases for many things)

---

### Post by Mister.Vash on 2008-09-20
you could add the following to your $HOME/.bashrc file

alias mp=mousepad


you could also add something like the following as well, you could specify options or a commonly edited program, etc.

alias mp-grub='mousepad /boot/grub/menu.lst'



You can always test alias in your current session to see if it works correctly, then put it in .bashrc file after you validate

---

### Post by unutbu on 2008-09-20
Note also that your bash shell can do TAB completion:
If you type the first few letters of a command and then press TAB, bash will complete the command if there is only one possible choice. The same is true of paths. 

So to type 
```

mousepad /boot/grub/menu.lst
```

you might only have to type
```

mous[TAB] /bo[TAB]/g[TAB]/me[TAB]
```

---

### Post by ferral-cat on 2008-09-21
> **ladr0n said:**
> I assume that you are using bash (the default command shell in Ubuntu).
Use the command "mousepad .bashrc" (ironic enough for you?) to open your bash configuration file for editing.
At the bottom, add an alias line or two.  Here is what I would use:
```

alias mp='mousepad'
alias smp='sudo mousepad'

```
Now when you type 'mp' the terminal interprets it as 'mousepad' and when you type 'smp' the terminal interprets it as 'sudo mousepad' (for editing system-wide config files).  
You can add aliases to do basically anything else using the same method.  For example, one of my most-used aliases is la='ls -a', which allows easy access to viewing hidden files.  Hopefully that will make you life just a little bit easier.

Thank you very kindly.  This is exactly the information I was looking for.  :guitar:

---

### Post by Steveway on 2008-09-21
You should use gksu instead of sudo, cause mousepad is a graphical application.

---

### Post by Zill on 2008-09-21
> **Steveway said:**
> You should use gksu instead of sudo, cause mousepad is a graphical application.
... and nano is the default CLI text editor ;-)
```
sudo nano /boot/grub/menu.lst
```

---

