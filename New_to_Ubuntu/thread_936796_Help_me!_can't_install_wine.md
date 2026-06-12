---
title: "Help me! can't install wine"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by sza on 2008-10-03
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87140&stc=1&d=1223030387[/IMG]

someone knows what the problem is?

---

### Post by Ryadt on 2008-10-03
Have you got backports update checked in the repos?
If so uncheck it and then retry.

---

### Post by MattThLinuxNewb on 2008-10-03
It looks like you need to enable some other repositories. In synaptic, try going to Settings > Repositories then check the (universe) (restricted) and (multiverse) boxes and try again.

---

### Post by sza on 2008-10-03
well, it looks like the wine version is for ubuntu 8.04, while I'm using 7.10...

can someone give me a version that works with ubuntu 7.10? because I've tried to install ubuntu 8.04 on my computer and I can't connect with it to the wireless while with the 7.10 I don't have that problem...
I prephere using the 7.10 version- can someone please give me a link to whine that works with ubuntu 7.10?

10X all

---

### Post by Ryadt on 2008-10-03
Uncheck the proposed and backports update in Software sources.
Then```
sudo apt-get update
```
Then retry to install.

---

### Post by sza on 2008-10-03
Thanx, you directed me to the problem...
when I looked in the software source i saw that in that window:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87141&stc=1&d=1223034284[/IMG]

the 3rd option was checked... I've unchecked it and tried again and it workd... 
thank you a lot!

---

### Post by Ryadt on 2008-10-03
It's under the Updates tab. Next to the one you are under.;)

---

### Post by sza on 2008-10-03
now I have another problem with wine...
I installed it because I want photoshop to run under my ubuntu...
so when I want to install it with wine, I have an error:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87143&stc=1&d=1223036938[/IMG]

<I've right clicked on the "setup.exe" file and told it to be opened with the program "wine" - is this the way to make it work?
why isn't it working?

10X

---

### Post by oldos2er on 2008-10-03
I googled this: [http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps) but it's for Dapper.

---

