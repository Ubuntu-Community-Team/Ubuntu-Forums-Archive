---
title: "[bash] File validation"
date: 2010-06-28
forum: Programming Talk
---

### Post by xsinsx on 2010-06-28
I was curious how i might test if a file exists or whether the argument is a filename at all. 

```
[color=#408080][i]#!/bin/bash
[/i][/color]
[color=#19177C]i[/color][color=#666666]=[/color]1 [color=#408080][i]#counter variable
[/i][/color][color=#19177C]new_file[/color][color=#666666]=[/color]1 [color=#408080][i]# new text file labler
[/i][/color][color=#19177C]headarg[/color][color=#666666]=[/color][color=#19177C]$1[/color] [color=#408080][i]# head command argument
[/i][/color][color=#19177C]FILE_NAME[/color][color=#666666]=[/color][color=#19177C]$2[/color] [color=#408080][i]# file argument used in chop
[/i][/color][color=#19177C]PARAMETERARG[/color][color=#666666]=[/color][color=#19177C]$3[/color] [color=#408080][i]# the number of times you want this chomped
[/i][/color][color=#19177C]NUMOARGS[/color][color=#666666]=[/color]3 [color=#408080][i]# required arguments 
[/i][/color][color=#19177C]E_ARGS[/color][color=#666666]=[/color]65 [color=#408080][i]# exit error for insufficent arguments
[/i][/color][color=#19177C]E_INT[/color][color=#666666]=[/color]68 [color=#408080][i]# exit error for not placing and integer as an argument
[/i][/color]

[color=#008000]**if**[/color] [color=#666666][[/color] [color=#19177C]$# [/color]-ne [color=#19177C]$NUMOARGS[/color] [color=#666666]][/color] [color=#408080][i]# Checks for number of arguments
[/i][/color][color=#008000][b]then
        [/b][/color][color=#008000]echo[/color] [color=#BA2121]"Usage: `basename $0` Arg1 Arg2 Arg3"[/color]
        [color=#008000]echo[/color] [color=#BA2121]"Insufficent Arguments"[/color]
        [color=#008000]exit[/color] [color=#19177C]$E_ARGS[/color]
[color=#008000][b]fi


if[/b][/color] [color=#666666][[[/color] ! -z [color=#008000]**$(**[/color][color=#008000]echo[/color] [color=#19177C]$headarg[/color] | sed [color=#BA2121]'s/[0-9]//g'[/color][color=#008000]**)**[/color] [color=#666666]]][/color]
[color=#008000][b]then 
        [/b][/color][color=#008000]echo[/color] [color=#BA2121]"Your argument must be a integer value number"[/color]
        [color=#008000]exit[/color] [color=#19177C]$E_INT[/color]
[color=#008000][b]fi


if[/b][/color] [color=#666666][[[/color] ! -z [color=#008000]**$(**[/color][color=#008000]echo[/color] [color=#19177C]$PARAMETERARG[/color] | sed [color=#BA2121]'s/[0-9]//g'[/color][color=#008000]**)**[/color] [color=#666666]]][/color]
[color=#008000][b]then
        [/b][/color][color=#008000]echo[/color] [color=#BA2121]"Your argument must be an integer value number"[/color]
        [color=#008000]exit[/color] [color=#19177C]$E_INT[/color]
[color=#008000][b]fi
 

while[/b][/color] [color=#666666][[/color] [color=#19177C]$i[/color] -ne [color=#19177C]$PARAMETERARG[/color] [color=#666666]][/color] [color=#408080][i]# main funtion
[/i][/color][color=#008000][b]do
    [/b][/color]head -[color=#19177C]$headarg[/color] [color=#19177C]$FILE_NAME[/color] | tail -[color=#19177C]$1[/color] > [color=#19177C]$new_file[/color].txt 
    [color=#19177C]headarg[/color][color=#666666]=[/color][color=#008000]**$((**[/color] [color=#19177C]$headarg[/color] [color=#666666]+[/color] [color=#19177C]$1[/color] [color=#008000]**))**[/color]
    [color=#19177C]i[/color][color=#666666]=[/color][color=#008000]**$((**[/color] [color=#19177C]$i[/color] [color=#666666]+[/color] [color=#19177C]$1[/color] [color=#008000]**))**[/color]
    [color=#19177C]filename[/color][color=#666666]=[/color][color=#008000]**$((**[/color] [color=#19177C]$filename[/color] [color=#666666]+[/color] [color=#666666]1[/color] [color=#008000]**))**[/color] 
[color=#008000]**done**[/color]

```

---

### Post by MadCow108 on 2010-06-28
man test

there are lots of flags for file testing, most important -f and -e

---

### Post by xsinsx on 2010-06-28
Thanks for your reply i was hoping that someone would just point me in the right direction thank you.

---

