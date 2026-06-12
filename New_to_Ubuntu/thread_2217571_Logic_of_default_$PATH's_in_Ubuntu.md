---
title: "Logic of default $PATH's in Ubuntu"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by Dave.YNA on 2014-04-17
Hello all,
    Just curious if there is an interesting reason why the default paths selected in Ubuntu are selected? My appears as:

[COLOR="#008000"]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games[/COLOR]

but I have been working on a redhat machine or two at work and noticed it is quite different. It will have directories such as [COLOR="#008000"]/bin/[/COLOR] and [COLOR="#008000"]/sbin/[/COLOR] etc..... I assume this is probably because these directories are intented for Root. If that is so, the confusing aspect is that if I run ifconfig which is located in /sbin/ifconfig, the binary is found without specifying the directory. How can that be if it is not in my PATH?

Cheers

---

### Post by SeijiSensei on 2014-04-17
It is in your path.  Each of the directories is searched in order from left to right until a matching binary name is found.  The /usr/local entries are at the beginning since self-compiled software is typically installed to /usr/local/bin. Presumably you would want your version of a program to be run in favor of the official version in the repository.  For example, my /usr/local/bin contains self-compiled versions of mplayer and ffmpeg, so if I type "mplayer" at the prompt I get /usr/local/bin/mplayer, not /usr/bin/mplayer.

---

### Post by Dave.YNA on 2014-04-17
Woops! Yeah, I missed that, it is in the path....

Thanks for the reply. I will now go get my eyes tested :P

---

