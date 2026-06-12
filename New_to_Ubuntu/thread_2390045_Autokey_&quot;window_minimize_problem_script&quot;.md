---
title: "Autokey &quot;window minimize problem script&quot; problem"
date: 2018-04-24
forum: New to Ubuntu
---

### Post by arcety on 2018-04-24
[COLOR=#111111][FONT=Ubuntu]I just switched to Linux and I am setting up my laptop. In windows, I use an AutoHotkey shortcut, to do the following:
- Open "chrome" when it is not active.
- Minimize "chrome" when it in the foreground.
- Bring it to the foreground when the window is not active.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I use the following code in "Autokey" which works nicely but I would love it if I can do this with a simple bash script:[/FONT][/COLOR]

```

#AutoKey script to toggle any windowed application, Nautilus as the example. Requires xdotool and wmctrl.
import subprocess
command = 'wmctrl -lx'
output = system.exec_command(command, getOutput=True) 

if 'google-chrome' in output:
winClass = window.get_active_class()
if winClass == 'google-chrome.Google-chrome':
system.exec_command("xdotool windowminimize $(xdotool getactivewindow)")
else:
system.exec_command("wmctrl -x -a google-chrome")
else:
system.exec_command("google-chrome")
#end script

```
[COLOR=#111111][FONT=Ubuntu]Now I tried to translate this to bash code but I get stuck in checking if chrome is running in the foreground. I had the following pseudocode in mind but I can not find the right shell commands:[/FONT][/COLOR]
```

f chrome is not open
open chrome
else
if chrome is on foreground
minimize chrome
else
bring chrome to foreground
end

```
[COLOR=#111111][FONT=Ubuntu]I tried to do obtain this behaviour in Linux by using a shell script in the Linux "shortcut" application. But up till now, I was not able to find a way to check if Google-chrome is in the foreground. I tried using the "xdotools" package but this doesn't seem to work:[/FONT][/COLOR]
```

if ($(xdotool search --name "Google Chrome") -eq $(xdotool getactivewindow))
xdotool windowminimize $(xdotool getactivewindow)
else
wmctrl -x -a google-chrome
end

```

[COLOR=#111111][FONT=Ubuntu]Do you maybe have some tips on what is the best way to achieve this? I now have the following ingredients:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To open google-chrome I use:
[/FONT][/COLOR]```

google-chrome &

```
[COLOR=#111111][FONT=Ubuntu]To minimize google-chrome I use:
[/FONT][/COLOR]```

xdotool windowminimize $(xdotool getactivewindow)

```
[COLOR=#111111][FONT=Ubuntu]To maximize google-chrome I use:
[/FONT][/COLOR]```

wmctrl -x -a google-chrome

```
[COLOR=#111111][FONT=Ubuntu]And I think I need to use something like this to check if chrome is on foreground:
[/FONT][/COLOR]```

wmctrl -lx
xdotool search --name "Google Chrome"
xdotool getactivewindow

```

[COLOR=#111111][FONT=Ubuntu]Thanks a lot in advance,
Greetings, Rick,[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]System information: Desktop: Hp Zbook G3 studio Distributor ID: Ubuntu Description: Ubuntu Bionic Beaver (development branch) Release: 18.04 Codename: bionic[/FONT][/COLOR]

---

### Post by again? on 2018-04-25
> **arcety said:**
> Dear Ubuntu Linux experts,

On my windows computer I use a "AutoHotKey" script to do the following actions when I click a given shortcut:
1: Start a given program when it is closed.
2. Bring an active program to the foreground when it is minimized.
3. Minimize a program when it is on the foreground.

Which desktop are you using?
Don't understand why you need a script to do this.
Isn't this the normal behaviour of a docked application launcher?

I know little python but installed autokey and the error appears to be in the **winClass**. 
I used the included autokey "Display window info.py" script to show the class.
[ATTACH=CONFIG]279439[/ATTACH]

The edited script now works for me.
```
#AutoKey script to toggle any windowed application, Nautilus as the example. Requires xdotool and wmctrl.
import subprocess
command = 'wmctrl -lx'
output = system.exec_command(command, getOutput=True)


if 'google-chrome' in output:
    winClass = window.get_active_class()
    if winClass == '[COLOR="#FF0000"]google-chrome.Google-chrome[/COLOR]':
        system.exec_command("xdotool windowminimize $(xdotool getactivewindow)")
    else:
        system.exec_command("wmctrl -x -a google-chrome")
        
else:
    system.exec_command("google-chrome")
#end script
```

---

### Post by arcety on 2018-04-26
Dear Guber2,

Thanks a lot for your reply! I'm using the following system.

Info:
Desktop: Hp Zbook G3 studio
Distributor ID: Ubuntu
Description: Ubuntu Bionic Beaver (development branch)
Release: 18.04
Codename: bionic

I'm new to Linux but I just wanted to mimic the behavoir I use on my windows machine in which I can toggle the chrome browser by pressing ctrl + alt + d. This makes it easier for me to switch windows since I have another toggle key on my mail program. So your saying you don't need autokey for this in linux?

Thanks in advance,
Greetings,
Rick,

---

### Post by again? on 2018-04-26
By default the dock launchers don't minimize a focused window.
Buggered if I know why they do this.
You can change by running in terminal...
```
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```

---

### Post by arcety on 2018-04-28
Ah thanks I now used dash to dock to do that.

---

### Post by kerry_s on 2018-04-28
you might also want to look into "devilspie2" i use it to maximize certain windows, but it can do a lot more.
i'm just starting to learn it myself.

---

### Post by arcety on 2018-04-29
Guber your script solved my problem. Do you maybe know how to translate it into a bash script? I updated my question above.

---

### Post by again? on 2018-04-29
This works for google-chrome.
```
#!/bin/bash

chromefocus=$(xdotool getwindowfocus getwindowname | grep -c "Google Chrome")

if [ "$chromefocus" -gt "0" ]; then
		xdotool windowminimize $(xdotool getactivewindow)
	else
		wmctrl -xa "google-chrome.Google-chrome" || /usr/bin/google-chrome
fi
```
If chrome is in focus, minimises the window.
    else
raises the chrome window **or** starts chrome if first command fails.

Works here when bound to keyboard shortcut.

---

### Post by arcety on 2018-04-30
Dear Guber,

Thanks a lot for your reply I learned a lot from your code! The script seems to work well when I paste it in the terminal but unfortunately, I couldn't paste it in the linux "Custom Key command" field. I, however, got it to run as a script. Just out of interest do you maybe know the reason why it won't run as a command on its own?

chromefocus=$(xdotool getwindowfocus getwindowname | grep -c "Google Chrome");if [ "$chromefocus" -gt "0" ];then xdotool windowminimize $(xdotool getactivewindow);else wmctrl -xa "google-chrome.Google-chrome" || /usr/bin/google-chrome;fi

[ATTACH=CONFIG]279509[/ATTACH]

---

### Post by again? on 2018-04-30
The shortcuts dialog isn't a shell interpreter.
You can only use a comand with arguments.
eg
```
gnome-screenshot --area --delay=4
```

To interpret shell operators when using the keyboard shortcut dialog you would need to use "sh -c" or "bash -c"
eg (**[COLOR="#B22222"]sh -c '[/COLOR]**command1; command2[COLOR="#B22222"]**'**[/COLOR])
```
**[COLOR="#B22222"]sh -c '[/COLOR]**chromefocus=$(xdotool getwindowfocus getwindowname | grep -c "Google Chrome");if [ "$chromefocus" -gt "0" ];then xdotool windowminimize $(xdotool getactivewindow);else wmctrl -xa "google-chrome.Google-chrome" || /usr/bin/google-chrome;fi**[COLOR="#B22222"]'[/COLOR]**
```

I mostly use scripts rather than long one liners.(simpler to backup scripts for future use)

More info:
[https://askubuntu.com/a/831850](https://askubuntu.com/a/831850)

Read the manual pages:
```
man sh
man gnome-terminal
```

---

### Post by arcety on 2018-05-01
Wow thanks a lot for the extensive explanation gruber! Again learned a lot.

---

