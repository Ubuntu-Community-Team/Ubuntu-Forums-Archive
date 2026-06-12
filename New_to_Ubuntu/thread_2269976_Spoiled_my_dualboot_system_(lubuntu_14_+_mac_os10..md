---
title: "Spoiled my dualboot system (lubuntu 14 + mac os10.4.) with bootrepair , cannot instal"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by max97 on 2015-03-19
Hi folks!

i was so happy i got 2 systems working on my ppc (11.2) : lubuntu was working next to mac os 10.4 !!!
i upgraded and updated everything - just didnt get my bluetooth adapter working but thought i gonna solve this problem....
Then the bootloader didnt work good ( i had to start 3 times) so i checked out the bootrepair program - i just used the automatic function ...
in the end a window opens and says . u have no grub-packeges enabeled, couldnt install a new grub2, so u got no grub on yo system anymore !!!

And this url :  [http://paste.ubuntu.com/10569812](http://paste.ubuntu.com/10569812)

I dont know if it is really the way to solve it but the program told me to write it down and maybe someone can help me....
Is there a way to get my dualboot (both systems, mainly mymac ) back again ? in the moment even the mac repair doesnt recognize the system but under lubuntu live knows about that partition...

hope someone can help me!??

Max

---

### Post by benrob0329 on 2015-03-19
Did boot-repair install grub? if not, you should run boot-repair again.

---

### Post by max97 on 2015-03-19
Hi thank u for your fast reply !

i run boot-repair the 3rd time ....  i guess i did sth wrong !?
i started a live-session mounted thebootloader-sections and harddrives and let run boot-repair - what i posted was the result again

---

### Post by benrob0329 on 2015-03-19
Are you running Boot-Repair as Sudo?
Can you boot to Lubuntu? If so, do a boot repair from there.

---

### Post by max97 on 2015-03-19
Yes im running it as sudo, but cant boot to Lubuntu -  i can make my choice it starts booting, but then stops with a terminal where i cant write sth and the letters are yellow...

---

### Post by benrob0329 on 2015-03-19
What are the choices?

---

### Post by max97 on 2015-03-19
cd-Linux-Mac Osx

---

### Post by benrob0329 on 2015-03-19
So:
```
CD
LINUX
MAC OS
```
Right?

---

### Post by max97 on 2015-03-19
exactly

for:
CD - c
Linux- l
Mac osx- x

---

### Post by benrob0329 on 2015-03-19
That doesn't look like grub, might be using a Macintosh boot loader. Do you sill have your installation CD?

---

