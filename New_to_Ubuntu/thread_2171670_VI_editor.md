---
title: "VI editor"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by jai_kaushik on 2013-09-01
hi ,installed ubuntu today..... in my college they started teaching C in terminal using vi editor on boss linux...
i installed ubuntu finr,its easy and fast but...in VI editor when i press arow keys to move up and down or right or left it types ABCD..and backspace ooption doestt delete anything it jus moves cursor back..
this doesnt happen at college...
i am a total a newb i dont know anything except C ...how to change that...please help...

---

### Post by scbingham on 2013-09-01
You might have set the incorrect keyboard on your system. Do the backspace & arrow keys work within other editors ie nano or gedit ?
On my system, within vi, the arrow keys work but the backspace only does a backspace, not delete. Within nano the backspace does delete too.

Ask at college if they have added any extra key mappings to their system.

vi is very powerful, especially when used at the command line but the commands are not very intuitive. There are other editors available which you may find easier to use.

It depends if college is trying to teach you C, or C and the vi editor, ask your tutor.

There are many links out there for all the vi commands & of course the man pages.

Good luck & have fun.

---

### Post by redmk2 on 2013-09-01
> **jai_kaushik said:**
> hi ,installed ubuntu today..... in my college they started teaching C in terminal using vi editor on boss linux...
i installed ubuntu finr,its easy and fast but...in VI editor when i press arow keys to move up and down or right or left it types ABCD..and backspace ooption doestt delete anything it jus moves cursor back..
this doesnt happen at college...
i am a total a newb i dont know anything except C ...how to change that...please help...

The default install of VIM on Ubuntu is vim-tiny.  You need to install the full version of VIM.  From the terminal do this```
sudo apt-get-install vim
```

[COLOR="#0000FF"]Edit:  /usr/bin/vi is indirectly  sym-linked to /usr/bin/vim.basic[/COLOR]

---

### Post by Impavidus on 2013-09-01
It may be something with your keyboard or terminal settings.

In my case backspace moves back and deletes when in insert mode and just moves back when in command mode, but I think it depends on your terminal settings.

Vim takes quite a while to get used to. If it's about C, not vim, you may be able to use a different editor. I programmed for a few years in gedit before switching to vim. Your tutor may use vim just because (s)he likes it.

---

### Post by Jonathan Precise on 2013-09-01
> **Impavidus said:**
> It may be something with your keyboard or terminal settings.

In my case backspace moves back and deletes when in insert mode and just moves back when in command mode, but I think it depends on your terminal settings.

Vim takes quite a while to get used to. If it's about C, not vim, you may be able to use a different editor. I programmed for a few years in gedit before switching to vim. Your tutor may use vim just because (s)he likes it.

+1. I recommend [FONT=courier new]nano[/FONT] for command-line editors and **gedit** for graphical text-editors.

---

### Post by siddharth007 on 2013-09-02
Hey.I suggest you follow this link for a small tutorial on vi/vim editor.Here is the [link]("http://bluesteel007india.blogspot.in/2013/01/tutorialsimplifying-vi-editor-in-linux.html")

---

### Post by newb85 on 2013-09-02
+1 to siddharth007's recommendation that you follow a tutorial.  vim-tiny will likely suit your needs just fine, but there's nothing wrong with replacing it with vim, if you wish.

In the case of your issue with the arrow keys, I suspect that you were still in *Insert Mode*, and that's why the arrow keys didn't behave as you expected them.  If you hit Esc to get to *Normal Mode*, I think you'll find the arrow keys work just fine.

---

