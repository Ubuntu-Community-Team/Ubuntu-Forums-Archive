---
title: "How to compile bash from an editor?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by tennis_girl on 2008-11-29
Hi,

can someone tell me how to compile bash from a text file like kate?
I mean what is the command in the terminal once I'm in the root?

thanks :)

---

### Post by the yawner on 2008-11-29
Hi. Welcome to the forums. :)
I am a bit confused over your question. Do you mean to compile a program from the source code? Kindly elaborate.

---

### Post by sujoy on 2008-11-29
normally to compile bash, you would use 
configure
make
make install

however if you want to compile your own program then (considering it is in c),

gcc /path/to/source/file -o output_file_name

other switches maybe applied as and when needed

---

### Post by __Ryan__ on 2008-11-29
If you are talking about BASH script itself, you can't compile it like like you would with a language such as C/C++.  The reason for this is that it is interpreted language which gets translated into machine code at runtime.

---

### Post by theozzlives on 2008-11-29
.bashrc is a text file that tells bash how to look and behave.

---

### Post by tennis_girl on 2008-11-29
I mean I wrote some bash scripts in a text file
#!/bin/bash
case ...

..
and saved the file as .sh
I'm looking for the comand line to comile my .sh file?
thanks for your welcome message btw :)

---

### Post by PmDematagoda on 2008-11-29
> **tennis_girl said:**
> I mean I wrote some bash scripts in a text file
#!/bin/bash
case ...

..
and saved the file as .sh
I'm looking for the comand line to comile my .sh file?
thanks for your welcome message btw :)

You can't compile shell scripts. You can execute them by doing:-
```
./*name-of-script*.sh
```
you may first want to make them executable with:-
```
chmod +x *name-of-script*.sh
```

---

### Post by tennis_girl on 2008-11-29
I would like to compile a .sh file(bash shell file)

---

### Post by __Ryan__ on 2008-11-29
You don't compile BASH script it is an interpreted language.  You can execute it on the command line.  You need to change it to be an executable before you run it which might be what you are asking.

To do this, if the file is called **script.sh**

```
chmod 755 script.sh
```

The text file is now executable.

I'm hoping this answers your question.

---

### Post by kevdog on 2008-11-29
Last time on this one:

bash shell scripts are interpreted not compiled -- hence there is no reason to compile them.

If you want a personal .bash or .sh file, compose the file, save it, do the following:

chmod +x <xxxxx.sh>

Copy the file to your personal bin directory since this is in your path (you have to make the directory since its not included by default):
mkdir -p ~/bin

cp <shell_script_file.sh> ~/bin/<shell_script_file.sh>

Ok now you can run the shell script from the command line by simply typing

<shell_script_file.sh>

NO NEED TO COMPILE!!!

---

### Post by tennis_girl on 2008-11-29
> **PmDematagoda said:**
> You can't compile shell scripts. You can execute them by doing:-
```
./*name-of-script*.sh
```
you may first want to make them executable with:-
```
chmod +x *name-of-script*.sh
```

thanks for your message, that's what I was looking for :)
and it works ;)

---

### Post by mr han on 2013-01-29
> **tennis_girl said:**
> thanks for your message, that's what I was looking for :)
and it works ;)


why you not use SH Compiler like "SHC"

you just need to do "shc -f file.sh" then you will get 2 file "file.sh.c" & "file.sh.c.x" 

you can use file.sh.c as executor, you just need to double click on the icon of "file.sh.c"

may can help you...:lolflag:

---

### Post by nothingspecial on 2013-01-29
please don't bump old threads to the top.

Closed.

---

