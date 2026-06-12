---
title: "Gnome Menu Help Please..."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by willbur on 2008-06-12
Hi Everyone

I've just downloaded a java program (decaf) for playing chess online. The java script to run the program is located at 

cd /home/will/Decaf/

on my machine and the terminal command that runs it is

java -jar Decaf.jar

All well and good - the program runs perfectly from the command line. My problem is in installing this lot in a menu item in the 'games' section of the 'applications' menu. I've used 'edit menus', 'new item', selected type: 'application in terminal', named it and put

cd /home/will/Decaf/ && java -jar Decaf.jar

in the 'command' field. When I try to run this, the terminal is invoked and a dialogue box says:

There was an error creating the child process for this terminal

What am I doing wrong, please?

---

### Post by Vivaldi Gloria on 2008-06-12
Does

```
java -jar /home/will/Decaf/Decaf.jar
```

work?

---

### Post by sdennie on 2008-06-12
Try changing the launcher command to:

```

bash -c "cd /home/will/Decaf/ && java -jar Decaf.jar"

```

---

### Post by Vivaldi Gloria on 2008-06-12
Ahh, I read now that you run in terminal. How about

```
gnome-terminal -x java -jar /home/will/Decaf/Decaf.jar
```

---

### Post by willbur on 2008-06-12
Thanks everyone - vor's reply worked perfectly, the others invoked a terminal, generated no error messages and then exited.

Regards and thanks to all

willbur

---

