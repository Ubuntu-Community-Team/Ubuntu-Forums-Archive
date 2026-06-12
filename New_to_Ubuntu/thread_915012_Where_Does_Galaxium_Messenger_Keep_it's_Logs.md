---
title: "Where Does Galaxium Messenger Keep it's Logs?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-09-09
I've been using Galaxium messenger for a while now as it's really the only Linux Messenger client I feel comfortable with, but one thing bugs me about it. It says that the conversation is being logged, but I can't find said logs anywhere! Does anyone know where they might be kept?

---

### Post by unutbu on 2008-09-09
I can't say for sure if this will work, but perhaps try
```

lsof -c galaxium
```

(change 'galaxium' to whatever command is used to start galaxium.)

The lsof command will list all files that are currently opened by galaxium.

If galaxium does not have the log file open at that moment, then the lsof command will not find the log file. 

Moreover, most apps are well behaved in the sense that they do not write to lots of different directories. Even if the log file per se is not listed in the lsof output, the output may give you a clue about which directories to check.

If the lsof output is too copious, try
```

lsof -c galaxium | less
```

---

### Post by whitethorn on 2008-09-09
Hi, I also have galaxium on my PC.  I just had a look and you can find the logs under

/home/your_user/.config/Galaxium/History/MSN/user@hotmail.com/nameofcontact@hotmail.com.db

:)

---

