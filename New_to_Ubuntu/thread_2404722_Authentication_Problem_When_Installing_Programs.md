---
title: "Authentication Problem When Installing Programs"
date: 2018-10-27
forum: New to Ubuntu
---

### Post by amandavanbeek on 2018-10-27
Sorry, newbie here.

I've downloaded the .deb file for Teamviewer and am trying to install the program. When clicking on "install" an authentication prompt comes up and I enter my password. The prompt goes away again, but the installation doesn't resume. Instead, I see the button "install" again. 

Am I missing something? Please help!

---

### Post by oldrocker99 on 2018-10-27
Try this:
```
sudo dpkg -i programname.deb
```

---

### Post by amandavanbeek on 2018-10-28
It doesn't work, doesn't recognize the filename?

---

### Post by amandavanbeek on 2018-10-28
error: cannot access archive 'teamviewer_13.2.26559_amd64.deb': No such file or directory

---

### Post by Impavidus on 2018-10-28
First go to the right directory. And to avoid typos in the filename, use tab completion. When you hit <tab>, the shell will try to complete the filename for you. If you stored the .deb file in Downloads, for example, use:```
cd Downloads
dpkg -i teamview<tab>
```

---

### Post by amandavanbeek on 2018-10-28
bash: syntax error near unexpected token `newline'

---

### Post by amandavanbeek on 2018-10-28
OMG it works!!! Thank you soooo much!!

---

