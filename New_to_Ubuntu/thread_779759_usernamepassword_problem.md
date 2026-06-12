---
title: "username/password problem"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-03
Hello,

I used Wubi to set up Ubuntu 8.04. I have a dual boot system booting 98SE and 2000Pro. I set it up from 98SE.

Everything seemed to work, Ubuntu loaded up, the computer rebooted, came up to the Ubuntu desktop and asked for a username and password.

Wubi asked for a password and I used "me" as the password. It did not as for a username. 

I have tried various and sundry things with no success, just wrong username or password error.

I am a long time windoze tech, but totally new to linux. Looking for answers to this before starting a new topic, I saw references to going to grub and using various commands and finding a boot menu with grub.

When I boot, first I get a choice of win2000 or 98, I choose 98 and I get a choice of windows or ubuntu. I choose Ubuntu and it boots to the desktop. Where is grub?

Any and all help greatly appreciated. Thank you.

---

### Post by frup on 2008-05-03
wubi may not use grub.

I could help you easily if it wasn't a wubi system.

---

### Post by Aearenda on 2008-05-03
The user name and password needed by Ubuntu at the main login screen has nothing to do with Grub. Grub is the equivalent of NTLDR for Windows XP, only much more flexible. What you need here is the equivalent of the Windows username and password. These are usually set on the first Wubi setup screen.

Have you tried using the same username as you have on Windows, and 'me' as the password?

---

### Post by Aearenda on 2008-05-03
By the way, you can get into the Grub menu if you press 'ESC' when the screen shows 'Press ESC to enter Menu' (or something like that - it goes past too quickly to read on my system) just after selecting Ubuntu instead of Windows 98. If you press down-arrow on the menu, you can select the 'recovery mode' startup. Lots of text scrolls by, then you should be able to choose 'Drop to root shell prompt' from the choices offered, and then use this command to discover what username was used at installation: ```
grep 1000 /etc/passwd
```
The first word on the output from this is the username you should log on to. Here's mine: ```
system:x:1000:1000:System Administrator,,,:/home/system:/bin/bash
```
So my username was 'system'.
Then press CTRL and d to exit and choose 'resume normal boot' from the menu that appears.
When the logon screen appears, you type the username, press Enter, then type your password, and press Enter.

If you are still stuck, repeat the recovery mode startup, go to the root shell prompt, and enter ```
passwd *username*
``` where *username* is the user name you just discovered. Enter a new 'UNIX' (it means Linux) password twice, and then resume the normal boot. This time, you should be able to log on!

---

### Post by wordmaster on 2008-05-03
Thank you very much for your help. Got the username, set the password, it worked! Your help is much appreciated.

---

### Post by Aearenda on 2008-05-03
I'm glad it's working for you now!

---

