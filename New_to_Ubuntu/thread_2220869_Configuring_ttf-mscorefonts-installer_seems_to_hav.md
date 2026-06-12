---
title: "Configuring ttf-mscorefonts-installer seems to have Stopped. Stalled. HELP"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by nwpll on 2014-04-29
Hi

I hve just done a  clean install of 14.04.

I then went to [http://www.enqlu.com/2014/03/things-to-do-after-installing-ubuntu.html](http://www.enqlu.com/2014/03/things-to-do-after-installing-ubuntu.html) and started to do some of the things it says to do after an install.

first thing i did was to ***sudo apt-get install ubuntu-restricted-extras ***and after a while it came to Configuring ttf-mscorefonts-installer and it now looks to have stopped. Last time i cancelled at this point when  tried to start again it said something like Close  sudo apt-get 

The OK at the bottom of the screen does not let me do anthing.

Can someone help me close this screen so i can carry on installing Vlc, Gimp, Rar etc.

To start again the only thing i can do is another clean install

Thanks

---

### Post by JeQhdMD on 2014-04-29
Don't reinstall for something so minor.   Just restart your PC and then go to the Ubuntu Software Center and install synaptic.   Use synaptic then to install the restricted extras - it seems more stable.  Note that with some of these restricted proprietary apps, a popup window with a Eula can open behind the active window.  So, minimize synaptic or the terminal window & check for that popup.

You can also install the ms corefonts independently of other apps via synaptic or ubuntu software center.   I usually wind up uninstalling the fonts as I've never needed them.

---

### Post by steeldriver on 2014-04-29
You know you need to use the TAB key to navigate the text mode ttf-mscorefonts-installer screen, right? Then SPACE or ENTER to "press" the OK button.

---

### Post by oldos2er on 2014-04-29
> **nwpll said:**
> The OK at the bottom of the screen does not let me do anthing.


Hit the Tab key to highlight 'Ok', then Enter to accept the EULA. If you've already closed the terminal, open a fresh one and run ```
sudo dpkg --configure -a
```

---

### Post by nwpll on 2014-04-29
Hi 

I did another clean install straight after i posted this Post. Now i am not trying to install anything i find the mouse and keyboard are not working. I should have stayed with 13.10.

This is the first time since Dapper a few years ago i have had any problem with an update.

Oh well time to look through the forum for the answers to my mouse and keyboard issues,

Thanks

Peter

---

