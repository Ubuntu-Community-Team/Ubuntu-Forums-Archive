---
title: "USERS appearred out of nowhere"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by spiderDuck on 2013-09-02
Hello. During some time yesterday, my laptop showed 6 more users than it should! I had only created 1 user and the other option was the Guest one. But yesterday there were about 6 others called names like "qmailr, qmailp, qmails" and so on. I could not delete them; not even through terminal with sudo commands, and also I could not turn off my laptop. I could just log out. I have formated the laptop since yesterday (not for this reason) so these users do not exist anymore. I just wanted to know what happened, if anyone knew, and what I am supposed to do if it happens again. Thank you in advace.

---

### Post by nerdtron on 2013-09-02
Some programs create a "user account" when they are installed. Example is the ubuntu-virt-server which will create the user/group libvirtd.
Don't worry, those account don't have password and you won't be able to use them to login to you computer. 
What program/s did you install before the accounts appeared? I think you installed qmail?

---

### Post by spiderDuck on 2013-09-02
I don't remember installing qmail but I was trying to get my wifi working at the time (actually I still am!) and since I'm no experienced user I probably downloaded qmail without being aware of it. However,do these accounts remain there forever? Is there not a way to delete them or just hide them somehow?

---

### Post by nerdtron on 2013-09-02
Those will be deleted when you uninstall the program that they came with. I'm not 100% sure but I think it does.

---

