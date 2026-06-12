---
title: "no launcher or top panel menus"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by kevbuntude on 2011-11-04
Hey I could really use some help getting my Ubuntu up and running. I'm a complete beginner.  I was trying to install Amarok and my computer shut down and now I have no launcher or top panel menus.  I have File, Edit, View, Search, etc... but no network, battery, or clock or any of that.  So I can't get on the internet and I can't open any programs.  I've been trying different commands to connect to a wireless network through the terminal but nothing works.  Can somebody please walk through what to do to fix this?

---

### Post by dFlyer on 2011-11-04
Have you tried a cntl-alt t to open a terminal and a reboot to see what happens?

sudo halt

---

### Post by scruffyeagle on 2011-11-04
> **kevbuntude said:**
> Hey I could really use some help getting my Ubuntu up and running. I'm a complete beginner.  I was trying to install Amarok and my computer shut down and now I have no launcher or top panel menus.  I have File, Edit, View, Search, etc... but no network, battery, or clock or any of that.  So I can't get on the internet and I can't open any programs.  I've been trying different commands to connect to a wireless network through the terminal but nothing works.  Can somebody please walk through what to do to fix this?

I'm using Ubuntu v10.04 LTS 32-bit. I had a similar problem, with my top panel disappearing. I never did figure out why it disappeared, or return it's appearance to the original automatic state, but I did find a solution that makes it available. It's a 3-part process.

1) Your menu-click functions probably still work, so do a menu-click on the desktop. Select the "Create launcher" item, so you can create a launcher on the desktop. A logical name for it would be "Gnome panel". The command should be "gnome-panel". (Note the hyphen. It's necessary.)

2) Use the launcher you just created. That should make the panel show up across the top of the screen.

3) Under System/Preferences, the drop-down menu should have the item "Startup Applications". Click to activate it. Click on "Add". Enter name & command, just like when you made the desktop launcher. Close the box.

When you reboot, you should find your panel available across the top of your Gnome desktop. Once you see that what you did works, the launcher on the desktop becomes unnecessary. You could delete it, or leave it there in case it's needed in the future.

---

### Post by dFlyer on 2011-11-04
What version of ubuntu are you running?

---

### Post by stinkeye on 2011-11-04
In 11.10 you cant create a desktop launcher with right click
and gnome-panel isn't installed by default.
If you were in an ubuntu session and the unity panel and launcher disappeared
then compiz is at fault.

You can log into your ubuntu 2d session
At the login screen select your account then click on the gear wheel
and select **ubuntu 2d** as the session.
Once logged in copy and paste this command in the terminal and hit enter.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]     
```

This will reset compiz to defaults and then re-enable the unity plugin.
Now you should be able to login to your ubuntu session and see the launcher and panel.

---

### Post by LinuxFan999 on 2011-11-04
I have heard that this is a very common problem in 11.10, and since it appears that you can't create a new panel, there are only 2 solutions:
1. Reinstall Ubuntu.
2. Open a terminal, instal a different Desktop Environment (KDE, XFCE, LXDE), and Uninstall Gnome, nautilus, and Unity.

---

### Post by llamabr on 2011-11-04
Wow, really?  A user loses his top panel, and the answer is to do a fresh install of the entire OS?

Question: if you log in as another user, does the new user have a top panel?

---

### Post by stinkeye on 2011-11-04
> **LinuxFan999 said:**
> I have heard that this is a very common problem in 11.10, and since it appears that you can't create a new panel, there are only 2 solutions:
1. Reinstall Ubuntu.
2. Open a terminal, instal a different Desktop Environment (KDE, XFCE, LXDE), and Uninstall Gnome, nautilus, and Unity.
If you don't know what your talking about please don't comment with bad advice.
Gnome3 doesn't use gnome-panel.
If you install gnome-shell gnome-panel will be installed for the fallback session.

> **llamabr said:**
> Wow, really?  A user loses his top panel, and the answer is to do a fresh install of the entire OS?

Question: if you log in as another user, does the new user have a top panel?
Should do, as you will be using the default compiz configuration.

---

### Post by kevbuntude on 2011-11-05
> **stinkeye said:**
> In 11.10 you cant create a desktop launcher with right click
and gnome-panel isn't installed by default.
If you were in an ubuntu session and the unity panel and launcher disappeared
then compiz is at fault.

You can log into your ubuntu 2d session
At the login screen select your account then click on the gear wheel
and select **ubuntu 2d** as the session.
Once logged in copy and paste this command in the terminal and hit enter.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]     
```

This will reset compiz to defaults and then re-enable the unity plugin.
Now you should be able to login to your ubuntu session and see the launcher and panel.

Wow.  I don't know what that was but it worked.  Thanks so much.

---

### Post by stinkeye on 2011-11-05
> **kevbuntude said:**
> Wow.  I don't know what that was but it worked.  Thanks so much.
No problem.
Compiz is a bit flakey in 11.10.
Usually it just needs a reload by opening a terminal with ctrl+alt+t and running
```
compiz --replace &
```

Sometimes that fails because the compiz unity plugin (the unity plugin controls the launcher and panel) has become disabled, then the method you just used will set compiz back to default and re-enable the unity plugin.

You can of cause do the same thing just using compizconfig-settings-manager.

---

### Post by kevbuntude on 2011-11-08
> **stinkeye said:**
> No problem.
Compiz is a bit flakey in 11.10.
Usually it just needs a reload by opening a terminal with ctrl+alt+t and running
```
compiz --replace &
```

Sometimes that fails because the compiz unity plugin (the unity plugin controls the launcher and panel) has become disabled, then the method you just used will set compiz back to default and re-enable the unity plugin.

You can of cause do the same thing just using compizconfig-settings-manager.
Hey, uh... so ever since I did that my has started running really slow.  Its an old computer and possibly on its last legs but if I can get some more life out of it I would like to.  Is there anything in what I just did that would take up more ram?  I tried unistalling compiz because somebody told me that it can really slow down a laptop, but then my system crashed and I can now only run ubuntu 2d or a recovery console.  I have since tried reinstalling compiz but it didn't help.  Any thoughts?

---

### Post by kevbuntude on 2011-11-08
> **kevbuntude said:**
> Hey, uh... so ever since I did that my has started running really slow.  Its an old computer and possibly on its last legs but if I can get some more life out of it I would like to.  Is there anything in what I just did that would take up more ram?  I tried unistalling compiz because somebody told me that it can really slow down a laptop, but then my system crashed and I can now only run ubuntu 2d or a recovery console.  I have since tried reinstalling compiz but it didn't help.  Any thoughts?
also it crashes quite often.

---

### Post by stinkeye on 2011-11-08
You can only run Unity 2d because unity 3d is a plugin for the compiz window manager.
Remove compiz and you remove unity 3d.

The 2d session uses a different version of unity with Metacity as the window manager.

If you really want to run compiz and your having problems I would
suggest using 11.04 for now.

---

