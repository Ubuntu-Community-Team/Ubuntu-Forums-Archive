---
title: "X11 Forwarding in KDE Service Menu"
date: 2012-07-09
forum: Programming Talk
---

### Post by Xplorer4x4 on 2012-07-09
I am trying to implement x11 forwarding in the exec line of a KDE Service Menu for Dolphin. I have enabled and verified x11 forwarding is working by opening konsole and trying to execute simple commands like xclock and konsole and konsole -e xclock which worked fine, however implementing it in a service menu has not prooven so easy. No matter what I do, activating the service menu command on a remote host tries to download the file to my Kubuntu Precise desktop and then execute the command. Here is the exec line since the rest of the .desktop file works.

Exec=ssh -X -C [email]user@something.com[/email] konsole --hold --workdir %f -e mktorrent -a 'http://someurl.com/announce' -p -l 21 %u

I also tried without the ' ticks but it made no difference. I assume I am missing something simple here?

---

