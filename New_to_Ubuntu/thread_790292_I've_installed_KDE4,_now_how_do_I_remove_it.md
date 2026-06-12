---
title: "I've installed KDE4, now how do I remove it?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2008-05-11
Hi 
mine is not the same problem  but as it is being discussed i thought i would be better if i discuss it right here.

I installed kde4 package add/remove programs application. After doing that i m getting this log in screen which is of kde and when i tried to uninstall it didnt go ..
what should i do to remove kde4 desktop package completely from my system and just have the nice old gnome display..

---

### Post by Joeb454 on 2008-05-11
> **kshtjsnghl said:**
> Hi 
mine is not the same problem  but as it is being discussed i thought i would be better if i discuss it right here.

I installed kde4 package add/remove programs application. After doing that i m getting this log in screen which is of kde and when i tried to uninstall it didnt go ..
what should i do to remove kde4 desktop package completely from my system and just have the nice old gnome display..

Actually I think you have a completely separate issue :)

---

### Post by PmDematagoda on 2008-05-11
kshtjsnghl, your post was not in line with the intent of the thread, therefore to prevent any confusion within the thread and also to improve the amount of help you receive I have moved your post along with any others that concern it to a new thread.

Also, don't worry about creating new support threads when there are others that talk about your same problem, since in the end it turns out to be more cleaner and efficient to try and solve your problems in a new thread with no comments than in a thread with thousands of comments:).

---

### Post by N.N. on 2008-05-11
First, try running the following command in the terminal to remove unused packages: ```
sudo apt-get autoremove
```
Then press CTRL+ALT+BACKSPACE to restart the xserver and check whether the KDM is still there. If it is, try following the instructions in the following link to remove all unnecessary KDE dependencies: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome).

---

### Post by atomkarinca on 2008-05-11
If you want to change the GDM theme at startup, System > Administration > Login Window > Local, you should see a list, select to your liking.

---

### Post by eldragon on 2008-05-11
oh god, i knew this one, happened to me a while ago, you are using kdm instead o gdm. 

here, 
[code]
sudo dpkg-reconfigure gdm
[\code]

pick gdm when you are asked :D

---

### Post by kshtjsnghl on 2008-05-11
hey i did that sudo dpkg-reconfigure gdm

 but i think it only asked which download manager i will be using but i want to uninstall kde4 - kdm. how do i do that??

I did according to the psychocat tutorial - 
 sudo aptitude remove kubuntu-desktop 

but it didnt help the next time i restarted it again gave me the same log in screen ..

---

### Post by kshtjsnghl on 2008-05-11
And yes when i ran sudo dpkg-reconfigure gdm and selected gdm it gave me this output - 
kshitij@kshitij-laptop:~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

edit : hey i restarted now and i got the gnome login screen thanks.. but now the problem is the progress bar at the booting up of the log in screen shows kubuntu on the top and not gnome and after loading completely it shows me the gnome log in screen.

how do i remove that??

---

### Post by eldragon on 2008-05-12
thats the usplash screen that got replaced...i really dont know what you did to get that messed up, installing kde4 didnt modify my usplash screen in the past. (a month ago).

i would do the following:
```

sudo apt-get remove kubuntu-artwork-usplash usplash-theme-ubuntu

```
and then
```

sudo apt-get install usplash-theme-ubuntu

```

havent tried it myself, give it a go :)

---

