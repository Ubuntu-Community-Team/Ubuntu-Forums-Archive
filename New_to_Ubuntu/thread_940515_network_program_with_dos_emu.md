---
title: "network program with dos emu"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by alpdo on 2008-10-07
i have this old dos accounting program which i share with everyone else...
everyone needs to run this program but the thing is when two machines are trying to run the program at the same it just wont run. but with dos box i runs just fine... in dosbox i cant print which i the program im trying to run needs to print...  anyone help???

---

### Post by talsemgeest on 2008-10-07
Do you know if it is supposed to run on more than one machine? Perhaps (but probably not, if it is an old dos program) there is some form of drm prevening it from running?

Sorry I can't be of more help. :(

---

### Post by faytaliti on 2008-10-07
first what program are you using.... If it's something like tally it should work on wine.
wine is a compatibility layer between linux and windows.
 you can install it by saying:
```
sudo apt-get install wine
```

---

### Post by alpdo on 2008-10-09
ok i tried running it on wine but it doesn't work....
i tried a little experimenting ....

what i did is that i have overwritten the command.com in freedos with the command.com from windows 98 :)
when i run my old dos program over the network from one of my pc's it work fine... but when i tried running on 2 computers it  says "bad command or filename"... my old dos program is supposed to be a multiuser system... but i can only run pc at a time.... 

is there a need to change anything with the dosemu.conf????

---

### Post by alpdo on 2008-10-10
ok ive stop for a while and tried putting my files on my ubuntu box then share it over the network... 
i mounted the network to one of my ubuntu machines then tried running the old dos programs... 
it just says access denied...
any ideas???

---

