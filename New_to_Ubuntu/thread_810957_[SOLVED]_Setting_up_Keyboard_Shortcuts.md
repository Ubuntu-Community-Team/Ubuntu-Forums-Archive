---
title: "[SOLVED] Setting up Keyboard Shortcuts"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Nxion on 2008-05-28
What I would like to know is how I would setup keyboard shortcuts for my applications. I mainly want to have shortcuts for terminal Firefox Virtualbox and maybe a few others. 

Thanks in advance.

---

### Post by issih on 2008-05-28
Terminal is easy, just open "System->Preferences->Keyboard Shortcuts"

In there one of the options is launching a terminal, just set a shortcut combination for it, I use ctrl alt T myself :)

Launching arbitrary applications is a bit trickier, but is achievable, it depends on what window manager you are running though.

Assuming you are running hardy heron and therefore compiz, you need to install "compizconfig-settings-manager" if you haven't already.

Launch "System->Preferences->Advanced Desktop Effects Settings"
Open the General Options Plugin, and go to the Commands tab.

You now need to expand the commands list, and set up commands for each application you want to launch.

e.g. Command line X :  firefox

Then expand the key bindings section and set the shortcut combination you want in the Run command X section.

Hope you follow that, its a bit fiddly I know

---

### Post by Nxion on 2008-05-28
Thanks for the prompt reply,

What window manager are you using? I am using Gnome, I went into System > Preferences > Keyboard Shortcuts. And I didn't see an entry for terminal. I found where there wass one for oping a home folder and a web browser but not a terminal. Do I have to install something else to get more functionally?

---

### Post by issih on 2008-05-29
Gnome is not the window manager, All the nomenclature is somewhat confusing at first. 

In essence Gnome is the "Desktop Environment", the bits of code that makes everything relatively cohesive and consistent from one application to the next.

The window manager is a specific bit of code to do with window positioning and layout, Gnome can use different window managers. Almost everything in linux is far more modular than windows.

Gnome's default window manager is called metacity, ubuntu however attempts to enable another one called compiz by default. whether this succeeds or not depends on your graphics hardware, if it fails it will fall back to using metacity. If you go to System->Preferences-Appearance, and look at the "Visual Effects" tab, if you have "none" selected, you are running metacity, anything else means you are running compiz.

You were in the right place for configuring a terminal shortcut, its lurking in their somewhere I assure you.

Sorry for the delay in replying, sleep intervened

---

### Post by drao on 2008-05-29
goto system->preferences->keyboard shortcuts(click on it), you will see a keyboard shortcuts window.Scrolled down, you will find Desktop, in that you can see Run terminal, click on it and it has shortcut field right to it. Click on it and press key combination whatever you like to set. You can set key combination for all whatever appear in that list . Hope you got the answer. Sorry if you know it already.

---

### Post by Nxion on 2008-05-29
> **issih said:**
> Gnome is not the window manager, All the nomenclature is somewhat confusing at first. 

In essence Gnome is the "Desktop Environment", the bits of code that makes everything relatively cohesive and consistent from one application to the next.

The window manager is a specific bit of code to do with window positioning and layout, Gnome can use different window managers. Almost everything in linux is far more modular than windows.

Gnome's default window manager is called metacity, ubuntu however attempts to enable another one called compiz by default. whether this succeeds or not depends on your graphics hardware, if it fails it will fall back to using metacity. If you go to System->Preferences-Appearance, and look at the "Visual Effects" tab, if you have "none" selected, you are running metacity, anything else means you are running compiz.

You were in the right place for configuring a terminal shortcut, its lurking in their somewhere I assure you.

Sorry for the delay in replying, sleep intervened

My apoligies to that, I am using Gnome with Openbox. Maybe that is why some of the shortcuts dont show up. Alt + F2 doesn't even work.

---

### Post by Nxion on 2008-05-29
> **drao said:**
> goto system->preferences->keyboard shortcuts(click on it), you will see a keyboard shortcuts window.Scrolled down, you will find Desktop, in that you can see Run terminal, click on it and it has shortcut field right to it. Click on it and press key combination whatever you like to set. You can set key combination for all whatever appear in that list . Hope you got the answer. Sorry if you know it already.

I have looked in there and It is not in there. I don't have my laptop with me at the moment otherwise I would include a screen shot. Could it be a case that Openbox wont me change that setting? And that is why it is not in there. I looked everywhere, There are only two categories, Desktop and Sound, I can find anywhere in anything how to set to open my terminal w/ a key combo. I do have compiz installed but not active at the moment. Should I just use that to set key combos?

Thanks!

---

### Post by issih on 2008-05-29
its very likely that it is because you are using openbox that the normal way of doing things doesn't work....

A quick google led me here:

[http://www.gbar.dtu.dk/index.php/Openbox](http://www.gbar.dtu.dk/index.php/Openbox)

which says that the file you need to modify is "~/.config/openbox/rc.xml"

Apparently keyboard shortcuts are configured in there. Hopefully there will be some already in there so you can copy the syntax, I can't really help there as I'm running compiz myself.

Good luck

---

### Post by urukrama on 2008-05-29
If you are using Openbox, you'll have to edit the rc.xml file, which is located in /home/USERNAME/.config/openbox/

In the keyboard section of that file, you can specify your key bindings. For example, to launch gmrun with the keys Alt+F2, you would add the following:

> <keybind key="A-F2">
      <action name="execute">
        <execute>gmrun</execute>
      </action>
    </keybind>

Make your changes to the file, reconfigure Openbox (either in the desktop menu (if you use that in Gnome), or enter the command *openbox --reconfigure* in a terminal)

See [here]("http://urukrama.wordpress.com/openbox-guide/#Key_mouse") for more info.

If you want more examples, you can see my rc.xml file [here]("http://urukrama.pastebin.com/f221730d2").

---

### Post by Nxion on 2008-05-31
Thanks for all the suggestions I got it all to work now. Openbox is so pretty :)

---

