---
title: "Emacs"
date: 2009-02-10
forum: Programming Talk
---

### Post by JFASI on 2009-02-10
I am experiencing some strange behavior in emacs over a terminal. I ssh into the machine, and everything is normal. Then I open emacs and the delete and backspace keys are switched. I googled the problem, and it recommended that i do this: 

normal-erase-is-backspace-mode

But some some reason, it refuses to switch it. Any ideas?

---

### Post by Barriehie on 2009-02-10
> **JFASI said:**
> I am experiencing some strange behavior in emacs over a terminal. I ssh into the machine, and everything is normal. Then I open emacs and the delete and backspace keys are switched. I googled the problem, and it recommended that i do this: 

normal-erase-is-backspace-mode

But some some reason, it refuses to switch it. Any ideas?

How about this in your .emacs file:
[php]
(normal-erase-is-backspace-mode 1)
[/php]Barrie

---

### Post by JFASI on 2009-02-10
No luck. This is exactly the issue, no matter where I place that, or how hard I hit return, it stubbornly refuses to switch modes.

Is there any way I can get emacs to print the keycode of whatever it is I'm hitting? Because I think it might be a mapping issue.

---

### Post by Barriehie on 2009-02-10
See if this [link]("http://www.gnu.org/software/emacs/manual/html_node/emacs/Rebinding.html#Rebinding") helps.

I'm not an expert at running emacs remotely but initially I'm thinking it might be the way it initializes on the other machine.

Barrie

---

