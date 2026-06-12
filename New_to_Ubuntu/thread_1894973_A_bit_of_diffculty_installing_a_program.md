---
title: "A bit of diffculty installing a program"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by TessaRact on 2011-12-13
Hello. I recently made a switch to Ubuntu (11.10 Oneiric Ocelot) after using Windows all my life. I really like what I am dealing with so far except I'm having difficulty installing a specific program, Weechat. I have had no problem with installing other programs.

Under Ubuntu Software Center History, it clearly states that weechat and its core/plugins are installed. However, when I search for it under Installed or Dash, the query returns nothing. I'm not really sure where to go from here. I suppose it is installed if it says it is but is there another way to check it to make sure it really is installed? How would I do that in terminal? I've tried removing and then installing it again. Tried to restart computer too just in case but it hasn't worked. Thank you for any insights.

---

### Post by haqking on 2011-12-13
> **TessaRact said:**
> Hello. I recently made a switch to Ubuntu (11.10 Oneiric Ocelot) after using Windows all my life. I really like what I am dealing with so far except I'm having difficulty installing a specific program, Weechat. I have had no problem with installing other programs.

Under Ubuntu Software Center History, it clearly states that weechat and its core/plugins are installed. However, when I search for it under Installed or Dash, the query returns nothing. I'm not really sure where to go from here. I suppose it is installed if it says it is but is there another way to check it to make sure it really is installed? How would I do that in terminal? I've tried removing and then installing it again. Tried to restart computer too just in case but it hasn't worked. Thank you for any insights.

i am not familiar with the app but from terminal type

```
weechat
```
 which may launch it

or ```
whereis weechat
```

which will show you where it maybe, likely to be in /usr/bin

---

### Post by jtarin on 2011-12-13
According to the Weechat "[QuickStartGuide]("http://www.weechat.org/files/doc/stable/weechat_quickstart.en.html")"......in a terminal issue the command
```
weechat-curses
```

---

### Post by TessaRact on 2011-12-13
> **haqking said:**
> i am not familiar with the app but from terminal type

```
weechat
``` which may launch it

or ```
whereis weechat
```which will show you where it maybe, likely to be in /usr/bin


Sorry I should have clarified what weechat is. It's a chat program for IRC.

[PHP]tessa@T:~$ weechat
weechat: command not found
tessa@T:~$ whereis weechat
weechat: /usr/lib/weechat

[/PHP]

---

### Post by jtarin on 2011-12-13
See my post above.

---

### Post by TessaRact on 2011-12-13
> **jtarin said:**
> According to the Weechat "[QuickStartGuide]("http://www.weechat.org/files/doc/stable/weechat_quickstart.en.html")"......in a terminal issue the command
```
weechat-curses
```

Wow, I feel smart...

Thank you!

---

