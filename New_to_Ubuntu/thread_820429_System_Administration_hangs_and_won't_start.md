---
title: "System Administration hangs and won't start"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-06
I recently installed Ubuntu 8.04 (a fresh install on a fresh partition from the downloaded CD).

Today, something strange has been happening when I've tried to start various programs from System -> Administration (e.g. Firestarter, Hardware Drivers, Synaptic Package Manager). The system hangs for around 15 seconds (the cursor changes to a circle), then it stops hanging; but, the program doesn't start.

When I open Update Manager and press Refresh, it hangs completely and I can't even close its window (although, after about 15 seconds, I can work on other windows).

Therefore, I don't have access to number of the System Administration programs.

I can open other non-Administration programs, such as Firefox.

What can I do to solve this problem?

---

### Post by skymera on 2008-06-06
Whats the output when you run them in the terminal?

---

### Post by Paddy Landau on 2008-06-06
> **skymera said:**
> Whats the output when you run them in the terminal?
How do I run them in terminal? (Sorry for the dumb question; I'm new at this. I do know how to start terminal, but not how to run adminstration tasks there.)

---

### Post by Paddy Landau on 2008-06-07
> **Paddy Landau said:**
> How do I run them in terminal? (Sorry for the dumb question; I'm new at this. I do know how to start terminal, but not how to run adminstration tasks there.)
OK, I figured it out. I went into terminal and ran:
```
gksu /usr/sbin/firestarter
```(I hope that's the right command.) I got the same result. The system hangs for about 15 seconds, and then the terminal just sits there doing nothing. :(

EDIT: Actually, I think something similar is happening with the automated updates. I clicked the "Update" button in the panel. The Update Manager opened and let me click "Install Updates". It's been sitting there doing nothing ever since, with the buttons grayed out.

---

### Post by Paddy Landau on 2008-06-09
Well, it looks as though no one has an answer to this problem.

I've just reinstalled a fresh installation of Ubuntu (overwriting the old one).

In future, I'll make regular partition backups with something like [Partimage]("http://www.partimage.org/") after making any important changes successfully.

---

### Post by Paddy Landau on 2008-06-09
My new, fresh install is giving problems, too. :(

There is a diference, though.

I can get into all functions in [FONT=Courier New][COLOR=Navy]System -> Administration[/COLOR][/FONT]. However, [FONT=Courier New][COLOR=Navy]System -> Administration -> Login Window[/COLOR][/FONT] gives an odd result. It first asks for my administrator password (as it should). After I enter the password, the Login Window opens; but it immediately closes again!

Entering the following command into a terminal window has the exact same effect:
```
gksu /usr/sbin/gdmsetup
```Can anyone give any clue as to how to solve this problem?

---

