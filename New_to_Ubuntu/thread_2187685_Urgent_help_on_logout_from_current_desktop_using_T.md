---
title: "Urgent help on logout from current desktop using TTY into login secreen"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by fatharraxman on 2013-11-13
I am using Ubuntu 13.10, I installed different desktops, lubuntu, gnome, lxde, and while I was browsing through them I logged into a desktop I barely know which is, where there is no bars, panels, widows, nothing but a blank screen, I can not open terminal even using Alt + Ctrl + T or get into Alt + F3 to use TTY, I restarted using the laptop external poweroff, and logged in into the same screen immediately, restarted again and used TTY from grub and made sudo service lighdm restart and and differnt logout terminal commands from [http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal](http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal)  but nothing at all
any help please....step by a step for a newobie

---

### Post by fatharraxman on 2013-11-13
I am in the recovery mode root waiting for an answer

---

### Post by steeldriver on 2013-11-13
The key combination to switch to a virtual terminal (TTY) is **Ctrl**-Alt-F*n*

If you have auto logged in to an Openbox based session, you should be able to bring up an application menu by right clicking anywhere on the background

If you want to disable auto login so that you can select a different desktop session from the GUI greeter screen, it will depend whether you are running lightdm or some other display manager - for lightdm, you will need to edit the lightdm.conf file e.g.

```
sudo nano /etc/lightdm/lightdm.conf
```

and remove the auto-login user from the [SeatDefaults] section. If you're doing that from the recovery console you will need to remount the filesystem with read-write permissions first.

---

### Post by fatharraxman on 2013-11-13
Well, First, I appreciate your quick response, Second, in answering your questions, (as a newbie) I dont understand much of what you are saying (lol), no offense, but I will answer as much as I can; > **Ctrl**-Alt-F*n*
 oh, how did I forgot that, thank you, > If you have auto logged in to an Openbox based session, you should be  able to bring up an application menu by right clicking anywhere on the  background
 yes I believe there is a back ground but no any right or left click or any button would work, > If you want to disable auto login so that you can select a different desktop session from the GUI greeter screen this is exactly what I am looking for, but do not know how, > sudo nano /etc/lightdm/lightdm.conf and remove the auto-login user from the [SeatDefaults] section. If  you're doing that from the recovery console you will need to remount  the filesystem with read-write permissions first. am in there now but do not know how to set it .

---

### Post by steeldriver on 2013-11-13
```

mount -o remount,rw /

nano /etc/lightdm/lightdm.conf

```

You can comment out the auto-login line, or delete it by arrowing down to the line and hitting Ctrl-k - then save (Ctrl-o) and exit (Ctrl-x). When you're done type 'exit' to get out of the root recovery shell.

---

### Post by fatharraxman on 2013-11-13
Oh my God , You are fabulous WOW, so but I have one more question sir, how could I let the login screen ask for my password? 
Thank You Very much 
You really  genius   				 				 					 						 	[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500")

---

