---
title: "need help with shell script (very basic)"
date: 2007-10-10
forum: Programming Talk
---

### Post by totalnub on 2007-10-10
hey guys i need to make a shell script for a class of mine. here are the requirements:

make a script called lslw, that is executed as ./lslw op, where op is either -w or -l. if op is -l, then the script should output the names of all the files in the current directory sorted in increasing order of the number of lines in the files. if op is -w, then it should output the names of all the files in the directory sorted in increasing order of the number of words in the files.

I really appreaciate the help that you guys give people :)

---

### Post by totalnub on 2007-10-10
anyone out there?

---

### Post by dwhitney67 on 2007-10-11
Any self-respecting programmer is not going to respond to your request for help unless you show that you have put some effort into the exercise yourself.  In other words, let's see what you have written up so far.

---

### Post by Compyx on 2007-10-11
> **totalnub said:**
> hey guys i need to make a shell script for a class of mine. here are the requirements:

<snip homework assignment>

I really appreaciate the help that you guys give people :)

Do your own homework, cheating your way through an education isn't helping anyone. Lazy b*stard

---

### Post by bigboy_pdb on 2007-10-12
The following two web pages would be helpful:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

If you're looking for a command, you can use the command "apropos" to search for keywords in manual pages. For example, "apropos reverse" searches the manual pages for the term reverse. Based on the information that's printed to the screen, you can figure out if one of the commands that were returned might be able to do what you want to do. Then you can look at the man page for that command using "man *command*" (use "q" to exit the man page). Be aware that there might not be a command to do what you want to do and that you'll have to script the whole procedure (or parts of it) using loops and conditional statements.

---

