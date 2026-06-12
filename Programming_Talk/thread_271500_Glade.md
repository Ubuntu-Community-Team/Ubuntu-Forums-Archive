---
title: "Glade"
date: 2006-10-04
forum: Programming Talk
---

### Post by dean703 on 2006-10-04
I cannot get Glade to run on Dapper. The program cannot find necessary libraries, even though they are installed. I get the message "consider adjusting the PKG_CONFIG_PATH enviornment variable if you installed software in a non-standard prefix"....How do I do that and why should I have to? Help, please, even if only to point me toward relevant documentation, I'm a newcomer to Ubuntu and linux. Thank you.

---

### Post by kaamos on 2006-10-04
(I assume that error is from installing glade and not from compiling your program.)

Why are you trying to compile glade from source? It is after all just a "sudo apt-get install glade" away.. That will install glade 2 for you which is atm a better idea since glade 3 uses widgets from gtk 2.10 that is not very common yet.

---

### Post by dean703 on 2006-10-05
I didn't compile it from source. I used the Synaptic Package Manager and it installed it the way it wanted to.

---

### Post by dean703 on 2006-10-14
The problem was resolved by installing libgtk1.2-dev and libgtk2.0-dev, and by installing newer versions of Pango and Glib.

---

