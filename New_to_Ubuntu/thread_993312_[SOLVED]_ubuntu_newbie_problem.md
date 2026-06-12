---
title: "[SOLVED] ubuntu newbie problem"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by MaGnOliA on 2008-11-25
hi

i am new to ubuntu , actually i just installed it today , but a problem occurred , well i was configuring compiz for desktop , & now after i write my user name & password , then the screen became a grid full of colors , i think there is a conflict 

i do not know what to do , really need help , as i loved linux very much & i wanna fix it

thanks

---

### Post by bobnutfield on 2008-11-25
Hello and Welcome!

To properly help, you'll need to provide a little more information.  Which version of Ubuntu are you running and what is your graphics hardware?

It could be a simple matter of installing the correct grahics drivers.

---

### Post by MaGnOliA on 2008-11-25
i am using the latest version 8.10

& it was running alright until i was configuring compiz 

a friend of mine was helping me installing it &  he told me the graphics driver was alright 

i just want to figure out a way to undo what i did

---

### Post by bhadotia on 2008-11-25
> **MaGnOliA said:**
> hi

i am new to ubuntu , actually i just installed it today , but a problem occurred , well i was configuring compiz for desktop , & now after i write my user name & password , then the screen became a grid full of colors , i think there is a conflict 

i do not know what to do , really need help , as i loved linux very much & i wanna fix it

thanks
Hi, and welcome!:)

How exactly were you trying to configure compiz? I mean were you using a GUI front-end such ccsm, gconf-editor etc. or were you trying to edit the configuration files manually? If you were following some guide link to it might also help i solving the problem.

> a friend of mine was helping me installing it & he told me the graphics driver was alright

Also, why don't you ask your friend if he/she can help. Or if he/she cannot help, then ask him/her to help you to describe what exactly you did when you were trying to configure compiz.

---

### Post by MaGnOliA on 2008-11-25
i was marking the check boxes i want , that's all

---

### Post by MaGnOliA on 2008-11-25
> **bhadotia said:**
> Hi, and welcome!:)

Also, why don't you ask your friend if he/she can help. Or if he/she cannot help, then ask him/her to help you to describe what exactly you did when you were trying to configure compiz.

as i was at college & now i am at home , i cant find him , so i am trying to know anything on my own

---

### Post by bobnutfield on 2008-11-25
If you want to undo what you have done, you just need to disable Compiz for the time being until you can zero in on the conflits, if any.  To disable compiz, go to System>Preferences>Appearance and on the Visual effects tab, check the "None" box.  The restart X (AltCtrlBackspce) or reboot.  That should get you back to metacity window manager.

---

### Post by bhadotia on 2008-11-25
> **MaGnOliA said:**
> as i was at college & now i am at home , i cant find him , so i am trying to know anything on my own

hmm... 

You were marking the check boxes .. this most probably means you were using the ccsm (this has a menu entry: System>Preferences>Advanced Desktop Effects Settings.. can you see it?).

Well, if you are a little familiar with the command line you can boot in to the Recovery Mode and delete the /home/your_username/.gconf and /home/your_username/.compiz files to undo the effect and then consult some good guide on customizing compiz to configure compiz again. This will also delete some other settings the you saved such as wallpaper etc. but they can be easily reconfigured.

EDIT:
Oh yes, as bobnutfield pointed out. If you can access your desktop in GUI mode then just browse into your home folder, press ctrl+h and delete the above two files to purge your configuration and reboot. Or do as bobnutfield says and follow some guide as this [one]("http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074")

---

### Post by MaGnOliA on 2008-11-25
> **bobnutfield said:**
> If you want to undo what you have done, you just need to disable Compiz for the time being until you can zero in on the conflits, if any.  To disable compiz, go to System>Preferences>Appearance and on the Visual effects tab, check the "None" box.  The restart X (AltCtrlBackspce) or reboot.  That should get you back to metacity window manager.

i would like to remind you that now i cannot log on ubuntu on the first place to do that

---

### Post by bobnutfield on 2008-11-25
OK, my bad, I had assumed you could get some the desktop but it was garbled partially.  You can reboot into recovery mode.  You will be given the option there of repairing and restoring your graphics defaults.  This the equivalent of running from the command line:

