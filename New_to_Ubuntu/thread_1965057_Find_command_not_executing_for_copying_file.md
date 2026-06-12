---
title: "Find command not executing for copying file"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by sandip250382 on 2012-04-25
Buddies, I am trying to copy the file 'xcopyq' from /home/sandip to /home/sandip/testdir using the below command and getting the error as shown below:-

sandip@manu:~$ find /home/sandip -type f -name '*xcopyq*' -exec cp{} /home/sandip/testdir/ \:
find: missing argument to `-exec'

Am I correctly writing the code ?

Any inputs will help me a lot.

---

### Post by Vaphell on 2012-04-25
```
find /home/sandip -type f -name '*xcopyq*' -exec [COLOR="Red"]cp{}[/COLOR] /home/sandip/testdir/ \[COLOR="Red"]:[/COLOR]
```

; is the proper ending marker
also parts of the command should be clearly separated, which is not the case with cp{}
```
... cp "{}" ...
```
"" as a safeguard against cp breaking names up to pieces on space chars.

---

