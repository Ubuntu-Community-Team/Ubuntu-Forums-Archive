---
title: "Switching Desktops with full screen TS Client"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by tlg on 2008-10-31
I would like to be able to use Ubuntu 8.04 Terminal Services Client in Full Screen mode in order to remotely access my office.

However when the TS Client is set to operate at full screen, there doesn't seem to be any way to get back to the Gnome desktop without disconnecting the session i.e there are no resize controls on the full screen window.

Is there a key sequence to enable getting back to the Gnome desktop, or alternatively to switch to the second Gnome Desktop?

Thanks in advance for any help on this.

---

### Post by outis on 2008-11-13
Hey this was getting me too.

Heres the fix:
	If you are stuck in it now, you can hit ctrl-alt-enter-right arrow or ctrl-alt-enter-left arrow.
	The ctrl-alt-enter should switch you back, but it auto switches back to full screen. The left/right arrow will eventually switch to the other ubuntu desktop screen, you just have to keep trying it.

	You can do the following as posted by handspringer at [http://ubuntuforums.org/archive/index.php/t-595384.html](http://ubuntuforums.org/archive/index.php/t-595384.html)
 		1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.
		2. Start this tool under SYSTEM -> PREFERENCES
		3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.


I'm not sure if there's a way to do it without the CompizConfig Settings Manager.  Well I am sure you can, I just dont know how.
To install ccsm run sudo apt-get install compizconfig-settings-manager
You have to have repositories for ccsm enabled: system>administration>software sources 
I found that at [http://www.uluga.ubuntuforums.org/showthread.php?t=595585](http://www.uluga.ubuntuforums.org/showthread.php?t=595585)

Hope that helps you, and anyone else that goes looking down the line.
It sure helped me out a lot.

-outis

---

### Post by tlg on 2008-11-15
Thanks for the info.
I now have ccsm installed and disabled Legacy Fullscreen Support, however the Ctrl-Alt_Enter sequence still only flashes the screen.

Occasionally it will bring up a plain white screen and when this happens, Ctrl-Alt-RightArrow brings up the viewport switcher box on the screen, but it won't actually switch.

When the RDP screen is full screen, Ctrl-Alt-Right/Left_Arrow keys have no effect.

Am I missing something?
Is there any other setting I need to set up?

BTW This is on Ubuntu 8.04 on a Dell Inspiron 640m laptop.

---

