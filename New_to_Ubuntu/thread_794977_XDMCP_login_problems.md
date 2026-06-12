---
title: "XDMCP login problems"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by cOzAtS on 2008-05-15
Ok, here it goes:
I've been fooling around with gdm (bad) install-unistalled xfce (too bad) and somehow i made my pc before login to seek for XDMCP computers through network. I clicked on my and then i disabled xdmcp access to my pc (the worst) Now all i get is a xdmcp window which can't find any machine to login and the only thing i managed to do is go to command line, bu i cannot start x (it says it is already in use). Anyway i'd like some cli commands (if there are any) to disable xdmcp login and to restore my default gdm settings!

Thnx in advance!!

(BTW im total noob so please explain what i have to do)

---

### Post by ZabiGG on 2008-05-15
Start with the link in my signature below.

When you feel you have a better idea how your system works, try again ;)

Cheers,

---

### Post by cOzAtS on 2008-05-15
Sorry if i didn't make it clear enough for you to help but the link you provided does not help. 
I just dont know how to bypass the xdmcp and login normally with gdm. All i can get is command line and i need some kind of command to restore gdm or disable xdmcp. For now i just want to login.

/interesting links though for future study..most of them...Plz there should be a command to disable it...or enable loggin in through it again. Anyone?

---

### Post by ZabiGG on 2008-05-15
Then you should post in the forum section relevant to your problem

[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

That's where you'll find the most passionate and knowledgeable help.

Me, I'm just the welcoming committee ;)

---

### Post by cOzAtS on 2008-05-15
i tried to but it didn't let me so i decided to post it here...if theres a mod who can move it to the right sub-forum....id be glad...

thnx for your time!!

---

### Post by ZabiGG on 2008-05-15
I'll find you help ;) Don't worry. Can you be a tad patient with me so that I consult with the experts I know? (we do receive around a 1,000 newbie questions every day...)

---

### Post by bodhi.zazen on 2008-05-15
Reboot your computer to recovery mode or go to a console at Control-Alt-F1 (or Control-Alt-F2).

If you boot to recovery mode you will be root. You can start an X session with :

```
apt-get install xubuntu-desktop
xfe4-session &
```

If you go to a console, stop X with :```
sudo /etc/init.d/gdm stop
```

You should be able to start a new X session with :```
xfce4-session
```

You may be able to configure from there.

See this thread if you can not get X started or need to configure from the command line:

[http://ubuntuforums.org/showthread.php?t=703313](http://ubuntuforums.org/showthread.php?t=703313)

---

### Post by ZabiGG on 2008-05-15
And help arrived ;o)

TYVM, eminent cheerleader saviour!

---

