---
title: "Don't know how to run Jedi Outcast..."
date: 2013-04-16
forum: New to Ubuntu
---

### Post by MadleSs on 2013-04-16
Hi guys,
I'm trying to run Jedi Outcast... I have downloaded it from this page
 ```
https://github.com/xLAva/JediOutcastLinux
```
But when I try to run ./jk2sp this message appears...
```
Initialising zone memory .....
----- FS_Startup -----
Current search path:
/home/radovan/Videos/JediOutcastLinux-JediOutcastLinux/code/Release/base

----------------------
0 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/radovan/Videos/JediOutcastLinux-JediOutcastLinux/code/Release/demo

----------------------
0 files in pk3 files
Error: Couldn't load default.cfg


```
Can anyone help? thanks...

---

### Post by The Squig on 2013-04-17
This looked interesting so I had a go. worked for me. Did you install it correctly? You will still need the original game to use this.

1. First of all you only need two files from the git repository. they can be found in code/release
[LIST]
[*]jk2gamex86.so
[*]jk2sp
[/LIST]

2. Secondly you need some orignal files from the game. either install the game in windows or use wine. After you install the game apply the  1.04 patch. this is required according to the instructions.

3. Now locate the directory where you installed the game and copy the _"base"_ folder located in GameData. Place it in the directory where you put the files from the git repository. it should look like this:
[LIST]
[*]yourDir/
[LIST]
         [*]base/
         [*]jk2gamex86.so
         [*]jk2sp
[/LIST]

[/LIST]


4. Open the terminal and go the the folder where you put jk2sp. make it executable by typing
```
chmod +x jk2sp
```

5. to run the game type
```
./jk2sp
```

this worked for me. if you have the steam version you dont need to apply the patch.

---

### Post by MadleSs on 2013-04-21
Oh thanks... I thought I don't need the original files... working now :)

---

