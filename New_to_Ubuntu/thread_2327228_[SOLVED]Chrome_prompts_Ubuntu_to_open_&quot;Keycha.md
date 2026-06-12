---
title: "[SOLVED]Chrome prompts Ubuntu to open &quot;Keychain&quot; everytime I log into a webpage"
date: 2016-06-08
forum: New to Ubuntu
---

### Post by Karl_Hungus on 2016-06-08
OK,

So the issue is that every time I open Google Chrome and log into ANYTHING at all Ubuntu prompts this "Keychain".



Is there anyway I could remove it? I don't want to use a "KeyChain" and if I did I would search for a super secure one. (can anyone recommend a good secure Key Chain service?)

How can I stop Ubuntu from prompting the built-in "KeyChain"?


Thanks in advance.

---

### Post by Zanden on 2016-06-09
Found this article on askubuntu maybe it can help you [http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot](http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot)

---

### Post by grahammechanical on 2016-06-09
I do not have this problem. But then again I do not have automatic login to the desktop. When I log into Ubuntu my password unlocks the keyring at the same time. I actually do not use Gnome keyring. Not specifically. I do not store passwords on my computer. I suppose that my user password is stored in gnome-keyring. And certain certificates authenticating software such a Chrome are stored in gnome-keyring but by and large, I am not in the habit of storing passwords on my computer. 

Look at this Ubuntu Security team FAQ under Software - gnome-keyring.

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

This is what the Gnome developers say about gnome-keyring.

[https://wiki.gnome.org/action/show/Projects/GnomeKeyring?action=show&redirect=GnomeKeyring](https://wiki.gnome.org/action/show/Projects/GnomeKeyring?action=show&redirect=GnomeKeyring)

And this is an earlier discussion about this problem on this forum.

[http://ubuntuforums.org/showthread.php?t=1466519](http://ubuntuforums.org/showthread.php?t=1466519)

In present day Ubuntu we go to System Settings>Security & Privacy>Password Settings. Ease of use and security are mutually exclusive. 

Regards.

---

### Post by Zanden on 2016-06-09
Are you logging into your google account in chrome?

---

### Post by CantankRus on 2016-06-09
To turn off google-chrome asking to save passwords when you log into a site,
go to **chrome://settings**  scroll to bottom ...click on **+Show advanced settings**
Untick "Offer to save your web passwords".

---

### Post by Karl_Hungus on 2016-06-13
> **Zanden said:**
> Are you logging into your google account in chrome?

Nope, I am not logging into a google account on the browser.

---

### Post by Karl_Hungus on 2016-06-13
> **CantankRus said:**
> To turn off google-chrome asking to save passwords when you log into a site,
go to **chrome://settings**  scroll to bottom ...click on **+Show advanced settings**
Untick "Offer to save your web passwords".

Thank you this seems to have been the solution.

---

