---
title: "[SOLVED] wireless router"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-24
I am trying to get another ubuntu machine on the internet, via connecting wirelessly to a linksys wirelessg broadband adapter, but when i try to connect to the network, it asks for a password that my dad set up and he doesnt remember it, so how can i change/remove the password?

---

### Post by teeleef on 2008-08-24
I'd consider pressing the small reset button and re-configuring the router again.
All then should be well :)


Teeleef

---

### Post by wolfen69 on 2008-08-24
see [this]("http://ubuntulinuxhelp.com/recover-your-forgotten-password-in-linux/"). but remember, instead of passwd username, you would do smbpasswd username

---

### Post by wolfen69 on 2008-08-24
> **teeleef said:**
> I'd consider pressing the small reset button and re-configuring the router again.
All then should be well :)


Teeleef

i think he meant the network password, not the password to get into the router. please clarify.

---

### Post by Kevbert on 2008-08-24
Removed (double post).

---

### Post by Kevbert on 2008-08-24
If you need to get the password for connecting to the router, this is stored by the router.  What you need to do is take a look at the router manual as you need some info from there.
To access the router you need to connect to it with your PC via an ethernet cable (assuming you have a network connection on your PC).  Open a browser and enter something like [http://192.168.0.1](http://192.168.0.1) (the exact address will be in the manual).  You'll then be used for a username and password (defaults are normally admin and password).  Once you've done this you should be able to find the passkey that you require (probably in wireless settings).
If you reset the router all setting will be reset to default values (including the passkey).
If you need additional info please post the router model and who supplied it (internet provider as they may have their own settings).

---

### Post by hyperhopper on 2008-08-24
Umm, I'm probably going to have to reset it because it is  a linksys model # WRT54GS version 6 wireless g broadband adapter 2.4 ghz. i dont have the manual or anything, and I am wondering, Kevbert, what is the default passkey?

---

### Post by hyperhopper on 2008-08-24
> **wolfen69 said:**
> i think he meant the network password, not the password to get into the router. please clarify.

I did in fact mean the password to connect to the network, not the router pass.

---

### Post by Kevbert on 2008-08-25
Ok. You can download the user manual [[COLOR="Red"]here[/COLOR]]("http://www.scribd.com/doc/200742/Linksys-WRT54G-User-Guide").  The passkey is specific to your personal router and you should not let anyone know this.  The address you need to put into the browser is [http://192.168.1.1](http://192.168.1.1) and the username should be empty (nothing, zilch),  The password is admin.  If the modem has been customized by your service provider then you'll need to contact them for this information as the username and password will have been changed (and even if you do a reset this will not change).  From there you should be able to find out the passkey (used to log on to wireless) or reset it.
I recommend that you change the username and password, for security reasons, as anyone who can see your wireless can change the routers' settings.  If you forget them you can always reset the router (hold in the reset button on the back of the router for 30 seconds) so that it goes back to the factory defaults (detailed earlier in this post).

---

### Post by hyperhopper on 2008-08-25
Help!!!!!!!!!!!
Emergency!!!!! I did the hard reset for 30 seconds, and now there is no internet on the computers connected to it! Family is killing me!!! The internet is going to modem but it seems to be stuck at the router!!! How tdo i get it back????

---

### Post by hyperhopper on 2008-08-25
fending....off....zombie....internet...addicts....bumpbumpbump!

---

### Post by Kevbert on 2008-08-25
Hi. You only need to perform a hard reset if there's a serious problem (eg the router locks up).  Hopefully you can connect the router via an ethernet cable to your computer network connection.  Open your browser and enter [http://192.168.1.1](http://192.168.1.1) then use nothing (blank, zilch) for the username and admin for the password.  Please remember that the passkey, pass phrase or whatever has to be the same on every PC and the router for everything to work and is case sensitive.

---

### Post by hyperhopper on 2008-08-25
Lol didnt work, i just unplugged all comuter-related appliances tor a minute and then everything worked, thanks anyways!!! LOL :KS

---

### Post by ingeva on 2008-08-25
> **hyperhopper said:**
> Lol didnt work, i just unplugged all comuter-related appliances tor a minute and then everything worked, thanks anyways!!! LOL :KS

Nice that you made it work, but I've had several routers (Cisco Topcom and D-link) and they all used Admin for username and had a blank default password.

Of course, this is needed if you want to set the WPA passkey.

---

### Post by nothingspecial on 2008-08-25
Maybe this will help with your other 2 issues, hope so :)

---

