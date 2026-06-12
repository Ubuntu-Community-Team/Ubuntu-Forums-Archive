---
title: "Bash question"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Herbon on 2014-02-25
I was missing around in the CLI, and get this every time I open a new terminal

```


No command 'Time' found, did you mean:
 Command 'hime' from package 'hime' (universe)
 Command 'time' from package 'time' (main)
Time: command not found
bash: /home/Bengrim/.bashrc: line 119: unexpected EOF while looking for matching `"'
bash: /home/Bengrim/.bashrc: line 120: syntax error: unexpected end of file
Bengrim@peanuttwo:~$ 


```

How do I correct it?? :(

---

### Post by Iowan on 2014-02-25
Check what's in /home/Bengrim/.bashrc down around line 119 and 120. Sounds like it got truncated.
(or the actual problem might be a couple of lines higher...)
You could always post it (in code tags, please).

---

### Post by varunendra on 2014-02-25
> **Herbon said:**
> > bash: /home/Bengrim/.bashrc: line 119: **unexpected EOF while looking for matching [COLOR="#FF0000"]`"'[/COLOR]**
Or a missing double-quote?

Probably post the contents of your .bashrc file if you can't figure out the error in the lines -
```
egrep -nv '^$|^#' .bashrc
```

---

### Post by Herbon on 2014-02-25
Here the output from "*egrep -nv '^$|^#' .bashrc*"

```

Bengrim@peanuttwo:~$ egrep -nv '^$|^#' .bashrc
6:case $- in
7:    *i*) ;;
8:      *) return;;
9:esac
13:HISTCONTROL=ignoreboth
16:shopt -s histappend
19:HISTSIZE=1000
20:HISTFILESIZE=2000
24:shopt -s checkwinsize
31:[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"
34:if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
35:    debian_chroot=$(cat /etc/debian_chroot)
36:fi
39:case "$TERM" in
40:    xterm-color) color_prompt=yes;;
41:esac
48:if [ -n "$force_color_prompt" ]; then
49:    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
50:    # We have color support; assume it's compliant with Ecma-48
51:    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
52:    # a case would tend to support setf rather than setaf.)
53:    color_prompt=yes
54:    else
55:    color_prompt=
56:    fi
57:fi
59:if [ "$color_prompt" = yes ]; then
60:    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
61:else
62:    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
63:fi
64:unset color_prompt force_color_prompt
67:case "$TERM" in
68:xterm*|rxvt*)
69:    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
70:    ;;
71:*)
72:    ;;
73:esac
76:if [ -x /usr/bin/dircolors ]; then
77:    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
78:    alias ls='ls --color=auto'
79:    #alias dir='dir --color=auto'
80:    #alias vdir='vdir --color=auto'
82:    alias grep='grep --color=auto'
83:    alias fgrep='fgrep --color=auto'
84:    alias egrep='egrep --color=auto'
85:fi
88:alias ll='ls -alF'
89:alias la='ls -A'
90:alias l='ls -CF'
94:alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
101:if [ -f ~/.bash_aliases ]; then
102:    . ~/.bash_aliases
103:fi
108:if ! shopt -oq posix; then
109:  if [ -f /usr/share/bash-completion/bash_completion ]; then
110:    . /usr/share/bash-completion/bash_completion
111:  elif [ -f /etc/bash_completion ]; then
112:    . /etc/bash_completion
113:  fi
114:fi
115:Time is '/bin/date "+%H hours %M minutes %S seconds"'
116:alias speak_time='espeak "Time is \'/bin/date "+%H hours %M minutes %S seconds"\'"'
117:alias speak_time='espeak "Time is \'/bin/date "+%H hours %M minutes %S seconds"\'"'
118:Time is '/bin/date "+%H hours %M minutes %S seconds"'
119:Time is '/bin/date "+%H hours %M minutes %S seconds"'
Bengrim@peanuttwo:~$ 


```

---

### Post by tgalati4 on 2014-02-25
Your espeak commands are failing.  Try running it in command line by itself:

```
espeak "Time is \'/bin/date "+%H hours %M minutes %S seconds"\'"
```

There is an issue with escaping your single quotes.  Perhaps use backticks or reverse the single and double quotes.

---

### Post by varunendra on 2014-02-25
@ Herbon,

Please edit your post and change the 'Quote' tags to 'Code' tags, so that the codes are easier to read and errors are easier to catch. Please follow the "Using Code Tags" link in my signature to see how.

By the way, what were you trying to achieve? Both write the current time and speak it up when the terminal opens?
The codes you have used for both the tweaks are clearly wrong. Please let us know what you want so we can suggest the correct format for it.

---

### Post by Herbon on 2014-02-26
> **varunendra said:**
> @ Herbon,
By the way, what were you trying to achieve? Both write the current time and speak it up when the terminal opens?
The codes you have used for both the tweaks are clearly wrong. Please let us know what you want so we can suggest the correct format for it.

At the time (no pun) was playing around with a idea that failed to pan out.
Now my goal is just to correct this issue (learn) and move on.

Sorry about the tag

---

### Post by varunendra on 2014-02-26
No problem with the code tags. It is easy to make the mistake until you see the difference. :)

