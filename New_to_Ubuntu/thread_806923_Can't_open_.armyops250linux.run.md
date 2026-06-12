---
title: "Can't open ./armyops250linux.run"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-25
Okay so i got americas army 2.5 off of filefront for linux..installed it to my desktop..i read the directions from this site 

[https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy)

i put in the sudo code   "sudo sh ./armyops250linux.run"

and then i tried it this way sudo sh ./armyops250-linux.run

then it says  "Can't open ./armyops250-linux.run"
what is going on? whats the right code?

---

### Post by shifty_powers on 2008-05-25
try

```
sudo chmod a+x ./armyops250linux.run
```

first

---

### Post by konungursvia on 2008-05-25
Two things: you might have to make sure it is executable in terms of permissions. You can chmod the file in terminal to make sure it's an executable according to your system. Then try 

```
./army* 
```

---

