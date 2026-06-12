---
title: "[SOLVED] Ubuntu won't start up... it died..... ;_;"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by CJ Master on 2008-10-19
Hello...

Alright main problem: Ubutnu wont start up. It gets around 60% on the progress bar the goes to a command prompt, except nothing works. (I tried "help", "start", "ubuntu", ect...)

Wondering why the topic prefix is "all varients"? Well my ubuntu start up is really pretty weird..... it uses Kubuntu to start up, Xubuntu for the login screen, and then it goes into ubuntu.

...And the thing is there's no apperent errors on the text propt either, the only one is that the firewall thingy didn't start up, and that was on the very top, not near the prompt.

:confused::confused::confused:

---

### Post by overdrank on 2008-10-19
> **CJ Master said:**
> Hello...

Alright main problem: Ubutnu wont start up. It gets around 60% on the progress bar the goes to a command prompt, except nothing works. (I tried "help", "start", "ubuntu", ect...)

Wondering why the topic prefix is "all varients"? Well my ubuntu start up is really pretty weird..... it uses Kubuntu to start up, Xubuntu for the login screen, and then it goes into ubuntu.

...And the thing is there's no apperent errors on the text propt either, the only one is that the firewall thingy didn't start up, and that was on the very top, not near the prompt.

:confused::confused::confused:

Hi and are you able to boot recovery mode ?

---

### Post by CJ Master on 2008-10-19
Well unless theres another way to boot into recovery mode besides the login screen, no.

---

### Post by jerome1232 on 2008-10-19
To try recovery mode mash the 'esc' key while your computer is booting up, you should get what's called the 'grub menu' it'll have a list of kernels, pick the highest one up that says recovery in it.

---

### Post by CJ Master on 2008-10-19
Unfortunantly I installed it via windows so I get the wubi menu. I tried doing that before though, but unfortuantnly it only gives the option of Windows or Ubuntu. (Weirdly not kubuntu or xubuntu, but I don't really care right now :P)

---

### Post by Bucky Ball on 2008-10-19
When you boot up, hit 'esc' and see if that takes you to a grub menu. If so, the recovery is the second one down. I am presuming you are booting and it is taking you straight to login without giving you the grub selection splash.

UPDATE: Sorry, Jerome1232 beat me to it! :)

---

### Post by jerome1232 on 2008-10-19
My laptop has a wubi install. I'm positive right after you select ubuntu, you can mash esc to get that grub menu.

---

### Post by CJ Master on 2008-10-20
Whoo, thanks very much, I did some repairs and now I hope i wont have to see windows again. :P

---

### Post by Bucky Ball on 2008-10-20
Great news. Quick overview of what you did to get it going, if you remember? Others with the same issue might then benefit from your efforts, too. :)

---

### Post by CJ Master on 2008-10-20
Sure thing.

Well I pressed ESC like a madman and got to the grub menu.

Then simply all I did was choose to repair the system files and fix the packages.

Then I restarted it and normal mode then, BOOM! Working Ubuntu. =]

---

