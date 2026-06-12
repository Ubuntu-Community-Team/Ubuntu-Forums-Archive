---
title: "Playing windows games on the Ubuntu network...."
date: 2012-01-23
forum: New to Ubuntu
---

### Post by linuxstew on 2012-01-23
Hello,

Is this possible to do by using the desktop click link that shows all networks?  I have 2 computers, one is Ubuntu and the other is Windows XP.  I can see my Windows drive and can see all in the shared folder.  I can play shared music from the Windows side on the Ubuntu side.   So would I be able to just add the game folder to the shared folder and click the game icon to start the game and have it play from the Windows side but showing up on the Ubuntu side?  This sounds like a server/client thing.  Is this possible? Please comment on the how-to's and why-nots about this.  I remember the old days of doing setenv: display = 0.0 or something like that but this probably is not the same thing.Thank you.

---

### Post by mastablasta on 2012-01-23
> **linuxstew said:**
>  So would I be able to just add the game folder to the shared folder and click the game icon to start the game and have it play from the Windows side but showing up on the Ubuntu side? This sounds like a server/client thing. 
 
no, it doesn't sound like a server client thing at all. and no it's not possible. what you want to do is run a windows software on a different and incompatible operating system. 
 
to run windows game in linux you need an emulator or at least API layer (such as WINE)
 
what game?
 
 
if you install wine, you might be able to mount the folder within it and then run it. though i am not really sure if it would actually work since it wasn't installed there in wine.

---

### Post by Mark Phelps on 2012-01-24
The reason you can listen to audio files, or play video files is that the app used to do this is a local one, installed inside Ubuntu, and all you're doing is pointing to files on a shared location.

Running games can NOT be done because the app is actually local to the Windows PC, not installed in Ubuntu.

---

