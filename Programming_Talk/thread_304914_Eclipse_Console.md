---
title: "Eclipse Console"
date: 2006-11-22
forum: Programming Talk
---

### Post by Quaker on 2006-11-22
Hi!!! I'm programing c in eclipse but in that program i need to create a raw socket wich is a problem because when i run it eclipse send's an error message teling me that i need to be sudo to run that program.
I've tried to start eclipse as - > sudo eclipse <- it still doesn't work.
Does anyone know how to run eclipse console as sudo, or if it possible to run the eclipse console as root.
I could run eclipse in the root acount but i'm trying to avoid it... can anyone help me???

---

### Post by smartalecks on 2006-11-22
?? not sure what you are trying to do, but if you right click the eclipse icon, go to properties, and in the command box add "gksudo" (without the quotes) to the beginning, and then run it'll run it as root.

---

### Post by andrewc6l on 2006-11-22
I don't think Eclipse can run a program under development as root if you're not root when you start. However, I can think of a couple of things you could do:

1. Create an External Tool that will set your executable as setuid root
Run -> External Tools -> External Tools -> New -> 
  Location: /usr/bin/sudo
  Working directory: where your app output folder is
  Args: /bin/chmod 4777 myapp

2. Create an External Tool that will just run your app under sudo:
Run -> External Tools -> External Tools -> New -> 
  Location: /usr/bin/sudo
  Working directory: where your app output folder is
  Args: myapp

Unfortunately, that doesn't help you if you're debugging. You might want to create a feature request at:
  [bugs.eclipse.org/bugs]("http://bugs.eclipse.org/bugs")

 - Andrew

---

