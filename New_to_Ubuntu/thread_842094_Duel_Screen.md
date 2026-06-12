---
title: "Duel Screen"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by BluePlum on 2008-06-27
Ok. I have hardy. I have a laptop. I connected it to another 15 inch screen. I now have to screens doing the exact same thing. How do i make it so 1 screen displays Desk 1. And the other Desk 2. Or if i cannot do this. How do i make it so when i move the mouse out of one screen. it moves into the other?

Thanks

---

### Post by BluePlum on 2008-06-27
New information.

[http://ubuntuforums.org/showpost.php?p=5271055&postcount=4](http://ubuntuforums.org/showpost.php?p=5271055&postcount=4) I followed that post but it didn't work. But i may be doing something rong ( which i probly am ) If it's any help i have an ATI radeon 9000

---

### Post by ChameleonDave on 2008-06-27
Duel?  I don't think that means what you think it means.

---

### Post by BluePlum on 2008-06-27
Can't it mean 2? lol

---

### Post by ChameleonDave on 2008-06-27
> **BluePlum said:**
> Can't it mean 2? lol

Well yeah, it means 2.  Two people with pistols or rapiers.

I think you might want to enable Xinerama.  Look it up on the forum.  Also, what graphics card do you have?  I alter these settings in nvidia-settings.

---

### Post by BluePlum on 2008-06-27
1. I'm noob i dont understand what xinerma is.
2. Ati Radeon 9000. Its old but gold!

---

### Post by BluePlum on 2008-06-27
Anyone? I kinda need to know really soon in my situation, Not being impatient.

---

### Post by oligray on 2008-06-27
LolLOLOLOL

the DUEL not meaning what you think was a joke... How old are you?? 

Duel is like a fight between 2 people
duAl is for 2

you spell it WRONG not rong... your spelling is atrocious and it makes it irritating to read and makes people less inclined to help you.. how about you search for it in google now.

using the word DUAL rather than duel.. cos tbh you might aswell be saying jewel

---

### Post by BluePlum on 2008-06-27
dont worry some how it's now working... YAY! Now for another question. The screen is now split in half. But the start Bar/Panel is only on 1 screen. How do i split that in half for both screens?

---

### Post by Pjotr123 on 2008-06-27
Read this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by dangermouse28 on 2008-06-27
I have Radeon mobility 9000 in my laptop. Install Urandr - works a treat!:)

---

### Post by BluePlum on 2008-06-27
The two last posts were a little.... Weird since i got it working. Just need my last question answerd XD!

---

### Post by Motorhead Kaze on 2008-06-30
Howdy there, well it seems you got your dual monitors going now, but as for the panels (task bars), I think these will only be on one side of the extended destop (1 monitor).  If you want 1 task bar for each... you will have to wait for a super Linux hack to help ... I would like to have one of those... Super Linux Guardian...

BTW, I understood you even if you spelled Dual as Duel.

---

### Post by ad_267 on 2008-06-30
Not quite sure if this is what you're after. I have dual monitors set up with Nvidia and I added another panel and window list to my other monitor. Just right click on a panel and select New Panel. Drag the new panel across to your other monitor. Right click on that and select Add to Panel and add a window list.

I'm using TwinView but I think this should work with xinerama too.

---

### Post by Motorhead Kaze on 2008-07-01
My dual monitor problem is solved!  I had turned on the propriety driver for my ATI graphics card and that kept my system from seeing that I had 2 monitors on. Once that was off, I 

```
gksudo gedit /etc/X11/xorg.conf
```

and added this red text.
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
       [COLOR="Red"] SubSection "Display"
            Depth           24
            Virtual         2560 1024
        EndSubSection[/COLOR]
EndSection

```
then I restarted X, went into system/preferences/screen resolution and unchecked the clone screens, and arranged my monitors there.  Of course, to edit your xorg.conf you will need to know the correct numbers for your virtual section, but you can find that info below.

Helpful links:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)
About switching off propriety drivers, etc. [http://ubuntuforums.org/showthread.p...tection&page=2](http://ubuntuforums.org/showthread.p...tection&page=2)

If you are using the proprietry nvidia drivers you can use nvidia's own configuration tool:
```

gksu nvidia-settings

```

---

