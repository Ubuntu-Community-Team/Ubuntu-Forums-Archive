---
title: "X doesn't boot (slim, ssh, xdm, rfkill ?)"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by David Kasparek on 2012-06-15
Hello,
I used to use Fedora for few years, but i wanted to change. Now I'm really novice in Ubuntu. I don't know how to describe my problem, so I try to describe last steps I've done:
Xubuntu 12.04 LTS
Acer TravelMate 2490

1) After instalation everything was fine. But I wanted to switch off bluetooth (BT) during booting the pc. I used this: rfkill block bluetooth. Then I had to forbid (ban?) bluez-applet (blueman), because after its start it switched BT on. So I use gui service settings. There I found, that the service rfkill... (+something) wasn't checked, so I did it. (Silly me! I was affraid, that this service won't start during boot).

2) Before rebooting I found in the Synaptics (Software package manager) some few *dm (xdm, sdm, etc.) packages, and I install them (I wanted to see differences...). Dependencies were OK, some few packages (ssh...?) have been added. The dialog window started, and I chose "slim" as *dm for X.

After rebooting the user bootsplash was shown (xubuntu "wallpaper" with moving stripe, which shows, that system is booting). Than black screen and nothing.

I supposed, that the problem could be with the sdm (slim) - the screen with user name and password. So I use Live cd, and changed the slim to xdm - on my harddisk (/media.../etc/display-manager). But it didn't help. So I switched it back to slim.

I attach photo of booting pc before it freezes.

I really don't know, where the problem is. Maybe between my PC and my chair.
Thank you for any help. Sorry for my language mistakes (I'm working on it).
David Kasparek

---

### Post by Jose Catre-Vandis on 2012-06-15
Don't think it has anything to do with the changes you made to bluetooth, but all the additional dm's you added in one go. Looks like xdm is trying to loading but one of the others is the default. Do you only get a blank screen? can you swithcto a different VT (CTRL+ALT+1) ? and login to remove the other dm's? The default installed is lightdm. Slim is a good one for light systems, but works a bit differently to the others.

Oh, and some advice - change one thing at a time, then test ;)

---

### Post by David Kasparek on 2012-06-15
Thank you for your answer and helpful advice. Although I couldn't switch to a different VT, I tried to change the *dm to default. This idea came after your answer, and it works! Thank you very much!
David Kasparek

---

### Post by firekage on 2012-06-15
> **David Kasparek said:**
> Thank you for your answer and helpful advice. Although I couldn't switch to a different VT, I tried to change the *dm to default. This idea came after your answer, and it works! Thank you very much!
David Kasparek

Can you post what you did? Good to know for future experiences.

---

