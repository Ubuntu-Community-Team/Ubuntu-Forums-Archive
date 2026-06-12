---
title: "Hibernation?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-16
1. Where is hibernation located in Ubuntu?

2. Can it be turned ON & OFF like in windows?

3. It's pros & cons?

Thanks.

---

### Post by john rosswrock on 2013-01-16
There is a way to do it and that is using terminal 
use this code:  sudo pm-hibernate      
or 
sudo pm-suspend-hybrid 
But before that know this that in Ubuntu 12.04 and newer, hibernation has been disabled by default in policykit and do read man pm-action.  

NOTE:THIS COMMAND IS A BIT RISKY (my computer sortof hang after i ran pm-hibernate,but that was due to low swap area)

---

### Post by john rosswrock on 2013-01-16
Hibernation cannot be turned on and off like windows thats wat i think i m not sure about it:(

---

### Post by irv on 2013-01-16
You can also turn it off and on under the power settings.
[ATTACH]230138[/ATTACH]

---

### Post by Yezinki on 2013-01-16
Thanks for replying.

How can I know that hibernation is ON or OFF on my machine running 12.04?

---

### Post by john rosswrock on 2013-01-16
> **irv said:**
> You can also turn it off and on under the power settings.
[ATTACH]230138[/ATTACH]

but the hibernate option is diabled over there and can only be possible through terminal

---

### Post by john rosswrock on 2013-01-16
> **Yezinki said:**
> Thanks for replying.

How can I know that hibernation is ON or OFF on my machine running 12.04?

Normally hibernate is always off and only runs when invoked through teminaland once the computer comes back from hibernation then the hibernate disables again.

---

### Post by irv on 2013-01-16
> **john rosswrock said:**
> but the hibernate option is diabled over there and can only be possible through terminal

Yes, Suspend works but not Hibernation. It is turned off because of bugs. There is a bugs report on this, also see:
[http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html")
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/990129]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/990129")
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/990129]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/990129")

---

### Post by john rosswrock on 2013-01-16
Thax irv for the info

---

### Post by Yezinki on 2013-01-16
Thanks.

---

