---
title: "Minimized window simply disappears; can't find it to restore it"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by 2muchcoffeeman on 2012-04-02
Wise ones,

Okay, so I've managed to commit a couple of newbie fumbles.

First, whenever I minimize a program window, such as a browser, the window does not "drop to the bottom of the screen" and, in the form of a button, take up placeholder residence in the panel. Instead, the window shrinks down to nothing and simply disappears from the desktop. Yet the window remains operative; I know this because I'm running Pandora in a browser window that I have minimized. The window has disappeared, yet I continue to hear the music. There is no icon in the panel to indicate the presence of the browser window. I don't know where to look to find the minimized window so that I can restore it. If I had to pause the Pandora stream, I don't know where to find the window to restore it to the screen, so that I could click on the Pandora "pause" button.

Second, what is this desktop element called? 

[IMG]https://picasaweb.google.com/104042435271852937991/Kubuntu?authuser=0&authkey=Gv1sRgCMKhiduP9PCGHQ&feat=directlink[/IMG]

(if you can't see the image, right-click on it and open it in a new tab)

I'm referring to the translucent rectangle in the background, indicated by the red arrow. It's not a *panel*; that's the bar at the bottom of the screen. It's not a program *window*. When I installed Kubuntu (via Wubi), this element -- whatever it's called, and I can't find an entry in the KDE glossary that describes it -- was a default feature of the desktop, and displayed my home directory.

More to the point of this post: Why did it disappear? What switch must I have thrown to make it go away, and how do I bring it back?

#-o

---

### Post by SeijiSensei on 2012-04-02
The minimized window may be assigned to a different desktop.  Try switching to the other desktop and see if the application appears there.

---

### Post by 2muchcoffeeman on 2012-04-02
Thanks, SeijiSensei . . . yes, I had looked at the other virtual desktops, hoping it was something as simple as that. Nothing. The other virtual desktops are empty.

---

### Post by SeijiSensei on 2012-04-02
My first suggestion in cases like these is to create a new user account (System Settings > User Management) and log into that.  Do you have the same problems with missing windows?  If not, then there's something screwy in the KDE settings on your normal account.  If the new account has the same problem, there's a system-wide problem with KDE.  You can quickly reset your personal KDE settings to the defaults by opening a Terminal ("Konsole" in KDE) and typing these commands:

```

cd ~
mv .kde .kde.old

```

Now log out and log back in.  You'll be greeted with the default KDE desktop without any customizations you may have made.

The transparent window you mentioned originally is the output of the Folder View widget.  If you put your mouse cursor over the window, a settings bar will appear to the right or left of the window depending on its location on the desktop.  If you click the X button, you'll never see the Folder View again.  You can restore it by right-clicking on the desktop, choosing Add Widgets, and double-clicking the Folder View item.  You can also change which directory is displayed by default by clicking the little wrench icon in the settings bar.

I never install using WUBI, so I don't know whether any of the things you're observing have to do with that.  I rather doubt it, but I can't say for sure.

---

### Post by 2muchcoffeeman on 2012-04-02
Thank you; I'll give your suggestions a try and will report back.

Is the code you supplied exact? Are there any assumed values (e.g., a user name) that I need to know, and need to fill in? Or is the code to be typed in exactly as you presented it?

And thanks for the info on the folder-view widget. I was familiar with the retracting settings toolbar, but did not know how to restore the widget once it had been erroneously deleted.

---

### Post by SeijiSensei on 2012-04-03
Both commands would be run at the terminal exactly as written with your normal privileges.  The first moves the focus to your home directory, represented by the tilde ("~"); the second renames .kde to .kde.old.

---

### Post by whatthefunk on 2012-04-03
Are you sure that you have a Task Manager in your lower panel?

---

### Post by 2muchcoffeeman on 2012-04-04
Being such a recent convert to Linux/Ubuntu, I gave it some thought and decided I need some more time and experience under my belt before jumping into the KDE deep end. I would be forever running to these boards to fix issues that are pretty minor. In the post above, for example, @whatthefunk asks:* Do you have a Task Manager in your lower panel?*

Answer: Uhhhh . . . . . :???:

It's easy to start clicking and dragging and poking around all the elements of KDE, and before you know it, some thread has pulled loose and the entire fabric begins to unravel, and there's no way to find my way back to the start of the chain of events. I couldn't even answer @whatthefunk's question!

In other words, I need to RTFM, and I think the best place to learn the manual is with Ubuntu, where there appear to be fewer moving parts than in Kubuntu. The desktop environment, for example, is simpler than it is with KDE. Sadly, the Unity environment also is more cartoonish and less feature-rich than the sleek KDE desktop, which I greatly prefer and want to get back to, someday. But for now, simplicity will serve me better. And it will save you the headache of repeated pleas for help.

So, I ended up removing Kubuntu entirely, and replaced it with Ubuntu -- as a dual-boot on my main laptop, and as a complete replacement for Win7 on my netbook.

But, to preserve something of the spirit of adventure, I *did* load the final beta version of Precise Pangolin, instead of stable Oneiric Ocelot. ;)

