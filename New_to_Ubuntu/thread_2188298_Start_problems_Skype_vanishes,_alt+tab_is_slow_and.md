---
title: "Start problems: Skype vanishes, alt+tab is slow and grouped, etc..."
date: 2013-11-16
forum: New to Ubuntu
---

### Post by stefan_03 on 2013-11-16
[SIZE=2][COLOR=#000000]Hey there,

Until yesterday I used Fedora19, but then I decided to install Ubuntu 13.10 with Unity. I don't know why and I am starting to regret it more and more. I an not a Linux beginner, but a Ubuntu beginner

1. When I start Skype and minimize the window, I have to go through the processes, end Skype and restart it (or open the Terminal and enter **skype**). On Fedora (with Gnome) there was an extension where you could see minimized apps in the task bar - I need this for Unity: [/COLOR][[COLOR=#000000]GNOME Extension[/COLOR]]("https://extensions.gnome.org/extension/584/taskbar")[COLOR=#000000]
2. The common alt+tab is horrible, I can't wait 5 seconds everytime when I switch between 2 windows. I installed Compiz and did all the recommended things, but it still takes long time and the items stay grouped - I hated this when it first appeared on Windows Vista and I still hate it. [/COLOR][[COLOR=#000000]GNOME Extension[/COLOR]]("https://extensions.gnome.org/extension/15/alternatetab")[COLOR=#000000]. My makeshift: I activated Ring Switcher on Compiz.
3. Is there a a possibility to see all opened programs, like the Super button on GNOME? --> [/COLOR][[COLOR=#000000]like this[/COLOR]]("http://kofler.info/uploads/images/blog/gnome30.png")[COLOR=#000000]
4. When I press the "start" button (Windows key), there are some special effects, where my PC is not able to handle them right, everything is juddering when it's opened - can I disable that? It is okay when it looks ugly, as long as it is fast.
5. How can I but a VPN connection to autostart?

Thanks, I am grateful for any help!

Stefan[/COLOR][/SIZE]

---

### Post by stefan_03 on 2013-11-16
[COLOR=#000000][FONT=arial]Fine, I'll start![/FONT][/COLOR]
[COLOR=#000000][FONT=arial]1. Trying a few times sudo apt-get install sni-qt:i386 + a few restarts, now it works[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]2. I think there is no solution available yet[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]3. don't know[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]4. oh god I still hate it, no solution yet[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]5. nmli con up uuid <uuid> works fine, I've created a button on my dekstop which I click on start up[/FONT][/COLOR]

---

### Post by Allavona on 2013-11-16
The open programs in Unity are represented on the launcher with the icon and a real teeny arrow. When I used Unity I ran a dock just so I could quickly see what I had going on. I hid the launcher and set the sensitivity so low that I had to hit the super key to show it!

---

### Post by kostkon on 2013-11-16
> **stefan_03 said:**
> 1. Trying a few times sudo apt-get install sni-qt:i386 + a few restarts, now it
A much better option, at least for me, is [skype-wrapper]("https://launchpad.net/~skype-wrapper/+archive/ppa"). It will integrate Skype into the messaging menu; no need for the skype icon with sni-qt.

---

### Post by stefan_03 on 2013-11-18
1. Solved, thank you!
2. I took an alternative switcher from Compiz
3. no solutions yet (but thanks for the hint with the tiny arrow)
4. I erased my hard drive and installed Ubuntu 12.04 - problem solved
5. as mentioned, no auto start but a start button on the Desktop

Thanks so far!

---

