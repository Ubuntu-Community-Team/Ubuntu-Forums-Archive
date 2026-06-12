---
title: "Installing Matlab...? No permission to create a directory"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by link- on 2008-06-19
I'm installing Matlab and when it ask me for the Matlab root directory I wrote /usr/local/Matlab2008, and its says that it will create file directory but then I get a message that I don't have permission to create '/usr/local/Matlab2008'.

Any help?

---

### Post by Sarah L on 2008-06-19
/usr/local is a system directory, so normal users won't be able to write to it. Did you run the installer using sudo?

Alternatively, you can install in a directory where you have write privileges (such as someplace in your home directory).

---

### Post by link- on 2008-06-19
No I didn't run it using sudo... I double click on installer and that's it. How do I run on sudo?

---

### Post by link- on 2008-06-19
Forget it I already run it on sudo. Solved

Thanks 
-link

---

