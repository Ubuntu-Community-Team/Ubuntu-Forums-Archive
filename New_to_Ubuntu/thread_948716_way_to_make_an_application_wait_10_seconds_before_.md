---
title: "way to make an application wait 10 seconds before it opens?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-10-15
like the title says i need to make some of my startup applications wait 10 seconds before opening 

the reason for this is that when i login i get a huge grey square around awn and conky, and if i close and then re-open them they work fine

---

### Post by howefield on 2008-10-15
Use the sleep command

eg sleep 10;pidgin

makes pidgin wait 10 seconds before launching, I guess you could add this to your sessions menu ?

---

### Post by lovinglinux on 2008-10-15
I have a script like that, which opens conky, cairo, tomboy....

just use the sleep command as mentioned above and add the script to the session. You can also give different sleep times to each application.

---

### Post by tjwoosta on 2008-10-15
thanks guys its working

---

