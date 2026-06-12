---
title: "xkeycaps"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-10-02
I keep disabling the caps lock with xkeycaps but it doesn't ever surive a reboot. Please help.

---

### Post by Toz on 2012-10-02
Try adding:
```
xmodmap -e "keycode 66 ="
```
...to the end of your **~/.bashrc** file.

---

### Post by cmcanulty on 2012-10-02
I tried that and rebooted still doesn't stick. In classic I can do this with layouts and that works but I want it to work ion xfce also as I am trying to ease into xfce.

---

### Post by Toz on 2012-10-02
Interesting. This works on my install. Are you using bash as your shell? Does it work if you run the command manually from a terminal window:
```
xmodmap -e "keycode 66 ="
```

---

### Post by cmcanulty on 2012-10-03
only until logout or reboot, very irritating and the main thing keeping me from xfce all the time as I hate capslock

---

### Post by Toz on 2012-10-03
Lets try it this way. Create a new startup application with the following command:
```
/usr/bin/setxkbmap -option "ctrl:nocaps"
```

---

### Post by cmcanulty on 2012-10-03
again doesn't survive logout or reboot

---

### Post by mike555 on 2012-10-03
when you set xkeycaps did you click on " write output " ? that is what keeps it after reboot.

---

### Post by cmcanulty on 2012-10-03
yes I did one thing, I can't pick anything but the suggested keyboard as the scroll bars don't seem to work. I run a HP Laptop g72t

---

### Post by Toz on 2012-10-03
Do you have the Xfce "Keyboard Layouts" plugin enabled (xfce4-kbd-plugin)? Maybe its resetting everything when it starts up.

---

### Post by cmcanulty on 2012-10-03
I just downloaded it & extracted it to home. What do I do next to enable it? I read the readme file and it had no directions.

---

