---
title: "Cant create a shortcut to .sh file"
date: 2018-09-25
forum: New to Ubuntu
---

### Post by yairbar on 2018-09-25
I made a small .sh file. 
I can run it from the terminal with ./NAME_OF_FILE.sh

i did the "edit>prefrenaces>behavior tab>ask each time", so then when i double click and select run nothing happens.

i tried creating a .desktop file but it didnt work as well.

also i gave executable permissions.

why cant i run the sh scrit out of the terminal? ideas? help?

thanks for reading :)

---

### Post by ajgreeny on 2018-09-25
What is the script for; show us the text it contains.

Does it run as user or do you need root permissions, ie does it require **sudo** to run?

---

### Post by Impavidus on 2018-09-25
I assume your .sh file is a shell script. You can run it in a terminal, so there's no permissions issue. The script file has execute permissions. But have you though about it that, when you start the script from the file manager, it doesn't automatically open a terminal window for the script? You can configure it to open a terminal, or use a .desktop file for that. Without a terminal, the script will run, but will have no place to read standard input or write standard output/standard error. If the script doesn't need those streams, that's fine, but the only way to see that the scipt works will be via its side effects or file I/O.

If you don't mind showing us the contents of the script, we may be able to find a solution.

---

### Post by yairbar on 2018-09-26
Hi thank you, its a very short shell script that cd's to a dir and then executes a program.
i tried setting the 'terminal' field to 'true', that didnt help.

turns out i had to add "bash -i" to the 'command' field in the .desktop file.
i think its because the sh script would run and then terminate by the end of the file, and by setting "bash -i" the shell became interactive, which is essentially just a normal shell like the ones that you get when you manually open a terminal... 

here you go:
[http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html)

thank you guys for responding :D

---

