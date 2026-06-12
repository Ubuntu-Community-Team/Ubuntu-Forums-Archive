---
title: "shell"
date: 2008-05-15
forum: Programming Talk
---

### Post by pr0x on 2008-05-15
hey guys am doing a bit of scripting at moment and i cant seem to get any further 

anyway ill explain

i have a script at the moment that does ermmmm

grab input
grab input
run command 
run command

but i want the commands to run in a new terminal 

any ideas??

---

### Post by Thanoulis on 2008-05-15
Try:
```
man gnome-terminal
```
I believe that the *--window-with-profile* option may suit you...

---

### Post by pr0x on 2008-05-16
thanks for the reply yeah a new window opens fine but i have no idea how to let the script run the commands on the new windows

---

### Post by dtmilano on 2008-05-16
>
>   -e, --command                                   Execute the argument to this option inside the terminal.
  -x, --execute                                   Execute the remainder of the command line inside the terminal.

---

### Post by pr0x on 2008-05-16
so for instance if i was to list a directory in a new terminal while the script is still running on first window i would

gnome-terminal -x --windows-with-profile=default ls

or something like that ??

thanks for reply too

---

### Post by pr0x on 2008-05-16
or is there a way to store a variable in a shell and when i open another console still be able to use that same variable name i.e. $macaddy stores address in one shell and open another shell and still be able to use the $macaddy

thanks

---

