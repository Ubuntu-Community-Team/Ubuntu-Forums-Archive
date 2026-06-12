---
title: "Ubuntu root Password"
date: 2008-08-08
forum: Recurring Discussions
---

### Post by docPhunk on 2008-08-08
ok i just changed my root password in xubuntu hardy and it was a simple

sudo passwd

and it prompted me to enter the new password without asking for the old password. it was a fresh terminal so i know it didn't already have root access. now im no guru or anything but couldn't a malicious script take advantage of this to set a password and gain root access. someone should check this out and let me know if im totally wrong.

---

### Post by -grubby on 2008-08-08
If you've used sudo in the last 15 minutes or so, your root password is saved for other programs to use without requiring you to enter your pass

---

### Post by docPhunk on 2008-08-08
ah so supposing some nasty batch got lucky it could gain root, i know i use sudo every 2 minutes or so and bet a lot of others do too. is there a way to disable this "grace period"

---

### Post by kajillin on 2008-08-08
Thats why we usualy suggest not to run as administrator. And if ur network is secure u realy shouldnt worry, and if its not i would be more worried about that.

---

### Post by docPhunk on 2008-08-08
well i use 'sudo cp' a lot to move app files into usr/local/whatever and 'sudo rm' to delete files without moving to trash since thunar doesnt let me delete files directly. as far as my network goes i got no worries this comp is behind a dedicated BSD firewall. i was only asking cuz it seems to be mn easily fixable hole in security

---

### Post by schauerlich on 2008-08-08
This post should help you do what you want:

[http://ubuntuforums.org/showpost.php?p=1093040&postcount=2](http://ubuntuforums.org/showpost.php?p=1093040&postcount=2)

Just set it to 0

---

### Post by sisco311 on 2008-08-08
> **docPhunk said:**
> well i use 'sudo cp' a lot to move app files into usr/local/whatever and 'sudo rm' to delete files without moving to trash since thunar doesnt let me delete files directly. as far as my network goes i got no worries this comp is behind a dedicated BSD firewall. i was only asking cuz it seems to be mn easily fixable hole in security

If you want to permanently delete a file in Thunar, hold down the Shift key while pressing Del or selecting Delete from the menu. You will still need to confirm the permanent removal.(Shift+Del+Enter)

---

### Post by docPhunk on 2008-08-08
> **sisco311 said:**
> If you want to permanently delete a file in Thunar, hold down the Shift key while pressing Del or selecting Delete from the menu. You will still need to confirm the permanent removal.(Shift+Del+Enter)

thats much easier thanks a lot all. im fairly new to the ubuntu community and you guys are awesome, i ask obscure questions at 1 in the morning and get answers in minutes. long live ubuntu

---

### Post by mcduck on 2008-08-08
..and if you are the owner of those files simple "rm" would also rmeove them without moving them to trash. No "sudo" needed. ;)

Actually I'd say most users don't need to use "sudo" that often. But, like already mentioned, the timeout can be changed.

---

### Post by Dremora on 2008-08-08
The whole argument over sudo vs su is pointless in my opinion, they both basically give you the same thing, it's just that sudo keeps a better "whodunnit" log and lets you manage accounts more easily.

As for scaring users away from using a root terminal, I always roll my eyes when someone links to the RootSudo page on the wiki, both are a tool, and maybe sudo is giving them a 9mm Beretta to shoot themselves in the foot with instead of a .44 Magnum, but they can both do considerable damage if not used right.

---

### Post by meborc on 2008-08-08
> **Dremora said:**
> As for scaring users away from using a root terminal, I always roll my eyes when someone links to the RootSudo page on the wiki, both are a tool, and maybe sudo is giving them a 9mm Beretta to shoot themselves in the foot with instead of a .44 Magnum, but they can both do considerable damage if not used right.

the link in question - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

you can nuke your box in million different ways, the point in linking the rootsudo page is to distribute information about the sudo and su differences... from there on it is everyones own decision what to use

the important thing is that people know what they are using and what they are risking in doing so :D

---

### Post by baggins on 2008-08-08
> **nathangrubb said:**
> If you've used sudo in the last 15 minutes or so, your root password is saved for other programs to use without requiring you to enter your pass
Yes but only within the terminal in which sudo was used. So [[COLOR="Green"]docPhunk[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5546498&postcount=3")'s nasty batch script would have to be executed in the same terminal. 
My usual MO is to use sudo in one terminal window and everything else in another. Like a friend said (freely translated from danish)  "the art of avoiding screwups, is to _not_ do stupid things!" :)


> **meborc said:**
> 
the important thing is that people know what they are using and what they are risking in doing so :D

Amen! :)

-- Jon

---

### Post by docPhunk on 2008-08-08
> **baggins said:**
> Yes but only within the terminal in which sudo was used. So [[COLOR="Green"]docPhunk[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5546498&postcount=3")'s nasty batch script would have to be executed in the same terminal. 
My usual MO is to use sudo in one terminal window and everything else in another. Like a friend said (freely translated from danish)  "the art of avoiding screwups, is to _not_ do stupid things!" :)




Amen! :)

-- Jon

im not so sure about that i used a fresh terminal to change my pw and it didnt prompt for the root pw. i wish id copied the term.

---

### Post by meborc on 2008-08-09
> **docPhunk said:**
> im not so sure about that i used a fresh terminal to change my pw and it didnt prompt for the root pw. i wish id copied the term.

it works like this: if you use sudo in one terminal and close it and open new terminal, then the password is still saved... BUT if you use sudo in one terminal, close it and open two terminals, then the one you opened last, will not have the password saved... stupid, i know...

---

### Post by baggins on 2008-08-09
> **meborc said:**
> it works like this: if you use sudo in one terminal and close it and open new terminal, then the password is still saved... BUT if you use sudo in one terminal, close it and open two terminals, then the one you opened last, will not have the password saved... stupid, i know...

Ok really? 
I always have 3-4 terminals open and rarely close any of them, so maybe that's why I've never had any problems. Or even noticed that sudo remembers passwords in this way. This actually seems unsafe, IMO.

-- Jon

---

