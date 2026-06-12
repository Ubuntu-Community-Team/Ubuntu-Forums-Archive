---
title: "[SOLVED] switching window managers"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-28
i have a little acer aspireone so i don't think the compiz effects will work.  i installed fluxbox,  not sure about any others.  my question is that when i type fluxbox in the terminal (how else to run it) there is an error because compiz is running (without cube) or so window manager is working so fluxbox couldn't find screens to manage.  how do I disengage whatever is managing my windows now without all hell breaking loose? and then what is the best way to apply another window manager (preferably not from the terminal)?   Thanks for your insights.

---

### Post by tuxxy on 2008-08-28
Select you DE at the logon screen

---

### Post by adamogardner on 2008-08-28
> **tuxxy said:**
> Select you DE at the logon screen

is that supposed to make sense to me?  so i reboot, then grub - choos ubuntu to login screen (mine is debian after changing some colors settings) then before I sign in select a tab to choose desktop enviornment.  I don't want to lose gnome, just compiz.  gnome is dektop enviornment.  compiz is window manager and thats what I want different.  Am I wrong?

---

### Post by snowpine on 2008-08-28
Fluxbox is an alternative to Gnome. Choose which one you want from Sessions when you log in. You can't run them both at the same time. :)

---

### Post by adult swim on 2008-08-28
perhaps you want to use metacity instead of compiz in gnome
to do that, boot into ubuntu, hit alt-f2 and type in ```
metacity --replace
```

---

### Post by adamogardner on 2008-08-28
> **snowpine said:**
> Fluxbox is an alternative to Gnome. Choose which one you want from Sessions when you log in. You can't run them both at the same time. :)

> **adult swim said:**
> perhaps you want to use metacity instead of compiz in gnome
to do that, boot into ubuntu, hit alt-f2 and type in ```
metacity --replace
```

thankyou for the advice (both of you)  I feel like I'm already using metacity since there are no advanced desktop settings.
and besides, the people with full cups of foamy ubuntucinos are all using othre window managers. Still I though gnome was a desktop enviornment that in addition to its suite of packages, within it you can switch window managers.  This is wrong, and fluxbox is a desktop enviornment?   rathre than defaulto metacity.  I'm in a very experimental stage (so metacity may come out winner) In a minute I will try and boot and study the logon screen.  since I just downloaded fluxbox it should appear in a menu at sign in, or start up?  We'll see.

---

### Post by Elfy on 2008-08-28
When you get your login window, choose sessions - bottom left of login window. You can leave compiz as it is - fluxbox doesn't start any of that.

Menus are a bit different - but I'm just getting used to it myself after about 10 days :)

There are some useful threads here on menus and keys, it's much better now I have multimedia keys working.

---

### Post by adamogardner on 2008-08-28
> **forestpixie said:**
> Menus are a bit different - but I'm just getting used to it myself after about 10 days :)

There are some useful threads here on menus and keys, it's much better now I have multimedia keys working.

I think we are talking about two different things regarding menus (and keys?)  I just meant that my login screen is not the normal ubuntlogin screen because I changed splash and color settings and so It's a debian logon dialogbox that comes up.   what do you mean by menus?  Is that another window manager?

---

### Post by billgoldberg on 2008-08-28
You don't start fluxbox once the computer is up and running, you need to select it in your login screen.

My fluxbox guide might be usefull for you.

---

### Post by adamogardner on 2008-08-28
yes i did it it worked.  
thankyou everyone.

---

### Post by snowpine on 2008-08-28
Hi Adam, I have never really understood the desktop environment/windows manager distinction myself! :)

If you decide to use Fluxbox (personally I think what you want is Gnome+Metacity) you will need to learn how to configure your menus, keys, startup, etc. There are lots of tutorials on how to do it, here is a megathread to get you started: [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

If your Fluxbox menus do not update when you add new apps, just use the 'sudo update-menus' command.

Hope that helps!

ps It shouldn't matter if you've switched your login theme to Debian; there should still be a Sessions option where you can choose Fluxbox.

ps ps BillGoldberg's tutorials are awesome too!!!

---

### Post by adamogardner on 2008-08-28
well after trying I determined that it's not good for that computer since I use the touchpad, and that right click is obstinant.  Is there a better way to open the menus than the right click?  also does the suppository contain the most updated version? :lolflag:

---

### Post by Elfy on 2008-08-28
You can change it easily to anything - in ~/.fluxbox ther is a file - keys

Mine looks like this

> OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12

None XF86AudioLowerVolume       :Exec aumix -v -5
None XF86AudioRaiseVolume       :Exec aumix -v +5

None XF86Forward              	:Exec amarok -f
None XF86Back             	:Exec amarok -r
None XF86AudioPause             :Exec amarok -t
None XF86AudioStop             	:Exec amarok -s

None XF86WWW			:Exec opera &
None XF86Mail			:Exec thunderbird &

None XF86Refresh		:Exec gnome-terminal

None XF86Calculator		:Exec xchat
None XF86AudioMedia		:Exec amarok

None XF86Standby		:Exec thunar

you could for instance change 

Mod1 F5 :Workspace 5 to  Mod1 F5 :RootMenu

then reconfigure with the right button menu and then the menu will open with Alt+F5

AFAIK the repository has the latest stable version, not sure what is in GIT nor if it is very stable or not.

---

### Post by snowpine on 2008-08-28
> **adamogardner said:**
> well after trying I determined that it's not good for that computer since I use the touchpad, and that right click is obstinant.  Is there a better way to open the menus than the right click?  also does the suppository contain the most updated version? :lolflag:

Yeah, I think Fluxbox is pretty useless without the right click, sorry to say. I do think the version in the "suppositories" is the latest (it used to be out of date before Hardy).

Maybe check out IceWM? It has a regular-click menu in the corner like the Windows start menu, and is very light-weight.

---

### Post by Elfy on 2008-08-28
Amazing what you don't read when you're reading -

> also does the suppository contain the most updated version? :lol:

---