> **Herbon said:**
> Now my goal is just to correct this issue (learn) and move on.
Oh, that is easy - simply delete the lines 115 to 119 !

If you wish to display the time on the terminal when you open it, change the line 115 to something like -
```
printf "Time is $(/bin/date +%H) hours, $(/bin/date +%M) minutes and $(/bin/date +%S) seconds\n"
```

And if you wish to keep your alias (the correct way), that is easy as well. Change the line 116 from
> **Herbon said:**
> ```
alias speak_time='espeak "Time is \'/bin/date "+%H hours %M minutes %S seconds"\'"'

```
To something like -
```
alias speak_time='espeak "Time is $(/bin/date +%H) hours, $(/bin/date +%M) minutes and $(/bin/date +%S) seconds"'
```
Or probably better (since it runs "/bin/date" only once) -
```
alias speak_time='espeak "Time is $(/bin/date +%T) seconds"'
```
..and delete the lines below these without a second thought.:P

---

### Post by tgalati4 on 2014-02-26
I would probably use xargs to hold the result of the date function then feed that to *espeak*.

[http://www.cyberciti.biz/faq/linux-unix-bsd-xargs-construct-argument-lists-utility/](http://www.cyberciti.biz/faq/linux-unix-bsd-xargs-construct-argument-lists-utility/)

[http://javarevisited.blogspot.com/2012/06/10-xargs-command-example-in-linux-unix.html](http://javarevisited.blogspot.com/2012/06/10-xargs-command-example-in-linux-unix.html)

Pseudo code:

```
date | xargs -n 3 espeak
```

---

### Post by Herbon on 2014-02-26
Great espeak useage commands

But how do I deleted lines "delete the lines 115 to 119 !"

---

### Post by newb85 on 2014-02-26
The easiest would probably be using a graphical text editor.  For example, the default for Ubuntu,
```
gedit .bashrc
```
Delete the lines, then save and close.

Other variants of Ubuntu come with different default text editors, like leafpad for Lubuntu.
Of course, you could also use a non-GUI text editor, like vi, but those aren't quite easy to pick up.

---

### Post by varunendra on 2014-02-26
> **Herbon said:**
> But how do I deleted lines "delete the lines 115 to 119 !"
If you are new to these things, probably the best and safest way would be what newb85 suggested above. You must enable "Show Hidden Files" option if you choose the normal method of opening files in gui applications ("File" menu > Open..), because the files/directories whose names start with a dot (.) are hidden by default.

Or, to do it via commandline -
```
cp .bashrc old.bashrc
sed -i '115,$ d' .bashrc
```
The first command will backup your current .bashrc file as "old.bashrc" file, just in case.
The second command will delete (d) the lines 115 to the last line (indicated by "$" in sed) in the .bashrc file.
You can run the above sed command without the "-i" option to see its result without actually modifying the file. The "-i" option (not applicable on all platforms) modifies the file instead of showing the output on the screen.

But if you wish to add the commands I suggested via commandline, well, that would be a bit tricky due to the use of single quotes.

A single quote is called a "Strong Quote", and conventionally, nothing inside it can retain its 'Special' meaning, not even the escape character backslash (\). Once it has started, you'll have to close the single quote first if you need anything to be escaped, including a following single quote (a starting single quote can be escaped, not 'after' a starting one until it is closed). However, if it occurs within a "Weak Quote" (double-quotes), it doesn't need to be escaped. More about this can be learnt here : [http://wiki.bash-hackers.org/syntax/quoting](http://wiki.bash-hackers.org/syntax/quoting)

So to add the proposed lines also via terminal, these will be the commands to be entered in the terminal -
```
echo **[COLOR="#0000CD"]"[/COLOR]**printf \"Time is \$(/bin/date +%H) hours, \$(/bin/date +%M) minutes and \$(/bin/date +%S) seconds\n\"**[COLOR="#0000CD"]"[/COLOR]** >> .bashrc
echo **[COLOR="#0000CD"]"[/COLOR]**alias speak_time=**[COLOR="#FF0000"]'[/COLOR]**espeak \"Time is \$(/bin/date +%T) seconds\"**[COLOR="#FF0000"]'[/COLOR][COLOR="#0000CD"]"[/COLOR]** >> .bashrc
```

Hope the above also explains the mistake you had made in your original attempts in creating the alias.

Have fun with your terminal ! :)

---

### Post by Vaphell on 2014-02-26
aliases are a crude form of automation, best used to hide a bunch of switches (eg *alias ll='ls -la'*, but once you want to achieve something even remotely complicated where you have to stack quotes in different flavors they become a mess.
I value readability so I'd set up a function which is pretty much a mini-script with clean syntax and no embedded quote nonsense.

```
speak_time()
{
    local hh; local mm; local ss;
    IFS=: read hh mm ss < <( date +%H:%M:%S )
    local t="Time is $hh hours, $mm minutes and $ss seconds"
    printf "%s\n" "$t"
    espeak "$t" 2>/dev/null
}
```

and if you fear bloat in your .bashrc you may put a fullblown script in your ~/bin (added to $PATH by default) and achieve the same thing.

---

### Post by Herbon on 2014-02-26
Fixed, and Thank you all

---

