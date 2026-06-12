---
title: "C# wait for program to load."
date: 2009-11-14
forum: Programming Talk
---

### Post by mickmouse13 on 2009-11-14
I have a program that opens about 30terminals. Dont ask why... i got bored and needed something to get my mind away from the lessons. 
anyway i have about thirty of these 
```
if (number != 0)
            {
                Process terminal = new Process();
                terminal.StartInfo.FileName = "gnome-terminal --geometry=20x5";
                terminal.Start();
            }
```
number is set to 1 so it will always run. 
my problem is though, that they all try to open at the same time. (screen lags for about 15seconds and then they all pop up at once) 
is there a way to make each terminal load, them move on with the code? 
2 things i thought of was a timer... and maybe some kind of ```
if (terminalopen=true){move do next part}
```
but then i wonder if this can be dome with so many terminals... unless i were to make a variable, and change the value at the beginning of every statement.. anyway what do you guys think? i want one terminal to open at a time and as soon as it finishes i want the next one to start.

---

### Post by emigrant on 2009-11-14
may be you could put a big for loop :D

[FONT=monospace]
[/FONT]```
if (number != 0)
            {
                Process terminal = new Process();
                terminal.StartInfo.FileName = "gnome-terminal --geometry=20x5";
                terminal.Start();
        for(int i=0; i<9999; i++){
        }


            }
```[FONT=monospace]

[/FONT]

---

### Post by mickmouse13 on 2009-11-14
Worked GREAT thanks alot. just successfully spammed myself....i needa find a life...

---

### Post by cszikszoy on 2009-11-14
System.Threading.Thread.Sleep (<milliseconds>);

---

