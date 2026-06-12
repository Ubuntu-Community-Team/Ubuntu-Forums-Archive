---
title: "[SOLVED] theres no &amp;quot;r&amp;quot; on terminal"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-05
hi,
some weeks ago i did something. dunno what, but now, when on terminal, every time i press "r" it act like if i would press "paste" (ctrl+v) so i cant write the "r" in terminal. 

in fact, i used to shut down my laptop by writing 

```
 sudo poweroff 
```

but now, as i cant write no "r" im doing the following:
```

sudo init 0
```



but anyway, why is this happening? can i fix it?

thaks

---

### Post by sisco311 on 2008-11-05
> **jsf_pp said:**
> 

but now, as i cant write no "r" im doing the following:
```

sudo init 0
```



:lolflag:

go to the keyboard shortcuts: Edit -> Keyboard Shortcuts... 

and change the shortcut for the Paste command to Ctrl+Shift+v

---

### Post by jsf_pp on 2008-11-05
> **sisco311 said:**
> :lolflag:

go to the keyboard shortcuts: Edit -> Keyboard Shortcuts... 

and change the shortcut for the Paste command to Ctrl+Shift+v


its not a joke man! really, its kinda frustrating actually.

anyway, honestly, i couldn't find EDIT -> KEYBOARD SHORTCUTS (where is that?)
and, something else:

paste in ctrl+v works fine, the problem is in terminal, when im trying to write an "r" it acts like if i would have press "paste"

thanks for anwsering :biggrin:

---

### Post by issih on 2008-11-05
Not that this helps really, but its worth pointing out.

Copy/paste in a terminal window doesn't work as normal. Mainly because ctrl+c is an old unix shortcut to terminate a process.

Consequently to copy and paste to/from a terminal window you have to add in a shift to the usual commands, so copy is ctrl+shift+c and paste ctrl+shift+v.

As for the keyboard shortcuts, the dialog for editing them can be found in the System->Preferences menu.

Unfortunately I'm pretty sure that as the terminal is set up to work differently, that the solution to your issue may well be somewhat more complex.

Sorry that isn't too useful

---

### Post by jsf_pp on 2008-11-05
> **issih said:**
> Not that this helps really, but its worth pointing out.

Copy/paste in a terminal window doesn't work as normal. Mainly because ctrl+c is an old unix shortcut to terminate a process.

Consequently to copy and paste to/from a terminal window you have to add in a shift to the usual commands, so copy is ctrl+shift+c and paste ctrl+shift+v.

As for the keyboard shortcuts, the dialog for editing them can be found in the System->Preferences menu.

Unfortunately I'm pretty sure that as the terminal is set up to work differently, that the solution to your issue may well be somewhat more complex.

Sorry that isn't too useful

dont worry man, thanks anyway! :grin:

---

### Post by Peter09 on 2008-11-05
The EDIT referred to is part of the terminal window. Open a terminal and look along the top for the edit tab, in there is keyboard shortcuts.

---

### Post by sisco311 on 2008-11-05
open your terminal and from the terminals Edit menu select the Keyboard Shortcuts option.

---

### Post by WelshChris on 2008-11-05
As long as the menu bar can be seen!

Right click the terminal and select 'show menubar' if it isn't.  I'm assuming it's the standard terminal, and not some strange third party one.

Kudos, though, for giving me an idea for a good practical joke =)
Change the shortcut to copy to the letter 'e'.

---

### Post by Joeb454 on 2008-11-05
I thought you meant your terminal was saying "Teminal" in the Title Bar ;)

I fail :(

---

### Post by jsf_pp on 2008-11-05
> **sisco311 said:**
> open your terminal and from the terminals Edit menu select the Keyboard Shortcuts option.

i went there already and, theres no "paste" edit part. only: sound, desktop and windows management.

and i repeat, the command "paste", i mean, when i press "ctrl+v" works ok. theres no problem with that.

thing is when im on terminal every time i write down the "r" key appears what is in the clipboard.

[IMG]http://i33.tinypic.com/21kh0e0.png[/IMG]

i took a screenshot to clarify my only 3 options.
again, thanks for your help guys.

---

### Post by Peter09 on 2008-11-05
No - we are talking about the terminal window itself - not the top panel

You need to open a terminal and use the edit function on its menu bar.

---

### Post by jsf_pp on 2008-11-05
big fail!!!

now i realize you were talking about this.

[IMG]http://i38.tinypic.com/2a0etsp.png[/IMG]

thanks
its solved!

---

### Post by sisco311 on 2008-11-05
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

