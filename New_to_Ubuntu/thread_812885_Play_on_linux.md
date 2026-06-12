---
title: "Play on linux"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
Does anyone know a guide or intro to playonlinux?
Official site doesn't have much info.

---

### Post by Golem XIV on 2008-05-30
Assuming you mean play games, there is a forum specifically dedicated to games on this site located [here]("http://ubuntuforums.org/forumdisplay.php?f=93")

Do you have any specific game or type of games in mind?

---

### Post by cristo-father on 2008-05-30
> **Golem XIV said:**
> Assuming you mean play games, there is a forum specifically dedicated to games on this site located [here]("http://ubuntuforums.org/forumdisplay.php?f=93")

Do you have any specific game or type of games in mind?

I am mentioning play on linux because i heard it has the ability to install severall versions of wine.
What i have in mind is nulldc,project64 and pes2008.

---

### Post by sweeneytodd on 2008-05-30
why do u need more than one version of wine, is it because of certain programs

---

### Post by Tomatz on 2008-05-30
> **cristo-father said:**
> I am mentioning play on linux because i heard it has the ability to install severall versions of wine.
What i have in mind is nulldc,project64 and pes2008.


N64 emulator for linux:

[http://mupen64.emulation64.com/](http://mupen64.emulation64.com/)

Check synaptic also ;)

---

### Post by cristo-father on 2008-05-30
> **Tomatz said:**
> N64 emulator for linux:

[http://mupen64.emulation64.com/](http://mupen64.emulation64.com/)

Check synaptic also ;)

I heard project64 has much better compatibility with games as well as better
frames per second.

---

### Post by Jadd on 2008-05-30
I think cristo-father is referring to [PlayOnLinux](http://www.playonlinux.com), the GUI application that lets you install Windows games on Linux easily. I haven't used it before though, so I can't help you, cristo-father! It looks like you just click Install and select the game from the list.

---

### Post by cristo-father on 2008-05-30
> **Jadd said:**
> I think cristo-father is referring to [PlayOnLinux](http://www.playonlinux.com), the GUI application that lets you install Windows games on Linux easily. I haven't used it before though, so I can't help you, cristo-father! It looks like you just click Install and select the game from the list.
Exactly. Sorry didn't notice it...:lolflag:

---

### Post by wpshooter on 2008-05-30
The "PlayOnLinux" website has words misspelled and other errors on it.

I don't know that I would want to trust anything that was offered on that site.

---

### Post by Tomatz on 2008-05-30
I have run mame32 under wine before quite sucessfully so i think pj64 _could_ work.

Give it a try using plain old wine from the repos ;)

---

### Post by cristo-father on 2008-05-30
> **wpshooter said:**
> The "PlayOnLinux" website has words misspelled and other errors on it.

I don't know that I would want to trust anything that was offered on that site.
It has some good reviews, like this one:
[http://wine-review.blogspot.com/2008/01/playonlinux.html](http://wine-review.blogspot.com/2008/01/playonlinux.html)

---

### Post by Vadi on 2008-05-30
It's made by French, and just has a poor English translation.

You can also try out Wine Doors, it does as a similar thing.

---

### Post by cristo-father on 2008-05-30
> **Vadi said:**
> It's made by French, and just has a poor English translation.

You can also try out Wine Doors, it does as a similar thing.

Is it better than playonlinux? Do you have a compatibility list?

---

### Post by Vadi on 2008-05-30
Here's their website: [http://www.wine-doors.org/](http://www.wine-doors.org/), check it out. It looked pretty good to me, although I don't use it (don't use wine either. ETQW and Savage 2 are on my time, and both native :))

---

### Post by cristo-father on 2008-05-30
> **Vadi said:**
> Here's their website: [http://www.wine-doors.org/](http://www.wine-doors.org/), check it out. It looked pretty good to me, although I don't use it (don't use wine either. ETQW and Savage 2 are on my time, and both native :))
Can't find the compatibility list in their website...

---

### Post by Vadi on 2008-05-30
I think you're confusing some things. Wine Doors, and PlayOnLinux, are programs that download & install Windows programs to run on wine for you.

For Wine compatibility, here's the database: appdb.winehq.org

---

### Post by cristo-father on 2008-05-30
> **Vadi said:**
> I think you're confusing some things. Wine Doors, and PlayOnLinux, are programs that download & install Windows programs to run on wine for you.

For Wine compatibility, here's the database: appdb.winehq.org

:confused:...Do you know any awesome tutorials to introduce me to the world of using apps from windows on linux(for free and preferably opensource)?

---

### Post by robalcorn on 2008-05-30
I never heard of playonlinux before this thread started. I have always used wine and cedega but I just downloaded playonlinux and works great!

---

### Post by cristo-father on 2008-05-30
> **robalcorn said:**
> I never heard of playonlinux before this thread started. I have always used wine and cedega but I just downloaded playonlinux and works great!
Happy i helped :). Still am looking for the ideal intro to the wine world.

---

### Post by justin whitaker on 2008-05-30
> **cristo-father said:**
> Happy i helped :). Still am looking for the ideal intro to the wine world.

Wine is pretty straight forward. 

If you download an .exe, you can execute it via wine, either by right clicking and selecting open, then selecting Wine from the applications box. You could also enter Wine in the run dialog underneath the applications. 

Or you can navigate to the directory and execute the following command: wine installer.exe (or whatever the application is called). 

The installer should run as it would on a normal windows box. It may ask to download a mozilla controller or some other helper application-click yes, and let the installer do it's thing.

If everything goes well, the applications menu should show the application you installed under Wine>Programs>Application Name. 

Then you just run the program as any other program on the system.

Not everything works, but a lot of things do. Check WineHQ's appsdb to find the odd tweaks, optimizations, and workarounds.

---

### Post by Vadi on 2008-05-30
> **cristo-father said:**
> :confused:...Do you know any awesome tutorials to introduce me to the world of using apps from windows on linux(for free and preferably opensource)?

Generally, you go to Applications - Add/Remove, install "wine". Then you get a Windows.exe, double-click on it, and the rest, hopefully, should be everything like on Windows.

Sometimes a program will need some sort of a special setup - you can google "*programname* wine ubuntu" in that case for some help.

---

### Post by tprender on 2008-08-18
> **robalcorn said:**
> I never heard of playonlinux before this thread started. I have always used wine and cedega but I just downloaded playonlinux and works great!


I just tried using POL to download Steam which previously would not work with Wine Doors. POL works great whereas WD kept complaining that I needed the Tahoma font even though I used WD to install it. I am currently downloading Half Life 2 and will report back as to whether it works or not.

---

### Post by Amarsingh0793 on 2008-08-20
I have PlayonLinux and it works great so far. But has anyone tried this with WarRock?

Thanks in advance

---

