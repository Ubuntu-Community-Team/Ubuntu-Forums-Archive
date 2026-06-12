---
title: "Small BASH clarification"
date: 2012-01-22
forum: Programming Talk
---

### Post by raja.genupula on 2012-01-22
I am a BASH learner .Recently at the time of playing with bash i have got this problem.


```
raja@raja-desktop:~$ chmod +x try.sh ; ./try.sh
[sudo] password for raja: 
root@raja-desktop:~# 

```
that's the output of script and code is

1 sudo -i
2 apt-get update 

(dont worry about that numbering , its just for understanding the lines)

so update not running why ?

Thanks in advance.

---

### Post by Lars Noodén on 2012-01-22
Your script also needs to declare which script interpreter it will use.  That needs to go on the very first line before anything else.

```

#!/bin/sh

sudo apt-get update 

```

Note that sh is different from bash in some ways.  It is actually [dash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dash.1.html)

Edit: changed to reflect Bachstelze's observation.

---

### Post by Bachstelze on 2012-01-22
That won't work because sudo -i spawns a new shell, so your update will only run after the shell has exited. Why not just do sudo apt-get update?

---

### Post by raja.genupula on 2012-01-22
Hi thank you guys , actually that's a solution . But what my case is i need to run a bunch of code as root . so how can i move there ? 

adding sudo to all commands is one solution . is there any other solution ?

Thank you guys.

---

### Post by Lars Noodén on 2012-01-22
You could run the script itself as root and then anything the script does will be as root.

e.g.
```

sudo ./try.sh

```

---

### Post by raja.genupula on 2012-01-22
> **Lars Noodén said:**
> You could run the script itself as root and then anything the script does will be as root.

e.g.
```

sudo ./try.sh

```

Yeah this one really good for me.

Thanks man
thank you very much .

---

### Post by ofnuts on 2012-01-22
> **raja.genupula said:**
> Hi thank you guys , actually that's a solution . But what my case is i need to run a bunch of code as root . so how can i move there ? 

adding sudo to all commands is one solution . is there any other solution ?

Thank you guys.
Prefixing the necessary commands with "sudo" isn't as bad as it looks, since you don't need to enter your pwd again when running successive sudo's from the same shell within some time span (15mn IIRC) . 

Sudo'ing the whole script gives you root privs for the whole script, bugs could be quite fatal :)

---

### Post by raja.genupula on 2012-01-22
> **ofnuts said:**
> Prefixing the necessary commands with "sudo" isn't as bad as it looks, since you don't need to enter your pwd again when running successive sudo's from the same shell within some time span (15mn IIRC) . 

Sudo'ing the whole script gives you root privs for the whole script, bugs could be quite fatal :)

actually my script is small one , i mean just 10 lines thats it . so i think i no need to worry about bugs .

Regarding my issue i think i need to run that script with root command as mentioned Lars Noodén.

Thanks to all for helping me.

---

### Post by ofnuts on 2012-01-22
> **raja.genupula said:**
>  so i think i no need to worry about bugs .
Famous last words....

---

