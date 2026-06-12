---
title: "problem with sudo dkms install -m psmouse -v elantech-x551c&lt;/p&gt; near"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by marcelgutierrez1994 on 2014-10-14
hi, couldn't install touchpad. this is the command
 sudo dkms install -m psmouse -v elantech-x551c</p> 
error is bash: error sintáctico cerca del elemento inesperado `newline'

please help, i search all day and not fin a solution. 
this is the link i follow to install touchpad
[http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/)
  
this is a solution than makes an user, if i fix it the problem with that explain me please


"[COLOR=#2C2C29][FONT=Tahoma]At last, it’s working! I reckoned that since the problem stemmed from a syntax error, I might as well remove “”: I believe introduces a new line that’s what was causing the error. Once I did that, it all worked fine. So thanks a lot for your tutorial![/FONT][/COLOR][COLOR=#2C2C29][FONT=Tahoma]
[/FONT][/COLOR]

---

### Post by damodaranudas on 2015-01-15
You should install first **Dynamic Kernel Module Support** (**DKMS**), then follow the touchpad install guide
```
 sudo apt-get install dkms
 
```

---

