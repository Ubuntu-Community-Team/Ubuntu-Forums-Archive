---
title: "A couple question about openbox and other stuff"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by afixane on 2012-06-21
Hi guys! :D

I recently try to install Ubuntu from minimal cd in my Netbook. Here's my question :


1. I try to install network-manager, and then try to open nm-applet on tint2, and it's worked! But, why when i highlight the nm-applet, something with yellow box appeared and "Networking disabled". Is there any way to solve this issue?


2. I try to change my wallpaper using nitrogen, but anytime i log in, the wallpaper is set to deault again. Is there any way to solve this issue?


3. Is there any "menu" for tint2?

4. Can i setup wicd for mobile connection?

---

### Post by 4Orbs on 2012-06-21
I really like [THIS OPENBOX GUIDE]("http://urukrama.wordpress.com/openbox-guide") and it should cover most of your questions.

---

### Post by afixane on 2012-06-21
Umm, yes, but it doesn't answer my first question :(

---

### Post by 4Orbs on 2012-06-21
Right-click on the network mgr applet and you should see the option to enable networking.
[ATTACH]220042[/ATTACH]
I don't use Tint2. The NMapplet in the pic is in Docker, which is a moveable system tray that's independant of the task bar.

---

### Post by afixane on 2012-06-21
I see "enable networking" option, but i can't click it.

---

### Post by Rodney9 on 2012-06-21
Good tint2 tutorial - 

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

[http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/](http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/)

---

### Post by 4Orbs on 2012-06-21
> **afixane said:**
> I see "enable networking" option, but i can't click it.
Since you are using Openbox with the minimal Ubuntu installation, you might need to add network-manager to the autostarted applications in the Openbox folder (.config/openbox/autostart.sh).

---

### Post by afixane on 2012-06-21
> **4Orbs said:**
> Since you are using Openbox with the minimal Ubuntu installation, you might need to add network-manager to the autostarted applications in the Openbox folder (.config/openbox/autostart.sh).

I still can't click it :(

---

### Post by 4Orbs on 2012-06-21
Did you restart your computer after adding network-manager to the autostart.sh?

If you did, then you might need to open the "Edit Connections" option and add your connection manually. Are you trying to connect wireless or wired?

Here's a screenshot of my autostart.sh

[ATTACH]220044[/ATTACH]

I don't have network-manager added because I use Xubuntu (which automatically starts it) and Openbox as an alternate session.

---

### Post by afixane on 2012-06-21
> **4Orbs said:**
> Did you restart your computer after adding network-manager to the autostart.sh?

If you did, then you might need to open the "Edit Connections" option and add your connection manually. Are you trying to connect wireless or wired?

No, i'm just log-out and login again. I'm trying to connect wireless connection

---

### Post by 4Orbs on 2012-06-21
If restarting the computer doesn't fix it (you should be able to just left-click on the nmapplet and see your wireless network as an available option), then you might need to install the driver for your specific network card. But you can't do that without a connection. Do you have a way to connect with a wire available?

---

### Post by afixane on 2012-06-21
Yes, i have a wired connection. But currently, i can post this thread using wicd....

---

### Post by 4Orbs on 2012-06-21
Do you mean that wicd is working wirelessly on your netbook? If so, then I believe that you need to disable wicd before trying to use network manager. And anyway, if wicd is working well then there is no need for network manager. Wicd is good stuff.

---

### Post by afixane on 2012-06-21
Yes, wicd work flawlessly on my netbook

---

### Post by 4Orbs on 2012-06-21
So, you are trying to use both wicd and network manager? You only need one or the other... no reason to have both.

---

### Post by afixane on 2012-06-21
No. I'm trying to search network manager alternative. But then i realized that wicd can't do Mobile Connection. However, i've purge wicd and all wicd dependency, but i still can't click enable networking.

---

### Post by 4Orbs on 2012-06-21
If network manager is the only one on your system now, and you have restarted the netbook after purging wicd, and you have network-manager listed in your ~/.config/openbox/autostart.sh file, then you should be able to enable networking.

I would make sure network manager is working with a wired connection first. Then open the "Edit Connections" and save the wired connection info but un-check the "Start Automatically" option. Then I would try connecting wirelessly. I haven't worked on a mobile connection for a long time, so can't offer any help there. My guess would be that you need a specific driver for the mobile connection and it's not installed. If so, then you'll need to do some searching for information to fix it.

---