> sudo dpkg-reconfigure -phigh xserver-xorg

That should turn off compiz and allow you to boot back into a default desktop.

---

### Post by dr.silly on 2008-11-25
> **MaGnOliA said:**
> i would like to remind you that now i cannot log on ubuntu on the first place to do that

That probably changes things ;) what you can do is set your compiz and window manager settings back to their defaults. This should fix your problem. To do that find your way into a command line (boot into recovery mode, or hit Ctrl+Alt+F1) and enter these commands:

```
rm -r /home/*username*/.compiz/
```
```
rm -r /home/*username*/.gconf/
```

---

### Post by bhadotia on 2008-11-25
> **bobnutfield said:**
> You will be given the option there of repairing and restoring your graphics defaults. 
That should turn off compiz and allow you to boot back into a default desktop.
Just curious:
Is that the default behaviour? I have never had any graphics problem so I don't know whether you automatically get prompted to solve the problem in Recovery Mode. Also will that also take care of turning compiz off?

---

### Post by bobnutfield on 2008-11-25
> **bhadotia said:**
> Just curious:
Is that the default behaviour? I have never had any graphics problem so I don't know whether you automatically get prompted to solve the problem in Recovery Mode. Also will that also take care of turning compiz off?

You know, now that you ask the question, I cannot be totally sure that it will in fact turn off compiz.  I have used Recovery Mode only once to correct a graphics driver issue, and, yes, it does give you a NCurses display with the option to reconfigure Xorg.  This, as I recall (it has been a while), asked me to verify and my graphics device and it automatically restored the default settings in Xorg.

I just assumed that that would disable desktop effects and return the metacity window manager,but I could be wrong.

---

### Post by Olivier2371 on 2008-11-25
You could always try to reboot the machine then go into safe mode, at point the vesa driver should in use, then you should be able to log in and change  your settings. then reboot.

Guys Tell me if I wrong about that.

---

### Post by bhadotia on 2008-11-25
> **bobnutfield said:**
> You know, now that you ask the question, I cannot be totally sure that it will in fact turn off compiz.  I have used Recovery Mode only once to correct a graphics driver issue, and, yes, it does give you a NCurses display with the option to reconfigure Xorg.  This, as I recall (it has been a while), asked me to verify and my graphics device and it automatically restored the default settings in Xorg.

I just assumed that that would disable desktop effects and return the metacity window manager,but I could be wrong.

@MaGnOliA
Then, we'll go step by step:
1. Reboot. If you dual boot with windows (or any other OS) the default screen will give you the option of booting into REcovery Mode. Otherwise press Esc and you'll get the option.
2. Now login giving your username and password.
3. If you are prompted to repair graphics do so. Otherwise give this command and go with the default options:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
give password as prompted.
4. Give the commands given by dr.silly- change the "username" there with your username.
5. Reboot by giving the command below and see if it works
```
sudo reboot
```
give password as prompted.

---

### Post by MaGnOliA on 2008-11-25
ok i'll try & tell you 

thanks

---

### Post by bhadotia on 2008-11-25
Wait, first see the little edition I made (it might be useful).

Good Luck:popcorn:

---

### Post by Olivier2371 on 2008-11-25
bhadotia,

I though that the following command has been rendered obsolete in 8.10. 

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by bhadotia on 2008-11-25
> **Olivier2371 said:**
> bhadotia,

I though that the following command has been rendered obsolete in 8.10. 

sudo dpkg-reconfigure -phigh xserver-xorg

Yeah, the new xserver has auto configuration feature and will not require the xorg.conf file for ost hardware. But the command is still very much in use- for situations like these:)

---

### Post by Olivier2371 on 2008-11-25
bhadotia,

Thanks for info.

---

### Post by MaGnOliA on 2008-11-25
thaaaaaaaaaaaaaaanks alot , it worked :D:D:D

---

### Post by bhadotia on 2008-11-25
> **MaGnOliA said:**
> thaaaaaaaaaaaaaaanks alot , it worked :D:D:D

Great !:)
Please mark your thread as solved now (click on "Thread Tools" on top right for the option).

---

