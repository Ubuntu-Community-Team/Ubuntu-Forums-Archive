---
title: "Order of execution of commands in bash script"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by PianoManEDTA on 2012-06-19
I'm trying to write a script that prompts the user for a number and opens that many terminal windows. The problem lies in the following segments:

The main script basically contains: 
```
gnome-terminal -x $HOME/workspace/StartupScripts/getAns
```

followed by: 
```
cat $HOME/workspace/StartupScripts/temp.txt | (read ANS; yesOrNo $ANS)
```

where getAns contains:
```
echo "Open how many terminals?"
read -t 12 NUMT
echo $NUMT > $HOME/workspace/StartupScripts/temp.txt
```

The subroutine yesOrNo seems to be working fine.

When I run initTerminals the first time, I'm prompted for a number by getAns, and the script stops. tempt.txt will contain whatever number I input. When I run initTerminals a second time (without logging out), the number of windows I specified previously is opened immediately, and, while I'm still prompted by getAns, it only changes subsequent runs. I've searched for ways to prevent initTerminals from continuing until getAns has completed, but the only surefire method to make the script work is to input some "sleep x" after the call to getAns, which isn't the way I'd like it to run.

If anyone knows of a better way to rework the entire program, I'm all ears, but I'd also like to understand what's going wrong in the current situation. Any pointers are greatly appreciated, thanks!

---

### Post by sudodus on 2012-06-19
I think the problem is that you start a new process with ```
gnome-terminal -x $HOME/workspace/StartupScripts/getAns
``` and the script continues immediately with the next command line without waiting for you to reply and the reply to be written to the file.

Would it be OK for you to do it from a terminal window instead? Change the script to something like this
```
$HOME/workspace/StartupScripts/getAns
cat $HOME/workspace/StartupScripts/temp.txt | (read ANS; yesOrNo $ANS)
```

---

### Post by PianoManEDTA on 2012-06-19
Thanks for the quick reply! I'm actually going for a script that runs on startup (executing initTerminals via Startup Applications), so the script would open its own terminal, preferably.

---

### Post by HiImTye on 2012-06-19
I'd use Zenity rather than opening up a terminal window, which I believe daemonizes which is the problem youre facing, i.e.
```
ANS=$(zenity --scale --text "number of terminals" --min-value=1 --max-value=20 --value=5 --step=1)
```

---

### Post by sudodus on 2012-06-19
In this case you can run this main script containing
```
$HOME/workspace/StartupScripts/getAns
cat $HOME/workspace/StartupScripts/temp.txt | (read ANS; yesOrNo $ANS)
...
``` in a terminal

```
gnome-terminal -e initTerminals
```

---

### Post by PianoManEDTA on 2012-06-19
> **HiImTye said:**
> I'd use Zenity rather than opening up a terminal window, which I believe daemonizes which is the problem youre facing, i.e.
```
ANS=$(zenity --scale --text "number of terminals" --min-value=1 --max-value=20 --value=5 --step=1)
```

This works perfectly! Switched to the text input box instead of a scale, but this is so much nicer than my previous method. I also tried: 

```
gnome-terminal -e initTerminals
```

but it didn't hold up.

HiImTye: If, by "daemonizes", you mean getAns is started in the background, why wouldn't adding a "wait" afterwards solve the problem? Doesn't "wait" prevent further commands from executing until background programs have completed?

Thanks again!

---

### Post by HiImTye on 2012-06-19
any program that daemonizes (is forked to the background) causes the script to continue as if the program has exited, so the script has no way of knowing whether input has been given or not. you could add an index to your file and make a loop to check if the index is greater than the launch time of your script but that is a lot more work than just using something that doesnt daemonize

---

### Post by anewguy on 2012-06-19
Hummmmm......I'm probably way off base here, but I thought there was a way to make these things synchronous - waiting on the completion before proceeding, and I thought you could do that in a script.  I'll do some more research.

EDIT:  I think "exec" in the bash shell does the "wait until".

Dave ;)

---

### Post by HiImTye on 2012-06-19
you can with any child process but anything that is forked to the background doesnt provide the terminal with any output after it is forked (when it is forked, it returns an exit code)

---

### Post by PianoManEDTA on 2012-06-20
Interesting, appreciate the extra info.

---

