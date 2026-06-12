---
title: "Impossibilitus Interruptus ..."
date: 2013-09-06
forum: Programming Talk
---

### Post by Langstracht on 2013-09-06
I am trying to write a script which will successively show the last, second last and last, third last second last and last ... and so on ,,, lines of a file, pausing after each increment and waiting for an "Enter" (or whatever) before continuing.

The displaying of the file content is covered by:

count=10

i=1

while [ $i -le $count ]

do

tail -$i filename.txt

i=`expr $i + 1`

done

Which seems to work just fine.

BUT I have been unable to accomplish the pause.

It seems that "read -p" and "pause ()" are both supposed to work.  But I have been unable to get them to do so.

Anyone have any ideas?

Help muchly appreciated ...

---

### Post by QIII on 2013-09-06
Moved to Programming Talk.

---

### Post by steeldriver on 2013-09-06
how about

```
i=1; while true; do read x; tail -n $((i++)) *file*; done
```

---

### Post by Langstracht on 2013-09-06
Thanks for the lightning response.

Alas it snagged me an error message - arithmetic expression: expecting primary: "i++"
 
I could pretend I knew what that meant ...

---

### Post by Crusty Old Fart on 2013-09-06
In keeping with your coding style, which is much different than mine, your script worked for me when I added the **[COLOR=blue]blue line[/COLOR]** shown in the code box below:
```

#!/bin/bash
set -e

count=10
i=1
while [ $i -le $count ]
do
tail -$i filename.txt
i=`expr $i + 1`
**[COLOR=blue]read -p "Hit [Enter] to continue or [Ctrl+C] to abort."[/COLOR]**
done

```

I'd have done it like this:
```

#!/bin/bash
set -e

for i in {1..10}; do
  tail -$i filename.txt
  read -p "Hit [Enter] to continue or [Ctrl+C] to abort."
done

exit 0

```

As you can see, steeldriver would have made it even shorter. :cool:

---

### Post by steeldriver on 2013-09-06
> **Langstracht said:**
> Thanks for the lightning response.

Alas it snagged me an error message - arithmetic expression: expecting primary: "i++"
 
I could pretend I knew what that meant ...

It probably means you're running it in sh (i.e. dash) rather than bash

---

### Post by Langstracht on 2013-09-06
In response to steeldriver - if you could tell me how to change that it would be most appreciated.

In response to Crusty Old Fart - alas it does not work for me.  The "Hit [Enter] to continue or [Ctrl+C] to abort." message shows up as displayed lines (albeit with the addition of ":read: 17: arg count") in between the various sections. Not a pause to be seen ,,,

---

### Post by steeldriver on 2013-09-06
Well the default shell is usually bash - so you must be doing something to change it to dash - either

[LIST]
[*]you changed your default shell to /bin/sh 
[*]you are running this inside a shell script with a #!/bin/sh shebang at the top 
[*]you are explicitly invoking it via sh on the command line i.e. [FONT=courier new]sh ./myscript[/FONT] 
[/LIST]
If you don't do any of those things, you should get a bash shell

---

### Post by Crusty Old Fart on 2013-09-06
It would be nice to see the entire content of your script in a code box. Otherwise, we're just guessing as to why what works for us isn't working for you.

---

### Post by Langstracht on 2013-09-06
In response to steeldriver - if I did any of those things it was inadvertently.  Info as to how "normal service might be resumed" would be very helpful.

In response to Crusty Old Fart - the sum total of the script was on the page.  Sorry I don't see a "code box option".

---

### Post by Crusty Old Fart on 2013-09-06
> **Langstracht said:**
> In response to steeldriver - if I did any of those things it was inadvertently.  Info as to how "normal service might be resumed" would be very helpful.

