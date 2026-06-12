---
title: "I want to try KDE without having to..."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by fikelfikel on 2008-10-26
1. Re-install ubuntu
2. Set everything up again
3. Lose all my Gnome apps

I use GNOME, but just want to give the latest KDE a try. I'm running Hardy Heron, and want all my GNOME apps to be the same. I'm just giving KDE a try, I'll be going back to GNOME then. Is there a way to install KDE without harming GNOME?

---

### Post by zvacet on 2008-10-26
It should be possible to have both desktops installed.In that case you will choose between one of them from **login screen>options**.If you see any problems with KDE or you simply don´t like it remove it like it is described [here.]("http://psychocats.s465.sureserver.com/ubuntu/puregnome")

---

### Post by ww711 on 2008-10-26
Try downloading and burning a live cd of kubuntu  and boot from that, or use the downloaded image and mount the live cd to virtual box.

---

### Post by lswest on 2008-10-26
just running ```
sudo apt-get install kubuntu-desktop
``` will install the Kubuntu apps and desktop environment.  It will, however, change the splash and will (I think) change the login manager to kdm, instead of gdm, but will allow you to boot to gnome after choosing it in the session menu at the login screen.

---

### Post by fooman on 2008-10-26
> **lswest said:**
> just running ```
sudo apt-get install kubuntu-desktop
``` will install the Kubuntu apps and desktop environment.  It will, however, change the splash and will (I think) change the login manager to kdm, instead of gdm, but will allow you to boot to gnome after choosing it in the session menu at the login screen.

it should *not* change to kdm (including the splash screen) unless you tell it to.

near the end of installing kubuntu-desktop...it will give you the choice of switching from gdm to kdm as your default desktop.  just say no if you want to stick with gdm.

---

### Post by ianhaycox on 2008-10-26
When I tried this in Edgy it messed up my menus by adding all the KDE apps, which was confusing. Things may have changed now.

However, this [http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/) may help to hide the GNOME/KDE options depending on the desktop environment.

---

### Post by fikelfikel on 2008-10-26
> **lswest said:**
> just running ```
sudo apt-get install kubuntu-desktop
``` will install the Kubuntu apps and desktop environment.  It will, however, change the splash and will (I think) change the login manager to kdm, instead of gdm, but will allow you to boot to gnome after choosing it in the session menu at the login screen.

Will all my apps stay? Are u sure this will work?

---

### Post by Elfy on 2008-10-26
All of yopur apps will stay and you will have a mishmash of gnome/kde apps in your menus - they will become loooonger ;)

If you think that you'll get rid then I would think about installing kde as a vm in virtual box or vmware as has been suggested

I used to have kubuntu and xubuntu in vm's 

Depends on memory availability really

---

### Post by sleepingdragon on 2008-10-26
> **fikelfikel said:**
> 1. Re-install ubuntu
2. Set everything up again
3. Lose all my Gnome apps

I use GNOME, but just want to give the latest KDE a try. I'm running Hardy Heron, and want all my GNOME apps to be the same. I'm just giving KDE a try, I'll be going back to GNOME then. Is there a way to install KDE without harming GNOME?

1. You don't have to, KDE and Gnome run happily side-by-side. Just choose your session type from the Options menu when you login.

2. KDE does come with sane defaults, so you install and play immediately. Of course, you will have to change some settings to make things "just right" for you, but it's all in the usual Settings menu.

3. Gnome apps work merrily in KDE. I've yet to find one that doesn't.

Since you're on Hardy, you shouldn't find any problems at all running Gnome apps in KDE. I do it all the time.

---

### Post by fikelfikel on 2008-10-26
> **lswest said:**
> just running ```
sudo apt-get install kubuntu-desktop
``` will install the Kubuntu apps and desktop environment.  It will, however, change the splash and will (I think) change the login manager to kdm, instead of gdm, but will allow you to boot to gnome after choosing it in the session menu at the login screen.

it's changing now and downloading. thanks. hope it works for me:KS

wat's the xubunu desktop like?

---

### Post by fikelfikel on 2008-10-26
[CENTER][SIZE=7]BIG PROBLEM!
[/SIZE][LEFT]I use Gnome PPP to connect, so when I install the KDE Desktop, will I not be able to connect?
[/LEFT]
[/CENTER]

---

### Post by fooman on 2008-10-26
> **fikelfikel said:**
> 
wat's the xubunu desktop like?

have a look:

[http://xubuntu.org/tour](http://xubuntu.org/tour)

as for your "big problem"...kubuntu-desktop should not affect anything in gnome execpt for the menus.  when you get to the login screen,  you can choose to boot into gnome or kde.  if you cannot connect in kde,  just logout (ctrl-alt-backspace) to the login screen again and choose gnome.  it should remain the same.

---

### Post by fikelfikel on 2008-10-26
> **fooman said:**
> have a look:

[http://xubuntu.org/tour](http://xubuntu.org/tour)

as for your "big problem"...kubuntu-desktop should not affect anything in gnome execpt for the menus.  when you get to the login screen,  you can choose to boot into gnome or kde.  if you cannot connect in kde,  just logout (ctrl-alt-backspace) to the login screen again and choose gnome.  it should remain the same.

If I launch this command in termanal:
sudo apt-get install kdeWill it work without affecting or changing Ubunu to Kubuntu?

---

### Post by sleepingdragon on 2008-10-26
> **fikelfikel said:**
> [CENTER][SIZE=7]BIG PROBLEM!
[/SIZE][LEFT]I use Gnome PPP to connect, so when I install the KDE Desktop, will I not be able to connect?
[/LEFT]
[/CENTER]

KDE uses KPPP, which in my humble opinion is certainly better than Gnome PPP and will provide all the same functions therein. Even if you prefer to stick with the Gnome app, it should still work.

---

### Post by prismpirate on 2008-10-26
Just like you can use Amarok in Ubuntu, you can use Gnome PPP in KDE, I think. As for keeping your apps, no apps will be removed. Instead, more apps will be removed, which makes menus messy and unorganized, unacceptable for a neat freak like me. To switch between Ubuntu and Kubuntu, just log out, select your session, (Bottom left) and your set.

---

### Post by Flyingjester on 2008-10-26
> **fikelfikel said:**
> it's changing now and downloading. thanks. hope it works for me:KS

wat's the xubunu desktop like?

like gnome but lighter, it the sudo apt-get install kubuntu-desktop should work, as did sudo apt-get install xubuntu-desktop did for me, i used both and have gnome, kde, and xfce on my compy.

---

### Post by XPuntu on 2008-10-26
It sounds like you just want to see how it looks without messing up your current setup. Why not install Virtualbox and then "try" out Kubuntu there?

---

### Post by Elfy on 2008-10-26
If you decide that you no longer wish to have kubuntu then you cannot just uninstall kubuntu-desktop, to do that you should have installed with aptitude instead - the commands to return to a pure gnome, or if you wish to go to kde for a pure kde can be found on the psychocat site - on the left pane - 'Playing Around'

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

