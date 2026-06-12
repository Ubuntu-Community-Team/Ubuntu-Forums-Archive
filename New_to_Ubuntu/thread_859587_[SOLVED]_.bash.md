---
title: "[SOLVED] .bash"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Toliot on 2008-07-14
hey,
im trying to make a bash script
so i made my file .bash
but how do i run it?:confused:
i made it in open office and saved it as .bash will that work?

thx, in advance:)

---

### Post by DGortze380 on 2008-07-14
it probably won't work.

you should use a text editor that does not save any formatting (I believe you can do this in openoffice, but you need to specify, a .odt or .doc won't work).

try Accessories>Text Editor (the program is gedit)
or a command line editor like vim ( [http://www.fprintf.net/vimCheatSheet.html](http://www.fprintf.net/vimCheatSheet.html) )

The commonly accepted extension for scripts is .sh  (but it won't really effect anything)

to run it, open a terminal, navigate to the directory 
chmod 700 nameOfMyScript
./nameOfMyScript

side note, be sure your script starts with the line below or it won't work.
#!/bin/bash

---

### Post by braddcadd on 2008-07-14
These links helped me write my first bash script:
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
[http://floppix.ccai.com/scripts1.html](http://floppix.ccai.com/scripts1.html)

Enjoy.

---

### Post by Toliot on 2008-07-14
> **DGortze380 said:**
> it probably won't work.

you should use a text editor that does not save any formatting (I believe you can do this in openoffice, but you need to specify, a .odt or .doc won't work).

try Accessories>Text Editor (the program is gedit)
or a command line editor like vim ( [http://www.fprintf.net/vimCheatSheet.html](http://www.fprintf.net/vimCheatSheet.html) )

The commonly accepted extension for scripts is .sh  (but it won't really effect anything)

to run it, open a terminal, navigate to the directory 
chmod 700 nameOfMyScript
./nameOfMyScript

side note, be sure your script starts with the line below or it won't work.
#!/bin/bash

thx, i made the extension .sh
but when i try to run it threw terminal
./hello.sh i get the error "bash: ./hello.sh: Permission denied"
how to fix?:confused:
thx in advance

---

### Post by DGortze380 on 2008-07-14
> **Toliot said:**
> thx, i made the extension .sh
but when i try to run it threw terminal
./hello.sh i get the error "bash: ./hello.sh: Permission denied"
how to fix?:confused:
thx in advance

You need to change the permissions first.

chmod 700 nameOfMyScript

---

### Post by Toliot on 2008-07-14
> **DGortze380 said:**
> You need to change the permissions first.

chmod 700 nameOfMyScript

how do i change the permissions :P?
sry im a complete linux newbie :(

---

### Post by Claus7 on 2008-07-14
Hello,

I would advise you not to name your scripts putting a dot in front of their names. And don't call them bash! Because you might end up with unwilling results.

Create a new script with a text editor. Save it and change its permissions as told (I prefer 755, yet 700 will fit your needs). This presuposes that you would have navigated to the folder you have created the script. Then run it as told. It should work.

EDIT: Let's say that your script's name is hello.sh and it is located in Desktop. Open a terminal from Applications -> System Tools -> Terminal and type there cd Desktop
Then type chmod 755 hello.sh
And then run the script as ./hello.sh

Regards!

---

### Post by Toliot on 2008-07-14
> **Claus7 said:**
> Hello,

I would advise you not to name your scripts putting a dot in front of their names. And don't call them bash! Because you might end up with unwilling results.

Create a new script with a text editor. Save it and change its permissions as told (I prefer 755, yet 700 will fit your needs). This presuposes that you would have navigated to the folder you have created the script. Then run it as told. It should work.

EDIT: Let's say that your script's name is hello.sh and it is located in Desktop. Open a terminal from Applications -> System Tools -> Terminal and type there cd Desktop
Then type chmod 755 hello.sh
And then run the script as ./hello.sh

Regards!

i got it to work so putting a dot infront of it makes the file hidden?
ill do that thx alot :)

---

### Post by Claus7 on 2008-07-14
> **Toliot said:**
> i got it to work so putting a dot infront of it makes the file hidden?
ill do that thx alot :)

Yeap, exactly. And not only that, yet you might mess it with hidden files that they are system default ones. Nice that you made it working.

Regards!

---

### Post by elmoosecapitan on 2008-07-14
Here are a couple suggestions:

1. Open Office works well for editing text but I personally prefer xemacs (or emacs) because of the syntax highlighting. The easiest way to get xemacs is by typing in a terminal:
```
$ sudo apt-get install xemacs
```
In which you will be prompted for your root (super-user/master) password. To run xemacs type in a terminal:
```
$ xemacs
```
or if you want to edit a file type:
```
$ xemacs ~/filepath/filename
```
Just remember that "C-" is simply 'ctrl', e.g., C-x C-f is ctrl+x ctrl+f.
Playing with options will allow you to have syntax highlighting.


2. Adding '#!/bin/scriptlanguage' as the very first line helps with compiling and error checking. Example: #!/bin/tcsh or  #!/bin/bash


3. To run a program type:

$ ```
compilername ~/filepath/filename
```

For example:

```
$ python ~/Desktop/help.py
```

or 

```
$ bash ~/Documents/Work/shuffle.bash
```


3.1 An alternative method is giving yourself execute permission for your specific file. So add permission(s) then execute:

```
$ chmod u+x ~/filepath/filename
$ ~/filepath/filename
```

Example:

```
$ chmod u+x ~/Desktop/help.py
$ ~/Desktop/help.py
```


To check if owner, group, user, or everyone already has read/write/execute permission type:

```
$ ls -l ~/pathfile/
```
and you should see something like:

-rw-r--r-- 1 richard richard    74572 2008-06-11 11:28 Physics of Falling EB114TS.jpg
-rw-r--r-- 1 richard richard      377 2008-07-03 13:44 refresh.html~
-rwx------ 1 richard richard    18002 2008-06-09 21:29 Schedule Fall 2008.ods
-rw-r--r-- 1 richard richard    21360 2008-06-26 10:03 schedule.ods

In which 'r' means read, 'w' means write, 'x' means execute, 'd' means directory. The hierarchy is Owner/User/Group, which means that the owner of Schedule_Fall_2008.ods has read/write/execute permission, where as the user 'richard' has read privileges, and group users have the same abilities as the user 'richard'.




good luck.


cheers

---

