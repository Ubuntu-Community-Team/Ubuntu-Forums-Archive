---
title: "Stop asking me for password... how?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by TopFan on 2008-11-13
I'd prefer not to be asked for my password every time I start my computer or wake it up from suspend. Is there any way to stop this?

---

### Post by ad_267 on 2008-11-13
> **TopFan said:**
> I'd prefer not to be asked for my password every time I start my computer or wake it up from suspend. Is there any way to stop this?

You can go to System - Administration - Login Window and I can't remember which tab it is but one allows you to set a user to automatically log in as.

---

### Post by eternalnewbee on 2008-11-13
> You can go to System - Administration - Login Window and I can't remember which tab it is but one allows you to set a user to automatically log in as.
**Main Menu > System > Administration > Login Window > Security** tab, and tick the box **Enable Automatic Login**. Don't forget to select your username under **User**.

---

### Post by ad_267 on 2008-11-13
> **eternalnewbee said:**
> **Main Menu > System > Administration > Login Window > Security** tab, and tick the box **Enable Automatic Login**. Don't forget to select your username under **User**.

Thanks, I'm not lazy, just not running Gnome at the moment :)

---

### Post by TopFan on 2008-11-13
I've done this and it still asks me for my password. Any other ideas?

On start up the computer ask for my password so it can access the default keyring. Is there any way of allowing permanent access to the keyring?

---

### Post by Rodney9 on 2008-11-22
> **eternalnewbee said:**
> **Main Menu > System > Administration > Login Window > Security** tab, and tick the box **Enable Automatic Login**. Don't forget to select your username under **User**.

I have done the above and I can login without a password when I do a full startup, but when I wakeup from sleep it asks for the password, how do I stop this ?, I need to login automatically all the time.

---

### Post by dBuster on 2008-11-29
With the auto-login enabled it was working fine until the most recent kernel update and now the auto login is not working either way either cold boot or resume from hibernate.  

Is this a known issue or something new?  Do I need to uncheck and then boot then check it again and reboot for the settings to update?

Thanks in advance.  This works like a charm when it does...:confused:

---

### Post by SunnyRabbiera on 2008-11-29
Typically auto login is a BAD idea, especially if you run administrative stuff.
I know its annoying to type in your password all the time, especially when you are the only user BUT it is a necessary evil.
Wonder why windows is so insecure?
Auto login, sure it makes things "easier" but it makes things less secure.

---

### Post by longfeltwant on 2009-07-13
I couldn't find any current information on how to fix this. I'm posting here my solution.

In my case my Ubuntu netbook is in my car for collecting GPS and OBD information. I specifically want to lower my security in favor if ease of use, because I need to quickly open it and start and stop software. Also battery life is an issue, so I can't avoid sleeping it. The current UI in Ubuntu, as far as I can tell, allows you to set up an automatic login when you start up, but not when you wake up from sleep.

People who want to do this likely already understand the security implications.

* Right-click on the Applications menu and chose Edit Menus
* Select System Tools and make sure that Configuration Editor item is checked
* Choose Applications -> System Tools -> Configuration Editor
* Select apps -> gnome-power-manager -> lock
* As you want, uncheck hibernate or suspend or whatever you want

---

### Post by spantch101 on 2010-08-02
thanks this was greatly appreciated... started to **** me off everytime the screen went black i had to type in my password... now if you could choose to be root at the install and not ask for a password everytime you do anything..

---

### Post by donkyhotay on 2010-08-02
> **spantch101 said:**
> thanks this was greatly appreciated... started to **** me off everytime the screen went black i had to type in my password... now if you could choose to be root at the install and not ask for a password everytime you do anything..

<shudders> Thats the #1 flaw in windows and is the reason windows is so easy to infect. You don't *ever* want to login as root, it creates so many problems forum rules forbid answering that question whenver it's asked.

---

### Post by Elfy on 2010-08-02
and with that I will close this old resurrected thread

---

