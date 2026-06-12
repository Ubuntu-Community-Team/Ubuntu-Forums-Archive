---
title: "Howto: Run avgupdate from avg gui (Feisty fawn)"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by pkslot on 2007-05-22
***ONLY TRIED ON UBUNTU 7.04***

I've gotten tired of updating my avg via the terminal. When i installed avg, it turned out that i couldn't update it from the gui.... Bummer.

Well, here's what i did to change it.

On my pc, the avg is installed in "/opt/grisoft/" and the updater is in "/opt/grisoft/avg7/bin" so simply open up your terminal and write
 ```
cd /opt/grisoft/avg7/bin
``` 
...to get there.

****
If this isn't the case on your pc, then try to typing 
```
avggui
```
in the terminal, and the path should show. Then simply switch the "/opt/grisoft" path to where you have it.
****

Now you have to make the avgupdate executable by all users by typing:

```
sudo chmod a+x avgupdate
```

Half way through.

I order to store files while downloading, the folder "run" needs to writable. To do so, type

```
cd ..
```

```
cd var/run
```

Now you should be in /opt/grisoft/avg7/var/
Then type
```
sudo chmod a+rw run
```

You're there. To get the folder writable, type

```
sudo chmod a+rw run
```


To test it, fire up your avg and press the update button


As this is my first howto, i hope it doesn't look too messy ;) but if that's the case...  then i'm sorry, but hope that it can be of use anyway.

---

### Post by MonsterTrimble on 2007-05-26
Success! Well, at least AVG doesn't say that it doesn't have permission!

---

### Post by plantman on 2007-11-17
[QUOTE=pkslot;2701293]***ONLY TRIED ON UBUNTU 7.04***

I've gotten tired of updating my avg via the terminal. When i installed avg, it turned out that i couldn't update it from the gui.... Bummer.

Well, here's what i did to change it.

On my pc, the avg is installed in "/opt/grisoft/" and the updater is in "/opt/grisoft/avg7/bin" so simply open up your terminal and write
 ```
cd /opt/grisoft/avg7/bin
``` 
...to get there.

****
If this isn't the case on your pc, then try to typing 
```
avggui
```
in the terminal, and the path should show. Then simply switch the "/opt/grisoft" path to where you have it.
****

Now you have to make the avgupdate executable by all users by typing:

```
sudo chmod a+x avgupdate
```

Half way through.

I order to store files while downloading, the folder "run" needs to writable. To do so, type

```
cd ..
```

```
cd var/run
```

Now you should be in /opt/grisoft/avg7/var/
Then type
```
sudo chmod a+rw run
```

**This is what happened for me...**
[HTML]
rms@rms-laptop:/opt/grisoft/avg7/var/run$ sudo chmod a+rw run
chmod: cannot access `run': No such file or directory[/HTML]
What do I do now? I am a total newbie! :confused:
I am running AVG instead of Clam.

---

### Post by nwgray on 2008-01-10
you need to go up one directory. Since you're already in the /run directory, you can't modify it using the chmod method. 

cd ..

this will take you back to the var directory. 

now run:

sudo chmod a+rw run

However, now when attempting to update, I get this error:

Update process failed.
Reason: Can not create file '/opt/grisoft/avg7/var/run/avgupdate.pid'.


Never mind - wrong directory had the chmod performed on it. that's what I get for trying to talk on the phone, IM, and do CLi work at the same time. 

Ideas?

---

### Post by ben2talk on 2008-08-12
Wow, complicated stuff!

You can simply go to the menu, right click and select to EDIT MENUS

Click ACCESSORIES, then you'll see the launcher for AVG
RIGHT CLICK the icon, and select PROPERTIES

I changed the name to AVG, and typed 'gksudo' in front of avggui

Now when I launch it, I have to enter password to give it permission, and the update function works through the gui.

To launch now, press ALT+F2 for the gnome launcher, and type AVG and hit ENTER.
Is that easy enough?

---

### Post by plantman on 2008-08-18
> **ben2talk said:**
> Wow, complicated stuff!

You can simply go to the menu, right click and select to EDIT MENUS

Click ACCESSORIES, then you'll see the launcher for AVG
RIGHT CLICK the icon, and select PROPERTIES

I changed the name to AVG, and typed 'gksudo' in front of avggui

Now when I launch it, I have to enter password to give it permission, and the update function works through the gui.

To launch now, press ALT+F2 for the gnome launcher, and type AVG and hit ENTER.
Is that easy enough?

Thanks! Works for me!

---

### Post by b1ackb1rd on 2008-08-23
I get an error message saying that I cannot download the update file

Can not download the file 'avg7info.ctf'..

Any ideas what I'm doing wrong?

---

