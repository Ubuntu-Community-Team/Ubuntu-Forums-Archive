---
title: "Is there any difference of kill xlogo when xlogo runs in the foreground or background"
date: 2020-04-21
forum: New to Ubuntu
---

### Post by oopsfrog on 2020-04-21
Hello, I got a troublesome problem. Could anyone give some ideas? :D



[LIST=1]
[*]Open a terminal
[*]Open the second terminal
[*]Excute command "$ xlogo" in the sceond terminal
[*]Find out the parent process of xlogo in the first terminal
(I find out that "bash" is the parent process)
[*]Terminate the parent process of xlogo in the first terminal
(Command:$ kill -9 PID of parent process)
At this moment, "xlogo" and the second terminal are gone.
[*]Open the third terminal.
[*]Excute the command "$ xlogo &" in the third terminal (Let xlogo running in the background)
[/LIST]
Teminate the parent process of xlogo in the first terminal
(Command:$ kill -9 PID of parent process)
At this moment, "xlogo" still alive, but the third terminal is gone.
By excuting the command "$ pstree", I find that "xlogo" belongs to "systemd".
[https://i.stack.imgur.com/S4Iu5.png](https://i.stack.imgur.com/S4Iu5.png)


Questions:
a) Why "xlogo" was killed with its parent process when "xlogo" ran in the foreground?
b) Why "xlogo" still alive and didn't die with its parent process when "xlogo" ran in the background?

I am searching for a long time on the net. But get nothing. Could anyone try to give some ideas on how to explain this?
thx

---

### Post by wildmanne39 on 2020-04-21
Hello and welcome to the forum.

*Thread moved to **New to Ubuntu for a more appropriate fit**.*

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Thanks

---

