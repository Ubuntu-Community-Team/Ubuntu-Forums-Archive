---
title: "Question to wildcards"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by hovzio on 2008-11-24
Hi, when I apply certain wildcards in a script, (as well as the prompt) I am getting unexpected results. 
For the most part I'm pretty comfortable with wildcards, nevertheless some things are (all of the sudden:) 
not making sense. Bellow I am trying to specify all files/directories within the current directory that start with 
a captital letter.
I enter:

~:$  ls [A-Z]*
a
b
C
or:

~:$  echo [A-Z]*
a b C

With grep (RE) it works:

~:$  ls | grep '\b[A-Z].*'
C

I was expecting ls/echo to output only directories starting with a Capital letter followed by andthing. "*"
Instead it just outputs the entire contents of the current directory, including the Directories that are 
lower case. Defining case size, in any character class within brackets, [a-z],[A-Z], doesn't seem to work 
properly.

I recently delved into regex and extended regex and I was thinking I may be seriously getting things 
mixed up. (probably am...) For the most part globbing is working fine, just; its ignoring the case of
the defined character class.. I came upon this problem while writing a little practice script. Since, I've 
solved the issue within the script with: ls | grep '\b[A-Z].*'. Nevertheless I still want to know what
I'm doing wrong. All the books I have here emphasize the usage of [A-Z] while using wildcards??I've also 
checked the shell builtins and as far as I can tell everything is set up correctly, default. Appreciate 
any help, thanks in advance.

---

### Post by cmnorton on 2008-11-24
If you are coming from Windows, there is a lot to learn about wildcards. 

New users can get tripped up on using wildcards to interpret file names that have a dot in them and also expecting that copying or moving will behave like xcopy. If you copy somehing and expect its output to expand by using an asterisk, it won't work the way you expect. Hence, the need to work with shell scripts. 

I would search these forums for terms like bash wildcards and globbing. In addition, here are some links. IBM's developer works site is very good.

[http://www.ibm.com/developerworks/library/l-bash2.html](http://www.ibm.com/developerworks/library/l-bash2.html)
[http://www.tuxfiles.org/linuxhelp/wildcards.html](http://www.tuxfiles.org/linuxhelp/wildcards.html)
[http://www.faqs.org/docs/abs/HTML/subshells.html](http://www.faqs.org/docs/abs/HTML/subshells.html)

---

### Post by glennric on 2008-11-24
If you type
```
ls REGEXP
```
this will list all files and directories including contents that match the given REGEXP.
If you don't want it to list directory contents you need to type
```
ls -d REGEXP
```
So for your example type
```
ls -d [A-Z]*
```

---

### Post by glennric on 2008-11-24
Sorry, I missed the part about the lower case versus capital letter issue.  I am not sure why ls does that.

---

### Post by Sand Lee on 2008-11-24
```
ls [[:upper:]]*
```

[http://linuxcommand.org/lts0050.php#wildcards](http://linuxcommand.org/lts0050.php#wildcards)

---

### Post by hovzio on 2008-11-25
> **Sand Lee said:**
> ```
ls [[:upper:]]*
```

[http://linuxcommand.org/lts0050.php#wildcards](http://linuxcommand.org/lts0050.php#wildcards)

Hi, thanks, I was aware of this solution, what if I want to use; [A-C]. Then I cannot use the "upper, lower, digit.. " solution. I've been reading about "language locales" , could this be the problem. Thanks for all the help.

---

### Post by Sand Lee on 2008-11-25
I am not sure, but locales aren't the problem - I'm in the US, and have the same "problem" as you do. I put problem in quotes, because after running: ls [A-Z] in a directory containing a file "c," c shows up in the output. but no multi-letter filename is printed. I haven't read about ls [A-Z], but from what I see so far, it looks like it just prints any file with a letter nambe between A and Z. Having an asterik after it will just include any file that starts with an alpha character.

---

### Post by hovzio on 2008-11-25
Hi, well I haven't stumbled on an answer yet. Very interesting indeed is that I tried the same at a friends pc, (suse) and it worked fine there. (Also seems to work fine on a centos.) Is this problem Ubuntu specific? I have two laptops running Hardy and bash acts the same on both. I know there are several workarounds including piping stdin to grep etc. Nevertheless, it would be nice to understand whats wrong since I'm seemingly sure that it worked fine in gutsy. Thanks

---

### Post by hovzio on 2008-12-06
Hi! I found a solution. (It works for me at least) I found the answer in:   "Classic Shell Scripting" Authors: Arnold Robbins & Nelson H. F. Beebe, pg. 153, Oreilly. Here it basically states that the behavior of wildcards is in some cases dependent upon the locales. It suggests that "unix traditionalists can use export LC_ALL=C to get behavior they are used to."

so, while in a term. emulator;

```
export LC_ALL=C

```
 
It works, (of course only for the current session) as I understand the LC_ALL variable overrides all other LC_* vars. Now to my question, in which file do I export LC_ALL=C to? I am not quite sure as to how this may impact the rest of the system. 

Is it alright to export LC_ALL=C in a script, are subshells in any way affected? How?

I would like globbing to work properly while using a standard terminal emulator; I am guessing its alright to put it in my ~/.bashrc file, Is it?? Or will this in have some negative affect, is it alright to globally apply it? I'm assuming its better not placed in ~/.profile, but am altogether uncertain.

I guess what I'm saying is that I don't thoroughly understand the solution. Is it ok to export this variable and in which startup file is it best placed? Thanks :p

---

