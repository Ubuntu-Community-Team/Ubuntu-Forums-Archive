---
title: "Error"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by binte asim on 2012-12-08
whenever I open my terminal i get the following command:

[my : command  not found
dba@dba-Inspiron-N5010:~$]

I don't understand why is this giving "my command not found"

---

### Post by steeldriver on 2012-12-08
Hello and welcome

It sounds like you have an error in your .bashrc file (or possibly your .profile) - if you would like help debugging it, then post the contents of that file here between ```
 tags and we can take a look

[CODE]$ cat -n ~/.bashrc
```

---

### Post by binte asim on 2012-12-09
Following is what I got:

```

1    # ~/.bashrc: executed by bash(1) for non-login shells.
     2    # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
     3    # for examples
     4    
     5    # If not running interactively, don't do anything
     6    [ -z "$PS1" ] && return
     7    
     8    # don't put duplicate lines or lines starting with space in the history.
     9    # See bash(1) for more options
    10    HISTCONTROL=ignoreboth
    11    
    12    # append to the history file, don't overwrite it
    13    shopt -s histappend
    14    
    15    # for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
    16    HISTSIZE=1000
    17    HISTFILESIZE=2000
    18    
    19    # check the window size after each command and, if necessary,
    20    # update the values of LINES and COLUMNS.
    21    shopt -s checkwinsize
    22    
    23    # If set, the pattern "**" used in a pathname expansion context will
    24    # match all files and zero or more directories and subdirectories.
    25    #shopt -s globstar
    26    
    27    # make less more friendly for non-text input files, see lesspipe(1)
    28    [ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"
    29    
    30    # set variable identifying the chroot you work in (used in the prompt below)
    31    if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    32        debian_chroot=$(cat /etc/debian_chroot)
    33    fi
    34    
    35    # set a fancy prompt (non-color, unless we know we "want" color)
    36    case "$TERM" in
    37        xterm-color) color_prompt=yes;;
    38    esac
    39    
    40    # uncomment for a colored prompt, if the terminal has the capability; turned
    41    # off by default to not distract the user: the focus in a terminal window
    42    # should be on the output of commands, not on the prompt
    43    #force_color_prompt=yes
    44    
    45    if [ -n "$force_color_prompt" ]; then
    46        if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    47        # We have color support; assume it's compliant with Ecma-48
    48        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    49        # a case would tend to support setf rather than setaf.)
    50        color_prompt=yes
    51        else
    52        color_prompt=
    53        fi
    54    fi
    55    
    56    if [ "$color_prompt" = yes ]; then
    57        PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    58    else
    59        PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    60    fi
    61    unset color_prompt force_color_prompt
    62    
    63    # If this is an xterm set the title to user@host:dir
    64    case "$TERM" in
    65    xterm*|rxvt*)
    66        PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    67        ;;
    68    *)
    69        ;;
    70    esac
    71    
    72    # enable color support of ls and also add handy aliases
    73    if [ -x /usr/bin/dircolors ]; then
    74        test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    75        alias ls='ls --color=auto'
    76        #alias dir='dir --color=auto'
    77        #alias vdir='vdir --color=auto'
    78    
    79        alias grep='grep --color=auto'
    80        alias fgrep='fgrep --color=auto'
    81        alias egrep='egrep --color=auto'
    82    fi
    83    
    84    # some more ls aliases
    85    alias ll='ls -alF'
    86    alias la='ls -A'
    87    alias l='ls -CF'
    88    
    89    # Add an "alert" alias for long running commands.  Use like so:
    90    #   sleep 10; alert
    91    alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
    92    
    93    # Alias definitions.
    94    # You may want to put all your additions into a separate file like
    95    # ~/.bash_aliases, instead of adding them here directly.
    96    # See /usr/share/doc/bash-doc/examples in the bash-doc package.
    97    
    98    if [ -f ~/.bash_aliases ]; then
    99        . ~/.bash_aliases
   100    fi
   101    
   102    # enable programmable completion features (you don't need to enable
   103    # this, if it's already enabled in /etc/bash.bashrc and /etc/profile
   104    # sources /etc/bash.bashrc).
   105    if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
   106        . /etc/bash_completion
   107    fi
```

---

### Post by steeldriver on 2012-12-31
Thanks - I don't see the problem there - I think it must be somewhere else (maybe your ~/.profile?)

I think it has to be some file that is read every time your terminal starts

---

### Post by binte asim on 2012-12-31
~./profile gave me this:
```
    
     1    # ~/.profile: executed by the command interpreter for login shells.
     2    # This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
     3    # exists.
     4    # see /usr/share/doc/bash/examples/startup-files for examples.
     5    # the files are located in the bash-doc package.
     6    
     7    # the default umask is set in /etc/profile; for setting the umask
     8    # for ssh logins, install and configure the libpam-umask package.
     9    #umask 022
    10    
    11    # if running bash
    12    if [ -n "$BASH_VERSION" ]; then
    13        # include .bashrc if it exists
    14        if [ -f "$HOME/.bashrc" ]; then
    15        . "$HOME/.bashrc"
    16        fi
    17    fi
    18    
    19    # set PATH so it includes user's private bin if it exists
    20    if [ -d "$HOME/bin" ] ; then
    21        PATH="$HOME/bin:$PATH"
    22    fi

```

I don't have any "examples" folder in bash folder (line 4)  either do I have "~/.bash_profile or ~/.bash_login"(as far as I've checked)

---

