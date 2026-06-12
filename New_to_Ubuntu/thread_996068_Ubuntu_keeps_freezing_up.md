---
title: "Ubuntu keeps freezing up"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by thetrevorharmon on 2008-11-28
Hello! So I have a dual-boot windows XP/Ubuntu computer. I've been trying to get WINE installed on Ubuntu so I can have Photoshop access on Ubuntu. The problem is that I'll boot to ubuntu and everything is fine. Then while in Ubuntu, it freezes up. It freezes after using firefox for a about 30 seconds. I have an internet filter (netnanny) and time limit (timecop) installed on the windows partition. Would that affect the ubuntu partition at all? Or is it something else? Thanks for any help you can offer!

---

### Post by Michael.Godawski on 2008-11-28
Freezing can be caused by many things... would be good to know your hardware, your specs, the Ubuntu version you are using. 

Does Ubuntu crash only when using firefox or does it not matter what you are doing?
Are you running compiz ? (extra visual effects)

---

### Post by jakupl on 2008-11-28
Does only firefox freeze up or the whole system.

If its only firefox, try to open a terminal when the computer is freezing, and write:
```
pkill firefox
```

---

### Post by icanfly0307 on 2008-11-28
Do you have the latest version of Firefox? Are there any Flash plugins running when your computer crashes? And, no, stuff on your Windows partition will not affect Ubuntu in anyway.

---

### Post by thetrevorharmon on 2008-11-28
Ok. Ubuntu version: 8.10. Specs: 200gb hard drive, 2GB ram, 3.0GB processor...the usual. I have the latest version of firefox, no extra visual effects (if i did, it wouldn't matter, i have dedicated video memory), no bad firefox plugins. i have no access to terminal. the computer is completely frozen up.  Would the fact i'm running it with a linksys wireless g pci card make any difference? It only crashes when I run firefox, as far as I know.

---

### Post by Mr. Picklesworth on 2008-11-28
Is the caps lock or num lock light blinking on your keyboard when it freezes?
What kind of computer is that? Are you connecting wirelessly or with a network cable?

What happens if, when it freezes, you press Ctrl + Alt + Backspace? That should reset the graphical environment, killing your session and landing you back at the login screen. If it does not, the problem is happening at a particularly low level.

---

### Post by thetrevorharmon on 2008-11-28
Yes, it is blinking when it freezes. Wireless internet, using a linksys network and pci card.

---

### Post by icanfly0307 on 2008-11-28
All I know is this: If your caps lock, num lock and scroll lock lights are blinking, it indicates a kernel panic. Have you updated your system recently? If not, try updating your kernel to a more recent version.

System > Administration > Update Manager > Check For Updates

---

### Post by Mr. Picklesworth on 2008-11-28
I find that wireless drivers are a very popular cause of kernel panics, so I'm betting it's that for now. Right click on the network manager (which you use to connect in the first place; generally visible as a some blue bars showing signal strength). Go to Connection Information and if there is more than one tab make sure you are looking at the tab for the wireless connection. There should be a field there mentioning the driver providing that connection.

There has been a kernel update (2.6.27-9) which may resolve your issue, too. To check if you have it, you can run "uname -r" in the terminal.

---

### Post by DWade on 2008-11-28
I have three questions.

1st is your computer a laptop?

2nd you said pci card or did you mean pcmia card.

3rd do you use a usb mouse with the laptop if that is what you are using.



I have an aircard.  If I use my usb mouse when the air card is running and down loading it will freeze ubuntu.  no keys (ie ctrl + alt + backspace) will work.  I have to shut it off and start over.  On the plus side all downloads or updates start off where it froze.

I have to make sure I use my synaptic touch pad when downloading.

I thought about placing a bug report. but.. time:lolflag:

---

### Post by thetrevorharmon on 2008-11-28
laptop: no. pc that i built myself.
pci card: just a card that i stick in my computer. I can't remember what you call that. 
usb mouse: yes, but its separate from my keyboard. its all wired.

my kernal version is 2.6.24-21-generic. i looked at my update manager, but i couldn't see a kernel update. there were a few i still needed to install. but none were dealing with kernel stuff.

---

### Post by Mr. Picklesworth on 2008-11-28
'My bad. Don't worry about kernel updates, then. Ignorant I jumped to conclusions! You're running Hardy, not Intrepid!

One thing to look into is proprietary drivers. Go to System -> Administration -> Hardware Drivers. If it lists some other drivers available for your hardware, it could be worth trying them. (Or if there are some proprietary drivers installed, try disabling them to see what happens).

---

### Post by thetrevorharmon on 2008-11-28
I actually went to ubuntu's "help and support" and tried this code:
```
sudo apt-get install nfs-kernel-server
```
it worked. i'm on ubuntu right now. i have no idea why it worked...but hey! it did. i also installed "windows wireless drivers", located my driver on the windows partition and installed it on ubuntu. maybe both of those combined did the job? anyways, thanks for the help.

---

