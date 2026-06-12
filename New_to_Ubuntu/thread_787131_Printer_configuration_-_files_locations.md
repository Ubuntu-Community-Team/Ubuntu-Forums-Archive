---
title: "Printer configuration - files locations?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by candtalan on 2008-05-08
I am trying to assist a friend who is a newcomer to (k)ubuntu and he has a strange problem with printing. My guess is that if a relevant printer configuration file could be deleted, he could reconfigure automatically ok, as he did initially, which worked.

Where is/are printer configuration file/s please?

(the original thread is
[http://ubuntuforums.org/showthread.php?t=785619](http://ubuntuforums.org/showthread.php?t=785619)
thanks)

---

### Post by candtalan on 2008-05-16
> **candtalan said:**
> I am trying to assist a friend who is a newcomer to (k)ubuntu and he has a strange problem with printing. My guess is that if a relevant printer configuration file could be deleted, he could reconfigure automatically ok, as he did initially, which worked.

Where is/are printer configuration file/s please?

(the original thread is
[http://ubuntuforums.org/showthread.php?t=785619](http://ubuntuforums.org/showthread.php?t=785619)
thanks)
Bump

---

### Post by Golem XIV on 2008-05-16
It would be good to know a bit more, like what printer we're talking about, how is it connected to the system, what is the specific problem, if there are any error messages, etc.

You can always try
```
sudo /etc/init.d/cupsys restart
```
in a terminal window to restart the printing system and see if it will help.

---

### Post by candtalan on 2008-05-16
> **Golem XIV said:**
> It would be good to know a bit more, like what printer we're talking about, how is it connected to the system, what is the specific problem, if there are any error messages, etc.

You can always try
```
sudo /etc/init.d/cupsys restart
```
in a terminal window to restart the printing system and see if it will help.

The printer is 
Epson Stylus Photo 1200 and it works perfectly from a live Cd in the system and it also worked perfectly after initial k/ubuntu install too!
Re boot does not help (is that the same effect as as sudo /etc/init.d/cupsys restart  ?)

Things went wrong after my newbie friend rebooted into xp and then later returned to k/ubuntu. No printer function (two printers in fact, but concentrating on one here to begin with)

So I am rather hoping to help the friend force a printer configuration clear out and reconfigure. That is why I am asking for any information re location of config files.
Thanks

---

### Post by Golem XIV on 2008-05-16
It could be that XP "left" something in the printer.  I would do this:
- Boot into XP, open the Printers folder and check the status of the printer.  It may be trying to get your attention for maintenance, cartridge change or similar.
- If there is maintenance pending, do it
- Shut down the computer. Unplug the printer from the computer and from the mains (even turned off many devices are still under power and keep settings).  Wait for one minute.
- Plug the printer back into the computer and then into the mains.  Turn on printer and computer.
- Log into Ubuntu and see if the problem persists.

---

### Post by Golem XIV on 2008-05-16
I forgot:  Linux printer drivers have a PPD extension.  Your printer config files should be in /etc/cups/ppd.  I think you will need root access to modify this directory.

To start Nautilus (the file browser) with root privileges, you can do two things:
Type **gksudo nautilus** in the terminal, or install the Nautilus gksudo plugin, either looking for **nautilus-gksu** in Synaptic or by typing in the terminal
```
sudo apt-get install nautilus-gksu
```
You may need to restart Nautilus for the changes to take effect:
```
killall nautilus
```
This will close and re-open all Nautilus windows.  Once this is done, you will have an "Open as administrator" option on the menu that you get when you right-click on something in Nautilus.  This second option is better in my opinion.

Don't forget that **playing around with Nautilus in admin mode is dangerous to your system**.  Do only what you have to do and then close the Nautilus admin window.

Also don't forget to first **make a backup** of the files you will be changing.

---

