---
title: "Can't find a program I installed..."
date: 2017-11-11
forum: New to Ubuntu
---

### Post by ddenney on 2017-11-11
I installed the IRC client Weechat, but I can't find it anywhere in the list of programs. I used Synaptic to install it. I rebooted my computer, but it still doesn't show up. Am I doing something wrong?

---

### Post by Bashing-om on 2017-11-11
ddenney; Hello -

How are you attempting to start weechat ( terminal based ) ?

I expect the binary to be /usr/bin/weechat ,

What shows:
```

sudo find / -name weechat

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ddenney on 2017-11-11
Thanks for the reply and help. I type in terminal just what you said, and got:

/usr/share/doc/weechat
/usr/lib/weechat
/usr/bin/weechat

I can't find an executable in file manager - only shell scripts. Any help would be highly appreciated.

---

### Post by Bashing-om on 2017-11-11
ddenney; Well, then :)

weechat is installed /

Activate another terminal interface - and in this new terminal type
```

weechat

```


that will start the client . ( it is terminal based - NO GUI ).

To quit out of weechat in the weechat status window type:
try:
```

/exit 

```

I do not use weecaht so can not be very explicit .

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by ddenney on 2017-11-11
Hey thanks. That worked.

---

### Post by Bashing-om on 2017-11-11
ddenney; Outstanding :)

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

As you have other issues and concerns, just open a new thread.

Thread - like unto dead men
[INDENT][INDENT]one to a box[/INDENT][/INDENT]

---

