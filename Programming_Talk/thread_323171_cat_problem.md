---
title: "cat problem ???"
date: 2006-12-21
forum: Programming Talk
---

### Post by theorem_hunter on 2006-12-21
hi all

i want to create scripts from the command line using cat... but...

dimitri@programming:~/SCRIPTS$ cat penguin.sh
cat: penguin.sh: No such file or directory

in all the example tutorials i have looked at cat is supposed to create the file for you if it does not exist :(
i have to use gedit each time, which is nice because it has syntax highlighting :)

I'd just like to know why cat doesn't create a file if it doesn't exist

( i have looked at man cat & info cat, but i couldn't find my solution there)

any thoughts?
thanks

---

### Post by xtacocorex on 2006-12-21
cat is just supposed to display file contents and do nothing else. Why it doesn't create a file if it doesn't exist, I don't know.

If you want to create a blank file you can use the touch command.
```
touch myfile.txt
```

You can always use a check in your bash script to figure out if the file exists.
```

if [-f $filename]; then
    cat $filename
fi

```

---

### Post by theorem_hunter on 2006-12-21
thanks, that was quick :)

i am following this tutorial

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

i thought touch was just supposed to update the time stamp of a new file, but thanks for pointing that out. 

is there anyway to get the Gnome terminal to do syntax highlighting for scripts i type in it?

i am also considering retrying emacs or vi (cant remember if it is possible to run code in the programs, but im sure the do syntax highlighting)

thanks :)

---

### Post by theorem_hunter on 2006-12-21
well i just found this out

cat > filename  will create a new file
cat >> filename will append to an existing file

---

### Post by xtacocorex on 2006-12-21
I don't think Gnome Terminal will do syntax highlighting, that's more of a function of an editor like emacs or vi.

---

### Post by theorem_hunter on 2006-12-21
ok thanks. but can vi or emacs execute scripts within the editor?

---

### Post by fatsheep on 2006-12-21
> **theorem_hunter said:**
> ok thanks. but can vi or emacs execute scripts within the editor?

Yep.  For Vim you would issue a command like **:!./scriptname** (assuming you are in the right directory, use the **:cd** command to print the current directory and **:cd <DIR>** to move around.  For emacs I don't know the command but I KNOW you can, you can even open a whole shell inside emacs if you want  to.

---

