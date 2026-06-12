---
title: "every boot i should re-type the wifi password"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by akkad on 2008-08-25
i have set my wireless network with a static IP address, where every boot when i try to access the internet i cant, but when i open the gnome network manager and select my wireless gateway then re-type the password again at that point the internet get back to work properly, so why is that and how to do it once rather than every boot???

---

### Post by anewguy on 2008-08-25
Do you have the PAM keyring manager package installed?  I think it came by default with 8.04, but not sure about releases prior to that.  Once that is installed, when you first set up your network connection it should also ask for a keyring password.  Enter your logon password and it should remember the key for your network and also avoid having the keyring manager ask for it's password.

---

### Post by akkad on 2008-08-25
i do have keyring, in fact this problem is appear only when i set my IP statically where when using DNS i have no problems, but so far i do need to set a static IP.

---

### Post by Victormd on 2008-08-25
Do you need to type the password for the router (WEP key) or the keyring?
If it's the keyring, the easiest thing is to simply set the keyring password to blank (the keyring password can be different from your user password).

This will increase vulnerability, BUT, for anyone to get to your keyring, they'll need to know your user password, so you're still protected by your user password. If your keyring password is the same as your user password, the security level is the same as leaving the keyring password blank (someone please correct me if this is wrong).

If it's the WEP key, then have the keyring store it and then do the above.

---

### Post by anewguy on 2008-08-25
So, not to be stupid (it isn't the first time!!) - but ---  is it asking for the keyring manager password or your network connection key?

I suppose you could try deleting the default keyring, then set up your network connection again (Connect to another wireless network) and then see if it wants to set up the keyring password.

I'm a little stumped right now, because normally this works as long as the keyring manager is installed and THEN you set up your network connection.

As long as you make the keyring password the same as your logon password it shouldn't ask for the keyring password either, but it also means someone would need to know your password if they used a different id to log on to your computer before they could access the keyring.

---

### Post by Victormd on 2008-08-25
> **anewguy said:**
> As long as you make the keyring password the same as your logon password it shouldn't ask for the keyring password either

This is how I had my setup (user password = keyring password) and it always asked for the keyring password. Once I set the keyring password to null, all was Ok. My system is setup to auto-logon and that could be the reason why the keyring kept asking for the password, I'm not sure.

---

### Post by akkad on 2008-08-25
plz take a look at the screenshot, it is not about keyring.

---

### Post by Victormd on 2008-08-25
Ok, so it's the WEP Key. I'm not at home so it'll be a bit difficult to give step-by-step instructions (using windows here). When I get home I'll post back with a possible solution (I'm going to try to set up my wireless using a static IP to see what happens)...

---

### Post by Victormd on 2008-08-25
Akkad, go to:
```
cd ~/.gnome2/keyring
```
and list the files. There should be a login.keyring (this is what I have) or default.keyring file. Open the file
```
sudo gedit login.keyring
```
and there should be a section like this:
> [1]
item-type=0
display-name=Passphrase for wireless network damasceno
secret=**[COLOR="Red"]your wep key here[/COLOR]**
mtime=1217391979
ctime=1217391979

[1:attribute0]
name=essid
type=string
value=**[COLOR="Red"]your wireless network name here[/COLOR]**
Check to see if these values match your wireless configuration

Or, you can go to APPLICATIONS>ACCESSORIES>PASSWORDS AND ENCRYPTION KEYS, go to the PASSWORDS tab and check the properties for your wireless there, copy and delete the existing passphrase to create a new one and see if that helps...

I did not run into the same problem as you when I switched to static IP so I did not get a chance to check whether my WEP key was requested. Actually, after I switched, I could not connect at all, and when I restarted, my computer locked up and I had to disable my wireless to login again. If in doubt, wait to see if someone who has had this comes in to help...

---

