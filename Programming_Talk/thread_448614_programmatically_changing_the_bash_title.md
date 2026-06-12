---
title: "programmatically changing the bash title"
date: 2007-05-19
forum: Programming Talk
---

### Post by mlanza on 2007-05-19
I use bash in the standard GNOME Terminal.  I know I can select 'Terminal > Set Title' to change the title bar; however, I'd like to do this programmatically with a command.  My purpose is to set up a few Alias commands as part of my environment.  The Alias commands will start up web servers, etc.  I want to concat a command to the end of the Alias in order to set the title bar name (making it clear which console affects what).

Thanks.
Mario T. Lanza

---

### Post by Tomosaur on 2007-05-19
To change the title used by gnome-terminal, use the following command:
```

gnome-terminal --title=title

```

e.g:

```

gnome-terminal --title=Hello

```

If you want to read documentation for many programs (and thus find out which command line options the program accepts, type the following command:
```

man <command>

```

e.g:
```

man gnome-terminal

```

Not all programs have a man page though (although most do).

---

### Post by neojinux on 2007-05-19
How about this way. Execute the following command to change your terminal window title

bash script: set_term_title
---
#!/bin/bash
print -Pn "^[]0;$1^G" 
---

I deploy it as a bash script. Say if you want to have the title "beautiful". Replacing "$1" with "beautiful"
execute "set_term_title beautiful"

---

### Post by mlanza on 2007-05-19
Thanks, that's a start but I can't seem to accomplish what I want even after looking over the help file.

How do I write an Alias that sets the title of the current terminal (or creates another and executes the following commands in it)?  I tried the

--tab
--execute
-x
--command

options.

I basically want this to happen:
1. change the title of the current terminal to "Something"
2. change the directory (e.g. "cd /var/www/mysite")
3. execute a command to start a web server (e.g. "mongrel_rails start")

---

### Post by shanz1999 on 2007-11-01
Using Escape Sequences To Set Gnome Terminal Options

   1. Edit the Terminal Profile (Edit - Profiles - Title and Command Tab), change dynamically-set title option to "replaces initial title".
   2. Edit a script file or run on the command line and change the PROMPT_COMMAND line to 

PROMPT_COMMAND='echo -ne "\033]0;"myWindowTitle"\007"'

where (in octal) \033   => <ESC>
                 0      => Ps = 0 (use string as a new icon name and title)
                 ;      => non-digit character
                 string => "myWindowTitle"
                 \007   => <BEL> (non-printing character)

The escape sequence I've employed is :-

ESC ] Ps ND string NP		OSC Mode
    ND can be any non-digit Character (it's discarded)
    NP can be any non-printing Character (it's discarded)
    string can be any ASCII printable string (max 511 characters)
    Ps = 0 -> use string as a new icon name and title
    Ps = 1 -> use string is a new icon name only
    Ps = 2 -> use string is a new title only
    Ps = 46 -> use string as a new log file name

    * The escape sequences are listed here 

[http://www.mit.edu/afs/athena/system/x11r4/src/mit/clients/xterm/ctlseq2.txt](http://www.mit.edu/afs/athena/system/x11r4/src/mit/clients/xterm/ctlseq2.txt)

---

### Post by fvu on 2007-12-21
Below is a generic bash function `nameTerminal()' to set the terminal title.  It works for different types of terminals.

See also: [http://www.fvue.nl/wiki/Bash:_How_to_change_tab_and_window_title_of_console](http://www.fvue.nl/wiki/Bash:_How_to_change_tab_and_window_title_of_console)

You might also want to try the `cdp' command: You define an environment variable `CDP_DIRS' for cdp to search and it will jump to the first found project.  The project name is tab completed.  If the destionation directory contains a file `.cdprc' it will be executed.  I'm planning on including `nameTerminal' within cdp, but you could rename already from within .cdprc.
See: [http://fvue.nl/wiki/Bash:_Change_directory_to_project:_cdp](http://fvue.nl/wiki/Bash:_Change_directory_to_project:_cdp)


Freddy Vulto
[http://fvue.nl/wiki](http://fvue.nl/wiki)

---8<-----------------------

```
# Set terminal title
# @param string $1  Tab/window title
# @param string $2  (optional) Separate window title
 # The latest version of this software can be obtained here:
# See: http://fvue.nl/wiki/NameTerminal
function nameTerminal() {
    [ "${TERM:0:5}" = "xterm" ]   && local ansiNrTab=0
    [ "$TERM"       = "rxvt" ]    && local ansiNrTab=61
    [ "$TERM"       = "konsole" ] && local ansiNrTab=30 ansiNrWindow=0
        # Change tab title
    [ $ansiNrTab ] && echo -n $'\e'"]$ansiNrTab;$1"$'\a'
        # If terminal support separate window title, change window title as well
    [ $ansiNrWindow -a "$2" ] && echo -n $'\e'"]$ansiNrWindow;$2"$'\a'
} # nameTerminal()
```

---

### Post by olejorgen on 2008-01-21
Weird... non of these methods work here...

---

### Post by stair314 on 2009-07-16
None of them work for me either. I'm using Ubuntu 8.04 / gnome-terminal.

---

### Post by stroyan on 2009-07-16
Here are some bash functions to set the terminal title and icon label.
```

function title {
    echo -en "\033]2;$1\007"
}

function icon_label {
    echo -en "\033]1;$1\007"
}

```
If you have the default PROMPT_COMMAND setting that sets the terminal title then changing the terminal title won't have a lasting effect.  The shell will change the title back as soon as it returns to the shell prompt.  To see the change you will need to either "unset PROMPT_COMMAND" or follow the title setting with a blocking command like "title new; sleep 3".

---

### Post by stair314 on 2009-07-17
So you're saying this should have an effect?
```

~$ unset PROMPT_COMMAND
~$ echo -en "\033]2;$1\007"

```
It still doesn't do anything on my machine.

---

### Post by stroyan on 2009-07-17
> **stair314 said:**
> So you're saying this should have an effect?
```

~$ unset PROMPT_COMMAND
~$ echo -en "\033]2;$1\007"

```
It still doesn't do anything on my machine.

Your terminal's title may also be changed back by a PS1 prompt.
Try the "sleep" version instead.
Note that the "$1" in the function's echo is the function argument.
You should use a different string if you use the echo outside of a function.

---

### Post by stair314 on 2009-07-17
Ah, I was just being stupid and overlooking the $1 in the midst of all those other punctuation marks. It works for me now.

---

### Post by efittery on 2010-05-14
This approach uses xprop and xdotool

#!/bin/bash
# file name:  set-title
#   uses: xprop and xdotool
#   requires 1 argument which is 
#   desired title string
#   Determines what the currently focused
#   window is and then its title to $1

thisWindow=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | awk '{ print $5}'`

xdotool set_window --name $1 $thisWindow

---

### Post by joxl on 2010-11-04
Similar to **stroyan**'s idea [above]("http://ubuntuforums.org/showpost.php?p=7628682&postcount=9"), but a little easier to use.  Put this in your ~/.bashrc file:

```
function title {
    echo -en "\033]2;$@\007"
}
```You'll need to re-start terminal, or run this command to make bash re-read the changes:

```
source ~/.bashrc
```From now on you should be able to simply change your title like this:

```
title new_bash_title
# -- or --
title it works with spaces too
```

---

### Post by axylone on 2011-05-30
The problem is that in the default ubuntu .bashrc, PS1 is set to replace the terminal's title every time it displays:


```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```

My solution is to save PS1 as PS1_NOTITLE before this line and then set PS1 in the nameTerminal function (find these lines and add the _NOTITLE and PS1=$PS1_NOTITLE):

```
if [ "$color_prompt" = yes ]; then
    PS1_NOTITLE='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1_NOTITLE='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt
PS1=$PS1_NOTITLE

function nameTerminal {
    PS1=$PS1_NOTITLE
    echo -en "\033]2;$1\007"
}
```

And to use the function:
```
$ nameTerminal "new title"
```

---

