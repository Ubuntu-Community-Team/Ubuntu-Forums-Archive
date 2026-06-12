---
title: "automatic login not working"
date: 2011-07-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sartic on 2011-07-31
I set it on setup and can not find option on menu?!

---

### Post by Harry33 on 2011-07-31
> **sartic said:**
> I set it on setup and can not find option on menu?!

If you have lightDM, did you try this.

Open (gksu gedit) the file /etc/lightdm/lightdm.conf
Change the values (in # Seat configuration)
from:
#default-user=bob
#default-user-timeout=5
#pam-service=lightdm
to:
default-user=username
default-user-timeout=0
pam-service=lightdm-autologin

* Note: username is your username

---

### Post by Brad55 on 2011-07-31
To turn off the login screen go to system>Administration>login screen and change it so you auto login.

---

### Post by sartic on 2011-07-31
Gnome2 had GUI for that. I can not find even admin part only system under applications.

---

### Post by cariboo on 2011-07-31
Many things are quite broken at the moment, if you want autologin, you'll have to edit the lightdm configuration file as Harry33 suggested, or wait until later on in the cycle to run Oneiric.

---

### Post by Bowmore on 2011-07-31
Check this if you use LightDM:

[http://ubuntuforums.org/showpost.php?p=11095806&postcount=28](http://ubuntuforums.org/showpost.php?p=11095806&postcount=28)

Not sure you also need to add
> pam-service=lightdm-autologinor if lightdm handles this automatically now. I haven't added this line and haven't seen no drawback but others say they have.

---

### Post by lucazade on 2011-07-31
I'm still waiting to enable autologin because "autologin-session" feature is not implemented yet.
(I'd use ubuntu-2d at the moment instead of standard ubuntu session)

---

### Post by MacUntu on 2011-07-31
> **cariboo907 said:**
> Many things are quite broken at the moment
Yeah, going to be a tough week for dev guys (Alpha 2 ahead).

I thought I fixed the Compiz crasher with latest Nux/Unity frum trunk, but it still seems a bit unstable (losing decoration all the time, etc.). Lightdm crashes from time to time, GDM crashes, GTK themes go to Win 95 style every time I look at the desktop for more than a second straight, Gedit fails to load on one system. What a pain. :D

So far it's the most bumpy ride on both of my systems since I started using Ubuntu(+1).

---

### Post by sartic on 2011-08-06
there is no progress... and restart is also missing :))

---

### Post by wind_clouds on 2011-08-06
Hi can you change the following settings on /etc/gdm/custom.conf file. 
 
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=(your username)
AutomaticLogin=(your username)
TimedLoginDelay=0
DefaultSession=gnome
 
Finally reboot it, This will automatically login your username.

---

### Post by sartic on 2011-08-06
there is no gdm folder

---

### Post by sartic on 2011-08-06
> **Harry33 said:**
> If you have lightDM, did you try this.

Open (gksu gedit) the file /etc/lightdm/lightdm.conf
Change the values (in # Seat configuration)
from:
#default-user=bob
#default-user-timeout=5
#pam-service=lightdm
to:
default-user=username
default-user-timeout=0
pam-service=lightdm-autologin

* Note: username is your username

I did this and I lost my alpha.. no boot :))

---

### Post by cariboo on 2011-08-06
I'd suggest you start in recovery mode, and undo the changes you made, as any mistakes in /etc/lightdm/lightdm.conf will make the system unbootable.

---

### Post by sartic on 2011-08-06
Nope. I will try Kubuntu alpha now ;)

---

### Post by wind_clouds on 2011-08-06
May i know which ubuntu version you are using?
which desktop you are using Gnome or KDE?

---

### Post by sartic on 2011-08-06
I had problem width Ubuntu. Now I am testing Kubuntu.
I prefer gnome 2 if this was question ;)

---

### Post by cariboo on 2011-08-07
It would help if you had stuck with Unity/Gnome-shell, so that we could help you trouble shoot the problem. Changing to a different version doesn't solve the problem.

---

### Post by sartic on 2011-08-07
I want to try also Lubuntu during alpha. I will be back in beta cycle width Unity on my notebook. My desktop is LTS :) Notebook for me is only for playing and it is pretty hot (it is summer; none of distros works good width my Toshiba, cooler is not working as it should).

ps: Now I am playing width Kubuntu and Chakra.

---

### Post by wind_clouds on 2011-08-08
Can you install gdm then try that /etc/gdm/custom.conf, because its work me in ununtu 11.04

---

### Post by sartic on 2011-08-08
Nope partition is gone, but I will remember you when I test Unity (beta) again :)

---

### Post by Harry33 on 2011-08-13
Fir those that do not like a visible display manager, there is always another possibility.
For automatic login only, there is NoDM (in Oneiric repos).

> This package prepares the system to automatically start an X session at
system boot. It is meant for devices like smartphones, but can be used on
a regular computer as well, if the security implications are acceptable.

---