In response to Crusty Old Fart - the sum total of the script was on the page.  Sorry I don't see a "code box option".
See if your script runs if you put the following line in as the very first line of your code (it's called a shebang):
```

#!/bin/bash

```

Here's how to make a code box:
```

[noparse]
[code]
This text
will appear
in a code
box

```
[/noparse]
[/code]

---

### Post by Langstracht on 2013-09-07
```

#!/bin/bash

set -e

count=10

i=1

while [ $i -le $count ]

do

tail -$i filename.txt

i=`expr $i + 1`

read -p "Hit [Enter] to continue or [Ctrl+C] to abort."


done

```

The above code displays every line it is supposed to ... plus the "Hit  [ ... abort." after each "batch" of lines.  It does NOT pause the output.

Thank you in advance for your much needed and much appreciated help.

---

### Post by Langstracht on 2013-09-07
Sorry, my last post was incorrect.

This

```

#!/bin/bash

set -e

count=10

i=1

while [ $i -le $count ]

do

tail -$i filename.txt

i=`expr $i + 1`

read -p "Hit [Enter] to continue or [Ctrl+C] to abort."


done

```

is the code that performs in the stated fashion.

The thanks in advance continues to apply.

---

### Post by Crusty Old Fart on 2013-09-07
> **Langstracht said:**
> ...
The thanks in advance continues to apply.
You might want to remember that you'll need to use the "shebang" as the first line of every bash script that you write in the future:
```

#!/bin/bash

```

---

### Post by Langstracht on 2013-09-07
The referred to "stated fashion" was the script NOT working.  So I am afraid I will not be marking the thread as solved.  Cos it ain't!

---

### Post by Crusty Old Fart on 2013-09-07
> **Langstracht said:**
> 
The above code displays every line it is supposed to ... plus the "Hit  [  ... abort." after each "batch" of lines.  It does NOT pause the output...

Well, maybe I don't understand what you want the script to do.
You write: "The above code displays every line it is supposed to ... plus the "Hit  [  ... abort." after each "batch" of lines." <-- That's what it's supposed to do. And you should be having to hit the [Enter] key to get the script to display each successive "batch" of lines.

The contents of the script I am testing are as follows:
```

#!/bin/bash

set -e

count=10

i=1

while [ $i -le $count ]

do

tail -$i filename.txt

i=`expr $i + 1`

read -p "Hit [Enter] to continue or [Ctrl+C] to abort."


done

```

To test the script, I created a file named: filename.txt, which contains the following:
```

This is line 1.
This is line 2.
This is line 3.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.

```
When I run the script, which I named listpause.sh, I get this:
```

$ ./listpause.sh
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.

```
The scripts pauses. Then I hit the [Enter] key and I get this "batch" of lines:
```

This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.

```
The scripts pauses again. And again, I hit the [Enter] key and I get this "batch" of lines:
```

This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.

```
And so on...until the script finally reaches the end of the loop counter. At that point, the last "batch" of output looks like this:
```

This is line 1.
This is line 2.
This is line 3.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.

```
...And the script stops, and I'm returned to my user prompt.
This is how the script is **supposed** to work. If this is **not** how you **want** it to work, then I have yet to understand what you're asking for.

If the behavior of the script, as I've explained above, **is the way you want it to work**, but it isn't working this way for you, then:
[LIST]
[*] Please post the output you get, in a code box, when you run it. 
[*]Also, please post the outputs you get from the following commands in separate code boxes: 
[/LIST][INDENT]```
echo "IFS = '$IFS'"
echo "PATH = $PATH'"
cat ~/.bashrc

```
[/INDENT]
On the other hand, if the behavior of the script, as I've explained above, **is [COLOR=#ff0000]NOT[/COLOR] the way you want it to work**, then please try to explain how you want it to behave.

Thanks,

Crusty

---

### Post by Langstracht on 2013-09-07
I want the script to:

display the last line 
pause

display the last two lines
pause

display the last three lines
pause

...

and so on until there are no more lines to display

as you have delineated.

For me, the script does just that ... except it does NOT pause ... but ploughs on through all the displays of all the lines.

It seems I have been unable to describe that ... for which I apologize.

The 3 commands you list result in the following responses:

*****************************************************************

IFS = ' 	
'

******************************************************************

PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

******************************************************************

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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

*********************************************************************

Thank you for your continued involvement.

---

### Post by steeldriver on 2013-09-07
Are you holding down the 'Enter' key after you execute the command? if so, the keyboard auto-repeat will make it look like you are responding to multiple read prompts

BTW your posts would be much more readable if you used the [CODE]...[&#8725;CODE] tags around your code

---

### Post by Crusty Old Fart on 2013-09-07
> **Langstracht said:**
> ...It seems I have been unable to describe that ... for which I apologize.
Yeah...well...that's why I told you to:
[LIST]
[*]Please post the output you get, in a code box, when you run it. 
[/LIST]

So, based on what you described, in lieu of posting the output, I'm assuming that when you run the script: it pukes out ten "batches" of lines, each ending with the "Hit [Enter]..." message, and then serves your user input prompt without you touching the keyboard since you gave the shell the command to run the script. I can simulate that by holding down the [Enter] key until the script finishes. Using my test file I get the following output, in a single dump:
```

$ ./promptpause.sh
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 3.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 2.
This is line 3.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.
This is line 1.
This is line 2.
This is line 3.
This is line 4.
This is line 5.
This is line 6.
This is line 7.
This is line 8.
This is line 9.
This is line 10.
Hit [Enter] to continue or [Ctrl+C] to abort.

```

> **Langstracht said:**
> ...The 3 commands you list result in the following responses:
Thanks. I'll put them into code boxes so I can read them more easily and to prevent myself from confusing backticks with single quotes, colons with semicolons, and periods with commas...etc:

```

$ echo "IFS = '$IFS'"
IFS = '     
'

```
That one looks okay.

Next:
```

$ echo "PATH = $PATH'"
PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

```
Ahhh...There's part of the problem--maybe even the whole crux. We'll fix this by editing your ~/.bashrc file a little later in this post.

The last one:
```

$ cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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

```

That looks good.

Now we'll fix the problem with your PATH environment variable by adding some code to the bottom of your ~/.bashrc file.

Before we do that, we should make a copy of ~/.bashrc so that we can revert back to it in case we hose the code addition. We'll name the copy of ~/.bashrc as: ~/.bashrc_original. Please execute the following command:
```

cp -p ~/.bashrc ~/.bashrc_original

```

Now we'll add the code we need to the bottom of your ~/.bashrc file. The code box below shows the entire contents of the ~/.bashrc file you should end up with. The code we're adding is shown in **[COLOR=blue]bold blue text[/COLOR]** at the bottom of the file. NOTE: Replace the instances of the bold red text: **[COLOR=red]your_user_name[/COLOR]** with whatever your user name is.
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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

[B][COLOR=blue]###########################################
# [/COLOR][COLOR=red]YOUR_USER_NAME'S[/COLOR][COLOR=blue] CUSTOM CONFIGURATION BELOW:
# Last edited: 09/07/2013
# =========================================
# Add /home/[/COLOR][COLOR=red]your_user_name[/COLOR][COLOR=blue]/bin to PATH
    export PATH=$PATH:/home/[/COLOR][COLOR=red]your_user_name[/COLOR][COLOR=blue]/bin
#
# END OF [/COLOR][COLOR=red]YOUR_USER_NAME'S[/COLOR][COLOR=blue] CUSTOM CONFIGURATION
###########################################[/COLOR][/B]

```

When you're satisfied that you've successfully edited your ~/.bashrc file, we need to load it with the following command:
```

source ~/.bashrc

```

> **Langstracht said:**
> Thank you for your continued involvement.
You're mighty welcome, Please follow the instructions I've given above very carefully. Please don't skip anything, especially making a copy of ~./bashrc before adding code to it.

When you're done, please run the script again and let us know what happened.

Thanks.

---

### Post by Crusty Old Fart on 2013-09-07
> **steeldriver said:**
> ...BTW your posts would be much more readable if you used the [CODE]...[&#8725;CODE] tags around your code
Yup...sure as hell would be.

---

### Post by steeldriver on 2013-09-07
COF I'm not sure I understand your reasoning for the suggested edit to the OP's .bashrc file

[LIST]
[*]the PATH environment variable should only affect whether the executable is found without giving an explicit path, not how it is executed 
[*]the default user setup already sets PATH="$HOME/bin:$PATH" (if it exists) in ~/.profile 
[/LIST]

---

### Post by Crusty Old Fart on 2013-09-07
> **steeldriver said:**
> COF I'm not sure I understand your reasoning for the suggested edit to the OP's .bashrc file...
Well, I did it because when I compared Langstracht's PATH to what I have in my PATH, /home/username/bin was the only path that was missing. Since the script runs for me, but doesn't run for him, I thought this may have been the reason for it. So, without having expert knowledge, this was a shot in the dark that I thought might fix the problem, without causing any harm. It seems to me that I had to do this to my .bashrc file at one time long ago, but my memory may not be right about that.
> **steeldriver said:**
>  
[LIST]
[*]the PATH environment variable should only affect whether the executable is found without giving an explicit path, not how it is executed 
[/LIST]

Okay. But for some weird reason, it doesn't seem to be found by bash, or maybe bash is finding it but not interpreting the read commands as it should...ugh! Before we put the bash shebang in, the script was throwing errors, Now, it isn't doing that, but it's blasting through the read commands without stopping on them.
> **steeldriver said:**
> 
[LIST]
[*]the default user setup already sets PATH="$HOME/bin:$PATH" (if it exists) in ~/.profile 
[/LIST]

[color=red][s][color=black]Alright, then how come $HOME/bin doesn't show up when we run:
```

echo "PATH = $PATH"

```[/color][/s]** Edit: Never mind. I reckon $HOME/bin was never created.**[/color]

Please don't take what I've written above as being argumentative for the sake of it. My questions are sincere. I have learned much from the Wizards on this forum. I expect that I'll have the good fortune of learning a few new things from you.

As you can see, I'm having a tough time cracking this nut.

How would you do it?

Do you think it would work if Langstracht ran the script with this command?
```

bash name_of_the_script

```
Now that I think about it, I wonder what command he's using to run it.
We haven't asked him that yet.
The following throws errors on my machine:
```

sh name_of_the_script

```
But, either of the following works fine for me:
```

./name_of_the_script

~~~ OR ~~~

bash name_of_the_script

```

---

### Post by Crusty Old Fart on 2013-09-07
Oh, man!
I have my threads confused. There's no "Jonathan" here.
Time to do some heavy editing.

---

### Post by Crusty Old Fart on 2013-09-08
To Langstracht:

I'd like you to answer some more questions:
[LIST=1]
[*]What Linux operating system are you running?
[*]Are you running your operating system in WUBI?
[*]What application did you use to create your script?
[*]What application have you been using to edit your script?
[/LIST]
In the code box below, please replace the text: **[color=blue]script.name[/color]** with the name of your script and post the output from the command
```

file **[color=blue]script.name[/color]**

```
Assuming the name of the file from which your script reads lines is: filename.txt, please post the output from the following command:
```

file filename.txt

```
Thanks,

Crusty

---

### Post by Langstracht on 2013-09-08
Much has been going on since my last post.  The vast majority of which is beyond my level of comprehension.

That aside, why this would be case I do not know, BUT... having made the suggested changes ... the script now works fine!  Glory be.

Seems odd that a pause which should result from a read command would or would not work based on a PATH ... but it seems to be so,

As for putting "code" in a code box ... sorry my pea brain did not make a connection between a display output and a command input.

Thanks to both for clearing this very aggravating situation up.

---

### Post by Crusty Old Fart on 2013-09-08
> **Langstracht said:**
> Much has been going on since my last post.  The vast majority of which is beyond my level of comprehension.

That aside, why this would be case I do not know, BUT... having made the suggested changes ... the script now works fine!  Glory be.

Seems odd that a pause which should result from a read command would or would not work based on a PATH ... but it seems to be so,

As for putting "code" in a code box ... sorry my pea brain did not make a connection between a display output and a command input.

Thanks to both for clearing this very aggravating situation up.
You're mighty welcome.

I really wish I could tell you why the changes we made to ~/.bashrc to modify your PATH fixed the problem. But, I can't because I don't know.

When steeldriver challenged me to explain my reasoning behind the changes I was suggesting, I thought to myself: Uh oh...now, for the sake of being honest, I'm going to have to risk looking like an idiot, admit that I really don't know what the hell I'm doing, and am just taking a "shot in the dark" that might hit the target yet wouldn't harm anything if it missed.

Fortunately, we got lucky and the shot hit the bulls eye. But, still, when it comes to giving a rational, logical, or technically sound explanation for it, I'm clueless. My reasoning was based purely on emotion--I just had a weird "gut" feeling that it might work. Sometimes, when all else fails, it helps to go with "gut" feelings, and at other times, doing so can make a huge mess of things. Knowing that adding another path to PATH wouldn't wreak havoc, I figured we had nothing to lose by taking the shot.

Hopefully, steeldriver, or one of the Wizards on this forum, will pop in here and enlighten us with a little bit of desperately needed education as to why this worked.

So, it's nice to know that things are working for you now. I shared your frustration with this problem more than you know. It was driving me nuts. Often, when I become as frustrated as I had, my patience suffers. I apologize, if during the course of this thread, I came across as being somewhat of an impatient ass. My frustration wasn't with you, but rather with the confusing nature of the problem. And now, the frustration still lingers because we never discovered the underlying cause of the problem, or why the solution worked--maybe we never will.

All the best wishes to you, Langstracht.

Crusty

```


    Thank you for marking your thread as: [SOLVED].

                         _---_
                        /_/|\_\
                       (/-O^O-\)
                __    /_\\/*\//_\    __
         ------vVVv----- o###o -----vVVv------
                          """

                   Darthroy was here.


```

---

