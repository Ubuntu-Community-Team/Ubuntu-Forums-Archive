---
title: "Learn bash scripting"
date: 2010-05-26
forum: Programming Talk
---

### Post by Drenriza on 2010-05-26
Where is a good place on the web to lern about bash scripting?
How to create bash scripts. And what all the driffent signs mean, and so on.
 
Learning it from the bottom, and then working your way up.
 
Are their any good books i should acquire? 
 
Thanks on advance.
Kind regards.
 
EDIT:
Is their a better "language" ? then bash that does the same as bash but is prehaps more flexiable?
 
I read about it here
> It would be so much simpler to write it in python, and if you use PIL for the image processing, you can end up with a program that you can use in windows and mac too. 
Again, I know your aim here is to learn bash scripting than to find the best way to do this, but I personally find shell too troublesome beyond a certain size.
 
Does this mean Python is better to use for scripts? or am i just walking the wrong path here?

---

### Post by garyedwardjohnston on 2010-05-26
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by mo.reina on 2010-05-26
> **garyedwardjohnston said:**
> [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

another one at tldp.org

[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html")

this is the one i used to learn bash

---

### Post by sfp100 on 2010-05-26
> **Drenriza said:**
> 
Is their a better "language" ? then bash that does the same as bash but is prehaps more flexiable?
 

Depends on the goal --- what you want to do. I use bash for many small jobs, but more exact I should say that I use whole toolbox coming in standard linux command line (sed, AWK, grep, vim and many more) -- for me bash is very convenient 'glue', for example if I wont to convert almost all jpg from directory to PNG format and I want to repeat it in some directiories I can use script like this:
```

#!/bin/sh
ls | awk 'BEGIN{FS="."}; $2~/jpg/ || $2~/JPG/ {print "convert "$0" "$1".png"}' >sk.sh
vim sk.sh
chmod +x sk.sh
./sk.sh

```what it do?

[LIST=1]
[*]listning all files from current directories and gives this list as input for AWK
[*]AWK get "." as field separator => $1 is a name, $2 is a extension (for example jpg)
[*]For all lines, where extension is 'jpg' or 'JPG' I print command converting this to PNG format and write it to file sk.sh
[*]open it file for remove unwanted lines (I want to convert **almost** all files) and add #!/bin/sh on top
[*]add 'executable' permision and execute the script
[/LIST]
**CAUTION**: above is an **example** -- I haven't tested this !!

But for many things I use own C small codes or other methods.

---

### Post by xsinsx on 2010-05-26
BASH is very important to learn. The key is to not get hung up trying to write scripts for everything. I find myself using the BASH utlilties to do everything whenever i need something done. The best way to learn in my opnion is to get in their and learn about the commands and utlilites i.e. VI, PICO, SED, AWK, etc. interactively so you know how they work and when they are used. learning the proper method for the grep command was my first big enlightment when I first started learning. Thats how i learned what I do know from BASH. Also once I felt i was getting a hang of the Command line and such I began reading this and from that day on I just keep plugging. [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) <<< The advanced bash-scripting guide.

---

### Post by Drenriza on 2010-05-27
what is the limitations of bash?

---

### Post by xsinsx on 2010-05-27
Its major limitation are as followed:

[LIST]
[*]It is not a complete language. It does what it does well though.
[*]It is not able to connect to a legion of RDBMS implementations seemlessly with DBI
[*]It can not be used outside of its envirorment meaning it cant be used outside of otehr linux/unix systems impletmenting the bash shell.
[/LIST]there are a few others the biggest thing is overcoming the fact it isnt portable outside of the bash shell whereas python, C++, Perl and such are found more extensivly on windows systems.

---

### Post by Drenriza on 2010-05-28
Okey.

Can the python, C++, Perl work on a linux system, and do the same tasks as bash?

Just curies.

---

### Post by geirha on 2010-05-28
As a beginner, stay away from the bash guides at tldp.org. They teach bad practice and in some parts they're just plain wrong. I recommend

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

---

### Post by xsinsx on 2010-05-28
Yes c++, perl, python are all available and most if not pre-installed are in the repos.

Perl has actually been called and was originally a "replacement" for unix admin who wanted a more general up to date language rather than using bash and awk.

personally Python is my fave of the 3 I listed but for general tasks or automation its easier normally to flush up a bash script.

---

### Post by Klau3 on 2010-05-28
My short favorite: _[[COLOR=#111111][FONT=Arial][SIZE=2]Bash Shell Scripting - 10 Seconds Guide[/SIZE][/FONT][/COLOR]]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html")_
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#222222][FONT=arial] 
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

---

### Post by geirha on 2010-05-28
> **Klau3 said:**
> My short favorite: _[[COLOR=#111111][FONT=Arial][SIZE=2]Bash Shell Scripting - 10 Seconds Guide[/SIZE][/FONT][/COLOR]]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html")_
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#222222][FONT=arial] 
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

The very first snippet in that guide is wrong...
```

echo $IFS | od -bc

```
That will never show what the IFS contains... I wonder if the author even tried executing that code him-/herself.

---

