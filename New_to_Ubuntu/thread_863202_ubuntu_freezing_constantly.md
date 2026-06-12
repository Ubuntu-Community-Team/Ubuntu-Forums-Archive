---
title: "ubuntu freezing constantly"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-18
is there some way of trapping or debugging errors when ubuntu 8.04 freezes?  it freezes to the point where i cannot even the mouse pointer on the screen and Ctrl + Print Scr + REISUB does nothing, so i am forced to hit the reset button on the PC case.  this has been occuring sporadically- at least once every few days now, used to happen at least once a day awhile ago- and i don't know where to look for the cause of the issue at this point.  any ideas or suggestions would be greatly appreciated.

thanks.

---

### Post by phantomjoker on 2008-07-18
heres a quick tip - doesnt help solve the problem but 

ALT + CTRL + BACKSPACE this reboots just the interface taking you back to the login screen! well ill get back to you with a solution to your freezing. By the way - report it to the error report forum.

hope I helped

---

### Post by deadgobby on 2008-07-18
Is there a program(s) you are using that freezes up? Is the system freezes up when system goes to sleep?

---

### Post by hyper_ch on 2008-07-18
do you have multiple computers?

---

### Post by houbysoft.xf.cz on 2008-07-18
Just wanted to say that you can also use CTRL+ALT+F1 to switch to the command-line interface, for example kill the program that is causing your computer to freeze (sudo killall <program name>) and then go back to the GUI with ALT+F7.
Hope it helps

---

### Post by hyper_ch on 2008-07-18
I think the gui freezes for him, so I asked about another box so that he can try to remotely login through ssh when that happens the next time... if x freezes then ctrl-alt-f1 won't help ;)

---

### Post by Matt26 on 2008-07-18
> **hyper_ch said:**
> I think the gui freezes for him, so I asked about another box so that he can try to remotely login through ssh when that happens the next time... if x freezes then ctrl-alt-f1 won't help ;)

correct, when my freeze up occurs- absolutely nothing repsonds- no mouse movement at all, no keyboard, no activity from HDD LED- the clock time even halts at the point when the freeze up occured!

would a remote login even work in this situation- i would think that since the OS is unresponsive to anything (even ctrl+prt scr+REISUB doesn't do anything) it wouldn't be able to accept network connections of any kind.

---

### Post by philinux on 2008-07-18
Have a look in /var/log/messages

See if anything useful to pinpoint the problem.

---

