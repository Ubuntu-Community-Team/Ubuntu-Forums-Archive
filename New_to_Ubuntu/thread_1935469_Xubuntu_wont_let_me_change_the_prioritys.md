---
title: "Xubuntu wont let me change the prioritys"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by Arman2k12 on 2012-03-04
Hello when ever i try to change the priority in task manager i get this error message 

An error was encountered by setting a priority to the PID 2738. It is likely you don't have the required privileges.

Look at the attachment image to see what im talking about also i am a newbie so go easy
how do i fix this? help asap thank you

---

### Post by raja.genupula on 2012-03-04
what you got if you tried in the terminal way i mean like this 

```
nice firefox 5 &
``` 
place your app name in the name of firefox 
priority level means that number 

try it .

---

### Post by Arman2k12 on 2012-03-04
Nope its still not working? any other advice look heres what i did

---

### Post by baumanno on 2012-03-04
You likely misspelled the process name, they're usually in lower-case. Try
```

$ ps aux | grep '/usr/bin/chromium'*
```

On my system, the process was called *chromium-browser*

---

