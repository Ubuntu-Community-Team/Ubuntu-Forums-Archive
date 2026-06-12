---
title: "Daily-Live &quot;CD&quot; has no password window...."
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-15
Hello, 

I just installed Ubuntu 11.10 daily-live oneiric-desktop-amd64 for July 15, after checking SHA256 and burning the iso file to a DVD.  My PC has Nvidia Geforce 7300GT.

After booting, the login screen only has 3 items: my name, Guest Account and Other.  It has no password box at all. When I click on my name, the desktop shows just a reddish-purple color. Note that in Ubuntu 11.04, if I click on my name I will see a password box in order to authenticate myself and login.  During the installation, I did set up the userid & password windows for myself.

Any suggestions?  Thanks a lot for your help.

:confused:

---

### Post by cariboo on 2011-07-15
I just did a fresh install using todays daily live CD, I get the same thing. I saw someone had logged in clicking on other, then entering the user name and password, I tried it, and am now posting from my fresh Oneiric install.

---

### Post by mc4man on 2011-07-15
After setting up lightdm has been showing password box for first user fine (haven't tried adding a user where it still may be broke

As an aside, -  indicator-session (power button) seems to need some help (updated after 07/15 install

---

### Post by cariboo on 2011-07-15
I found that after I logged out after using other to log in, that lightdm work the way it should, clicking on my user name brought up a password box. 

Indicator-session on my system seems to have reverted to the same look as Natty

---

### Post by mc4man on 2011-07-15
Mine has taken a different path - duped choices
Doesn't quite seem to be replacing  indicator-me as of yet

---

### Post by iClouseau88 on 2011-07-15
Hello cariboo907 & mac4man,

First, I followed cariboo907's suggestion:

First, hit "Other" when login screen appears.  Next, enter user id (which later turned out to be wrong) and hit login.  Password box now appears, entered my password. I hit ENTER but then I got the original login screen without password box.

After reboot, I tried hitting Guest Account and used the same password as above. Unity loads! I took this golden opportunity to configure wired & wireless connections in NetworkManager.  By the way, the session indicator icons appear on the top right corner of the screen.

I was able to configure wired connection easily but wireless connection screen was grayed out for a while.  Eventually I succeeded in setting up wireless connection. 

Then NM crashed. "NM problem cannot be reported because of obsolete packages. Please upgrade the following and check if problem still occurs:
initramfs-tools, initramfs-tools-bin, isc-dhcp-client, isc-dhcp-common, libplymouth2, plymouth, mountall"

Went to Synaptic to upgrade the above packages and make sure "gedit" is installed.  Next I blacklisted "nouveau" and "lbm-nouveau", before activating nvidia-current".

While I was still logging in the Guest Account, there was a message that shows my user id to be "yy888" instead of the usual "tt888".  During installation I probably hit the wrong key.  Anyway, this gives a clue as to why I couldn't login as my name in the first place.

Finally, I  reboot in order to complete the upgrade of "initramfs-tools" and other packages. After loggin in, I update the system and everything is normal now. 

:)

PS: Is there a way to revert userid from "yy888" back to "tt888"?

---

### Post by cariboo on 2011-07-15
It would probably be easier to create a new user, then to change the username.

---

### Post by mc4man on 2011-07-16
> **cariboo907 said:**
> It would probably be easier to create a new user, then to change the username.
Atm  - a new user will get the same deal when logging in - no box.
Using 'other' one time will then provide a password box for future logins

Also any new user account will get the wrong shell in the gnome-terminal, solution post 3 here
[http://ubuntuforums.org/showthread.php?t=1804555](http://ubuntuforums.org/showthread.php?t=1804555)

---

