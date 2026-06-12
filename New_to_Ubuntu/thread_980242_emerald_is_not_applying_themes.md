---
title: "emerald is not applying themes"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by enri2 on 2008-11-12
whats the command to enter in new session???????????

---

### Post by tjwoosta on 2008-11-13
> whats the command to enter in new session??????????? 

im not sure what you mean by enter in new session but i think i can help with emerald


to make emerald start do this (it will replace the gtk window decorator with the emerald window decorator)
```
emerald --replace
```


to make emerald start every time you login do this..

go to "system-preferences-sessions" and choose the startup programs tab

then click the "add" button and put the emerald --replace command in the command box and put whatever you want in the other boxes

---

