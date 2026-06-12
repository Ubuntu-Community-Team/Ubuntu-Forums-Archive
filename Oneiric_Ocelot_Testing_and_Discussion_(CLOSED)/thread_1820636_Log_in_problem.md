---
title: "Log in problem"
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by LatinaLover93 on 2011-08-07
after using the update-manage -d command in ubuntu 11.04, i upgraded to 11.10. There was a error during the installation, but i dont know what that error was. All i know about it is that something failed to update/install. but it finished even with the error and now when i choose a user account to log in to, the log in box dissapears, it doesnt even get to ask for my password, it just dissapears. any help?

---

### Post by x-shaney-x on 2011-08-07
You could try:

```
sudo dpkg --configure -a
```To try to finish the installation or ```
sudo apt-get -f install
```

I'm a bit out of tune with upgrade problems but the above commands often came in useful in my debian Sid days :)

---

### Post by mc4man on 2011-08-07
> **LatinaLover93 said:**
> after using the update-manage -d command in ubuntu 11.04, i upgraded to 11.10. There was a error during the installation, but i dont know what that error was. All i know about it is that something failed to update/install. but it finished even with the error and now when i choose a user account to log in to, the log in box dissapears, it doesnt even get to ask for my password, it just dissapears. any help?

When I did an upgrade several weeks ago there was an error with doc-base, I gather I fixed ok though while doing was presented with several options i knew nothing about ( though think I've read that has been fixed

What you describe sounds like what was happening for awhile on iso installs - if so, at login screen - 
choose 'other', type in your username and proceed. It it is this then future logins should be normal

---

### Post by LatinaLover93 on 2011-08-07
i cant log in to run any commands, and even if i choose other, the box still dissapears. Im still fairly new to ubuntu. So is there like a safe mode i could go into to trouble shoot?

---

### Post by Catharsis on 2011-08-08
See if you can log in on a different virtual terminal -- it might just be the graphics that are messing with it.

Hit Ctrl+Alt+F2 and it should give you a command prompt asking you to login. See if you can enter your username and password and login.

---

### Post by LatinaLover93 on 2011-08-08
> **Catharsis said:**
> See if you can log in on a different virtual terminal -- it might just be the graphics that are messing with it.

Hit Ctrl+Alt+F2 and it should give you a command prompt asking you to login. See if you can enter your username and password and login.
i was able to log in like that, so i gues it is a graphical problem. When i ran apt-get update, it showed that i had obsolete packages that i should remove. so i ran autoremove thinking it just might be a conflicting package problem. But that didnt work. Then i saw that it wanted to instal and upgrade some packages. But i cant do that, since i dont know how to connect to a wifi network through terminal. Anybody know the commands?

---

### Post by Catharsis on 2011-08-08
Type ```
startx
```into the terminal and your desktop should start.

---

### Post by LatinaLover93 on 2011-08-08
> **Catharsis said:**
> Type ```
startx
```into the terminal and your desktop should start.
i've done that and got the following

Xauth: file /home/anthony/.Xauthority does not exist

Fatal server error:
server already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

ddxsig giveup- closing log
invalid MIT-Magic-cookie-1 key xinit: giving up
xinit- unable to connect to x server: connection refused
xinit: server error

---

### Post by Catharsis on 2011-08-08
> **LatinaLover93 said:**
> i've done that and got the following

Xauth: file /home/anthony/.Xauthority does not exist

Fatal server error:
server already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

ddxsig giveup- closing log
invalid MIT-Magic-cookie-1 key xinit: giving up
xinit- unable to connect to x server: connection refused
xinit: server error

Ah right, sorry. Forgot that it's already running on VT 7. You have to enter```
sudo service lightdm stop
```first. At least I think that's the command since Ubuntu switched to LightDM.

---

### Post by LatinaLover93 on 2011-08-08
> **Catharsis said:**
> Ah right, sorry. Forgot that it's already running on VT 7. You have to enter```
sudo service lightdm stop
```first. At least I think that's the command since Ubuntu switched to LightDM.i've done that, and i got the following
stop:unknown instance
is it relevant that the gdm logon screen is being used, and not the lightdm. i didnt switch to gdm manually it was just used by default

---

### Post by Catharsis on 2011-08-08
> **LatinaLover93 said:**
> i've done that, and i got the following
stop:unknown instance
is it relevant that the gdm logon screen is being used, and not the lightdm. i didnt switch to gdm manually it was just used by default

Oh. Then yes, the command would be```
sudo service gdm stop
```

---

### Post by LatinaLover93 on 2011-08-09
I've done all that, it started the desktop, and then the desktop dissapeard, here is a vid i took of me doing what you said, and it disappearing again. and this vid was taken with my ipod touch so the video quality aint the best
[http://www.youtube.com/watch?v=qu85mXdwlVA](http://www.youtube.com/watch?v=qu85mXdwlVA)

---

### Post by dino99 on 2011-08-09
you should use lightdm now

sudo apt-get install lightdm lightdm-gtk-greeter
sudo apt-get purge gdm

---

### Post by Catharsis on 2011-08-09
You should also just do a fresh install. It's clear that this is a problem with X, which is terrible to troubleshoot, especially if you don't have any experience and don't know where to start looking. Every step forward reveals more problems, so I would just cut my losses if I were you.

---

### Post by LatinaLover93 on 2011-08-09
> **dino99 said:**
> you should use lightdm now

sudo apt-get install lightdm lightdm-gtk-greeter
sudo apt-get purge gdm
i cant do that because i cant connect to any of my wifi networks, unless theres a way to connect to them through terminal

---

### Post by LatinaLover93 on 2011-08-09
> **Catharsis said:**
> You should also just do a fresh install. It's clear that this is a problem with X, which is terrible to troubleshoot, especially if you don't have any experience and don't know where to start looking. Every step forward reveals more problems, so I would just cut my losses if I were you.
i was afraid of a fresh install. o well i'll give the forums another day and if it aint solved by tomorrow i'll fresh install. and does python have anything to do with x? because the error i had when upgrading to 11.10 had something to do with python.

---

### Post by cariboo on 2011-08-09
> **LatinaLover93 said:**
> i cant do that because i cant connect to any of my wifi networks, unless theres a way to connect to them through terminal

There are instructions to manually connect to a wifi network [here]("http://ubuntuforums.org/showthread.php?t=571188")

If you are running a testing version, it might be an idea to buy a network cable to connect to your router, as at times you need a working network connection to do updates, and in some cases download and install the driver for your wireless device.

---

### Post by LatinaLover93 on 2011-08-09
is there a repair option for ubuntu if i burn 11.10 to a cd?

---

### Post by dino99 on 2011-08-10
> **LatinaLover93 said:**
> is there a repair option for ubuntu if i burn 11.10 to a cd?


always burn at the slowest speed

---

### Post by LatinaLover93 on 2011-08-10
> **dino99 said:**
> always burn at the slowest speed
i already know that...i learned the hard way though =/ thanks for reminding though

---

### Post by Catharsis on 2011-08-10
> **dino99 said:**
> always burn at the slowest speed

I think he means using the LiveCD to repair a broken installation, like the Windows install disks. And no, there's nothing like that in Ubuntu, you just do a fresh install.

---

### Post by LatinaLover93 on 2011-08-10
> **Catharsis said:**
> I think he means using the LiveCD to repair a broken installation, like the Windows install disks. And no, there's nothing like that in Ubuntu, you just do a fresh install.That is what i meant n damn =/ o well time to fresh install i guess

---

