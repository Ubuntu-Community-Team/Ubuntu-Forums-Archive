---
title: "Problems with Terminal"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Starcruiser322 on 2012-04-01
I recently installed Ubuntu and immediately got to learning what I could, and was downloading apps and using terminal to install them in no time.
Recently, whenever I enter a command into Terminal (i.e. cd /home) all that is shown on the next line is ">". No current directory information or anything. Also, if executing code that involves an output, I still only see ">".
I have been installing a few new apps, as it is a fresh install of Linux. I suspect problems with Wine, but I'm obviously no expert. 
It was working fine before, any ideas what caused this? If you need a list of my recently installed apps, I can post it.

Update: I got it to work, somehow, with some directories again. I am having this problem still with /home/nick/_PlayOnLinux's virtual drives_/rosettastone/drive_c
The underlined is where the problem starts. Possibly an unsupported file system? I really need to find a hidden folder in that directory that doesn't display even when show hidden and backup files is checked.
I already tried changing permissions, that didn't change anything. After the chmod command, I still got ">".

---

### Post by oldos2er on 2012-04-02
Did you change your .bashrc? It's a hidden file in your home folder, and among other things it controls the way your prompt appears.

---

### Post by Paddy Landau on 2012-04-02
When you type a multi-line command, by default subsequent lines begin with ">". 

This means you have somehow started to type a command that is not finished.

There are two ways to do that; either end the command with a backslash (this indicates that there is more to come), or start a quote -- either single (') or double (").

Examples (my typing in black and [COLOR=Red]red[/COLOR], the computer's entry in [COLOR=Navy]**blue**[/COLOR]):
```
**[COLOR=Navy]$[/COLOR]** ls --group-directories-first **[COLOR=Red]\[/COLOR]**
**[COLOR=Navy]>[/COLOR]** --almost-all
[COLOR=Navy]**.abe**[/COLOR] *(etc.)*

[COLOR=Navy]**$**[/COLOR] echo **[COLOR=Red]"[/COLOR]**I have started with a quote, but
[COLOR=Navy]**>**[/COLOR] finished on line 2.**[COLOR=Red]"[/COLOR]**
[COLOR=Navy][B]I have started with a quote, but
finished on line 2.[/B][/COLOR]

[COLOR=Navy]**$**[/COLOR] echo **[COLOR=Red]'[/COLOR]**I have again started with a quote, but
[COLOR=Navy]**>**[/COLOR] finished on line 2.**[COLOR=Red]'[/COLOR]**
[COLOR=Navy][B]I have again started with a quote, but
finished on line 2.[/B][/COLOR]

**$** ls -lA ~/PlayOnLinux[COLOR=Red]**'**[/COLOR]s virtual drives/rosettastone/drive_c
[COLOR=Navy]**>**[/COLOR] [FONT=Verdana]*Oops, there is a quotation mark on the previous line and Linux is waiting for me to finish!*[/FONT]
```When you need to include a quotation mark in a line, you need to tell Linux that it is not the start of a quotation but to be used literally. There are two ways: (1) include it in a different type of quotation mark, or (2) use the backslash.

The following are valid examples to do what you want.
```
ls [COLOR=Red]"[/COLOR]/home/nick/PlayOnLinux's virtual drives/rosettastone/drive_c[COLOR=Red]"[/COLOR]
ls [COLOR=Red]"[/COLOR]${USER}/PlayOnLinux's virtual drives/rosettastone/drive_c[COLOR=Red]"[/COLOR]
ls ~/[COLOR=Red]"[/COLOR]PlayOnLinux's virtual drives[COLOR=Red]"[/COLOR]/rosettastone/drive_c
ls ~/PlayOnLinux[COLOR=Red]\[/COLOR]'s[COLOR=Red]\[/COLOR] virtual[COLOR=Red]\[/COLOR] drives/rosettastone/drive_c
```In the first example, you cannot use "~" because the surrounding quotes would prevent Bash from interpreting it. However, you can use environment variables (e.g. ${USER}) within double quotes (but not within single quotes).

In the last example, I have used backslash to tell Linux not to interpret the single quote or the spaces (otherwise the spaces would be interpreted as ending one argument and beginning another).

I hope you understand what happened.

Now for something cool. Try typing the following, where [COLOR=Red]*[tab]*[/COLOR] means that you press the Tab key:
```
ls ~/Pla[COLOR=Red]*[tab]*[/COLOR]/ros[COLOR=Red]*[tab]*[/COLOR]/dr[COLOR=Red]*[tab]*[/COLOR]
```Did you notice what happened?

By the way, if you start a second line accidentally, press Ctrl-C to cancel it.

---

