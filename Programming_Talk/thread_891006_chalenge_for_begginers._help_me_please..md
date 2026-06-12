---
title: "chalenge for begginers. help me please."
date: 2008-08-15
forum: Programming Talk
---

### Post by Alwex on 2008-08-15
Can someone help me with the following task?
I need to make a little program which can open and, as well close an executable file. for example 1.exe.



and also i need a little function which can disconnect from internet when it is executed.
can u help me please? sorry if bad location for thread but i thought here would me most suitable.

thanks in advance.

p.s. i know only c++ programming. and some php and others. but i dont mind if u can help me to do that with another language.

p.p.s. sorry my bad english.

---

### Post by Alwex on 2008-08-15
please. i need your help. can u? or tell me if it is , by real, an imbossible task?

---

### Post by lisati on 2008-08-15
Hint: A function to open a file, which should work in both C and C++, is fopen(). If you use fopen(), it's good programming manners to use fclose() when you've finished with it.
Hint 2: If you want to learn the name of the progam you're running, look at argv[0]

---

### Post by jimi_hendrix on 2008-08-15
no it is not impossible but i dont know enough to tell you how to do it (it shouldnt be that hard to fingure out though)...try google?

---

### Post by Alasdair on 2008-08-15
This sounds like a good use for some shell script rather than a full blown C++ program, for example if you want to run your program 1.exe for a second before killing it try something like:

[PHP]
#!/bin/sh

#btw: programs in linux usually don't end in .exe
~/1.exe &
sleep 1
killall 1.exe
[/PHP]

To disconnect from the net you can use the ifdown command.

---

### Post by jinksys on 2008-08-15
If you wish to open and close an executable, I would use a shell script.  That is, unless the program you want to run requires root access, like ifdown.  In that case I would write a simple C wrapper that would be setuid.

 WRAPPER CODE IN C
```


#include <stdio.h>
#include <stdlib.h>

int main(){

system("sh myscript.sh");

exit(0);
}

After compiling run:

$ sudo chown root wrapperprogram
$ sudo chmod u+s wrapperprogram


```

You could actually just use the system(...) functions to execute your commands, however using a script is easier since you do not have to recompile your code if your commands change.

```

#!/bin/sh
# Brings network down
ifdown eth0


```

If your commands don't require root access, then  you don't need the wrapper program.  However, if they do require root access you need the wrapper program because you cannot setuid shell scripts.  Be careful though, anything with root access can be very dangerous unless you know what you are doing.

Good Luck!

---

### Post by Alwex on 2008-08-16
Thanks a lot for helping people. now i am not at home but as soon as i get home i will try all posted ideas.

---

### Post by Alwex on 2008-08-16
> **Alasdair said:**
> This sounds like a good use for some shell script rather than a full blown C++ program, for example if you want to run your program 1.exe for a second before killing it try something like:

[PHP]
#!/bin/sh

#btw: programs in linux usually don't end in .exe
~/1.exe &
sleep 1
killall 1.exe
[/PHP]

To disconnect from the net you can use the ifdown command.

shall i only write this in a .php file and run it with an apache server? because if so, like i learnt, it doesn't work...:(

---

### Post by Reiger on 2008-08-16
Let's start the other way: what do you want to do with your .exe?
Run it?
Run it from within a 'master' app?
Read it [in a terminal for instance] ?
Read it in a 'master' app?
Write to it?

---

### Post by jinksys on 2008-08-16
> **Alwex said:**
> shall i only write this in a .php file and run it with an apache server? because if so, like i learnt, it doesn't work...:(

That is a bash script, not PHP code.

---

### Post by Alwex on 2008-08-17
> **Reiger said:**
> Let's start the other way: what do you want to do with your .exe?
Run it?
Run it from within a 'master' app?
Read it [in a terminal for instance] ?
Read it in a 'master' app?
Write to it?

just want a small program which runs it. like a doubleclicked oppening.
for example i want to open and close winamp... just open it.


2. can i create bash from windows? or only linux?

---

### Post by LaRoza on 2008-08-17
> **Alwex said:**
> 
2. can i create bash from windows? or only linux?

What are you trying to ask? bash is a shell and its language. You can write bash scripts in any editor, but you need to run them in bash.

---

### Post by Kadrus on 2008-08-17
[Bash]("http://en.wikipedia.org/wiki/Bash")=Bourne Again Shell

---

### Post by Alwex on 2008-08-17
> **LaRoza said:**
> What are you trying to ask? bash is a shell and its language. You can write bash scripts in any editor, but you need to run them in bash.

bash is like c++ for example?

