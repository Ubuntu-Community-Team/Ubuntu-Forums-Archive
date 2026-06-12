---
title: "Problems with SPE 0.8.2.a - no output."
date: 2006-01-27
forum: Programming Talk
---

### Post by phibxr on 2006-01-27
I have quite a strange problem with SPE 0.8.2.a when i try to execute a script in gnome-terminal via the menu in the program.

If the script only consists of output-commands like "print 'test'", nothing is visible in the terminal window, but if I put a "raw_input()" *somewhere* in the script, everything works.

The problem is not that the window is closing without the raw_input(), but that there simply is no output visible.

---

### Post by Se7h on 2006-01-27
Are you running the .py directly through SPE?

Can you paste the source displayed in another IDE? (vim for example)

---

### Post by stani on 2006-01-29
Hi phibxr,
I'm new to Ubuntu myself, so I quickly try to find the code how to run a script through a terminal. I had problems to find out and it worked more succesful for Konsole then for the gnome-terminal. Maybe I could ask the question somewhere on this forum. SPE wants to do the following:
- open a terminal (whatever)
- change the path of the terminal
- execute a python script with "python script.py arguments"
- close the terminal or leave it open

So I think for Konsole I managed already quite well, if someone can give me the code for gnome-terminal I'd be happy to fix it. You can experiment with this settings in the Preferences>Paths.

Can someone of you bring me in contact with an Ubuntu guru who might help me out?

For now, would you mind installing Konsole and see if that does what you want?

Stani

---

### Post by UbuWu on 2006-01-31
[QUOTE=stani]
Can someone of you bring me in contact with an Ubuntu guru who might help me out?
[/QUOTE]

You should try the motu or devel mailing lists: [https://lists.ubuntu.com/mailman/listinfo/](https://lists.ubuntu.com/mailman/listinfo/)

---

