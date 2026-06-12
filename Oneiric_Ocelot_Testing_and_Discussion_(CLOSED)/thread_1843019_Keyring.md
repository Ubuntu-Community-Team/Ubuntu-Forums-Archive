---
title: "Keyring"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by c0stalkayk3r on 2011-09-12
Did a fresh (re)install of 11.10 yesterday and it seems now that Keyring keeps popping up asking for me to authenticate. I hated this is older version and as I'm the only one who uses this computer I usually just put in no password. I have my Ubuntu set to auto login and I hate having to "Login" anyway. Now it seems it pops up when I launch Google Chrome and there's no way of turning it off. Is there a setting somewhere for this or what package does it belong to so I can file a bug report.

---

### Post by haqking on 2011-09-12
> **c0stalkayk3r said:**
> Did a fresh (re)install of 11.10 yesterday and it seems now that Keyring keeps popping up asking for me to authenticate. I hated this is older version and as I'm the only one who uses this computer I usually just put in no password. I have my Ubuntu set to auto login and I hate having to "Login" anyway. Now it seems it pops up when I launch Google Chrome and there's no way of turning it off. Is there a setting somewhere for this or what package does it belong to so I can file a bug report.
 
make it a blank password for the keyring (not recommended) or turn off autologin.

Your keyring password should be unlocked automatically when you login to your system, however if you have set your system to auto-login then you get the annoying keyring prompt.  
This can be removed see here:

[http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/)

However it is better to remove auto-login from the login screen preferences and actually physcially login to your system thus removing this message.

A blank password is never recommended, people often assume it doesnt matter if they are the only user of the system, but it is not just about that, scripts in your browser or services can then run under your admin account without prompt for authentication due to blank password.

See here about why sudo is supported in the canonical model and the root account is disabled by default, it is possible to enable root and possible to have a blank password but neither are recommended.

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Have fun

Regards

haqking

---

### Post by c0stalkayk3r on 2011-09-12
> **haqking said:**
> you can make the keyring pasword the same as the login password.  Or make a blank password for the keyring (not recommended) or turn off autologin.

Your keyring password should be unlocked automatically when you login to your system, however if you have set your system to auto-login then you get the annoying keyring prompt.  
This can be removed see here:

[http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/)

However it is better to remove auto-login from the login screen preferences and actually physcially login to your system thus removing this message.

A blank password is never recommended, people often assume it doesnt matter if they are the only user of the system, but it is not just about that, scripts in your browser or services can then run under your admin account without prompt for authentication due to blank password.

See here about why sudo is supported in the canonical model and the root account is disabled by default, it is possible to enable root and possible to have a blank password but neither are recommended.

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Have fun

Regards

haqking

Thanks for the info. I get what your saying about not keeping password blank, but having to "login" to keyring defeats the purpose of auto login IMHO. I'll try the steps listed in that link and hope that helps.

Thanks!

---

