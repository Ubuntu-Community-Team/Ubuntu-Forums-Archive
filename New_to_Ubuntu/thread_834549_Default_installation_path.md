---
title: "Default installation path?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by kenai- on 2008-06-19
Is there a default installation path in ubuntu where all the applications end up?

I'm trying to find the file "gtkrc-2.0" ( "~/.purple/gtkrc-2.0" ), so I can customize the chat window in pidgin.

---

### Post by chrisccoulson on 2008-06-19
"~/.purple/gtkrc-2.0" is part of your Pidgin user profile. This is different to where the application is stored. The tilda character "~" actually refers to your home folder (/home/<user_name>), and if you type it in to a terminal it will be substituted automatically:
```
gedit ~/.purple/gtkrc-2.0
```

---

### Post by kenai- on 2008-06-19
> **chrisccoulson said:**
> "~/.purple/gtkrc-2.0" is part of your Pidgin user profile. This is different to where the application is stored. The tilda character "~" actually refers to your home folder (/home/<user_name>), and if you type it in to a terminal it will be substituted automatically:
```
gedit ~/.purple/gtkrc-2.0
```

Awesome, worked just fine. Thanks! :)

---

