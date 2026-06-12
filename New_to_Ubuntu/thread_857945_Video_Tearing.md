---
title: "Video Tearing?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by LifeTheHound on 2008-07-13
Well, I'm a total linux noob but I at least know I have a 64 bit processor (if that helps). With any kind of videos i play on my linux, there is video tearing.  I have the latest Ubuntu linux 8.04.  
Thanks for any advice :)

[edit]
More info about the problem, and steps I took in order:  
Video Card: ATI Radeon X300
No video if "xv" driver is selected (smplayer)--using 'x11' instead tears like crazy.  Using "gl" makes the screen flicker like crazy.
I believe I have this 'compiz' thing, since I can make my desktop into a cube and everything looks way way prettier than my windows xp.  

**What I did.**
1. Uninstalled default drivers, installed the ones from ATI's website (8.7) instead (I put them on desktop and did that 'sudo' thing they told me to).  After reboot, [COLOR=RED]VIDEOS WORKED PERFECTLY WITH XV, BUT COMPUTER HAD WRONG RESOLUTION, AND EFFECTS DIDN'T WORK[/COLOR] (too slow to even drag windows).  
2. Then I used a terminal to do type "aticonfig --initial" and restarted.  This fixed resolution and all GUI/effects problems in my linux, but [color=red]NOW XV DOESN'T WORK AGAIN AND I'M RIGHT WHERE I STARTED.[/COLOR]. Videos now tear like crazy again now that I have to use the horrible 'x11' thing. :)

Please please help.  I want my good resolution and effects but also watchable video, not just one or the other.

---

### Post by The Tronyx on 2008-07-13
What kind of video card do you have?

---

### Post by LifeTheHound on 2008-07-13
your gonna think im an idiot .. but how do i check for that? [ [ sorry ] ]

---

### Post by Canis familiaris on 2008-07-13
To know the video card just enter this command in the terminal.
(To run Terminal: Applications->Accessories->Terminal)
```
lspci | grep VGA
```

---

### Post by LifeTheHound on 2008-07-13
thanks :)
it said the following after i typed that command :

ATI Technologies Inc RV370 5B60 [ Radeon X 300 (PCIE) ]

---

### Post by Canis familiaris on 2008-07-13
I am assumning you have Compiz enabled i.e. 3rd effecdts enabled. If thats the case you can either:

(1) Use Metacity i.e. plain desktop with no 3rd effects
Press Alt + F2 and type:
```
metacity --replace
```

(2) Or you could fix your Compiz. I also had ATi card and this tip worked for me and now I can see movies without flickering. But this tip did not solve taearing in Celestia and Google Earth.

[http://ubuntuforums.org/showpost.php?p=5222068&postcount=6](http://ubuntuforums.org/showpost.php?p=5222068&postcount=6)

---

### Post by The Tronyx on 2008-07-13
> **Anurag_panda said:**
> I am assumning you have Compiz enabled i.e. 3rd effecdts enabled. If thats the case you can either:

(1) Use Metacity i.e. plain desktop with no 3rd effects
Press Alt + F2 and type:
```
metacity --replace
```

(2) Or you could fix your Compiz. I also had ATi card and this tip worked for me and now I can see movies without flickering. But this tip did not solve taearing in Celestia and Google Earth.

[http://ubuntuforums.org/showpost.php?p=5222068&postcount=6](http://ubuntuforums.org/showpost.php?p=5222068&postcount=6)

I would agree assuming you are using Compiz.  Try turning off 3D desktop effects and see if that eases the problems you are experiencing.

---

### Post by LifeTheHound on 2008-07-13
thank you for your help :)

---

### Post by The Tronyx on 2008-07-13
> **LifeTheHound said:**
> thank you for your help :)

So did that take care of the problem then? :)

---

### Post by LifeTheHound on 2008-07-30
Uh...actually, could you tell me what exactly to do, step by step?  I have no idea what that post means (or where/what this "appropriate sections of your xorg.conf" is referring to).  :(

I also updated my first post to tell more about my problem and what I did.

---

### Post by markbuntu on 2008-07-30
WHy don't you try first right clicking anywhere on the desktop and in the box that comes up choose Change Desktop Backgroud. Then choose Visual Effects and choose None.

This should get rid of the flickering for when you need it too.

---

