---
title: "Reasons to get familiar with the Terminal"
date: 2009-12-15
forum: Recurring Discussions
---

### Post by The_Pirate_King on 2009-12-15
While you don't absolutely need to use the terminal if you don't want to, there are a lot of very good reasons to do so.  I am pretty much a noob to Ubuntu, but nonetheless I really like using the terminal. 

1. You will learn more about computers this way than any other.  
2. If you learn the terminal well in one Linux/Unix operating system, the same commands often apply to others, and some of the commands or at least the general concepts will be useful in a windows environment as well. 
3. For certain tasks, I find the terminal to be far faster.  For example, if you want to navigate to a directory, it's a simple one-line command.  You can even create multiple folders within a directory with the mkdir command, which is something that would take you many clicks and right clicks to do with the GUI. 
4. Reliability.  The terminal will almost always work to get what you want done, even if your GUI is broken. 
5. When you make a mistake in the terminal, it will often give you an error message that tells you about what went wrong, or what you need to do differently.  In the GUI, you can spend tons of time searching aimlessly for a program or feature and making little progress. 
6. If you're a fast typer, you'll be able to do things faster than ever. 
7. The terminal is not as scary as it seems.  In fact, it is very intuitive once you put the time into learning different commands.  

Try it out, familiarize yourself with the basics, and you'll find it to be an extremely powerful tool.

---

### Post by ankspo71 on 2009-12-15
> **The_Pirate_King said:**
>   I am pretty much a noob to Ubuntu, but nonetheless I really like using the terminal. 


Me too. Good post.:D

---

### Post by Diametric on 2009-12-15
I like this post and find it critical if you're going to be a Linux user.  However, one thing I have found somewhat frustrating is how some of the commands change.  I am currently working through a redhat9 book while on and Ubuntu system and did not anticipate how many commands and PATH issue would be different.  My own fault to be sure, and it has forced me to be inquisitive and therefor learn more...I just thought it would be a bit more standardized.  Yes.  Learn the console.  Do it or Kaiser Soze will come and get you!

---

### Post by The_Pirate_King on 2009-12-15
Commands changing is a bit annoying... but the general construct doesn't change, right?  The majority of them stay the same?  In comparison with a GUI interface, which changes constantly.

---

### Post by lotharmat on 2009-12-15
> **The_Pirate_King said:**
> While you don't absolutely need to use the terminal if you don't want to, there are a lot of very good reasons to do so.  I am pretty much a noob to Ubuntu, but nonetheless I really like using the terminal. 

1. You will learn more about computers this way than any other.  
2. If you learn the terminal well in one Linux/Unix operating system, the same commands often apply to others, and some of the commands or at least the general concepts will be useful in a windows environment as well. 
3. For certain tasks, I find the terminal to be far faster.  For example, if you want to navigate to a directory, it's a simple one-line command.  You can even create multiple folders within a directory with the mkdir command, which is something that would take you many clicks and right clicks to do with the GUI. 
4. Reliability.  The terminal will almost always work to get what you want done, even if your GUI is broken. 
5. When you make a mistake in the terminal, it will often give you an error message that tells you about what went wrong, or what you need to do differently.  In the GUI, you can spend tons of time searching aimlessly for a program or feature and making little progress. 
6. If you're a fast typer, you'll be able to do things faster than ever. 
7. The terminal is not as scary as it seems.  In fact, it is very intuitive once you put the time into learning different commands.  

Try it out, familiarize yourself with the basics, and you'll find it to be an extremely powerful tool.

+1 Terminal FTW

---

### Post by Cuco3 on 2009-12-15
Good post. I'd like to add that it's easier to view and install software via the terminal than synaptics or add/remove programs.

to update your repository and install updates for Ubuntu or programs
```
sudo apt-get update && sudo apt-get upgrade
```To search for programs
```
aptitude search <yoursearchstring>
```And ofcourse...
```
sudo apt-get install <programname>

or

sudo apt-get remove <programname>
```If you add aliases to your .bashrc file, you can automate a lot of the commands.

---

### Post by amauk on 2009-12-15
nice post

You missed the two big ones, though

**Pipes** - Ability to chain commands together.
output of one program is fed into the input of another, and so on
makes the CLI environment very efficient, with the ability to perform quite complex operations by chaining lots of simple tasks together

**Script-ability** - Flow control and automation.
Following on from pipes, CLI shells give you the ability to dictate complex flow controls, which can be automated into scripts that act as a single program

---

### Post by Cuco3 on 2009-12-15
> **amauk said:**
> nice post

You missed the two big ones, though

**Pipes** - Ability to chain commands together.
output of one program is fed into the input of another, and so on
makes the CLI environment very efficient, with the ability to perform quite complex operations by chaining lots of simple tasks together

**Script-ability** - Flow control and automation.
Following on from pipes, CLI shells give you the ability to dictate complex flow controls, which can be automated into scripts that act as a single programCan you give some examples that would demonstrate what you mean, please? I'm dying to learn more about the terminal.

---

### Post by slakkie on 2009-12-15
> **The_Pirate_King said:**
> Commands changing is a bit annoying... but the general construct doesn't change, right?  The majority of them stay the same?  In comparison with a GUI interface, which changes constantly.

What commands are changing? I haven't noticed any (big) changes on the cli tools I use daily.

The only anoying factor regarding the cli is using it on Solaris/Debian/FreeBSD where different tools are used, GNU tar, Solaris tar, ps, snoop/tcpdump, and writing scripts which work on all of these platforms.

---

### Post by sisco311 on 2009-12-15
> **Cuco3 said:**
> Can you give some examples that would demonstrate what you mean, please? I'm dying to learn more about the terminal.

```
man bash | less --pattern\= "Pipelines"
```
:evil:

---

### Post by northern lights on 2009-12-15
> **Diametric said:**
> However, one thing I have found somewhat frustrating is how some of the commands change.  I am currently working through a redhat9 book while on and Ubuntu system and did not anticipate how many commands and PATH issue would be different.
While the package management tools differ from RedHat to Ubuntu/Debian, both systems ship with *bash* as the default shell. Hence the native bash commands are without exception the same. These are two very good reads:
[Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")
[BASH programming howto]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

> **Cuco3 said:**
> Can you give some examples that would demonstrate what you mean, please? I'm dying to learn more about the terminal.
| is a pipe. Pipes let you use the output of a program as the input of another one.Run```
ls -a | grep .gnu
```from within your home folder - pipes are very intuitive.

---

### Post by Cuco3 on 2009-12-15
Thanks northernlights & sisco311

I have a better understanding of what pipelines do now and how they help out administrators and power users. Very interesting stuff.

Anybody else have other interesting examples that show the power of pipelines?

---

### Post by Tibuda on 2009-12-15
> **Cuco3 said:**
> Thanks northernlights & sisco311

I have a better understanding of what pipelines do now and how they help out administrators and power users. Very interesting stuff.

Anybody else have other interesting examples that show the power of pipelines?

This lists all your local folder bookmarks:
```
grep '^file://' ~/.gtk-bookmarks | cut -d' ' -f1 | sed 's|^file:/\+|/|'
```

This lists the last 10 files used by OpenOffice:
```
grep '<URI>file://' ~/.recently-used | head -n10 | sed -r 's|<URI>file://(.*)</URI>|\1|g'
```

I use them in scripts to generate [Openbox pipemenus]("http://icculus.org/openbox/index.php/Openbox:Pipemenus").

---

