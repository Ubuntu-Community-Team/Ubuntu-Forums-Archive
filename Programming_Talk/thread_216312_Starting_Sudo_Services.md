---
title: "Starting Sudo Services"
date: 2006-07-15
forum: Programming Talk
---

### Post by larry on 2006-07-15
Hello,

I recently learned how to export a directory to my path by editing the bash_profile file.
Now, I also need to start automatically, every time I switch on the machine, a service as a superuser.
Of course I want everything to take place "silently" without being prompted for a password.
Which file should I modify for that? And how?
Many thanks

Larry

---

### Post by LordHunter317 on 2006-07-15
This belongs in the server or a desktop support forum, not here really.   You also titled the thread pretty badly; 'How to start a program at boot' would be more descriptive.

You'll want to write an initscript.  You can probably copy an existing initscript (/etc/init.d) and modify it to your needs.  Then link it into /etc/rc2.d, following all the other scripts there.

---

