---
title: "ubuntu totally fubard, need help reloading gnome."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by phread59 on 2008-08-27
My audio died after an update.  I have been following a sticky on repairing the audio.  I erased and reloaded ALSA.  There was a warning that said Gnome could be affected.  Well they're right.  Gnome is gone.  I need to get to a point where I can access terminal and sudo it back.  I have the syntax I need I just cannot get to terminal.

Any suggestions on how to boot and get to terminal?  I try to log into my desktop but I keep getting denied because it is not there.  I realize I can reinstall.  But I really don't want to do that and loose everything again.  I really could use some help here please.  I have tried a rescue reboot and that failed.  I have tried the live CD and it returns- current level with Synaptic. I tried to sudo it and tried to install with install with synaptic and can't get it onto the hard drive.  I'm missing something simple here.  Help would be very much so appreciated.

I'm booting from Fluxbuntu I have on a pendrive right now.  I don't want to have to go back to Windughs if I don't have to.  I'd like to get Gnome fixed before I go back after the audio.  BTW Ryhtembox would see songs on a CD but put a red ball with a line through it if you tried to play it.  It would return the following message if you clicked on the ball;-

Failed to connect stream: invalid argument.

Happened after an update.  Ubuntu see's my onboard audio card.  Audio just will not play.  If someone has a suggestion on how to fix it I'd appreciate a hand.  BTW audio on Fluxbox and Windughs is just fine.  It is a definate Ubuntu software issue.

Mark Shuman

---

### Post by louieb on 2008-08-27
Choose recovery mode from GRUB. That will give to a terminal and you will be user root.
Another option is to choose to do a normal boot and when you get to the login screen press Ctrl+Alt+F1 to get to a full screen terminal that you can log on to.
Good Luck.

---

### Post by mocoloco on 2008-08-27
You do know you can get to a terminal with Ctrl+Alt+F2, right?  If that's not working the problem's not with Gnome, it's your whole system.

---

