---
title: "Grub won't boot ubuntu... Any way to get it to?"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by Lucypie on 2011-12-28
Alrighty. I'm cool.... Really... weirdly.. calm. About a week ago I reinstalled windows and ubuntu side by side to give windows a tad more room for games (33.3 gigs is not enough to play HUGE games.... So 100 might be.)

Today, I decided to reinstall my programs with Apt On Cd. I have natty, and I used the CD to restore some programs. Then I restored my /etc and /home folders... which I forgot was from 11.11... Oops ? I have Apt on Cd with KDE & XFCE and then another which has my update to 11.11... but after restoring those folders, I couldn't access admin and when I restarted I got a blank, purple screen. Oh well.... Any way to get grub to boot ubuntu, and after that, how can I log in (since i lost admin privs) and how can I restore my admin? Would it be easier to reinstall Ubuntu? I can do that... I've done it before. Partitions are already set up, just a matter of reinstalling. Just don't wanna. 

Ahhh, the feeling of "I don't even care" has come over me... Seeing thisi s the seventeenth (or more) time I've done this.... :D 

With love & happiness--Lucy..

---

### Post by Rhizoid on 2011-12-28
You should still be able to log in, just not to the GUI desktop.  Try pressing CTRL + ALT + f1 - do you get a login prompt?  If so, try logging in with your normal username and password, then letting us know in here.  If not - I see a reinstall on your horizon ;)

---

### Post by grahammechanical on 2011-12-28
Did you give Grub a purple background image? No? Then I am guessing that you see a Grub boot menu and you can select to boot Ubuntu. By the time you see that purple screen Grub has done its job. This is my guess. I think the purple screen is the Plymouth background image that appears while Ubuntu loads and just before it hands over to the log in screen.

So, you install Natty (11.04) but then overwrite the /etc and the /home folders with files from a Oneiric 11.10 install. Correct? Oops, indeed!

Natty is based on Gnome 2. Oneiric on Gnome three. Natty uses the Gnome Display Manager (GDM) for log in. Oneiric uses LightDM for the log in.

Do you have copies of the /etc folder and the /home folder from an 11.04 install? If not then an install of 11.10 is the way out, I would guess.

Regards.

---

### Post by Lucypie on 2011-12-28
Did I give grub a purple menu? Nope, but it had one so, I have no idea if it did its job. 

@Rhizoid -- I can't get to that screen, but if I get to it, I shall try :) 

@Graham -- I do not have a 11.10 disk. I have my original 11.04 disk and I have 3 Apt On Cd's that contain all my programs & upgrades (including KDE, XFCE, and 11.10). I cannot get into the filesystem for Ubuntu to restore anything. 

If this cannot be resolved by simple means, I will simply reinstall 11.04, restore all programs, and "pick my way" through my old settings.

---

