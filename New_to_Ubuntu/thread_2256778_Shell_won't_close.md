---
title: "Shell won't close"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by djailer on 2014-12-14
It looks like I have a shell wnidow open on my desktop.  I suspect a 2 year olds hands might have gotten to the keyboard.   If I type exit it tells me "Shell exited.  Another one is launching.'   I shutdown completely and when it started up again the shell window is still there.  I can execute commands from it but I want it to go away and stay away.  Any ideas?

---

### Post by CRYy0OKmKpJgc on 2014-12-14
Try
```
gconftool --recursive-unset /apps/gnome-terminal
```

---

### Post by papibe on 2014-12-14
Hi djailer.

If it appears after you reboot, it may be in 'Startup Applications'.

If it only happens when you open a terminal, please run these commands and post back the results (you can copy/paste the text):
```
diff ~/.bashrc /etc/skel/.bashrc 

diff ~/.profile /etc/skel/.profile
```
If you are unable to open a 'clean' terminal, you can press Ctrl+Alt+F1 to get a prompt text. Then run these (similar) commands:
```
diff ~/.bashrc /etc/skel/.bashrc > ~/diff.log

diff ~/.profile /etc/skel/.profile >> ~/diff.log
```
Then get back to the graphic environment by pressing Ctrl+Alt+F7, and paste the content of the diff.log file.

Regards.

---

### Post by djailer on 2014-12-15
```
gconftool --recursive-unset /apps/gnome-terminal
```  didnt do anything...it just returns to the prompt.I looked at StartUp Applications and did not see a terminal app there.  I attached a screen shot of them just in case.

Here is the output from the commands above:


```
kenneth@doug:~$ diff ~/.bashrc /etc/skel/.bashrc
```
6c6,9
< [ -z "$PS1" ] && return
---
> case $- in
>     *i*) ;;
>       *) return;;
> esac
8,10c11,13
< # don't put duplicate lines in the history. See bash(1) for more options
< # ... or force ignoredups and ignorespace
< HISTCONTROL=ignoredups:ignorespace
---
> # don't put duplicate lines or lines starting with space in the history.
> # See bash(1) for more options
> HISTCONTROL=ignoreboth
22a26,29
> # If set, the pattern "**" used in a pathname expansion context will
> # match all files and zero or more directories and subdirectories.
> #shopt -s globstar
> 
27c34
< if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
---
> if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
84a92,95
> # Add an "alert" alias for long running commands.  Use like so:
> #   sleep 10; alert
> alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
> 
97c108,111
< if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
---
> if ! shopt -oq posix; then
>   if [ -f /usr/share/bash-completion/bash_completion ]; then
>     . /usr/share/bash-completion/bash_completion
>   elif [ -f /etc/bash_completion ]; then
98a113
>   fi
100d114
< export JAVA_HOME=/usr/lib/jvm/java-6-sun
kenneth@doug:~$ 


```
kenneth@doug:~$ diff ~/.profile /etc/skel/.profile
kenneth@doug:~$ 
```

---

### Post by sandyd on 2014-12-15
Its a cairo dock widget

Right click -> remove

---

### Post by djailer on 2014-12-15
I have seven widgets currently on my cairo-dock.  None of them are a terminal.  I have Firefox, KMyMoney, Macslow's cairo clock, Applications, Folders, and Snapshot.   Is there one hidden in there somewhere?


Also, should probably mention I am using 14.04.

I am attaching a screenshot of a normal terminal window alongside this annoying one.   I can create new tabs, shutdown the computer and navigate using this terminal - just like the regular one.   I just cannot close it or move it.

---

### Post by sandyd on 2014-12-15
> **djailer said:**
> I have seven widgets currently on my cairo-dock.  None of them are a terminal.  I have Firefox, KMyMoney, Macslow's cairo clock, Applications, Folders, and Snapshot.   Is there one hidden in there somewhere?


Also, should probably mention I am using 14.04.

I am attaching a screenshot of a normal terminal window alongside this annoying one.   I can create new tabs, shutdown the computer and navigate using this terminal - just like the regular one.   I just cannot close it or move it.

From what ive found, this is a picture of cairo-dock's terminal applet
[IMG]http://www.linuxnov.com/wp-content/uploads/2012/04/Cairo-Dock-3.0.0-Terminal-Applet-Screenshot.png[/IMG]

Looks like yours, except a different color

Does middle clicking close it by any chance?

---

### Post by djailer on 2014-12-17
Nope.  It does enter a '1' however.   Middle-clicking doesn't work on some of the other applets either so maybe something is broken somewhere?  It works on some though...

---

### Post by CantankRus on 2014-12-17
Right click on cairo-dock .....cairo-dock > configure.
Click on advanced mode at bottom left.
Type in "**termina**l" in the filter box at top left and press enter.
Disable terminal.

---

### Post by djailer on 2014-12-18
That did it!  Thanks.   I disabled the terminal in cairo-dock.

---

