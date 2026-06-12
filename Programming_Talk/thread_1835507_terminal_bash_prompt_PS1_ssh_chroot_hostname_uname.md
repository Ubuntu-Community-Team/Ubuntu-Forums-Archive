---
title: "terminal bash prompt PS1 ssh chroot hostname uname"
date: 2011-08-29
forum: Programming Talk
---

### Post by masuch on 2011-08-29
Hi,

I made colored PS1 by copy/paste from different web sites:

PS1="\e[1;31;48m\e]2;`/usr/bin/tty 2>/dev/null| /bin/sed -e 's:/dev/::'` +$SHLVL:\s  \u@\H  \w   `uptime`\a\`if [ \$? -eq 0 ]; then echo \[\e[32m\]\:\-\); else echo \[\e[31m\]\:\-\( ; fi\` \$(< /proc/loadavg) \e[1;33m`/usr/bin/tty | /bin/sed -e 's:/dev/::'` \[\e[30;1m\]jobs=\[\e[1;33m\]\j\[\e[30;1m\] \[\e[34;1m\]\t\[\e[30;1m\] \[\e[32;1m\]\w\[\e[30;1m\]\[\e[30;1m\]\n\[\e[34;1m\]`if [ $(hostname -s) != $(more /etc/hostname) ]; then echo "\[\e[31m\]CHROOT\e[01;32m@"; fi``if [ -n "$SSH_CLIENT" ]; then echo "\[\e[31m\]SSH\e[01;32m@"; fi`\\e[34;1m`if [ $UID -eq "0" ]; then echo "\[\e[31m\]"; fi`\u\e[01;32m@\e[01;34m\h\[\e[30;1m\] \[\e[1;33m\]\$SHLVL:\\!:\#\[\e[30;1m\] \\$ \[\e[0m\]"

It shows basic information:

window title: pts/number +embedded terminal:shell username@hostname directory uptime
1.line: smilies ~ result of last command; loadavg; pts/number; jobs=number; time; directory
2.line: CHROOT(if any)@SSH(if any)@username(ROOT in red color)@hostname subshell:history_sequence:command_sequence #(for root) or $(for normal user) 


I have a problem to properly detect hostname in chroot. At this moment I am using different result between "more /etc/hostname" and "hostname" commands. But I would like to have hostname command running in chroot properly. Is it possible and how? (I have read it should be included in coreutils with chroot --hostname switch but when I installed coreutils version 8.12 it does not know this parameter.)

The same for uname command.

Another problem is to detect embedded ssh or chroot calls. I would like to amend PS1 to show in "2 line" something like CHROOT(number)@SSH(number). Is there any way how to count it ?


Thank you very much for any hint, discussion or advice to linux newbee.

---

