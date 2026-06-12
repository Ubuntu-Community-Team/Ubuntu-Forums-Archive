---
title: "Path environment Permanently"
date: 2019-10-04
forum: New to Ubuntu
---

### Post by ortollj on 2019-10-04
[COLOR=#ff0000]Q1:[/COLOR][COLOR=#000000]can someone explain me where I have to put the [/COLOR]
[COLOR=#000000]3 path in ~/.profile ([/COLOR][COLOR=#000000] what does mean the first[/COLOR][COLOR=#ff0000] .[/COLOR][COLOR=#000000] in :                  [/COLOR][COLOR=#ff0000].[/COLOR][COLOR=#000000] "$HOME/.bashrc"):[/COLOR]

[COLOR=#000000]PATH="/usr/local/texlive/2019/bin/x86_64-linux:$PATH"
PATH="~/Downloads/pythontex-master/pythontex:$PATH"[/COLOR]
[COLOR=#000000]PATH="~/Downloads/SageMath:$PATH"[/COLOR]

[COLOR=#000000]to have them permanently[/COLOR]
[COLOR=#000000](please do not tell me  the usual blabla -> type in a shell:[/COLOR]

[COLOR=#000000]export PATH="/usr/local/texlive/2019/bin/x86_64-linux:$PATH"
export PATH="~/Downloads/pythontex-master/pythontex:$PATH"[/COLOR]
[COLOR=#000000]export PATH="~/Downloads/SageMath:$PATH"[/COLOR]
[COLOR=#000000]source ~/.bashrc [/COLOR]

[COLOR=#000000]because that does not work ! when I restart my PC and do a echo $PATH[/COLOR]
[COLOR=#000000]they have disapeared [/COLOR]

```
[COLOR=#000000]# ~/.profile: executed by the command interpreter for login shells.[/COLOR]
[COLOR=#000000]# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login[/COLOR]
[COLOR=#000000]# exists.[/COLOR]
[COLOR=#000000]# see /usr/share/doc/bash/examples/startup-files for examples.[/COLOR]
[COLOR=#000000]# the files are located in the bash-doc package.[/COLOR]

[COLOR=#000000]# the default umask is set in /etc/profile; for setting the umask[/COLOR]
[COLOR=#000000]# for ssh logins, install and configure the libpam-umask package.[/COLOR]
[COLOR=#000000]#umask 022[/COLOR]

[COLOR=#000000]# if running bash[/COLOR]

[COLOR=#000000]if [ -n "$BASH_VERSION" ]; then[/COLOR]
[COLOR=#000000]    # include .bashrc if it exists[/COLOR]
[COLOR=#000000]    if [ -f "$HOME/.bashrc" ]; then[/COLOR]
[COLOR=#000000]        . "$HOME/.bashrc"[/COLOR]
[COLOR=#000000]    fi[/COLOR]
[COLOR=#000000]fi[/COLOR]

[COLOR=#000000]# set PATH so it includes user's private bin if it exists[/COLOR]
[COLOR=#000000]if [ -d "$HOME/bin" ] ; then[/COLOR]
[COLOR=#000000]    PATH="$HOME/bin:$PATH"[/COLOR]
[COLOR=#000000]fi[/COLOR]
```

[COLOR=#ff0000]Q2:[/COLOR][COLOR=#000000] texlive ask me to add these 2 paths:[/COLOR]
[COLOR=#000000]export PATH="/usr/local/texlive/2019/texmf-dist/doc/man:$MANPATH" 

export PATH="/usr/local/texlive/2019/texmf-dist/doc/info:$INFOPATH" [/COLOR]
[COLOR=#000000]but why when I do a echo $MANPATH and echo $INFOPATH I see nothing[/COLOR]
[COLOR=#000000]I suppose these 2 env Vars do not exist ?

[/COLOR][COLOR=#ff0000]Q3:[/COLOR][COLOR=#000000] sometime I got the message:
ortollj@ortollj-SATELLITE-C70-B:~$ export PATH="/usr/local/texlive/2019/bin/x86_64-linux:$PATH"
ortollj@ortollj-SATELLITE-C70-B:~$ export PATH="~/Downloads/pythontex-master/pythontex:$PATH"
ortollj@ortollj-SATELLITE-C70-B:~$ export PATH="~/Downloads/SageMath:$PATH"
ortollj@ortollj-SATELLITE-C70-B:~$ source ~/.bashrc

Command 'lesspipe' is available in the following places
 * /bin/lesspipe
 * /usr/bin/lesspipe
The command could not be located because '/bin:/usr/bin' is not included in the PATH environment variable.
lesspipe: command not found
Command 'dircolors' is available in '/usr/bin/dircolors'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
dircolors: command not found

and the cmd ls is not known (I have to exit this shell and take a new one and ls still exist again !



[/COLOR]

---

### Post by Holger_Gehrke on 2019-10-04
A1: Just put one line```
PATH=[COLOR=#000000]$HOME/Downloads/SageMath:[/COLOR][COLOR=#000000][COLOR=#000000]$HOME/Downloads/pythontex-master/pythontex:[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][COLOR=#000000]/usr/local/texlive/2019/bin/x86_64-linux:[/COLOR][/COLOR]$PATH[/COLOR]
```[COLOR=#000000]into ~/.profile before the block that checks for the existence of ".bashrc". No need to have three lines, no need for quotes (there's no characters in there that would make them necessary) and no export. 'export' marks a variable so it gets copied into the environment of new processes started by the shell. Once that marks is set, you don't need to re-set it after every change to the value of the variable.[/COLOR]

A2: MANPATH and INFOPATH tell the documentation readers 'man' and 'info' what directories to search for files. They aren't set on Ubuntu. I can't imagine any good reason to add them to PATH since there should be no executable files in directories listed in those variables. Are you sure texlive doesn't actually ask you to [COLOR=#000000]add '/usr/local/texlive/2019/texmf-dist/doc/man[/COLOR]' to MANPATH and '[COLOR=#000000]/usr/local/texlive/2019/texmf-dist/doc/info' to INFOPATH ? That would actually make some sense ...[/COLOR]

A3: Probably some typo in the commands to set the PATH, likely a forgotten "$". PATH lists the directories to search for executables, if that list is wrong the system won't find the programs.

Holger

---

### Post by ortollj on 2019-10-04
thank you  for your answer A1 it is ok now ;-).
about A2 you are right in fact textlive asked me :
Add /usr/local/texlive/2019/texmf-dist/doc/man to MANPATH.
Add /usr/local/texlive/2019/texmf-dist/doc/info to INFOPATH. 

But I'm still lost when I see this post:[https://askubuntu.com/questions/60765/how-do-i-add-a-directory-to-manpath-or-infopath](https://askubuntu.com/questions/60765/how-do-i-add-a-directory-to-manpath-or-infopath)
what do I need to do precisely ?

---

### Post by ortollj on 2019-10-04
so I did that ;

```
ortollj@ortollj-SATELLITE-C70-B:~$ echo $PATH
/home/ortollj/bin:/home/ortollj/Downloads/SageMath:/home/ortollj/Downloads/pythontex-master/pythontex:/usr/local/texlive/2019/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
ortollj@ortollj-SATELLITE-C70-B:~$ export MANPATH=/usr/local/texlive/2019/texmf-dist/doc/man:$MANPATH
ortollj@ortollj-SATELLITE-C70-B:~$ export INFOPATH=/usr/local/texlive/2019/texmf-dist/doc/info:$INFOPATH
ortollj@ortollj-SATELLITE-C70-B:~$ source ~/.profile
ortollj@ortollj-SATELLITE-C70-B:~$ echo $PATH
/home/ortollj/bin:/home/ortollj/Downloads/SageMath:/home/ortollj/Downloads/pythontex-master/pythontex:/usr/local/texlive/2019/bin/x86_64-linux:/home/ortollj/bin:/home/ortollj/Downloads/SageMath:/home/ortollj/Downloads/pythontex-master/pythontex:/usr/local/texlive/2019/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
ortollj@ortollj-SATELLITE-C70-B:~$
```


but the result is for me incomprehensible: certain path are now in duplicate!

---

### Post by Holger_Gehrke on 2019-10-04
'man' by default searches for manual pages in the directories given in '/etc/manpath.config'. If you set MANPATH to some list of directories **only** directories in that list are searched unless the list ends with a colon (':'), begins with one or contains a double colon. In that case the list of directories to search is generated from $MANPATH with the directories from the configuration put in the end or the beginning of the list or in place of the '::'.
'info' searches for files in a default directory that AFAIK is compiled in (/usr/share/info seems to be the directory in question on Ubuntu). If you set INFOPATH, only a colon at the end is documented as getting replaced with the default directory.

So putting
```

export MANPATH=/usr/local/texlive/2019/texmf-dist/doc/man:
export INFOPATH=/usr/local/texlive/2019/texmf-dist/doc/info:

```
after the PATH-line in ~/.profile should make the manual-pages and info documents available. Instead of setting MANPATH you could edit /etc/manpath.config or possibly create a user-specific configuration file '~/.manpath' and add a line saying
```

MANPATH_MAP /usr/local/texlive/2019/bin/x86_64-linux /usr/local/texlive/2019/texmf-dist/doc/man

```

Holger

---

### Post by ortollj on 2019-10-04
Thanks  Holger.

---

