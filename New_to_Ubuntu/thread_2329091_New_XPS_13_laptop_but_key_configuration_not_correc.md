---
title: "New XPS 13 laptop but key configuration not correct - or at least different"
date: 2016-06-27
forum: New to Ubuntu
---

### Post by Neil_Nand on 2016-06-27
Hello,

Recently I got myself a Dell XPS 13 laptop but I've noticed a couple of problems with the key configuration but as I'm not to well versed with Ubuntu to workout how to fix it myself.

On my desktop, I also have Ubuntu on that, when I press the Windows / Super key the dash (I think that's the correct name) comes up & I can type into the search field, I cannot seem to do this with my new laptop.

The other problem I have is after enabling four multiple desktops when I press Ctrl + Alt + Arrow Key to move between them it doesn't always work, it sometimes decides to move the currently active window to either the left, right or full screen of the current desktop, like if I'd dragged the top bar of it to any side of the screen. Again this isn't an issue with my desktop.

I've looked at the Shortcuts list in All Settings > Keyboard but haven't found anything obvious so solve this.

The laptop comes with Ubuntu 14.04.

Thanks in advance for any help,
Neil.

---

### Post by Geoffrey_Arndt on 2016-06-28
I have the "Workspace Switcher" icon (after enabling workspaces via "System Settings>Appearance>Behavior") in my Launcher Pane (the default pane at the left of the screen) .    

To switch desktops, I use the mouse to click on the workspace icon in the panel, and then, just click on one of the 4 windows that pop up.    Works great.   Ctrl+Alt+Arrow Key works also, but only if there is a workspace to move into (meaning 1 move operation at a time).    On my laptop, the Super Key does more than 1 thing . . a quick press will open the dash/search screen.    An extended press will open the "hot-key" dialog window.

---

### Post by Neil_Nand on 2016-07-05
> **Geoffrey_Arndt said:**
> I have the "Workspace Switcher" icon (after enabling workspaces via "System Settings>Appearance>Behavior") in my Launcher Pane (the default pane at the left of the screen) .    

To switch desktops, I use the mouse to click on the workspace icon in the panel, and then, just click on one of the 4 windows that pop up.    Works great.   Ctrl+Alt+Arrow Key works also, but only if there is a workspace to move into (meaning 1 move operation at a time).    On my laptop, the Super Key does more than 1 thing . . a quick press will open the dash/search screen.    An extended press will open the "hot-key" dialog window.

Thanks for the reply, I think there may have been a misunderstanding of my original post though.

Everything you've described is how it should work, however that's not how it is actually working on my laptop.

Pressing Ctrl + Alt +Arrow some times changes workspace but a lot of the time it will just 'snap' the currently active window to the side instead. The super key does nothing, either when pressed or held down.

What I'm trying to achieve is functionality you've described, as that's how it should work, but I've no idea how to get that working. I've looked through the keyboard shortcut settings but cannot find it.

---

### Post by Geoffrey_Arndt on 2016-07-06
I've read that these hotkeys work as expected on Ubuntu 16.04 which uses a much later kernel (4.4x).    However, doing a re-install is a lot of work in some cases (other cases not so much).

Anyway,  without having the device myself (to test various options), the best advice I know of is to do some focused searches on "Dell XPS Keybindings Ubuntu" or just "Changing Dell XPS Keybindings" . . .  A couple of other good resources to search are the Arch Linux Forums and the AskUbuntu forums.   That is the first route I would check out if I had that machine & issue.

Note:   I recall that many Dell laptops allow for control of keybindings via the UEFI/BIOS . . . have you checked that out?

---

### Post by DuckHook on 2016-07-06
> **Neil_Nand said:**
> I've looked through the keyboard shortcut settings but cannot find it.Your problem may (only *may*) be caused by a misconfigured keyboard improperly chosen at system install. For most English speakers, you want your country locale and Standard US keyboard. To reconfigure keyboard, from a virtual console (<Ctrl>+<Alt>+<F1>), do:```
sudo dpkg-reconfigure keyboard-configuration
```...and answer the questions, making sure to choose "standard US keyboard". You will have to reboot before setting will take effect. Also post output from:```
locale
```

---

### Post by Neil_Nand on 2016-08-08
Hello,

Thanks for the replies - you've both gave me an a good direction to look in as I had no idea what to do.

I've managed to solve the desktop switching issue, I installed an application called "CompizConfig Settings Manager" & disabled then enabled "Desktop Wall" based on something I recently read on another thread. This told me that I had something called "Grid" was enabled and the shortcut keys for that were the same as for the desktop switching, it appears Grid snaps a window to either side of the screen or maximises it. Changing the shortcut keys for Grid seems to have solved this issue.

The Super key not displaying the launcher though is still an on going issue. Using CompizConfig Settings Manager I found what I believe to be the correct place to set the shortcut for it titled "Key to show Dash, Launcher & Help Overlay" in the "Ubuntu Unity Plugin" but every time I set it to the super key it automatically disables the shortcut. If anyone has any ideas on that it'd be great to hear.

Thanks again for all the replies so far, managed to solve half the problem now.

---

### Post by CatKiller on 2016-08-08
One of the configuration things that Dell does is to disable the Super key. I have no idea why. I think it's just a package that you can remove, but I don't know for sure because I installed 16.04 over the top of mine.

Edit: the package is called dell-super-key. Just remove it with your package manager of choice.

---

### Post by Neil_Nand on 2016-08-09
Hello,

You have no idea how thankful I am for that answer, this has been a problem for me since I got the laptop in April! Why Dell decided to add such a stupid package I'll never understand.

Thanks so much again, that's both my main problems solved now!

---

### Post by CatKiller on 2016-08-09
Awesome! Glad to hear it :)

---

### Post by gerbenvaneerten on 2017-01-25
Great! Kept fooling around with dconf without being able to solve this issue. This worked fine.

---

