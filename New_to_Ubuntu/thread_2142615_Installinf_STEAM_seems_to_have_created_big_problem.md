---
title: "Installinf STEAM seems to have created big problems..."
date: 2013-05-06
forum: New to Ubuntu
---

### Post by Florio on 2013-05-06
Hi guys.

I installed Lubuntu on my wife's ACER Aspire One late last year, and the netbook was running very well until this morning.

The other day my son discovered that a particular game, Team Fortress 2,  was available for Linux, and so he asked me to install it on the Aspire  One. To do this, I first had to download STEAM. This seemed to take  ages. When I then tried to download the game, I discovered that it was  massive (12 Gb) and that there was nowhere near enough space on the hard  disk. So I quit the installation.

This morning when my wife turned on the computer, nothing seemed to  work, and everything was blocked. She left it running, and when I came  home I saw that several windows were open with Task Manager, and that  the mouse and touchpad were not responding. Since then I have managed to  reboot the computer, but now there is no internet connection at all,  and the wireless settings seem to have disappeared.

I suspect that the installation of STEAM is responsible for all of these  problems, and so I would like to uninstall it, but have received the  following message:
Software Index is broken. It is impossible to install or remove andy  software. Please use the package manager "Synaptic" or run "sudo  apt-get-install-f" in a terminal to finx this issue at first.

I have tried running the command but am receive the message:
command not found.

Could someone possibly give me advice on what to do?

Many thanks,

Florio

---

### Post by verymadpip on 2013-05-06
try
```

sudo apt-get install -f
```

Note the spaces & hyphens.

Good luck

---

### Post by Florio on 2013-05-06
Many thanks, verymadpip. Your reply has been a big help. I have now managed (I think) to remove STEAM via the Synaptic package manager, there is just a question mark icon left on the desktop. My real worry at this stage regards the internet connection. I cannot really understand why this has vanished and cannot for the life of me remember how to set it up.

---

### Post by verymadpip on 2013-05-06
Hi there, glad to help.  I expect you can just delete the icon, or it may vanish after a restart.

I'm not much good with networking TBH, but...do you still have a network manager icon in the panel?  It could be as simple as enabling networking & wireless from the dropdown menu. (They'll need to have check marks/ticks or whatever next to them - enable both).
Of course it could be something much more nightmarish :D

In my experience all the *buntus have "just worked" regarding networking so I'm hoping it's something straightforward.

---

