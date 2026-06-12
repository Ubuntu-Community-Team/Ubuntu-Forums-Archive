---
title: "[SOLVED] Instand messaging/pidgin/windows-live account"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by AKsuited09 on 2008-08-01
I have an account on windows live messenger. I would like to run an IM-program, and i have tried the  pidgin thing but i can not get it running. Is it the source, the windows, the fedora core or thecenstos/rhel download i should choose?

Any other tips on IM-programs? Design is not a big deal to me, but i would like to have personal pictures and a webcam-function, and file-sharing.

---

### Post by drs305 on 2008-08-01
```
sudo aptitude install pidgin
```

It installs to ~/.purple

It's accessed from the 'Internet' menu.

I know AIM and yahoo are supported by pidgin. msn is also listed.

---

### Post by dca on 2008-08-01
Pidgin should be there after default Ubuntu GNOME install under the Internet menu under Applications...

---

### Post by stevoo on 2008-08-01
you dont even need to get it from the website.

Open up a terminal window
And type 
```
sudo apt-get install pidgin
```
Put your password and this will install it.

You can find it then by going to Application->internet->pidgin

---

### Post by kestrel1 on 2008-08-01
Try AMSN:
[http://www.amsn-project.net/](http://www.amsn-project.net/)
```
sudo apt-get install amsn
```
should do what you want.

---

### Post by AKsuited09 on 2008-08-01
i'll try this. I can't believe how helpful people around here are ! Thanks alot

---

### Post by dca on 2008-08-01
If Pidgin doesn't work for you, you can (if you're running Ubuntu gnome vers) access 'Add/Remove Software' from bottom of 'Applications' menu on main menu bar...
 
Select 'All Available Apps' from drop-down and type in messenger as your search string and it will give you a plethora of IMs to choose from...
 
("Heffe, do you know what a plethora is???")  sorry, three amigos humor.

---

### Post by AKsuited09 on 2008-08-01
It's working. Im totally impressed by ubuntu! Have got almost everything up and running. 

Still, i can't find anything to use webcams in pidgin.

---

### Post by AKsuited09 on 2008-08-01
One more thing too, if anybody here can explain to me how i get the box-3d-thing to work. I have set the graphic effects at high.

---

### Post by AKsuited09 on 2008-08-01
anybody?

---

### Post by LowSky on 2008-08-01
You need to install compiz manager

```
sudo apt-get install ccsm
```

it will then be under System>Preferences> Advanced desktop settings


> **dca said:**
> 
 
("Heffe, do you know what a plethora is???")  sorry, three amigos humor.

I watched that movie this weekend!!!

[quote=Three Amigos]

[COLOR="Red"]Jefe: I have put many beautiful pinatas in the storeroom, each of them filled with little suprises.[/COLOR] 
[COLOR="Blue"]El Guapo: Many pinatas? [/COLOR]
[COLOR="Red"]Jefe: Oh yes, many! [/COLOR]
[COLOR="Blue"]El Guapo: Would you say I have a plethora of pinatas? [/COLOR]
[COLOR="Red"]Jefe: A what? [/COLOR]
[COLOR="Blue"]El Guapo: A *plethora*. [/COLOR]
[COLOR="Red"]Jefe: Oh yes, you have a plethora. [/COLOR]
[COLOR="Blue"]El Guapo: Jefe, what is a plethora? [/COLOR]
[COLOR="Red"]Jefe: Why, El Guapo? [/COLOR]
[COLOR="Blue"]El Guapo: Well, you told me I have a plethora. And I just would like to know if you know what a plethora is. I would not like to think that a person would tell someone he has a plethora, and then find out that that person has *no idea* what it means to have a plethora. [/COLOR]
[COLOR="Red"]Jefe: Forgive me, El Guapo. I know that I, Jefe, do not have your superior intellect and education. But could it be that once again, you are angry at something else, and are looking to take it out on me?[/COLOR] [/quote]

---

### Post by drs305 on 2008-08-01
> **AKsuited09 said:**
> One more thing too, if anybody here can explain to me how i get the box-3d-thing to work. I have set the graphic effects at high.

AKsuited09 - it's best to mark this thread solved with the Thread Tools link at the top right of the first post and then start a new thread with this issue. ;-)

---

### Post by kestrel1 on 2008-08-01
To use a webcam AMSN should do it.

---

### Post by AKsuited09 on 2008-08-01
ok, thanks, will do :)

---

