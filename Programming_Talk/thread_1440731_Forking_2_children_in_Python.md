---
title: "Forking 2 children in Python"
date: 2010-03-27
forum: Programming Talk
---

### Post by BlackSwordD2 on 2010-03-27
i need one parent with 2 children in python. and i keep having issues especially with variables not being global.

also, is it better to use threads or forks? (as of right now im using forks and in linux)

---

### Post by slavik on 2010-03-28
depends, are you looking for truly concurrent threads?

---

### Post by Happyfase on 2010-03-28
<off topic>

Thought of something completely different when I read the title of this thread.

---

### Post by ic3man5 on 2010-03-28
Like slavik said[COLOR=Black], it depends if you need true concurrent threads. Without looking at some code or errors we can't help you too much. Another option would be to use the subprocess module and do your communication through the pipe or sockets. If you don't need concurrent threads, Python threads would probably be the way to go.[URL="http://ubuntuforums.org/member.php?u=67597"][COLOR=#D40000][B]
[/B][/COLOR][/URL][/COLOR]

---

