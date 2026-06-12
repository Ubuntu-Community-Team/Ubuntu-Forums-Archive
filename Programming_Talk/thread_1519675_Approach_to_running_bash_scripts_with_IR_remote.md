---
title: "Approach to running bash scripts with IR remote"
date: 2010-06-28
forum: Programming Talk
---

### Post by Neovos on 2010-06-28
I have an IR remote setup going and have a ton of scripts attached to the various buttons on it which all work fine. What I ran into was basically having more functions then I did buttons and wanted to make a type of numeric code input where I could just add scripts as I needed them without needing to change the button mapping on everything. The problem I'm having is that I have the below script opens up a Zenity prompt in which I would like to be able to enter numbers from the remote control and press "OK" and enter. But what I think is happening is that the Zenity script is still "running" and waiting to finish before the irexec daemon is free to enter the codes for the numbers themselves. Anyone know of a way to break off that zenity entry script so that irexec can be free to enter numbers from the remote? I would THINK it would be here in ~/.lirc/default:

```
begin
    remote = Streamzap_PC_Remote
    prog = irexec
    button = YELLOW
    config = /home/brian/bin/scripts/ir_remote/code_input.sh
    repeat = 0
    delay = 0
end
```

but adding & at the end of the config line does nothing. Any ideas? This is my script so far below: 

```
#!/bin/sh

INPUT=$(zenity --entry --text="Enter the code of the desired function")

if [ $INPUT = "0" ]; then
	gnome-screensaver-command --lock && pmi action suspend
else
        zenity --info --title="Code Input" --text="\"$INPUT\" is not a recognized code"
fi
	
exit 0
```

on a side note, that second zenity info window doesn't seem to pay attention to anything I put into it and not sure why? It says "all updates complete" which is what happens when you don't specify any text at all ```
zenity --info
```

---