### Post by Toz on 2012-10-03
Sorry if my last post was confusing. I was wondering if you had the plugin already running in your panel (it's called "Keyboard Layouts"). I was thinking that it may be resetting everything. Have a look at the items in your panel and see if it is there. If it is, remove it and try again.

Can you post back the contents of your ~/.bashrc file?

---

### Post by cmcanulty on 2012-10-04
here it is with my password listed as pw (not actually pw). I still don't know how to enable that plugin I downloaded
[HTML]	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF' 

alias ud='echo pw | sudo -S apt-get update -y && sudo -S apt-get upgrade -y  && sudo apt-get clean -y'
alias go='xdg-open'
alias dug='echo pw | sudo -S apt-get dist-upgrade -y'

alias lox='xfce4-session-logout --logout'
alias log='gnome-session-quit'

alias lol='lxsession-logout'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export MOZ_DISABLE_PANGO=1 
export PATH=$PATH:/var/lib/gems/1.8/bin
export EDITOR="gedit"
alias visudo='-E visudo'[/HTML]

---

### Post by Toz on 2012-10-04
> here it is with my password listed as pw (not actually pw). I still don't know how to enable that plugin I downloaded

You don't need to enable it, I was just wondering whether it was. If it is, you will see it listed in the (right click Panel), Panel -> Panel Preferences -> Items tab,

If you want to install and try the plugin, its available in the repositories:
```
sudo apt-get install xfce4-xkb-plugin
```

Here is another suggestion:
[LIST=1]
[*]If you don't have a ~/bin directory (a bin directory in your #HOME directory), create one:
```
mkdir ~/bin
```
[*]Create a script file
```
leafpad ~/bin/disable_caps_lock
```
[*]Copy/paste this code
```

#!/bin/bash
sleep 10
xmodmap -e "keycode 66 ="

```
[*]Make the script file executable
```
chmod +x ~/bin/disable_caps_lock
```
[*]Create an startup entry
Settings Manager -> Session and startup -> Application Autostart
...Set the command to /home/<userid>/bin/disable_caps_lock where <userid> is your system login id.
[/LIST]

---

### Post by vasa1 on 2012-10-04
I wonder how OP installed xfce. Maybe it wasn't a "full" install?

---

### Post by rai4shu2 on 2012-10-04
Actually, it's just a default Xubuntu install that gives you xfce4-xkb-plugin, not necessarily Xfce. Not everyone does a clean install (like I do every time I do a dist upgrade).

---

### Post by vasa1 on 2012-10-04
> **rai4shu2 said:**
> Actually, it's just a default Xubuntu install that gives you xfce4-xkb-plugin, not necessarily Xfce. Not everyone does a clean install (like I do every time I do a dist upgrade).
Whatever you (or I) do or did isn't the point :)
OP could explain what he has or hasn't.

---

### Post by cmcanulty on 2012-10-05
None of that worked but I did find a fix at this link. 

[http://software.clapper.org/cheat-sheets/xfce.html]("http://software.clapper.org/cheat-sheets/xfce.html")

Can someone please post how to modify the command I used and add it to startup apps but instead of nocaps make it an additional backspace.
```
/usr/bin/setxkbmap -option 'ctrl:nocaps'
```
 

 I do have the xfce4-kbd-plugin installed but I can't find it or see how to enable or use it.Can anyone please tell me where it is or how to use it? xkeycaps is easy to use but won't keep after a logout or reboot.

---

### Post by LewisTM on 2012-10-05
Add this to your startup commands and you should be good to go:
```
sh -c "sleep 10;setxkbmap -option caps:backspace"
```
The sleep delay is to prevent any Xfce keyboard settings from overwriting your option at login.

For the Xkb plugin, once installed, you can just add it as a new panel item. One note though: it will cause trouble if you don't set the Xfce Settings Manager/Keyboard/Layout to use System Defaults. It's a useful plugin for defining the Compose key and multiple layouts. I know a hack to include any setxkbmap option in its settings but it's a bit complicated. The startup command should do the trick.

Cheers!

---

### Post by cmcanulty on 2012-10-05
I went to synaptic and found the file for it and so added this custom application launcher but it does nothing
```
/usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-xkb-plugin
```

---

### Post by LewisTM on 2012-10-05
The Xkb plugin is not an executable program, it's a panel plugin.
You must right-click a panel -> Panel -> Add new items -> Keyboard layouts

But really, you don't have to add it unless you want to have multiple layouts or if you are unhappy with your Compose key position and don't want to set it with a setxkbmap command at login.

---

### Post by cmcanulty on 2012-10-05
the trouble is , keyboard layouts isn't in the list for me

---

### Post by LewisTM on 2012-10-05
This is NOT the dialog for the Xfce panel, this looks like an old GNOME 2 panel dialog. Hence the last item in the list...

---

### Post by cmcanulty on 2012-10-06
I got it fixed somehow. I did so many tweaks I have no idea how.But I am logged into xfce why does the gnome panel dialog show? OK I think I have figured out the gnome-panel is running. But when I type xfce4-panel in the terminal I get this also but it sure isn't visible. I would like to run the gnome-panels I have set up in gnome-classic and the xfce panels in xfce and xubuntu that's the only way I can compare them and learn xfce. But I don't know how to do that without losing my gnome-panels for classic. So somehow the xfce4-panel is running but not visible. It is in autostart. If I remove gnome-panel from autostart I get nothing so have to start it in terminal to see any icons or do anything.
```
cmcanulty@HPTech:~$ xfce4-panel
xfce4-panel: There is already a running instance

cmcanulty@HPTech:~$
```

---

### Post by LewisTM on 2012-10-06
You shouldn't have any panel command in your autostart. Instead, you should pick Xfce or GNOME session from the login manager. Mixing panels from different DEs is a bad idea. 

We are deviating from the OP. I suggest you open a new thread if you experience problems running Xfce. Include you Ubuntu version and the steps you took.

---

