---
title: "[SOLVED] How to install login screen theme"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by abhilash1989 on 2008-09-13
Ive downloaded a login screen theme named                                '48213-Relaxing-_Water-0.1.tar.bz2'
Now how to install it???

---

### Post by k33bz on 2008-09-13
SYSTEM> ADMINISTRATION> LOGIN WINDOW
it will prompt you for your PW, 
enter it in
go to LOCAL tab
click on add, and click on the file

---

### Post by wolfen69 on 2008-09-13
i've never done it because i do autologin, but i would go system>administration>login window>local and click the +add button. then just navigate to the file. if that doesn't work, unzip it first, then try again. maybe someone else will know for sure.

---

### Post by k33bz on 2008-09-13
> **wolfen69 said:**
> i've never done it because i do autologin, but i would go system>administration>login window>local and click the +add button. then just navigate to the file. if that doesn't work, unzip it first, then try again. maybe someone else will know for sure.

NOOOOOOOOOOOOOOOOOOOOOO

dont unzip it, it will not work if you unzip it.

---

### Post by SilverAdder on 2008-09-15
Im in the same situtaion... I downloaded a .tar.bz2 file with a theme but when i go to select the package it isnt recognized. If the file is .tar.gz it is however... Could i just repack it? And how?

EDIT: Oh god sorry, never mind, i found it.

---

### Post by waspbr on 2008-09-15
[LIST]
[*]just go to system>Administration> Login windows

[*]enter your admin password

[*]go to the local tab

[*]drag and drop the tar.bz2 file into the list of other themes

[*]a dialogue will pop up, press install 

[*]you should be able to see a new theme listed.
[/LIST]

---

### Post by SilverAdder on 2008-09-15
> **waspbr said:**
> [LIST]
[*]just go to system>Administration> Login windows

[*]enter your admin password

[*]go to the local tab

[*]drag and drop the tar.bz2 file into the list of other themes

[*]a dialogue will pop up, press install 

[*]you should be able to see a new theme listed.
[/LIST]

Oh thanks, i didn't know i could do it like that.

---

### Post by waspbr on 2008-09-17
You can do the same thing (drag and drop) when installing icon/metacity/gtk2/pointer themes in the Appearance preferences* menu on the themes tab.

just download the compressed file and drag and drop it into the list.





*right click on desktop and choose "Change desktop background" or on the menu panel, Preferences>Appearance

---

### Post by Ganjafreak on 2009-11-28
K, I don't have that login window thing I have something called Login screen im on 9.04 jaunty can someone tell me how to do it now?

I mean i click screen one and click unlock asks for a pw entered and then nothing else happens.

---

### Post by adalal on 2009-11-28
Go on gnome-look.org, and they actually have instructions on installing login screens...

---

### Post by Ganjafreak on 2009-11-29
[FONT=Comic Sans MS]I am running ubuntu 9.04 jaunty, It don't have that it says login screen and when I click it it says do you want to automatically login and wait 30 secs to let others login or enter your information yourself but to be able to change any other those fields you have to click "unlock" and enter your password[/FONT]

---

### Post by 3rdalbum on 2009-11-29
> **Ganjafreak said:**
> [FONT=Comic Sans MS]I am running ubuntu 9.04 jaunty, It don't have that it says login screen and when I click it it says do you want to automatically login and wait 30 secs to let others login or enter your information yourself but to be able to change any other those fields you have to click "unlock" and enter your password[/FONT]

You're not running Ubuntu 9.04 then, you're running 9.10.

The GDM login screen in 9.10 is completely different to the earlier login screen, and it doesn't accept the same themes.

You can theme it by issuing the command in a terminal:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

This brings up the normal Gnome Appearance window, but any changes you make here will only affect the login screen. You may be able to unzip the older login screen theme and use the background from the previous login screen, as the "wallpaper" for the new screen.

---

### Post by skarychinezeguie on 2010-02-18
i'm sorry but i been playin with this for a couple hours now. no matter what i try i can't get any other settings than what's in the screenie. All i wanna do is change the background image on the login screen, or possibly install a theme from gnome-look.org but i can't find any directions that will get me past what i've already seen. And i can't find anything on gnome-look about installing login themes. Please help.

---

### Post by ayip_eiger on 2010-03-20
yes, i meet same problems, any idea to install login screen in ubuntu 9.10?? Nothing option on Appearance Windows..:p:p

---

### Post by anoopkmohan4u on 2010-05-11
iam not able to change my login screen. i only can find the change my desktop theme.
iam using ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011.
please help me to find a resolution for this issue.
i get the same issue in the picture posted by a friend above.

---

### Post by caspah on 2010-06-27
> **k33bz said:**
> SYSTEM> ADMINISTRATION> LOGIN WINDOW
it will prompt you for your PW, 
enter it in
go to LOCAL tab
click on add, and click on the file
  genius, i must have spent 6 hours trying to use the splash program for this

---

### Post by komputerkurt on 2010-07-10
NOT SOLVED!!!!
Also I need help with this too. :/

---

### Post by urbanjugle on 2010-07-17
how to change login screen in 10.4??? There are NO tabs after you log into Login Screen Settings.

---

### Post by ronsahagun on 2010-08-14
> **urbanjugle said:**
> how to change login screen in 10.4??? There are NO tabs after you log into Login Screen Settings.
Same thing here. There are no tabs to change the login window theme in Ubuntu 10.04. I'm using the Netbook Edition, if that info's needed.

---

### Post by Vaphell on 2010-08-14
sadly the thing is that stuff that made it possible to have full-blown login screen themes is deprecated since 9.10 because of changes in gnome. Gnome devs cut some, reworked some and old functionality is not there. You can modify some things like fonts, background, but you can't completely reskin whole login screen.
On a bright side - faster boot times.

---

### Post by a.a95 on 2010-11-14
But no window login button appears

---

### Post by Jonker on 2011-04-01
How doese it work with 10.10?

---

### Post by Rhys_Mayhew on 2011-05-14
> **Ganjafreak said:**
> K, I don't have that login window thing I have something called Login screen im on 9.04 jaunty can someone tell me how to do it now?

I mean i click screen one and click unlock asks for a pw entered and then nothing else happens.

im in exactly the same situation.

---

### Post by kaizen666 on 2011-05-22
No answers to this one yet? 
I would also like to change the login background. 
Anyone know the sequence for the command prompts on the terminal?

thanks :D

---

