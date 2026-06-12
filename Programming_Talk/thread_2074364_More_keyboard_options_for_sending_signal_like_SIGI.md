---
title: "More keyboard options for sending signal like SIGINT"
date: 2012-10-21
forum: Programming Talk
---

### Post by rjvencken on 2012-10-21
What other signals can I send to a process NOT running in the  background? I am already using CTRL+C > SIGINT and would like to keep  CTRL+Z as is. I need at least one more option similar to CTRL+C. I'm  looking for a keystroke NOT "kill <-signal> <ID>".

---

### Post by trent.josephsen on 2012-10-21
Use the stty command to see what keystrokes your terminal interprets.

```
% stty -a
speed 38400 baud; rows 24; columns 80; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = M-^?; eol2 = M-^?;
swtch = M-^?; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc ixany imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
```

Here the only relevant options are:
intr = ^C -- Ctrl+C sends SIGINT
quit = ^\ -- Ctrl+\ sends SIGQUIT
susp = ^Z -- Ctrl+Z sends SIGTSTP

Despite the name, the "kill" option refers to deleting the current line and has nothing  to do with SIGKILL.

I guess you could handle SIGQUIT and use Ctrl-\. But if this is part of your user interface, you should make your program handle the key sequence, not the signal. In fact, that goes for Ctrl-C as well. Vim, for instance, turns off terminal interpretation of control sequences and interprets Ctrl-C by itself.

---

