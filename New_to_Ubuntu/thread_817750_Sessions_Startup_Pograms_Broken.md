---
title: "Sessions Startup Pograms Broken"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by jakeo25 on 2008-06-03
Hello,

I added an entry to the System->Preferences->Sessions-> Startup Programs in Hardy and broke something.  I am unable to login, with the message "Authentification failed".  Yes, I was trying to make my wireless network automatically connect.  

When I research this, posts talk about a 

$HOME/.gnome2/session 

file, but there is none on my machine.

I have started Hardy in safe mode and need to know which file has the session information that I can manually edit, or restore to a default configuration.

Thanks in advance.

Jake

---

### Post by aysiu on 2008-06-04
When you're in recovery mode, type ```
cd /home
ls
``` Can you see your username in the list? And, if so, what happens if you type ```
cd /home/*username*/.gnome2
ls
```? 

Is *session* not in that list?

---

