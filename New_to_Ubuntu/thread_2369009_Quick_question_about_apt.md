---
title: "Quick question about apt"
date: 2017-08-17
forum: New to Ubuntu
---

### Post by radioactive.exe on 2017-08-17
I've dabbled in arch (specifically with manjaro) and the one thing that I really liked was the "pacman" package manager, specifically I could update and upgrade everything just by typing "sudo pacman -Syu". 

That being said I primarily use ubuntu and ubuntu based distros, so I was wondering if there was a similar command for apt. Right now when I want to do the same thing, I have to type "sudo apt update && sudo apt upgrade", so the question is can I just do "sudo apt <insert command> " and achieve the same thing as with pacman? 

---

I am a relatively new user to ubuntu and linux as a whole, so I'm probably missing something obvious.

---

### Post by vasa1 on 2017-08-17
Can't you come up with an alias you like?

---

### Post by ajgreeny on 2017-08-17
Or you could simply create a root cron job to run the **apt-get update** command automatically every day or twice daily, whatever you want, then run **sudo apt upgrade**  manually whenever you want.

---

### Post by johndough2 on 2017-08-19
Hi

Doesn't the root terminal remember previous commands and allow you to scroll thru?  One arrow key, and then Enter?

Obviously if you use the terminal frequently then....

---

### Post by ajgreeny on 2017-08-19
> **johndough2 said:**
> Hi

Doesn't the root terminal remember previous commands and allow you to scroll thru?  One arrow key, and then Enter?

Obviously if you use the terminal frequently then....

Yes, it does, just the same as the normal user terminal, so you have a good point, unless this user makes a lot of use of the root terminal for other command-line work and then might have to search through the history.

However, a simple alias to run the update and upgrade commands in the user terminal would be most sensible as suggested by vasa1, eg
```
alias upgrade='sudo apt update && sudo apt upgrade'
```

---

