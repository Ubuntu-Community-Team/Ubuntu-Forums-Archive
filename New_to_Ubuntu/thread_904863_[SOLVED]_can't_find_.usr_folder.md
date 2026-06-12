---
title: "[SOLVED] can't find .usr folder"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by scotcella on 2008-08-29
Hi all,

I wanted to add some a custom Australian English dictionary for open office, and I need to install it in /usr/lib/openoffice/share/dict/ooo

I can't find the /usr folder anywhere even though I have opened the Home folder and pressed CTRL + H.

But when I type in the location manually, it shows up and opens the right folder..odd

How can I see it so it shows on my screen?

---

### Post by m_ad on 2008-08-29
Confused what you mean. Can't you just navigate nautilus to /usr?

---

### Post by mikewhatever on 2008-08-29
There is a difference between .usr and /usr. I've never seen anything like .usr, while /usr is just where it should be. It isn't in your home folder, since home is /home/your-name.
What do you have to do to add the dictionary? To open /usr with nautilus, press alt+f2 and type nautilus /usr.

---

### Post by hopkinsjeni on 2008-08-29
My USR folder is accessible by going to 
computer > Filesystem > USR
not my home folder, hope that helps

---

### Post by wolfen69 on 2008-08-29
just do ```
gksudo nautilus
``` and go to usr folder. then copy and paste.

---

### Post by Joeb454 on 2008-08-29
or if you prefer the easy way, hit Alt+F2 and enter ```
gksudo nautilus /usr/lib/openoffice/share/dict/ooo
```

---

### Post by scotcella on 2008-08-29
> **hopkinsjeni said:**
> My USR folder is accessible by going to 
computer > Filesystem > USR
not my home folder, hope that helps

Ah this was what I was trying to look for.....  oops yes..  this one..

Yes I already know about the gksudo nautilus command

But was trying to the manual way of getting there was I was doing something else as well..  

Thanks to all those that posted..  it had been while and couldn't work out why I could use the nautilus but the hand to mouse way wasn't going where I wanted it to...

---

