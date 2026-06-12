---
title: "jobs command"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by ric_Poirier on 2014-08-13
Hello,

Today I was reading about how to run a process "background", so as to be able to continue typing commands in the same terminal as the process runs. One of the suggested methods was unclear to me, or to be more precise, was came out in the terminal was unclear to me. What I dit was:

[LIST=1]
[*]I ran the command **top** in the terminal. The program worked fine, and I could no longer type anything in this terminal. 
[*]I pressed **Ctrl+Z** to stop the process, so as to be able to type another command in the same terminal. The output was: ```
[1]+  Stopped                 top
```, which is pretty clear. 
[*]I ran the command **bg** (background) to start the process **top** again, but in the background. The output was: ```
[1]+ top &
```. That's fine. 
[*]Finally, to see my background processes, I typed the command **jobs** in the terminal (I checked, **man jobs** is not working). The output was: ```
[1]+  Stopped                 top
```. 
[/LIST]

Now my question is: in the **jobs** output, why is it still mentionned that the process **top** is stopped? From what I have been reading, the command **bg** should have gone on with the top program from where it had left after I paused it with **Ctrl+Z**.

Thanks,

Éric

---

### Post by frankmorris2 on 2014-08-13
Hello,

From what I can understand, the command top is not a good choice for this kind of operation. The top command needs to display some text on the terminal.

I tried the following instead.

Command to use:
```
ping -c10 127.0.0.1
```

This simple command will simply ping the local machine 10 times in about 10 seconds.

To make sure the command won't send text to the terminal, I redirect the output to the file /tmp/ping_output.txt

```
ping -c10 127.0.0.1 > /tmp/ping_output.txt
```

I wait 10 seconds for the command to complete.

I can see the result:
```
cat /tmp/ping_output.txt
```

Now, I will use the jobs management.

I start the command and CTRL+Z after 2 seconds
```
ping -c10 127.0.0.1 > /tmp/ping_output.txt
```

I get the message:
```
[1]+  Stopped                 ping -c10 127.0.0.1 > /tmp/ping_output.txt
```

The job is stopped, waiting for me to use bg.

When I type bg, I get the confirmation that the job is restarted in the background (notice the "&"):
```
[1]+ ping -c10 127.0.0.1 > /tmp/bob.txt & 
```

If I type
```
cat /tmp/ping_output.txt
```
repeatedly, I will see the contents of the file growing during the 10 seconds.

Now I know the job is actually completing in the background.

If the command is non-interactive, you can send it easily to the background.

I am by no means an expert, but I'm sure some skilled Ubuntu Gurus on this forum will give you a much more detailed explanation.

Have a nice day.

---

### Post by ian-weisser on 2014-08-13
> **ric_Poirier said:**
> Now my question is: in the **jobs** output, why is it still mentionned that the process **top** is stopped? From what I have been reading, the command **bg** should have gone on with the top program from where it had left after I paused it with **Ctrl+Z**.


Stopping and backgrounding are different and usually unrelated.
If you stop a process, it stays stopped until you start it again. (pause/resume)
If you background a process, it stays backgrounded until you foreground it again.

If you background a stopped process (like stopping top and then backgrounding it), it will stay stopped and backgrounded.
If you start it while backgrounded, it will then run in the background.
If, instead, you foreground it while stopped, it will remain stopped in the foreground.

A convenient reason to stop/start a process is to prevent two  resource-hungry jobs from slowing your system to a crawl. The nice  commands do a good job of automating priorities, so you needn't muck about with stop.

Your 6 consoles, GUI terminal applications, and terminal multiplexers (screen, tmux) mean that you rarely need to bg/fg jobs anymore.

---

### Post by Impavidus on 2014-08-14
Some programs don't like being run in the background. When you try to run them in the background they may stop themselves or do strange things. This is usually the case for programs that expect input from the terminal, like top, vim, nano. Think of what would happen if you would get a new prompt to give further commands to the shell and at the same time run a program that expects input from the terminal, where would your commands go, to the shell or to the backgrounded program? Programs that don't need input from the terminal are usually OK to run in the background, but as they may write output to the terminal it may still mess up your terminal.

---

### Post by ric_Poirier on 2014-08-15
Ok, I understand better now.

From what I can read [here]("http://www.computerhope.com/unix/ubg.htm"), usually stopped jobs which we background with **bg** should then resume, but no input rom the terminal is now possible (which can explain why some jobs stay stopped): "The stopped job will resume operation, but remain in the background. It will not receive any input from the terminal while it's in the background, but it will keep running [...]" 

> Your 6 consoles, GUI terminal applications, and terminal multiplexers  (screen, tmux) mean that you rarely need to bg/fg jobs anymore.
I have started using screen instead, and I like it very much. Thanks for the suggestion!

Thanks for your answers!

Éric

---

