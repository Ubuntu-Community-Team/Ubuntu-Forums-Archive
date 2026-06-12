---
title: "How To: Create a lightweight installation"
date: 2006-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Pitbull11188 on 2006-12-24
[SIZE="5"]**Purpose:**[/SIZE] Inform an end user as to how they could quickly and easily create a lightweight ubuntu install able to run much more than adequately on an older computer. 

[SIZE="5"]**System:**[/SIZE] This faq is aimed at those middle aged computers that aren't quite ready for a minilinux distribution, but cannot run the bloated Gnome and KDE distributions common today. Ex. A P2 with 128mb ram.
[SIZE="5"][B]
Materials:[/B][/SIZE]  The current Ubuntu Linux alternate install cd, an older computer, and 1-2 hours depending upon computer speed and user prowess.

[SIZE="5"]**Instructions:**[/SIZE]

       [LIST]

[/LIST]Commence with a server installation
	[LIST]
[/LIST]Upon reboot login

```
[SIZE="3"]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install x-window-system-core xserver-xorg
sudo apt-get install fluxbox 
sudo apt-get install xterm
sudo apt-get install xmms
sudo apt-get install gaim
sudo apt-get install firefox
sudo apt-get install abiword 
sudo apt-get install xpdf
sudo apt-get install (any other personally required programs)[/SIZE]
```


[SIZE="5"]**Notes:**[/SIZE]Fluxbox is not known for ease of use so if you're uncomfortable with that I suggest you go with jwm or icewm or something similar. However learning to use fluxbox was probably one of the best things I ever did, and it only took me approximately 3 hours.

---

### Post by gimfred on 2007-03-25
hmmm... I thought this would be a howto to recompile the kernel/programs for your own machine :confused: . Ah Well... Thanks though, I'm sure it is of use to many folks
 :) 
just wanted uptodate info (people seemed to have stopped at 2.4 ;)

---