The switch back to Ubuntu hasn't eliminated all puzzlers. At the moment, for example, I can't figure out how to get Rhythmbox to load and play a .pls file from a local radio station. I've downloaded/installed all the plug-ins that Ubuntu instructed me to install (I was presented with a long list of plug-ins etc. that the dialog box said I needed to install, and I merely clicked "install." I assumed that was all that would be needed). Yet Rhythmbox still won't play the stream. So I've got some more research to do.

Give me some time with the Linux playbook and some experience with it in the Ubutnu environment, and I think I'll be better equipped to tackle Kubuntu.

Thanks for your help.

---

### Post by whatthefunk on 2012-04-04
Its really easy to check if you have a task bar or not....could have asked:)

---

### Post by 2muchcoffeeman on 2012-04-04
LOL, I'm sure it is, thanks. I just don't want to abuse the privilege of resorting to the forums for every little problem. I'm confident I'll be back into Kubuntu after a little bit of time getting used to Ubuntu specifically, and Linux more generally.

---

### Post by JonasBid on 2012-04-04
Hi
I'm absolutely new to Linux/Ubuntu so I kindly ask since I experience a similarity to this problem.  I use ubuntu 11.10

Same situation when I minimize a program window, the window shrinks down to nothing and simply disappears from the desktop. Yet the window remains operative. I find the windows using ALT-TAB or using  my Task manager on the left side, works fine, BUT when there is 2 of the same kind?

Example with Thunderbird, I write a draft, save the draft, do not close it or minimize it & go back to Thunderbird MAIN using Task Manager or ALT-TAB, find what I was looking for & now I want to ALT-TAB back to draft, but no go. 

How to find the draft the easiest way. Yes I know I will find it in drafts folder Thunderbird, but I miss the ability to ALT-TAB to the window, I experience that using ALT-TAB or Task Manager takes you to the top window of a program not to the sub-window?

Thanks for your help in explaining: How do I do that? Cheers

---

### Post by jerome1232 on 2012-04-04
alt+` (above the tab key on a us keyboard) will tab between open windows of the application your in. In the alt+tab menu, pressing alt+up will open the group of windows for that application, or simply pausing on the application for about 3 seconds will unfold it as well so you can tab through it's windows.

---

### Post by whatthefunk on 2012-04-04
> **2muchcoffeeman said:**
> LOL, I'm sure it is, thanks. I just don't want to abuse the privilege of resorting to the forums for every little problem. I'm confident I'll be back into Kubuntu after a little bit of time getting used to Ubuntu specifically, and Linux more generally.

The forums are here to help, so please ask away:)

You should also keep in mind that Ubuntu and Kubuntu, although based on the same OS, use entirely different desktop environments and so any GUI fix you find in Ubuntu will probably not be the same in Kubuntu.  When I first started using Kubuntu I had no idea how to do anything either, but after a while playing around, I figured it out.  Just play around ith it, break it like you did before, and learn how to fix it.

---

### Post by cmcanulty on 2012-04-04
check out ubuntu classic and xfce4 or xubuntu all can be easily installed from synaptic and not mess up your system just pick one at logon much easier to configure than unity or kubuntu

---

### Post by JonasBid on 2012-04-05
> **jerome1232 said:**
> alt+` (above the tab key on a us keyboard) will tab between open windows of the application your in. In the alt+tab menu, pressing alt+up will open the group of windows for that application, or simply pausing on the application for about 3 seconds will unfold it as well so you can tab through it's windows.

COOL, Thank you! Simply pausing on the application works marvelous & saved me from RTFM :-) I have us keyboard but another language installed so pausing is what works for me. Cheers

---

### Post by 2muchcoffeeman on 2012-04-16
> **whatthefunk said:**
>  keep in mind that Ubuntu and Kubuntu, although based on the same OS, use entirely different desktop environments and so any GUI fix you find in Ubuntu will probably not be the same in Kubuntu.  When I first started using Kubuntu I had no idea how to do anything either, but after a while playing around, I figured it out.  Just play around ith it, break it like you did before, and learn how to fix it.

Roger that; I much prefer the KDE desktop environment to Unity, and I'm looking forward to returning to it. But I figure I need some time to learn some basic OS mechanics.

For example, take the comment from @cmcanulty, above. In it, (s)he says:

> all can be easily installed from synaptic

. . . and I have no idea what *synaptic* is, let alone how one installs anything from it. I know there are mountains of documentation, somewhere, that explain it. My job is to find it and read it.

I'm certainly game for breaking Ubuntu and learning how to fix it. My limited experience is that it has been easier to fix Ubuntu than it was to fix even minor mishaps in Kubuntu.

Recently Ubuntu presented me with a dialog that instructed me to "get" or "install" (or something)  any one of several different . . . things (programs? scripts? packages?). It was a dialog that assumed I knew how to do what it was instructing me to do. But I don't. I'll be taking that particular episode to its own thread.

Once I get stuff like that down, I'll be jumping back into Kubuntu.

---

### Post by whatthefunk on 2012-04-16
To be honest, youll learn just as much from Kubuntu as from any other Linux distro.

To answer some of your questions, Synaptic is a package manager program.  I think its installed by default in Ubuntu...have a look in your menus for it.  (In Kubuntu, Muon is the default package manager...)

The "get" and "install" thing youre talking about is probably this:
```
sudo apt-get install PROGRAM_NAME
```

You can use that to install programs in the terminal.  I personally find it much easier to do this than to use a package manager.

---

