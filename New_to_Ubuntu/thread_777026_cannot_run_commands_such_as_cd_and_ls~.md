---
title: "cannot run commands such as cd/ and ls~"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by pympnplaya on 2008-05-01
i cannot run any commands in terminal without getting "-bash: : command not found".  i have been searching for answers and have only come up with my path or shell or something is wrong but i do not know how to fix it.  when i type "echo $PATH", it returns "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" which i am guessing is not what it is supposed to return.  i am a newbie to xubuntu, please help thanx.

---

### Post by aeiah on 2008-05-01
.

---

### Post by mikeyphi on 2008-05-01
Hi there!
Your PATH is OK....
Your CD/ should read  CD /
likewise ls should have a 'space' before the next bit of code

---

### Post by Bothered on 2008-05-01
There should indeed be a space between commands and their arguments. Also, your PATH environment variable looks normal.

---

### Post by sayakb on 2008-05-01
The path environment variable is okay. Plus, the CLI commands are case sensitive, and you should reconsider the "space" you leave after the cd and ls commands.

---

### Post by pympnplaya on 2008-05-02
well that was easy enough, thank you everyone!

---

