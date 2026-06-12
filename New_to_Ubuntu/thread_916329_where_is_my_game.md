---
title: "where is my game??"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-10
I dwnloaded the game super maryo chronicles or smc using the package manager, but now i cant find it, its not in the games menu?

where is it?

how can i activate it? any terminal command?

thx

---

### Post by Crafty Kisses on 2008-09-10
Run the package name in the Terminal.

---

### Post by faraz_k86 on 2008-09-10
i tried that but i dont know what to write, i tried smc and supermaryochronicles but on both i got a command not found

---

### Post by ByteJuggler on 2008-09-10
> **faraz_k86 said:**
> i tried that but i dont know what to write, i tried smc and supermaryochronicles but on both i got a command not found

OK, general, in cases like this, you'd go back into Synaptic, find the package (smc in this case), click on the "Properties" button, and go and check what files the package installs where.  Then you can usually deduce where the program file has been put.  In this case, the program file is at:

```
/usr/games/smc
```

Normally (on my gutsy server) "/usr/games" is on the search path by default, so just entering "smc" at the prompt therefore finds the program file and starts it.  In your case I surmise that "/usr/games" is therefore not on the search path for whatever reason, hence why you get "command not found" error.  You can enter the full path in the meantime (as above), or you can fix your PATH to include /usr/games.  Or you can create yourself a new launcher for the game on the desktop.

---

### Post by faraz_k86 on 2008-09-11
k thx so what i shud do in the terminal is cd /usr/games[ is this command right?] and then type smc, will that work?

and if i have to make a new launcher, what should i write in the command box?

---

### Post by ad_267 on 2008-09-11
You only have to type smc, because /usr/games is in your PATH. You can use smc for the command in a launcher.

---

### Post by faraz_k86 on 2008-09-11
what do you mean by "in ur path"

like i said when i type only smc in terminal i get a command not found??

---

### Post by Bulat Sirazetdinov on 2008-09-11
You can use menu customizer: Applications->Add/Remove...
Maybe your "smc" game is available there to add to Games menu.

---

### Post by robalcorn on 2008-09-11
I installed it from :[http://www.getdeb.net/release/2630](http://www.getdeb.net/release/2630)

first install smc-data than install smc and it will put the icon in for you under applications/games

---

### Post by t0p on 2008-09-11
Or, you can run it from the terminal by typing in

```
/usr/games/smc
```

---

### Post by ad_267 on 2008-09-11
Oh ok well /usr/games is in my path but maybe not yours.

Your path is a list of directories where the shell will look for executable files if you type a command.

---

### Post by faraz_k86 on 2008-09-12
thanks guys, the command /usr/games/smc/ worked.

---

