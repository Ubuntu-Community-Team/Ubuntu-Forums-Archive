---
title: "'You Have Mail' when logging onto Ubuntu server"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by thault on 2014-02-18
when I log onto my Ubuntu server, amongst the system information it posts one of the lines is You Have Mail. What's this for?

---

### Post by newb85 on 2014-02-18
If you issue the command
```
mail
```
at the command prompt, what is the result?

---

### Post by thault on 2014-02-18
It's a message from apticron. How do i clear it?

also would you know anything about using apticron and the updates? It has 5 packages marked for updates for me and I can't update using ```
sudo apt-get upgrade
```

---

### Post by coldcritter64 on 2014-02-19
When you read it in terminal with the mail command, keep pressing return (enter) till the full message is displayed and you get past the EOF (end of file) mark. Press the letter q to quit mail and press return (enter) and the message is saved (and hence cleared from notifying you again of having mail, for that message).

Post any errors back here when using sudo apt-get update or sudo apt-get upgrade if you are having problems updating etc with the terminal.

---

