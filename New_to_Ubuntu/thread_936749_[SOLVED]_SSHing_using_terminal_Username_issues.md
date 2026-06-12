---
title: "[SOLVED] SSHing using terminal Username issues"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2008-10-03
Ey guys, so I need to ssh to a computer on campus. It connects fine and everything but only one problem. It doesn't ask for my username. Only my password. It says: 

"aaron@T60:~$ ssh -X round.math.ucdavis.edu
The authenticity of host 'round...)' can't be established.
RSA key fingerprint is b8:....:c5.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'round....5' (RSA) to the list of known hosts.
aaron@round....u's password: 
Permission denied, please try again."

It doesn't even prompt me for my username, which is different from aaron@T60 on the computer I'm sshing to. Any help greatly appreciated!

---

### Post by TheLions on 2008-10-03
try ssh -X [email]username@round.math.ucdavis.edu[/email]

---

### Post by StunnerAlpha on 2008-10-03
You, sir are a friggin genius!

---

### Post by TheLions on 2008-10-03
Thanks!

---

