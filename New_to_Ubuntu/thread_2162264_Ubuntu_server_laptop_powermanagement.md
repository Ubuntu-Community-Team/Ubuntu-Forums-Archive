---
title: "Ubuntu server laptop powermanagement"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by rez001 on 2013-07-13
Hey all!


Ive been trying to figure out how to have my laptop stay on while the lid is down. I don't want a gui on my laptop so this is all terminal. Can anybody help me by providing the exact code I need to fix this issue.


version : 12.04.2 LTS


Thank you !

---

### Post by farrinux on 2013-07-13
Look here..... [http://askubuntu.com/questions/141866/keep-ubuntu-server-running-on-a-laptop-with-the-lid-closed](http://askubuntu.com/questions/141866/keep-ubuntu-server-running-on-a-laptop-with-the-lid-closed)

---

### Post by Sin@Sin-Sacrifice on 2013-07-13
Search for the cli equivelent to this: [http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid)

If I ran Ubuntu I might know it, but unfortunately I do not. Should lead you in the right direction anyhow.

---

### Post by rez001 on 2013-07-13
thanks guys both of the links lead me to the right direction... 

for 12.04.2 LTS this is how I did it.

/etc/acpi/events/           (if you don't have acpi then sudo apt-get install acpi)



inside of it is the green text powerbtn.sh

sudo nano powerbtn

the last two lines you comment by putting # infront of it

# event=button................
# action=......................

(*btw the ....... is the rest of it i just didnt want to type it out)

then restart the server

---

### Post by farrinux on 2013-07-14
You are welcome.  Please make sure to mark this thread solved.

---

