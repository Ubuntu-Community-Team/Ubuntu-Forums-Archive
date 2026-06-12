---
title: "How to go to the line having a particular word in GVIM?"
date: 2013-04-08
forum: Programming Talk
---

### Post by twistedpairu on 2013-04-08
Hi,
When i open a file (*.SUM*), I want the cursor to go to a line having a particular word (: ERROR). and that line should have the first occurrence word(: ERROR) from the beginning of the gvim file(*.SUM*)
Presently iam using the following command in my .gvimrc, but the cursor is going to the line having the second occurrence of the word (: ERROR)
autocmd BufReadPost *.SUM* /: ERROR
Plz help me out

---

### Post by schragge on 2013-04-08
Try ```
autocmd BufReadPost *.SUM* 1;/: ERROR
```

---

### Post by twistedpairu on 2013-04-08
Hi schragge, many thanks its working. iam thinking the buffer read has stopped after the first read of THE WORD (: ERROR ). aM I RIGHT? AND Can you please explain what was happening before?

---

### Post by schragge on 2013-04-08
Most probably, you have a command in one of Vim's startup files (*~/.vimrc*, *~/.vim/**, */etc/vim/**) that makes Vim jump to the last known cursor position in file. I.e. if you were at the end of file when leaving it last time, Vim would first jump to the end and then try to search from that point forward. I just specified an interval, or *range* in vim parlance on which the command should have effect.
```
1;/regex/
``` means from the line 1 to the first occurence of [regular expression]("http://manpages.ubuntu.com/manpages/precise/en/man7/regex.7.html") in //. Semicolon (**;**) means jump to the start line of a range before executing the command. If you omit the command, Ex will just jump to the last line of the range.

See explanation or ranges in Vim documentation: [Quick Reference]("http://vimhelp.appspot.com/quickref.txt.html#Q_ra"), [User Manual]("http://vimhelp.appspot.com/usr_10.txt.html#10.3"), [Reference Manual]("http://vimhelp.appspot.com/cmdline.txt.html#cmdline-ranges").

The command argument of *autocmd* is an Ex or command-line mode command. Basically, this is what you get inside a Vim session with ```
:1;/: ERROR
``` Note the **:** as first character of the command.

---

