---
title: "Nvidia X Server settings window blank"
date: 2021-10-03
forum: New to Ubuntu
---

### Post by optmed on 2021-10-03
hi everyone, 

Ubuntu 20.04 on a HP ZBook G2 here. By way of trying to address the issue described at [https://ubuntuforums.org/showthread.php?t=2467506&p=14060865#post14060865](https://ubuntuforums.org/showthread.php?t=2467506&p=14060865#post14060865), I switched to "Intel" using the "Nvidia X Server settings". 

Now, after re-booting, the "Nvidia X Server settings" window is blank (please see screenshot)...what can I do?

thanks!

---

### Post by optmed on 2021-10-03
I did some digging, and came across this command, which returned the following result: 

 [I]$ prime-select query
nvidia

[/I]which (I guess) shows that switching to "nvidia" through "Nvidia X Server settings" didn't quite work as expected...

I then did 

[I]$ sudo prime-select intel

[/I]which (after re-booting) did the trick: 

[I]$ prime-select query
intel

[/I]except that the main dialogue "Nvidia X Server settings" remained blank...

any idea?

---

