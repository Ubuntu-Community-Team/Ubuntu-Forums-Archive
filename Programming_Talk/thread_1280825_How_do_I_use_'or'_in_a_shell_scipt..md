---
title: "How do I use 'or' in a shell scipt."
date: 2009-10-02
forum: Programming Talk
---

### Post by dragos240 on 2009-10-02
Hi,

I want to make a shell script that asks me if I want to:

1. Open GDM on startup
2. Nothing.

I want it to ask me that. If I press 1, gdm will start, if I press 2, it will instead, not run gdm, and I will be returned to a tty terminal.

---

### Post by wojox on 2009-10-02
You wouldn't use or. You want an if/else statement.

---

### Post by dragos240 on 2009-10-02
Thanks. Could you give me an example on how to use that? I would appreciate it.

---

### Post by NoaHall on 2009-10-02
#! /bin/bash
echo "Choose"
read choice
if [ $choice == "1" ]; then
startx
elif [ $choice == "0" ]; then
exit
else
echo "choose the right one!"
fi

---

### Post by carnagex420x on 2009-10-02
#!/bin/sh
# Start GDM

GDM_START="y"

echo "Start GDM?"
read GDM_VAR

if [ $GDM_VAR = $GDM_START ]; then
clear
echo "Starting GDM"
startx

else
clear
echo "Staying at Command Line"

fi

---

### Post by dragos240 on 2009-10-02
> **NoaHall said:**
> #! /bin/bash
echo "Choose"
read choice
if [ $choice == "1" ]; then
startx
elif [ $choice == "0" ]; then
exit
else
echo "choose the right one!"
fi

Thanks!

---

### Post by dragos240 on 2009-10-02
It works great. I moved the script to /etc/rc.d/ and put it in /etc/rc.conf, and it works great :) I modified it a bit so it started gdm rather than X directly, and added a choice list. So I know what I'm picking. It's interesting how all this works. What is a good site for learning bash scripting, I know some things, but not too much, and it would really help in the future.

---

### Post by NoaHall on 2009-10-02
Good :) Didn't want to give it all to you, wasn't sure how you would want it to lay out - but I guessed you'd change it anyway.

---

### Post by carnagex420x on 2009-10-02
Theres a quick run down of bash scripting here.

[http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html](http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html)

---

