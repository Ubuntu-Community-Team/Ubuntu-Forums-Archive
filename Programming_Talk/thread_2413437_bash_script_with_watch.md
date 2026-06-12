---
title: "bash script with watch"
date: 2019-02-25
forum: Programming Talk
---

### Post by jduns on 2019-02-25
I made this script: ```
 watch -n 3600 -x play /mnt/musica/login.wav && zenity --info --text="<span size=\"xx-large\">Time is $(date +%Hh%M).</span>\n\nricordati di <b>bere</b>." --title="drink time" 
```
but it's not working. I tred also | instead of &&.
Saved as "sometitle.bash" (obviously executable).
What is wrong?
Thank you

---

### Post by TheFu on 2019-02-25
Did you run it in bash debug mode?

---

### Post by freemedia2018 on 2019-02-25
I've tried several different options, trying to get watch to run leafpad more than once:

```
watch -d 5 $(leafpad &)
```

I don't think this is really what watch is for, though I've read claims it can do this.

```
while [[ 1 ]] ; do sleep 3600 ; play /mnt/musica/login.wav && zenity --info --text="<span size=\"xx-large\">Time is $(date +%Hh%M).</span>\n\nricordati di <b>bere</b>." --title="drink time" ; done
```

You might have more luck with that.

---

### Post by jduns on 2019-02-26
> **freemedia2018 said:**
>  

```
while [[ 1 ]] ; do sleep 3600 ; play /mnt/musica/login.wav && zenity --info --text="<span size=\"xx-large\">Time is $(date +%Hh%M).</span>\n\nricordati di <b>bere</b>." --title="drink time" ; done
```

You might have more luck with that.

Thank you: it works! 

Just another small problem. It works but the zenity window is not before other. How can I put before the other windows? I'm trying with windows rules.

[IMG]https://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]

---

### Post by freemedia2018 on 2019-02-26
[https://askubuntu.com/questions/7377/how-to-start-an-app-with-always-on-top-set](https://askubuntu.com/questions/7377/how-to-start-an-app-with-always-on-top-set)

explains how to do this with window rules (if you have compiz-plugin installed) and alternatively how to do the same using wmctrl.

---

### Post by jduns on 2019-02-26
> **freemedia2018 said:**
> [https://askubuntu.com/questions/7377/how-to-start-an-app-with-always-on-top-set](https://askubuntu.com/questions/7377/how-to-start-an-app-with-always-on-top-set)

explains how to do this with window rules (if you have compiz-plugin installed) and alternatively how to do the same using wmctrl.

I have Kubuntu. So in settings -> Windows management -> Windows rules, I can add a new rule, as "keep above" for the window with a title="drink time".

---

### Post by TheFu on 2019-02-26
The intended use for watch is to rerun a command that will eventually finish ... say a huge file is being copied between systems and you'd like to notice when it is finished.  watch also clears the window before the next run of the command, so only the changed data jumps out for a human watching the output.

$ watch ls -l name-of-file

This will run the same **ls -l** command and when the file size stops changing, it is done.  **du** could be used too.  If I'm moving a file, I'll watch the source location of the file using **watch ls -l** and when watch returns a file-not-found error, then I know the move is done.

Or looking for strings in a log file using **grep**.  I use watch for that all the time.   

If I need to run a command every 45 minutes, then I use 'sleep' to launch it.

But the great and terrible thing about Unix is that the commands cannot tell if we are showing pure genius or pure stupidity. They just do what we tell them to do.

---

### Post by jduns on 2019-02-27
> **TheFu said:**
> The intended use for watch is to rerun a command that will eventually finish ... say a huge file is being copied between systems and you'd like to notice when it is finished. watch also clears the window before the next run of the command, so only the changed data jumps out for a human watching the output.

$ watch ls -l name-of-file

This will run the same **ls -l** command and when the file size stops changing, it is done. **du** could be used too. If I'm moving a file, I'll watch the source location of the file using **watch ls -l** and when watch returns a file-not-found error, then I know the move is done.

Or looking for strings in a log file using **grep**. I use watch for that all the time. 

If I need to run a command every 45 minutes, then I use 'sleep' to launch it.

But the great and terrible thing about Unix is that the commands cannot tell if we are showing pure genius or pure stupidity. They just do what we tell them to do.

Thak you, TheFu, but I have [already answered]("https://ubuntuforums.org/showthread.php?t=2413437&p=13840615#post13840615") .

I can add that I have added a new command to my script, with which I also send a notification to the smartphone: ```
./notify.sh --text "ricordati di bere"
```, after creating this [ATTACH]282654[/ATTACH] script.

---

