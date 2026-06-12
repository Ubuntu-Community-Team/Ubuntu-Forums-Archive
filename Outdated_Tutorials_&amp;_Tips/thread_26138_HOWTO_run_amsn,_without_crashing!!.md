---
title: "HOWTO: run amsn, without crashing!!"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-04-11
Hello,
sorry if this solution has been already proposed i searched the forum didn't find any solutions in the topic i saw

to run amsn without crashing and with sound do the following:
```

sudo apt-get install amsn esound-clients
gedit ~/amsn&

```

paste inside it
```

#!/bin/bash
export LD_ASSUME_KERNEL=2.2.5 && amsn

```

then [COLOR=blue]chmod +x ~/amsn[/COLOR]

then edit the amsn link,
```

sudo gedit /usr/share/applications/amsn.desktop

```

replace
```

Exec=amsn

```

with
```

Exec=/home/whatever_is_your_username/amsn

```


open amsn, go to tools -> preferences -> others and replace [COLOR=Blue]play $sound[/COLOR] with [COLOR=Blue]esdplay $sound[/COLOR], set the file manager to [color=blue]nautilus $location[/color]

---

### Post by kuleali on 2005-04-13
thank's ..

---

### Post by Gandalf on 2005-04-13
[QUOTE=kuleali]thank's ..[/QUOTE]
 no problem

---

### Post by XplOzIOn on 2005-04-24
[QUOTE=Gandalf]Hello,
sorry if this solution has been already proposed i searched the forum didn't find any solutions in the topic i saw

to run amsn without crashing and with sound do the following:
```

sudo apt-get install amsn esound-clients
gedit ~/amsn&

```

paste inside it
```

#!/bin/bash
export LD_ASSUME_KERNEL=2.2.5 && amsn

```

then [COLOR=blue]chmod +x ~/amsn[/COLOR]

now create a link in your panel with the command /home/user/amsn
click on it, go to tools -> preferences -> others and replace [COLOR=Blue]play $sound[/COLOR] with [COLOR=Blue]esdplay $sound[/COLOR][/QUOTE]
 Gandalf i just did what you posted and when i click on it, it doesnt open anything :( im having real bad time with amsn, for some readon it crashes when i click on log in

//help

---

### Post by Gandalf on 2005-04-24
[QUOTE=XplOzIOn]Gandalf i just did what you posted and when i click on it, it doesnt open anything :( im having real bad time with amsn, for some readon it crashes when i click on log in

//help[/QUOTE]
 it's not for some reason, the reason is known, uncompatibility of amsn with the latest kernel version
if you run ~/amsn what happens? (in terminal)

---

### Post by XplOzIOn on 2005-04-25
[QUOTE=Gandalf]it's not for some reason, the reason is known, uncompatibility of amsn with the latest kernel version
if you run ~/amsn what happens? (in terminal)[/QUOTE]
 Hmm well i just redo everything and rebooted the pc, now it open an run withour problems. Maybe i did something wrong.
  Once again thank for the tip Gandalf the white :)

---

### Post by Gandalf on 2005-04-25
[QUOTE=XplOzIOn]Hmm well i just redo everything and rebooted the pc, now it open an run withour problems. Maybe i did something wrong.
  Once again thank for the tip Gandalf the white :)[/QUOTE]
 no problem :D

---

### Post by bored2k on 2005-04-26
Thanks Gandalf. Apparently it worked.

---

### Post by Gandalf on 2005-04-26
[QUOTE=bored2k]Thanks Gandalf. Apparently it worked.[/QUOTE]
 no problem :D

---

### Post by ykpaiha on 2005-04-27
if that can help :
Ihad the freeze probleme with the standard version and I downloaded the cvs (fresh cvs snapshot from amsn soundforge) to make the things right.

---

### Post by svanac on 2005-05-15
What can I do?

It's still doesn't work....!!

---

### Post by zxc on 2005-05-15
Mine works perfectly. Thanks Gandalf =c)

---

### Post by Gandalf on 2005-05-15
[QUOTE=zxc]Mine works perfectly. Thanks Gandalf =c)[/QUOTE]
 no problem

@svanac verify you are running /home/user/amsn and not amsn

---

### Post by svanac on 2005-05-19
Yes, I'm make that.

The first time after installation all work well, 
Next time it isn't run.

---

### Post by zaxer on 2005-06-13
Great info.

My GAIM used to crash from time to time without telling me why :)

---

### Post by gustavobrust on 2005-07-16
:grin:  :grin: 
Thank you very much Gandalf... 
I was breaking my head to make amsn works, and now it worked perfectly! 
See you!

---

### Post by xodeus on 2005-08-04
How do I make this for several users?

Please guide me through..

---

### Post by yoshic on 2005-08-05
hi, thanks for this, it's been helpful  :)  :)  :)  
and this gave me an idea and i did this instead:
as root edit the ams script located in /usr/bin/ (with gedit, vi, nano..etc) 
*  it looks like this
```
#!/bin/sh
cd /usr/share/amsn && /usr/bin/wish amsn
``` 
*   then change the last  line with this:
```
export LD_ASSUME_KERNEL=2.2.5 && cd /usr/share/amsn && /usr/bin/wish amsn
``` 

well it's a bit different but it works too, yeah, i'm a bit lazy  ;-)  ;-)

---

### Post by yoshic on 2005-08-08
[QUOTE=xodeus]How do I make this for several users?

Please guide me through..[/QUOTE]
the tip in my last post will work for any user, so you don't have to do more work than this

---

### Post by rogeriovinhal on 2005-08-10
I did the script, but I have a problem on running it directly from "Applications" menu in Gnome.
The fact is that I didn't install aMSN from APT-GET, so I made my own shortcut to it using SMEG, but it doesn't run if I change the shortcut to the script.

If I click twice in it in nautilus, it asks me if I want to open or execute, and the I choose execute, but it doesn't do anything at all with the shortcut in the menu.

Any ideas?

---

### Post by rogeriovinhal on 2005-08-12
Up.

---

### Post by xodeus on 2005-08-13
[QUOTE=rogeriovinhal]I did the script, but I have a problem on running it directly from "Applications" menu in Gnome.
The fact is that I didn't install aMSN from APT-GET, so I made my own shortcut to it using SMEG, but it doesn't run if I change the shortcut to the script.

If I click twice in it in nautilus, it asks me if I want to open or execute, and the I choose execute, but it doesn't do anything at all with the shortcut in the menu.

Any ideas?[/QUOTE]
 Does it run if you start it via console?

---

### Post by rogeriovinhal on 2005-08-13
[QUOTE=xodeus]Does it run if you start it via console?[/QUOTE]
 Yes, it does.

---

### Post by xodeus on 2005-08-13
What if you try to make a custom launcher in the gnome panel? Does it work?

---

### Post by ykpaiha on 2005-08-13
a lot of headeaks this amsn...
work fine for a time then without warning stop and freeze!!!
I will look closely as well in a new msn messenger 
Mercury
[http://www.mercury.to/](http://www.mercury.to/)
let' see...

---

### Post by rogeriovinhal on 2005-08-14
[QUOTE=xodeus]What if you try to make a custom launcher in the gnome panel? Does it work?[/QUOTE]
 How do I do that?

---

### Post by jrincon87 on 2005-11-30
Hey, I followed the instructions and now it works perfectly. I'm not an advanced user, but what's the reason why aMSN works well with this? What does this fix?
I assume it has to be with the kernel version but I can't figure out why.
Thanks.

---