---

### Post by lisati on 2008-08-17
> **Alwex said:**
> bash is like c++ for example?

I'd say that it's more like what you can type in the terminal, with a few extra "bells ans whistles" (features) thrown in for good measure.

---

### Post by Kadrus on 2008-08-17
> can i create bash from windows? or only linux?
Read the wikipedia article that I linked above,you will see that it is cross platform.
> 
It has also been ported to Microsoft Windows using the POSIX emulation provided by Cygwin, to MS-DOS by the DJGPP project and to Novell NetWare.


---

### Post by LaRoza on 2008-08-17
> **Alwex said:**
> bash is like c++ for example?

Your questions are very vague, and almost meaningless.

Is bash like C++? Well, compared to ducks, elephants are much like horses.

Bash (and shell scripting in general) is interaction (open a terminal) and you can write shell scripts and run them with the terminal.

Here is a shell script I wrote and posted: [http://ubuntuforums.org/showpost.php?p=5535477&postcount=78](http://ubuntuforums.org/showpost.php?p=5535477&postcount=78)

You can run it by following the instructions in the sticky.

---

### Post by Alwex on 2008-08-17
> **LaRoza said:**
> Your questions are very vague, and almost meaningless.

Is bash like C++? Well, compared to ducks, elephants are much like horses.

Bash (and shell scripting in general) is interaction (open a terminal) and you can write shell scripts and run them with the terminal.

Here is a shell script I wrote and posted: [http://ubuntuforums.org/showpost.php?p=5535477&postcount=78](http://ubuntuforums.org/showpost.php?p=5535477&postcount=78)

You can run it by following the instructions in the sticky.

yeah. i understood that is programming language. but, where u write it_ what i need for that script to run. if iwrite a c++ script i need borland c++ . what i need for that kind of language? this is what i havent understood.

---

### Post by LaRoza on 2008-08-17
> **Alwex said:**
> yeah. i understood that is programming language. but, where u write it_ what i need for that script to run. if iwrite a c++ script i need borland c++ . what i need for that kind of language? this is what i havent understood.

There are two broad types of languages, compiled and interpreted.

For C, for example, you would have to write the program out, then compile it. 

```

~/p$cat p.c
#include <stdio.h>

int main(int argc,char ** argv)
{
    puts("Hello world");
    return 0; 
}
~/p$gcc p.c
~/p$./a.out
Hello world
~/p$

```

Contrast that with this bash example (interpreted):

```

~/p$cat p.sh
#!/bin/bash

echo "Hello world";
~/p$./p.sh
Hello world
~/p$

```

The sticky explains what the #! line means and how to do this step by step.

There are interpreters for C also (like tcc), but C isn't usually used that way.

---

### Post by Alwex on 2008-08-18
> **Alasdair said:**
> This sounds like a good use for some shell script rather than a full blown C++ program, for example if you want to run your program 1.exe for a second before killing it try something like:

[PHP]
#!/bin/sh

#btw: programs in linux usually don't end in .exe
~/1.exe &
sleep 1
killall 1.exe
[/PHP]

To disconnect from the net you can use the ifdown command.

ok. now i got the difference.
please can someone make this code work in windows not linux?
i mean to translate it?

---

### Post by LaRoza on 2008-08-18
> **Alwex said:**
> ok. now i got the difference.
please can someone make this code work in windows not linux?
i mean to translate it?

See my wiki. [http://laroza77.wikidot.com/windows](http://laroza77.wikidot.com/windows)

---

### Post by pmasiar on 2008-08-18
> **Alwex said:**
> I need to make a little program which can open and, as well close an executable file. for example 1.exe.

and also i need a little function which can disconnect from internet when it is executed.

Everyone assumed OS is Linux? Or Windows? Which one you need?

---

### Post by Alwex on 2008-08-18
> **pmasiar said:**
> Everyone assumed OS is Linux? Or Windows? Which one you need?

i needed it to run from windows

---

### Post by Alwex on 2008-08-18
> **LaRoza said:**
> See my wiki. [http://laroza77.wikidot.com/windows](http://laroza77.wikidot.com/windows)

links not working... page error 404

---

### Post by pmasiar on 2008-08-18
> **Alwex said:**
> i needed it to run from windows

That's big difference!

All previous advice (with so many thanks) was for Linux, irrelevant to you.

Yo can write simple batch (.BAT file) to run any program. Just enter full path to executable into a .BAT file.


[http://en.wikipedia.org/wiki/Batch_file](http://en.wikipedia.org/wiki/Batch_file)

[http://en.wikipedia.org/wiki/Windows_PowerShell](http://en.wikipedia.org/wiki/Windows_PowerShell)

I am not sure how to disconnect in commandline on Windows - any takers?

---

### Post by Kadrus on 2008-08-18
> links not working... page error 404
It works fine
-------------------
 Windows
Batch

Article

Batch Files

    * Commands (Online Reference)

------------------------
That's its content.

---

### Post by Alwex on 2008-08-18
> **pmasiar said:**
> That's big difference!

All previous advice (with so many thanks) was for Linux, irrelevant to you.

Yo can write simple batch (.BAT file) to run any program. Just enter full path to executable into a .BAT file.


[http://en.wikipedia.org/wiki/Batch_file](http://en.wikipedia.org/wiki/Batch_file)

[http://en.wikipedia.org/wiki/Windows_PowerShell](http://en.wikipedia.org/wiki/Windows_PowerShell)

I am not sure how to disconnect in commandline on Windows - any takers?

yeah. that was why i was soooo confused. i thanked the effort of trying helping me.now... any comands for connecting or disconnecting internet in .bat file?

and is there any randomize function i can use?

or can io make a /bat which opens one which close a proram and run them from a c++ script using system() function?

---

### Post by Mr.Macdonald on 2008-08-18
Please Please use Google translator to read these posts and web sites
[The Translator]("http://translate.google.com/translate_t")
put the forums url in the "Translate a Web Page" bar
remember that the translation will not come perfectly

No offense but your english is where your lacking
aside from installing Ubuntu (recommended) you can do a few things

you should install Bash so lets explain it:
similar to command prompt in linux their is a terminal, this terminal sits in sleep mode until you enter a command such as cd (change current directory), Bash and MSDOS (command prompt) are called shells (spelled like from the sea)

read these sites on bash
[Shells]("http://en.wikipedia.org/wiki/Shell_(computing)")
[Bash]("http://en.wikipedia.org/wiki/Bash")

en espanol, no se su idioma (in spanish) y no se si funcionan
[Shells]("http://es.wikipedia.org/wiki/Shell_(computing)")
[Bash]("http://es.wikipedia.org/wiki/Bash")

to install Bash
[Go Here]("http://www.akadia.com/services/cygwin_tools.html")

this is where you are kind of on your own. I don't know php or anything about the microsoft version of Bash

after you install Bash write this as "netdown.sh"
```
#!/bin/sh
# Brings network down
ifdown eth0
```

save that where you can access it with php
and use
```

exec('bash ./netdown.sh')

```
in php (can someone else check this??)

Good Luck

PS write more in depth questions and explain your problem in a single post an please translate to and from you native language

---

### Post by Alwex on 2008-08-19
> **Mr.Macdonald said:**
> Please Please use Google translator to read these posts and web sites
[The Translator]("http://translate.google.com/translate_t")
put the forums url in the "Translate a Web Page" bar
remember that the translation will not come perfectly

No offense but your english is where your lacking
aside from installing Ubuntu (recommended) you can do a few things

you should install Bash so lets explain it:
similar to command prompt in linux their is a terminal, this terminal sits in sleep mode until you enter a command such as cd (change current directory), Bash and MSDOS (command prompt) are called shells (spelled like from the sea)

to install Bash
[Go Here]("http://www.akadia.com/services/cygwin_tools.html")

this is where you are kind of on your own. I don't know php or anything about the microsoft version of Bash

Good Luck

PS write more in depth questions and explain your problem in a single post an please translate to and from you native language

no problem about english. i know i have a problem with it. But i better understand from english than by google translation. 
my problem is only this: i want to make a program wich opens and closes a .exe file (process) and one who connect or disconnect internet. I only know c++. All this i want to make them run in windows. one friend of mine told me that this is possibile with bash for windows. he onlyy heard about it. iwanted to know:
what i need to install to make bash working?
do i only have to write bash code in notepad and save it with .bat extension?
Can anyone write me a similar code to 
```
 ~/1.exe &
sleep 1
killall 1.exe  
```
which i need to write in WINDOWS and have the same meaning?


or if u have another idee of how can i make that small program, please tell me.

---

### Post by Alwex on 2008-08-21
any ideea? anyone can help me? please...

---

### Post by unca.paka on 2008-08-21
A simple google search of "windows + bash" will get you loads of results. It may just be my understanding, but your not going to have the same level of control in Windows using a bash shell, as you will in a linux shell.

If you already know c++, why not write a program using the windows system calls for networking, running external apps, etc. Not a c++ programmer myself, but I would imagine there are ways to do it.

---

