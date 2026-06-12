---
title: "help with script"
date: 2011-06-01
forum: Programming Talk
---

### Post by Blackbug on 2011-06-01
I am writin a script which will open around 10 new konsole with different PWD. At these paths i have a script, which will start in this way
./myscript_application1 start
 
I need to put this './myscript_application1 start' on the newly opened konsole by itself.
 
different PWD's are for various applications. I have 10 applications and each has this script.
 
I need to write a common script, which i can run from anywhere and start all these applications on new konsole automatically.

---

### Post by sanderd17 on 2011-06-01
Why do you need to open it in a console? Can't you just run the script without console?

You can runs scripts in parallel by adding an '&' to the end of each line.

If you really need to open a console, you can use something like

```

gnome-terminal --working-directory=/path -e ./my_script

```

again, append an '&' if you want to open multiple consoles at once.

---

