---
title: "Basic journal script with bash"
date: 2011-11-15
forum: Programming Talk
---

### Post by Neoncamouflage on 2011-11-15
I played around with bash a good bit a few months ago, and sadly I've forgotten most of what I learned. One of the things I came across and learned to do back then was create a journal script that, every time I typed the command in, it would bring up a file and insert the current date/time at the end. Now at the time I didn't need it, just did it for practice, but now it would actually come in handy.

So my question is, does anybody happen to have this script on hand, or know how to whip one up? Or at least know the source of such a thing, so that I can set it up myself. I remember how to set up aliases for my own commands, but as for the actual programming itself, I'm lost.

---

### Post by Vaphell on 2011-11-15
something like
```
#!/bin/bash

echo $(date): $@ >> log.txt
$@
```?

```
./script ls -la
``` will execute ls -la and append $date: ls -la to the log file

```
$ cat log.txt
Tue Nov 15 11:03:25 CET 2011: ls -la

```

there will be problems though, for example with globs: ./script ls *.jpg will pass not *.jpg as a param but the whole list of matching files (bash will expand it before passing inside). You'd have to do '*.jpg'. Whitespaces also are problematic.

you can also do something similar with the last command you entered. If you want to record it after the fact just do
```
echo $(date): !! >> log.txt
```
!! = last command

---

### Post by geirha on 2011-11-15
Bash already logs your commands for you to ~/.bash_history. By default it doesn't add a timestamp, but you can modify the special HISTTIMEFORMAT variable to achieve that.

E.g. add the following line to ~/.bashrc: 
```
HISTTIMEFORMAT="%Y-%m-%d %H:%M:%S "
```

Then, open a new terminal window or run **source ~/.bashrc** in your current shell session, and try it out:
```

testuser@pilot:~$ echo 'Hello, World!'
Hello, World!
testuser@pilot:~$ history
    1  2011-11-15 22:07:09 echo 'Hello, World!'
    2  2011-11-15 22:07:11 history
testuser@pilot:~$ 

```

Also see [http://mywiki.wooledge.org/BashFAQ/088](http://mywiki.wooledge.org/BashFAQ/088) if you want the history to be written to ~/.bash_history after each command instead of only when you cleanly exit the shell.

EDIT: And after posting, I reread your question and realized we both misunderstood it. You want a command that opens a file named something like journal-<current date>.txt in your favorite editor? Then maybe something like this function (which you put in ~/.bashrc):
```

journal() { 
    local file="$HOME/Documents/Journal-$(date +%Y-%m-%d_%H:%M:%S).txt"
    touch "$file"
    xdg-open "$file"
}

```

---

