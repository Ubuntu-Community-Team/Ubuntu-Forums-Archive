---
title: "how do i install .emerald themes??(absolute noob)"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by JMGM123456 on 2008-06-19
I downloaded ubuntu 8.04 and found nice themes on Beryl. But after i downloaded them i just couldn't make them work, i get a message ".emerald does not appear to be a valid theme". 

Please help

---

### Post by forestpixie on 2008-06-19
You need to install emerald first, from a terminal

```
sudo apt-get install emerald
```

It will be in your system > preferences menu afterwards, open emerald from there and use the import button to get the theme installed.

---

### Post by JMGM123456 on 2008-06-19
Thank you i just did this but how do i make the team apply to my interface?? I didn't find anything to make it work

---

### Post by forestpixie on 2008-06-19
You have to add it to compiz so that it runs as the window manager, make sure that you have visual effects set to custom in appearances. Of course you alos need to make sure you have video driver installed.

If you haven't got the settings manager install it 

```
sudo install compizconfig-settings-manager
```

run it with ```
ccsm
```

Then I think that window manager is in either general options or cube, I could be wrong though as I don't have it installed here and am going from memory.

---

### Post by JMGM123456 on 2008-06-19
I did just like u told me, but wen i run ccsm i get smtg like "unsupported value at path..." three times, although compiz runs fine. I searched the hole utility but i found nothing... this may be due to my ignorance of what i'm searching for, but found nothing related to emeraled...

---

### Post by philinux on 2008-06-19
You should have the menu item:-

System>Prefs> Advanced Desktop Effects

This is ccsm, no need to run it from the terminal.

---

### Post by redbob on 2008-06-19
These options, like the hole or the fire and water effects, are not shown in Emerald Settings. You will see then in System/Preferences/Advanced Desktop Effects Settings. This option is available just after you have installed compizconfig-settings-manager.

---

### Post by JMGM123456 on 2008-06-19
ok, but the problem remains... I didn't find out how to make the emerald themes i found work. Anyone?

---

### Post by issih on 2008-06-19
Compiz is a window manager, emerald is a window decorator, they do different jobs.

Themes in linux comprise several elements.
Window Decorations: Borders, min/max/close buttons
gtk Theme: look of controls, drop downs etc
fonts:
icons:
colours:

These can all be changed within the appearance preference dialog.

Compiz can use different window decorators. By default it uses a variation of gnomes default one, so the theme set in the appearances dialog are used to draw the window borders.

If you tell compiz to use emerald, the default window decorator is replaced, and the theme specified in the emerald manager are used to draw the window borders. Everything else is still controlled by the appearances dialog.

The easiest way to switch window decorator is probably to install fusion icon (search in synaptic) then run it. You can switch the window decorator being used directly from the icon.

So to make your themes work, install fusion icon, switch to using emerald, then open emerald manager and install your themes, and select the one you want.

Hope that helps.

---

### Post by JMGM123456 on 2008-06-19
ok i did it, i was looking for similar threats when i found the code "emerald --replace" worked fine instantly. Thank u people for helping me out.

Best regards

---

### Post by JMGM123456 on 2008-06-19
Noooooo!! now after i close the terminal in which i ran the command the window border completly disappears!!I have to re-run "emerald --replace" and keep terminal open. Seems like i'll need some more help

---

### Post by forestpixie on 2008-06-19
> This is ccsm, no need to run it from the terminal.

I said this because the op was already at the terminal.

```
emerald --replace
```

That isthe right code and I think that you need to have it in compiz for it to work on reboot - ther is a search option in ccsm - use it to search for window-manager - if it says other than emerald --replace change it.

---

### Post by Victormd on 2008-06-19
Go to system>preferences>sessions and add a session (start up command) with the command: ```
emerald --replace
```
and restart... :)

If you don't want to restart just yet, type ALT+F2 and enter the above command...

---

### Post by philinux on 2008-06-19
I must admit I'm intrigued with emerald. Compiz is running fine on my system.

Seems a bit convoluted just to get a different windows decorator running.

I might have a go after I fix my vbox intrepid setup.

---

### Post by Victormd on 2008-06-19
Yeah... when I upgraded to hardy, I didn't use emerald for quite a while because I couldn't get it to work (in gutsy it was straight forward) then I found out that in hardy, you have to set it up to start otherwise, it goes back to the default decorator...

But when you think about it, it's pretty straight forward (once you know what the problem is)... :)

---

### Post by JMGM123456 on 2008-06-19
okay thanks victor it works perfect now:)

---

### Post by Victormd on 2008-06-19
any time! :)

---

### Post by dnns123 on 2008-06-19
You put it in sessions? Funny, it doesnt happen to me. After a fresh install, I just install ccsm,emerald, and compiz fusion icon. Open emerald, import the theme from your desktop (assuming you've downloaded them), select the theme. Close emerald, open Compiz fusion icon and select reload window manager (you can skip this part by restarting the comp, but this is faster). close compiz fusion icon. Thats it!

---

### Post by Victormd on 2008-06-19
dnns123, are you using gutsy or hardy?
Gutsy does this automatically but in Hardy, it doesn't...

It could also be that compiz fusion icon automatically adds this for you. I don't have it installed so I just add it manually to sessions. More so, by doing this, every time you import a theme, it's automatically applied, no need to reboot, restart, or anything else...

---

### Post by dnns123 on 2008-06-19
hardy, I'm not sure if the fusion icon does it for me, but its the way i know how to use it. The fusion icon is handy incase the themes disappear for some unknown reason; just reload the window manager.

---

### Post by gnrathon on 2008-06-19
great Yuo got it
but now every time u restart or log off, the window decorator will go back to the original.
you can simply just press Alt+F2 to bring up the "Run" dialog and type in 
emerald --replace.

If you want this to happen automatically at start-up simply go to 
System>Prefrences>Sessions

Then click on Add and once the dialog pops up Type in Emerald [or what ever you want] for the name.
Then for Command type in emerald --replace and thats it

now emerald runs automatically at start-up.

---

### Post by LoneWulf on 2008-06-20
Where can i install compiz fusion icon? cant find it anywhere

---

### Post by gnrathon on 2008-06-20
its in the add/remove application

just search for compiz
youll find it

---

### Post by wariskampar on 2008-06-20
In my opinion, noob like myself need to d/load Compiz Fusion Icon to avoid confusion. This program made me understood the different between Windows Decorator and Windows Manager(Compiz vs Metacity and GTK vs Emerald).

---

### Post by LoneWulf on 2008-06-20
hehehe thanks, found it in synaptic though, under "fusion icon".:)
I kept looking under "compizfusion icon" and obviously couldnt find it...](*,)
Thank you

---

