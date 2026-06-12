---
title: "Xubuntu Oneiric Auto Login"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Chrissd on 2011-10-19
Hi all,

How do I enable auto login for Xubuntu now I've upgraded. It used to just do it. Now it sits on what I think is gdm and I have to click login. In users and groups it has a box that enabled login without password, but nowhere for auto login.

'cat /etc/gdm/custom.conf' shows the following 

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=chrissd
TimedLoginEnable=true
TimedLogin=chrissd
TimedLoginDelay=10
DefaultSession=xubuntu

```

Thanks

---

### Post by gsmanners on 2011-10-19
If by upgraded, you mean that you're using 11.10, then it might have switched into lightdm. The file for that is /etc/lightdm/lightdm.conf (with some options like this):

```
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
```

---

### Post by Chrissd on 2011-10-19
Hi,

It's changed appearance, but it's still not logging in. Can I not remove lightdm and go back to gdm?

Is that just a case of

```
aptitude purge lightdm
aptitude install gdm
```

Will everything be back to how it was after that?

Edit: Apparnetly not, I have to uninstall Xubuntu if I want to do that
```

sudo apt-get remove lightdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ibus-gtk libibus-1.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  lightdm xubuntu-default-settings xubuntu-desktop

```

---

### Post by gsmanners on 2011-10-19
Actually you can remove those packages with no real harm done (as long as you add them back before doing a dist-upgrade in the future).

---

### Post by Chrissd on 2011-10-19
I uninstalled those packages and now it just sits there with a black screen. :(

How do I fix this? :(

---

### Post by miegiel on 2011-10-19
> **Chrissd said:**
> I uninstalled those packages and now it just sits there with a black screen. :(

How do I fix this? :(

Assuming your GUI isn't loading when you boot. Boot into recovery mode, choose terminal with networking and reinstall *lightdm*, *gdm* or both.

---

### Post by bryncoles on 2011-10-19
Assuming it takes you to a command prompt  (i.e. the GUI isn't loading, as miegiel suggested)  you could also try typing ```
startx
```  ... or is there a space (start x) to start the GUI, and then reinstall lightdm, gdm as suggetsed.   

That might work!

---

### Post by breek on 2011-10-19
AFAIK autologin in lightdm works only on ubuntu, not on derivatives (i still don't understand why this can't be done with xfce, etc).
gdm is now gdm3 and auto log in doesn't work either.
i'm testing ubuntu studio 11.10 (xfce) on an external drive and if i solve some issue using *slim* with autologin maybe i'll upgrade on the daily-use pc (and of course i'll report what i did)

---

### Post by gsmanners on 2011-10-19
> **breek said:**
> AFAIK autologin in lightdm works only on ubuntu, not on derivatives

Wrong. Autologin works fine in Xubuntu.

---

### Post by breek on 2011-10-19
that would be good! how can i enable/disable it? i've tried creating lightdm.conf with autologin rule but doesn't work.
(on [beta 1 auto login](http://xubuntu.org/node/49) did't work and i missed this fix:))

---

### Post by jm.mico on 2011-10-19
> **gsmanners said:**
> Wrong. Autologin works fine in Xubuntu.

Not that fine. My file

/etc/lightdm/lightdm.conf

looks like:

```
[SeatDefaults]
autologin-user=jmico
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=xubuntu.desktop
```

and I have set it to not ask for password on login. Still I have to click on the lightdm to be able to login. 

I must say I installed originally ubuntu, and then xubuntu-desktop. I hate this unity new stuff.

But, please, how do I get autologin ???

Thnks!!

Juanma.

---

### Post by breek on 2011-10-19
i've now tried on a fresh installed xubuntu and there was no /etc/lightdm/lightdm.conf
i've created it like this
```

[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=your_user_name
autologin-user-timeout=0

```
and it works

---

### Post by razumok on 2011-10-19
> **breek said:**
> i've now tried on a fresh installed xubuntu and there was no /etc/lightdm/lightdm.conf
i've created it like this
```

[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=your_user_name
autologin-user-timeout=0

```
and it works

thanks breek, I just tried it and it works

---

### Post by jm.mico on 2011-10-20
> **razumok said:**
> thanks breek, I just tried it and it works

Here it works too. Thanks!

---

### Post by breek on 2011-10-23
in ubuntustudio user-session must be set as xfce
;)

---

### Post by scania_gti on 2011-10-24
And Kdm have autologin, not only Lightdm.
After some time autologin was gone, [found solution here]("http://wiki.sabayon.org/index.php?title=En:HOWTO:_Setting_Up_Autologin").

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-24
thanks for the tip!!  I wondered how to do this

---

### Post by Chrissd on 2011-10-31
Changed the Desktop which also acts as a file server to a rolling distribution. I've just not got the time to be trying to keep up with everything that changes on all the different computers I have. Laptops are still XUbuntu still since they can remain at the default settings! :D

---

### Post by peternz on 2011-11-27
Worked great thanks breek. Xubuntu 11.10 (alternate install).

> **breek said:**
> i've now tried on a fresh installed xubuntu and there was no /etc/lightdm/lightdm.conf
i've created it like this
```

[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=your_user_name
autologin-user-timeout=0

```
and it works

---

