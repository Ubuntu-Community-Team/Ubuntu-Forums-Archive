---
title: "can't make my themes work :("
date: 2008-06-15
forum: New to Ubuntu
---

### Post by homerm06 on 2008-06-15
ok when i was on ubuntu 7.1 the themes would switch once they were clicked. on ubuntu 8.04 they don't... i don't know what it can be. i have emerald installed and i "think" i have compiz activated??? is there a way to get my themes up and STAY on after reboot?

---

### Post by meborc on 2008-06-15
are you talking about gtk or emerald? if emerald, then try alt+F2 and type **emerald --replace** while compiz is running and emerald theme is selected in the emerald menu

---

### Post by Ub1476 on 2008-06-15
Do you mean the themes in Appearance>Controls?

All of those are located in ~/.themes (~ = /home/username).

You can check there and see if everything is alright. Have you tried to download a new theme and install and enable that for instance?

If it's Emerald themes, try to run (Alt+F2) "emerald --replace".

---

### Post by homerm06 on 2008-06-15
> **meborc said:**
> are you talking about gtk or emerald? if emerald, then try alt+F2 and type **emerald --replace** while compiz is running and emerald theme is selected in the emerald menu

i'm using emerald but i don't know if compiz is runnin

---

### Post by meborc on 2008-06-15
> **homerm06 said:**
> i'm using emerald but i don't know if compiz is runnin

then alt+F2 and **compiz** just to make sure :)

you can't use emerald without compiz

---

### Post by homerm06 on 2008-06-15
ok i did the emerald replace thingy, now my borders are missing?????

---

### Post by Ub1476 on 2008-06-15
If you want to use Emerald to handle window borders, you need to run ccsm, and click on Window decorator>Path to/Command> Type in "emerald --replace". The default is Metacity.

Make sure Compiz runs and a theme is selected for Emerald. Do yo use a nVidia card?

---

### Post by homerm06 on 2008-06-15
> **Ub1476 said:**
> If you want to use Emerald to handle window borders, you need to run ccsm, and click on Window decorator>Path to/Command> Type in "emerald --replace". The default is Metacity.

Make sure Compiz runs and a theme is selected for Emerald. Do yo use a nVidia card?

see i just found out that once i close the terminal, my borders go away. i don't know if that info might be helpful...

and yea i use an nvidia card, how did i get to that window decor?

---

### Post by quinnten83 on 2008-06-15
Hi, 
I think you need to be a bit more specific here.
You are not sure if you are running Emerald
And you still have not made clear which theme you are talking about, so let's start from the start:

when you go to
system>preferences>appearance in the visual effects tab, wich one is selected? 
That way we know if you are running compiz or not.
I believe you need compiz to run emerald.
If visual effects are not selected, then select them and report what message you get if any.
we can take it to the next step then...

---

### Post by Ub1476 on 2008-06-15
You have to install Advanced Desktop Effects, found in Add/remove. Then you can run it from System>Preferences or launch "ccsm". 

Some nVidia card has a bug with Compiz, so you need to enter an option into xorg.conf. You can read about it [here]("http://wiki.compiz-fusion.org/Hardware/NVIDIA"), under "Additional Configuration".

You might have to add the option,

```
 Option  "AddARGBGLXVisuals"  "True" 
```

To Section "Device" (where your graphic card is listed) in xorg.conf.

To open xorg.conf, write in terminal:

```
gksudo gedit /etc/X11/xorg.conf
```

But this isn't necessary the problem. I for instance (with nvidia 7900gs), don't have to do this.

I suggest you check in System>Preferences>Sessions, and see if Compiz/Desktop effects is enabled there. That makes sure it autostarts. You most also enable it in System>Preferences>Appearance>Visual Effects.

Then try to logout and in, if Compiz works (shadows, fading, etc), but Emerald do not (and it's used in ccsm>Window decoration), you need to edit xorg.conf.

---

### Post by homerm06 on 2008-06-15
> **quinnten83 said:**
> Hi, 
I think you need to be a bit more specific here.
You are not sure if you are running Emerald
And you still have not made clear which theme you are talking about, so let's start from the start:

when you go to
system>preferences>appearance in the visual effects tab, wich one is selected? 
That way we know if you are running compiz or not.
I believe you need compiz to run emerald.
If visual effects are not selected, then select them and report what message you get if any.
we can take it to the next step then...

Ok lol i'm sorry... I see "Extra" but now i have a bigger prob...

---

### Post by homerm06 on 2008-06-15
oy sorry guys never mind i just rolled back to gutsy... i did some research, my video card an NVIDIA GeForce4 MX4000 has had some issues with hardy... i think that may be the reasons for my dysfunctional computer...

i just have one off topic question.... how do i go about installing a different video card on ubuntu? do i just swap out my old one and add the new one then let ubuntu update the drivers?

---

