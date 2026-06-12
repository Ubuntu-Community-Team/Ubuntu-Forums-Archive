---
title: "WoW Text Problem"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Pergi on 2008-07-12
Hello, i have World of Warcraft on Ubuntu and i have a problem.
I cant read text at game. I cant read the chat, the text of quests and the names of the players. Nothing.

I think that this is a font problem, so i took from windows the fonts and i pasted them on ubuntu at the folder ".fonts".
But i cant see the text yet.

If you know how i can solve it, please post a reply. 
Thank you very much

---

### Post by hyper_ch on 2008-07-12
install mstcorefonts

---

### Post by Pergi on 2008-07-12
At terminal i have to write 

```
sudo apt-get install mstcorefonts
```

??

I did it and returned 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mstcorefonts

```

A picture of how i am in game

[http://i200.photobucket.com/albums/aa98/Heironious/Screenshot-1.png](http://i200.photobucket.com/albums/aa98/Heironious/Screenshot-1.png)

---

### Post by hyper_ch on 2008-07-12
it's mst**t**corefonts

the command is right, just package name not quite ;)

---

### Post by avam323 on 2008-07-12
if hyper's suggestion doesn't work, you may need to reinstall wine and/or WoW. (but before you reinstall wow, try the Repair.exe util in your WoW folder.) Good luck. I had trouble at first too.

---

### Post by Pergi on 2008-07-12
I did it but the problem is remaining :/

I found threads from other ppl that had the same problem, and in the threads, there is no answer about how to solve it :(

I will do now repair as avam proposed.

---

### Post by hyper_ch on 2008-07-12
well, I copied over my win install of WoW... that worked perfectly...

---

### Post by mriedel on 2008-07-12
I used to play WoW through wine using a native windows parition and I never came across that error. If you have that option or if you can copy a WoW installation from a windows partition, try that option. If you can't, try reinstalling WoW now that you have microsoft fonts.

---

### Post by Pergi on 2008-07-12
I did repair, but the problem is remaining once again.

I have a win installation, but it is without the updates.
This means that i have to download the updates 2Gb approximately.
Or i will copy the patches from this installation to the win installation. I hope that it will work.

Thank you very much for the help.

---

### Post by Pergi on 2008-07-12
I did right now the thing with the Registry and my problem solved!!! omg

But one little little problem is remaining :P
My minimap is white. I cant see the content of minimap, the town that i am in.

---

