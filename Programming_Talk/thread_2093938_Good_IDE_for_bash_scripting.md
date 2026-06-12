---
title: "Good IDE for bash scripting"
date: 2012-12-12
forum: Programming Talk
---

### Post by CaptainMark on 2012-12-12
I'm trying to find a decent ide to use with bash scripting, it seems a lot of the top ides kind of overlook bash, I'm using geany but I would like one that has support for collapsing and expanding various sections of script like it does with python, for example collapse an IF statement so its out of the way to make long code more manageable, I would also like to find one if possible that can run your script from a single click button with a more verbosive output (like running `bash -x /path/to/script` in a terminal) if tried tweaking geany to use the bash -x flag and it doesn't seem to work.

Any recommendations?

Thank you
Mark

---

### Post by Abhinav Kumar on 2012-12-12
> **CaptainMark said:**
> I'm trying to find a decent ide to use with bash scripting, it seems a lot of the top ides kind of overlook bash, I'm using geany but I would like one that has support for collapsing and expanding various sections of script like it does with python, for example collapse an IF statement so its out of the way to make long code more manageable, I would also like to find one if possible that can run your script from a single click button with a more verbosive output (like running `bash -x /path/to/script` in a terminal) if tried tweaking geany to use the bash -x flag and it doesn't seem to work.

Any recommendations?

Thank you
Mark
Hi CaptainMark,
In my knowledge, there is no IDE for shell scripting. However, there are plugins which can be used in the combination of text-editor. 

[http://www.linuxquestions.org/questions/linux-software-2/ide-for-bash-shell-programming-797620/](http://www.linuxquestions.org/questions/linux-software-2/ide-for-bash-shell-programming-797620/)

Regards,
Abhinav

---

### Post by drmrgd on 2012-12-12
You might have to go with a DIY IDE, which is basically something like Gedit or Kate to do the scripting (I use Kubuntu, which has Kate by default and there are a lot of the features you describe like collapsing code blocks and you can even open a mini term window at the bottom of it), and a terminal window alongside where you can test out the scripts.  

Also, when I'm developing a piece of code and need some debugging, I usually add the line 'set -x' at the top of the script so that I don't have to explicitly declare it each time I run the script.  Then when I'm satisfied, I just remove the line (or comment it out for short term use).  

It's not an all in one.  But two windows side by side is still pretty convenient to me.

---

### Post by CaptainMark on 2012-12-12
> **drmrgd said:**
> I usually add the line 'set -x' at the top of the script so that I don't have to explicitly declare it each time I run the script.  Then when I'm satisfied, I just remove the line (or comment it out for short term use).I didn't now about this, I'll use that one, thanks
I'll also investigate some plugins,

---

### Post by ofnuts on 2012-12-13
> **CaptainMark said:**
> I'm trying to find a decent ide to use with bash scripting, it seems a lot of the top ides kind of overlook bash, I'm using geany but I would like one that has support for collapsing and expanding various sections of script like it does with python, for example collapse an IF statement so its out of the way to make long code more manageable, I would also like to find one if possible that can run your script from a single click button with a more verbosive output (like running `bash -x /path/to/script` in a terminal) if tried tweaking geany to use the bash -x flag and it doesn't seem to work.

Any recommendations?

Thank you
MarkKate (the editor that comes with KDE) will expand/collapse code sections and do syntax highlighting for shell scripts. And you can have part of the window as a terminal session to test out things...

---

### Post by mbnoimi on 2013-05-22
> **ofnuts said:**
> Kate (the editor that comes with KDE) will expand/collapse code sections and do syntax highlighting for shell scripts. And you can have part of the window as a terminal session to test out things...

I'm looking for same thing, I used Kate but it's not suitable because I'm looking for one with auto-complete just like Qt Creator or eclipse.

PS
Kate supports auto complete but it works inside file scope, I want full featured auto completion just like usual IDEs

---

### Post by mbnoimi on 2013-05-28
Bump

---

### Post by alan9800 on 2013-05-29
you might be interested in the "code folding" feature of code::blocks:
[http://www.codeblocks.org/docs/main_codeblocks_en3.html#x3-310001.11.10](http://www.codeblocks.org/docs/main_codeblocks_en3.html#x3-310001.11.10)

---

### Post by Drenriza on 2013-05-29
> **CaptainMark said:**
> I'm trying to find a decent ide to use with bash scripting, it seems a lot of the top ides kind of overlook bash, I'm using geany but I would like one that has support for collapsing and expanding various sections of script like it does with python, for example collapse an IF statement so its out of the way to make long code more manageable, I would also like to find one if possible that can run your script from a single click button with a more verbosive output (like running `bash -x /path/to/script` in a terminal) if tried tweaking geany to use the bash -x flag and it doesn't seem to work.

Any recommendations?

Thank you
Mark

I do a good amount of Bash scripting, where i purely use the CLI and Vim (or Emacs for those who uses that).
On my MacBook Pro i use Iterm2 and on my home Ubuntu 12.04 machine i just use the terminal.

And i doubt how usefull a auto-complete feature would be with Bash if i'am to be honest.

Though i use IDE's for object orientated programming, such as C# / Java.

---

### Post by mbnoimi on 2013-05-29
>  you might be interested in the "code folding" feature of code::blocks:
I consider Kate one of the best code editors and it has "Auto brackets" feature which is somehow alternative to "code folding". Any way, this is not what I asked for.

I'm looking for any software has full featured auto completion for bash scripting just like usual IDEs

---

### Post by mbnoimi on 2013-05-29
> And i doubt how usefull a auto-complete feature would be with Bash
Using full featured auto-complete option make writing the script so quick, neat and easy to remember. Because it lists the variable you've created and default variables, the default templates you want to use (ex. if statement), functions you've created and the default available functions... etc (all that available in traditional IDE such as Qt Creator and eclipse)

---

### Post by alan9800 on 2013-05-29
> **mbnoimi said:**
> I'm looking for any software has full featured auto completion for bash scripting just like usual IDEsauto completion is available in Code::Blocks:
[1.11.11  Auto complete](http://www.codeblocks.org/docs/main_codeblocks_en3.html#x3-320001.11.11)

---

### Post by mbnoimi on 2013-05-29
> auto completion is available in Code::Blocks:
As far as I know it works just like kate so it works under file scope only (for example: it can't run auto complete for date function)

---

### Post by rnPTKDb on 2013-12-01
This Eclipse Plugin seems to work after a bit of configuration: [http://ubuntuforums.org/showthread.php?t=1535014](http://ubuntuforums.org/showthread.php?t=1535014)
See User Guide: [http://sourceforge.net/apps/trac/shelled/wiki/Documentation/UserGuide](http://sourceforge.net/apps/trac/shelled/wiki/Documentation/UserGuide)

Needs Eclipse 4.2.x (Juno) or 4.3.x (Kepler), shows man page output on mouse hover on each word - which I find the most useful feature.

---

### Post by PaulEdwards on 2014-05-29
You could try [Griffon]("http://griffon.lasotel.fr/en/") which is an IDE specifically designed for BASH scripting. Its features include autocomplete, syntax highlighting, error detection, and more.

---

