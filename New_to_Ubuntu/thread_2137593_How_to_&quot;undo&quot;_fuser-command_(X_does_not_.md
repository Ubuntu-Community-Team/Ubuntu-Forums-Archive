---
title: "How to &quot;undo&quot; fuser-command? (X does not start, CUI is OK)"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by tortilla on 2013-04-21
[FONT=arial]Hi,
originally had some locking problems with my system (ubuntu 12.04, 64 bit) and found the following command, and without more thinking just applied it:
[/FONT]
[FONT=arial]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
[/FONT]
[FONT=arial]
(like was recommended at: [/FONT]http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem)

Then got those problems with login in from GUI. So my problem is:
- login GUI window shows correct
- accepts password normally
BUT then shows some rows very quickly and does show again the login  window 
(password IS ok because tried how it would show for wrong pw and  for it gave error msg).

ctrl-alt-F1 and login via command line is OK.


Finally later on some one informed that the first command is not good and:
[I]The process "fuser" will access the communication with the graphics card, and possibly eliminate it. If you plan to execute this command first type (ctrl+alt+F2) and execute it in a different tty session, so your graphics is not changed while it is used by your Xorg session.
[/I]
and elsewhere found that the original command has been OK earlier, but not any more for 12.04 or later releases.

There are a lot of question pages related to that similar problem but so far none of those have helped:
- rename .Xauthority
- change its ownership (if owned by root)
- remove .Xauthority
- re-installed lightdm, tried gdm instead of it. 
- re-installed graphics drivers
- changed pw
- added via CUI another user and tried for "him"
- rebooted
- and many others many times

But no way.

So my question is that if I have applied that WRONG command to 12.04:
[FONT=arial]sudo fuser -cuk /var/lib/dpkg/lock; [/FONT]

The what that does impact to graphics? 
how I could "undo" impact of it? what I should re-install and in which order?
or is there some magic command that I don't just know?

---

### Post by steeldriver on 2013-04-21
The only reason I can think it would impact graphics is if you killed an in-progress update of a driver / xserver / display manager package - have you tried doing a 'fix broken packages' with

```
sudo apt-get install -f
```

---

### Post by tortilla on 2013-04-29
> **steeldriver said:**
> The only reason I can think it would impact graphics is if you killed an in-progress update of a driver / xserver / display manager package - have you tried doing a 'fix broken packages' with

```
sudo apt-get install -f
```

unfortunately did not help :(

---

### Post by mansonfan78 on 2013-04-29
I had a similar problem once when the xserver got updated, don't remember how I fixed it.  You could try reinstalling/reconfiguring the xserver and/or video driver.  I believe it would be "xserver-xorg-core" and maybe "xserver-common".  And the "fix broken packages" never worked for me either.

---

